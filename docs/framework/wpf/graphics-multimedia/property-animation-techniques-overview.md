---
title: 屬性動畫技術概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
ms.openlocfilehash: 0b4bf6d4963f32ad83f762fce73c805197ff9c9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181849"
---
# <a name="property-animation-techniques-overview"></a>屬性動畫技術概觀
本主題說明建立屬性動畫的不同方法︰分鏡腳本、本機動畫、時鐘與每一畫面格動畫。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該要熟悉[動畫概觀](animation-overview.md)中所述的基本動畫功能。  
  
<a name="summary"></a>
## <a name="different-ways-to-animate"></a>建立動畫的不同方式  
 因為有許多建立動畫屬性的不同案例，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了數種建立動畫屬性的方法。  
  
 針對每一種方法，下表會指出方法是否能用於每個執行個體、樣式、控制項範本或資料範本；它是否能用於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，以及該方法是否能讓您以互動方式控制動畫。  「每個執行個體」指的是將動畫或分鏡腳本直接套用至物件之執行個體，而非樣式、控制項範本或資料範本的技術。  
  
|動畫技術|案例|支援 XAML|以互動方式控制|  
|-------------------------|---------------|-------------------|--------------------------------|  
|分鏡腳本動畫|每個實例<xref:System.Windows.Style>， <xref:System.Windows.Controls.ControlTemplate>，<xref:System.Windows.DataTemplate>|是|是|  
|本機動畫|每個執行個體|否|否|  
|時鐘動畫|每個執行個體|否|是|  
|每一畫面格動畫|每個執行個體|否|N/A|  
  
<a name="storyboard_animations"></a>
## <a name="storyboard-animations"></a>分鏡腳本動畫  
 如果要在<xref:System.Windows.Media.Animation.Storyboard>中定義和應用動畫[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，在 動畫啟動後以對話模式控制動畫、創建複雜的動畫樹或在<xref:System.Windows.Style>中<xref:System.Windows.Controls.ControlTemplate>設置動畫或 。 <xref:System.Windows.DataTemplate> 要對<xref:System.Windows.Media.Animation.Storyboard>物件進行動畫處理，它必須是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>，或者必須用它來設置 或<xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkContentElement>。 如需詳細資訊，請參閱[分鏡腳本概觀](storyboards-overview.md)。  
  
 是<xref:System.Windows.Media.Animation.Storyboard>一種特殊類型的容器<xref:System.Windows.Media.Animation.Timeline>，它提供其包含的動畫的目標資訊。 要使用 進行<xref:System.Windows.Media.Animation.Storyboard>動畫處理，可以完成以下三個步驟。  
  
1. 聲明<xref:System.Windows.Media.Animation.Storyboard>一個和一個或多個動畫。  
  
2. 使用<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>附加屬性指定每個動畫的目標物件和屬性。  
  
3. （僅限代碼）定義<xref:System.Windows.NameScope>或<xref:System.Windows.FrameworkContentElement><xref:System.Windows.FrameworkElement>的 。 註冊要使用 該<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>進行動畫處理的物件的名稱。  
  
4. 開始<xref:System.Windows.Media.Animation.Storyboard>。  
  
 開始<xref:System.Windows.Media.Animation.Storyboard>將動畫應用於它們為它們設置動畫並啟動它們的屬性。 開始有<xref:System.Windows.Media.Animation.Storyboard>兩種方法：可以使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A><xref:System.Windows.Media.Animation.Storyboard>類提供的方法，也可以使用<xref:System.Windows.Media.Animation.BeginStoryboard>操作。 動畫[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]化的唯一方法是使用操作<xref:System.Windows.Media.Animation.BeginStoryboard>。 操作<xref:System.Windows.Media.Animation.BeginStoryboard>可以在<xref:System.Windows.EventTrigger>屬性<xref:System.Windows.Trigger>或 中使用。 <xref:System.Windows.DataTrigger>  
  
 下表顯示了支援每個<xref:System.Windows.Media.Animation.Storyboard>開始技術的不同位置：每個實例、樣式、控制項範本和資料範本。  
  
|開始分鏡腳本的方法…|每個執行個體|Style|控制項範本|資料範本|範例|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>和<xref:System.Windows.EventTrigger>|是|是|是|是|[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>和屬性<xref:System.Windows.Trigger>|否|是|是|是|[在屬性值變更時觸發動畫](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>和<xref:System.Windows.DataTrigger>|否|是|是|是|[操作說明︰在資料變更時觸發動畫](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法|是|否|否|否|[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 有關<xref:System.Windows.Media.Animation.Storyboard>物件的詳細資訊，請參閱[分鏡腳本概述](storyboards-overview.md)。  
  
## <a name="local-animations"></a>本機動畫  
 本地動畫提供了一種為任何<xref:System.Windows.Media.Animation.Animatable>物件的依賴項屬性設置動畫的便捷方法。 當您想要將單一動畫套用至屬性，且您不需要在動畫啟動後以互動方式控制動畫時，請使用本機動畫。 與動畫<xref:System.Windows.Media.Animation.Storyboard>不同，本地動畫可以為不與<xref:System.Windows.FrameworkElement>或 關聯的物件設置動畫。 <xref:System.Windows.FrameworkContentElement> 您也不必為這種類型的動畫定義 。 <xref:System.Windows.NameScope>  
  
 本機動畫只能在程式碼中使用，且無法在樣式、控制項範本或資料範本中定義。 本機動畫啟動後，您無法以互動方式控制它。  
  
 若要使用本機動畫建立動畫，請完成下列步驟。  
  
1. 創建<xref:System.Windows.Media.Animation.AnimationTimeline>物件。  
  
2. 使用要<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>設置動畫的物件的方法將 應用<xref:System.Windows.Media.Animation.AnimationTimeline>到指定的屬性。  
  
 下面的示例演示如何為 的寬度和背景顏色設置<xref:System.Windows.Controls.Button>動畫。  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>時鐘動畫  
 當<xref:System.Windows.Media.MediaPlayer.Clock%2A>您想要在不使用 動畫的情況下使用物件<xref:System.Windows.Media.Animation.Storyboard>，並且希望在動畫啟動後創建複雜的計時樹或互動式控制動畫時，請使用物件。 可以使用 Clock 物件為任何<xref:System.Windows.Media.Animation.Animatable>物件的依賴項屬性設置動畫。  
  
 不能直接使用<xref:System.Windows.Media.Animation.Clock>物件在樣式、控制項範本或資料範本中設置動畫。 （動畫和計時系統實際上使用<xref:System.Windows.Media.Animation.Clock>物件在樣式、控制項範本和資料範本中設置動畫，但它必須從 為您創建這些<xref:System.Windows.Media.Animation.Clock>物件。 <xref:System.Windows.Media.Animation.Storyboard> 有關物件和<xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.Clock>物件之間的關係的詳細資訊，請參閱[動畫和計時系統概述](animation-and-timing-system-overview.md)。  
  
 要將單個<xref:System.Windows.Media.Animation.Clock>應用於屬性，請完成以下步驟。  
  
1. 創建<xref:System.Windows.Media.Animation.AnimationTimeline>物件。  
  
2. 使用<xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A>的方法<xref:System.Windows.Media.Animation.AnimationTimeline>創建 。 <xref:System.Windows.Media.Animation.AnimationClock>  
  
3. 使用要<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A>設置動畫的物件的方法將 應用<xref:System.Windows.Media.Animation.AnimationClock>到指定的屬性。  
  
 下面的示例演示如何創建 並將其<xref:System.Windows.Media.Animation.AnimationClock>應用於兩個類似的屬性。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 若要建立計時樹狀結構並使用它來建立屬性的動畫，請完成下列步驟。  
  
1. 使用<xref:System.Windows.Media.Animation.ParallelTimeline><xref:System.Windows.Media.Animation.AnimationTimeline>和 物件創建計時樹。  
  
2. 使用<xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A>根<xref:System.Windows.Media.Animation.ParallelTimeline><xref:System.Windows.Media.Animation.ClockGroup>的  
  
3. 反覆運算 和<xref:System.Windows.Media.Animation.ClockGroup.Children%2A><xref:System.Windows.Media.Animation.ClockGroup>應用其子<xref:System.Windows.Media.Animation.Clock>物件。 對於每個<xref:System.Windows.Media.Animation.AnimationClock>子級，請使用<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A>要設置動畫的物件的方法將 應用<xref:System.Windows.Media.Animation.AnimationClock>到指定的屬性  
  
 如需時鐘物件的詳細資訊，請參閱[動畫和計時系統概觀](animation-and-timing-system-overview.md)。  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>每一畫面格動畫：略過動畫和計時系統  
 當您需要完全略過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統時，使用此方法。 此方法的一個案例為物理動畫，其中動畫的每個步驟需要根據最後一組物件互動來重新計算物件。  
  
 每一畫面格動畫無法在樣式、控制項範本或資料範本中定義。  
  
 要逐幀設置動畫，請註冊包含要設置動畫<xref:System.Windows.Media.CompositionTarget.Rendering>的物件的物件的事件。 系統會針對每個畫面呼叫一次此事件處理常式方法。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 每次封送處理視覺化樹狀結構中已保存的轉譯資料，跨越到組合樹狀結構時，就會呼叫您的事件處理常式方法。  
  
 在事件處理常式中，執行動畫效果所需的任何計算，並使用這些值設定您想要建立動畫的物件屬性。  
  
 要獲取當前幀的表示時間，<xref:System.EventArgs>與此事件關聯的可以強制轉換為<xref:System.Windows.Media.RenderingEventArgs>，該<xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>屬性可用於獲取當前幀的渲染時間。  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Media.CompositionTarget.Rendering> 頁面。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [分鏡腳本概觀](storyboards-overview.md)
- [動畫和計時系統概觀](animation-and-timing-system-overview.md)
- [相依性屬性概觀](../advanced/dependency-properties-overview.md)
