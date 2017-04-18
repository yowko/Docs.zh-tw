---
title: "建立屬性動畫技術概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動畫, 屬性, 方法"
  - "屬性, 動畫的方法"
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 建立屬性動畫技術概觀
本主題說明建立屬性動畫的各種方法：腳本、本機動畫、時鐘以及單格動畫。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要條件  
 若要了解本主題，您應該熟悉[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)中說明的基本動畫功能。  
  
<a name="summary"></a>   
## 各種建立動畫的方法  
 因為屬性動畫會在許多不同的情況下建立，所以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會提供多種建立屬性動畫的方法。  
  
 下表指出每種方法是否適用於個別執行個體 \(Per\-Instance\)、樣式、控制項樣板或資料範本，是否適用於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，以及是否可以讓您以互動方式控制動畫。  「個別執行個體」是指將動畫或腳本直接套用至物件執行個體 \(而非樣式、控制項樣板或資料範本\) 的技術。  
  
|動畫技術|案例|支援 XAML|可以用互動方式控制|  
|----------|--------|-------------|---------------|  
|腳本動畫|個別執行個體、<xref:System.Windows.Style>、<xref:System.Windows.Controls.ControlTemplate>、<xref:System.Windows.DataTemplate>|是|是|  
|本機動畫|個別執行個體|否|否|  
|時鐘動畫|個別執行個體|否|是|  
|單格動畫|個別執行個體|否|N\/A|  
  
<a name="storyboard_animations"></a>   
## 腳本動畫  
 當您想要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中定義並套用動畫、在動畫開始之後以互動方式進行控制、建立複雜的動畫樹狀結構，或者在 <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> 或 <xref:System.Windows.DataTemplate> 中建立動畫時，請使用 <xref:System.Windows.Media.Animation.Storyboard>。  要以 <xref:System.Windows.Media.Animation.Storyboard> 建立動畫的物件，必須是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>，或者必須用來設定 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>。  如需詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 <xref:System.Windows.Media.Animation.Storyboard> 是一種特殊的容器 <xref:System.Windows.Media.Animation.Timeline>，提供所含動畫的目標資訊。  若要以 <xref:System.Windows.Media.Animation.Storyboard> 建立動畫，請完成下列三個步驟。  
  
1.  宣告 <xref:System.Windows.Media.Animation.Storyboard> 以及一個或多個動畫。  
  
2.  使用 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 和 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> [附加屬性](GTMT)指定每個動畫的目標物件和屬性。  
  
3.  \(限程式碼\) 定義 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 的 <xref:System.Windows.NameScope>。  註冊物件名稱，以該 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 建立動畫。  
  
4.  開始 <xref:System.Windows.Media.Animation.Storyboard>。  
  
 開始 <xref:System.Windows.Media.Animation.Storyboard> 會將動畫套用至要建立動畫的屬性並啟動。  有兩種方法可以開始 <xref:System.Windows.Media.Animation.Storyboard>：您可以使用 <xref:System.Windows.Media.Animation.Storyboard> 類別提供的 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法，或使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作。  在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，唯一建立動畫的方法是使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 動作。<xref:System.Windows.Media.Animation.BeginStoryboard> 動作可用於 <xref:System.Windows.EventTrigger>、<xref:System.Windows.Trigger> 屬性或 <xref:System.Windows.DataTrigger> 中。  
  
 下表顯示每種 <xref:System.Windows.Media.Animation.Storyboard> 開始技術適用的不同位置：個別執行個體、樣式、控制項樣板及資料範本。  
  
|開始使用腳本的方法…|個別執行個體|樣式|控制項樣板|資料範本|範例|  
|----------------|------------|--------|-----------|----------|--------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和 <xref:System.Windows.EventTrigger>|是|是|是|是|[使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和屬性 <xref:System.Windows.Trigger>|否|是|是|是|[當屬性值變更時觸發動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和 <xref:System.Windows.DataTrigger>|否|是|是|是|[How to: Trigger an Animation When Data Changes](http://msdn.microsoft.com/zh-tw/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法|是|否|否|否|[使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 如需 <xref:System.Windows.Media.Animation.Storyboard> 物件的詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
## 本機動畫  
 本機動畫提供便利的方式，來以任何 <xref:System.Windows.Media.Animation.Animatable> 物件的[相依性屬性](GTMT)建立動畫。  當您想要將單一動畫套用至屬性，而且不需要在動畫開始之後以互動方式控制時，請使用本機動畫。  不像 <xref:System.Windows.Media.Animation.Storyboard> 動畫，本機動畫會以與 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 無關的物件建立物件的動畫。  您也不需要針對此型別的動畫定義 <xref:System.Windows.NameScope>。  
  
 本機動畫只能在程式碼中使用，並且不能在樣式、控制項樣板或資料範本中定義。  本機動畫在開始之後，就不能以互動方式控制。  
  
 若要使用本機動畫建立動畫，請完成下列步驟。  
  
1.  建立 <xref:System.Windows.Media.Animation.AnimationTimeline> 物件。  
  
2.  使用您要建立動畫之物件的 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> 方法，將 <xref:System.Windows.Media.Animation.AnimationTimeline> 套用至您指定的屬性。  
  
 下列範例顯示如何將 <xref:System.Windows.Controls.Button> 的寬度和背景色彩顯示為動畫。  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## 時鐘動畫  
 當您想要以動畫顯示但不使用 <xref:System.Windows.Media.Animation.Storyboard> 時，以及想要建立複雜的時間樹狀結構或在動畫開始之後以互動方式控制時，就可以使用 <xref:System.Windows.Media.MediaPlayer.Clock%2A> 物件。  您可以使用 Clock 物件，將任何 <xref:System.Windows.Media.Animation.Animatable> 物件的[相依性屬性](GTMT)做成動畫。  
  
 您無法直接在樣式、控制項樣板或資料範本中使用 <xref:System.Windows.Media.Animation.Clock> 物件建立動畫   \(動畫和計時系統確實會在樣式、控制項樣板及資料範本中使用 <xref:System.Windows.Media.Animation.Clock> 物件建立動畫，但是必須從 <xref:System.Windows.Media.Animation.Storyboard> 為您建立 <xref:System.Windows.Media.Animation.Clock> 物件。  如需 <xref:System.Windows.Media.Animation.Storyboard> 物件與 <xref:System.Windows.Media.Animation.Clock> 物件之間關係的詳細資訊，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)\)。  
  
 若要將單一 <xref:System.Windows.Media.Animation.Clock> 套用至屬性，請完成下列步驟。  
  
1.  建立 <xref:System.Windows.Media.Animation.AnimationTimeline> 物件。  
  
2.  使用 <xref:System.Windows.Media.Animation.AnimationTimeline> 的 <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> 方法建立 <xref:System.Windows.Media.Animation.AnimationClock>。  
  
3.  使用要建立動畫之物件的 <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> 方法，將 <xref:System.Windows.Media.Animation.AnimationClock> 套用至您指定的屬性。  
  
 下列範例顯示如何建立 <xref:System.Windows.Media.Animation.AnimationClock> 並將其套用至兩個類似的屬性。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 若要建立時間樹狀結構並使用它來建立屬性動畫，請完成下列步驟。  
  
1.  使用 <xref:System.Windows.Media.Animation.ParallelTimeline> 和 <xref:System.Windows.Media.Animation.AnimationTimeline> 物件建立時間樹狀結構。  
  
2.  使用根 <xref:System.Windows.Media.Animation.ParallelTimeline> 的 <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> 建立 <xref:System.Windows.Media.Animation.ClockGroup>。  
  
3.  逐一查看 <xref:System.Windows.Media.Animation.ClockGroup> 的 <xref:System.Windows.Media.Animation.ClockGroup.Children%2A>，並套用其子 <xref:System.Windows.Media.Animation.Clock> 物件。  針對每個 <xref:System.Windows.Media.Animation.AnimationClock> 子系，使用要建立動畫之物件的 <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> 方法，將 <xref:System.Windows.Media.Animation.AnimationClock> 套用至您指定的屬性  
  
 如需 Clock 物件的詳細資訊，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。  
  
## 單格動畫：略過動畫和計時系統  
 當您需要完全略過 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫系統時，請使用這個方法。  這個方法的其中一個案例就是物理動畫，動畫中的每個步驟都需要根據上一組物件互動重新計算物件。  
  
 單格動畫無法在樣式、控制項樣板或資料範本內定義。  
  
 若要逐格建立動畫，請註冊物件的 <xref:System.Windows.Media.CompositionTarget.Rendering> 事件 \(這個物件包含您要建立動畫的物件\)。  每個畫面格都會呼叫此事件處理常式方法一次。  每次 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將[視覺化樹狀結構](GTMT)中保留的呈現資料封送處理至複合樹狀結構，就會呼叫事件處理常式方法。  
  
 請在您的事件處理常式中，執行動畫效果需要的任何計算，並且以這些值設定您要建立動畫之物件的屬性。  
  
 若要取得目前畫面格的展示時間，與這個事件關聯的 <xref:System.EventArgs> 可以轉型為 <xref:System.Windows.Media.RenderingEventArgs>，提供 <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> 屬性供您用來取得目前畫面格的呈現時間。  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Media.CompositionTarget.Rendering> 頁面。  
  
## 請參閱  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)