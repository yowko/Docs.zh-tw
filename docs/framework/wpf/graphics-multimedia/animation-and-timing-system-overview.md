---
title: 動畫和計時系統概觀
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: d0ac2a8160a1e6f9bcdb333593ec207954b391aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187711"
---
# <a name="animation-and-timing-system-overview"></a>動畫和計時系統概觀
本主題介紹計時系統如何使用動畫<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>類為屬性設置動畫。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您可以如[動畫概觀](animation-overview.md)中所述，使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫來以動畫顯示屬性。 這也有助於熟悉相依性屬性。如需詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。  
  
<a name="timelinesandclocks"></a>
## <a name="timelines-and-clocks"></a>時間軸和時鐘  
 [動畫概述](animation-overview.md)描述了 表示<xref:System.Windows.Media.Animation.Timeline>時間段的方式，動畫是生成輸出值的類型。 <xref:System.Windows.Media.Animation.Timeline> 就其本身，a <xref:System.Windows.Media.Animation.Timeline>. 除了描述一段時間之外，別無他法。 是時間表的物件<xref:System.Windows.Media.Animation.Clock>可以真正工作。 同樣，動畫實際上不會為屬性設置動畫：動畫類描述如何計算輸出值，但它是<xref:System.Windows.Media.Animation.Clock>為動畫創建的，它驅動動畫輸出並將其應用於屬性。  
  
 A<xref:System.Windows.Media.Animation.Clock>是一種特殊類型的物件，它維護 的<xref:System.Windows.Media.Animation.Timeline>計時相關運行時狀態。 它提供了對動畫和計時系統至關重要的三位資訊：<xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>和<xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>。 <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> A<xref:System.Windows.Media.Animation.Clock><xref:System.Windows.Media.Animation.Timeline>使用其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>： 、 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>、 、 等描述的計時行為確定其目前時間、進度和狀態。  
  
 在大多數情況下，將自動為時間表<xref:System.Windows.Media.Animation.Clock>創建 。 使用<xref:System.Windows.Media.Animation.Storyboard>或<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法設置動畫時，將自動為時間表和動畫創建時鐘，並將其應用於其目標屬性。 還可以使用<xref:System.Windows.Media.Animation.Clock><xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>的方法顯式創建<xref:System.Windows.Media.Animation.Timeline>。 該方法<xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType>為<xref:System.Windows.Media.Animation.Timeline>調用它的的創建適當類型的時鐘。 如果<xref:System.Windows.Media.Animation.Timeline>包含子時間表，它也為他們創建<xref:System.Windows.Media.Animation.Clock>物件。 生成的<xref:System.Windows.Media.Animation.Clock>物件排列在與創建物件樹的結構相匹配<xref:System.Windows.Media.Animation.Timeline>的物件樹中。  
  
 不同類型的時間軸有不同類型的時鐘。 下表顯示了對應于某些不同類型的<xref:System.Windows.Media.Animation.Clock><xref:System.Windows.Media.Animation.Timeline>類型。  
  
|時間軸型別|時鐘類型|時鐘用途|  
|-------------------|----------------|-------------------|  
|動畫（從<xref:System.Windows.Media.Animation.AnimationTimeline>繼承）|<xref:System.Windows.Media.Animation.AnimationClock>|產生相依性屬性的輸出值。|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|處理媒體檔案。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|組和控制其子<xref:System.Windows.Media.Animation.Clock>物件|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|組和控制其子<xref:System.Windows.Media.Animation.Clock>物件|  
  
 可以使用 方法將<xref:System.Windows.Media.Animation.AnimationClock>創建的任何物件應用於相容的依賴項屬性<xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A>。  
  
 在性能密集型方案中（如為大量類似物件進行動畫處理）中，管理自己的<xref:System.Windows.Media.Animation.Clock>使用可以提供性能優勢。  
  
<a name="timemanager"></a>
## <a name="clocks-and-the-time-manager"></a>時鐘和時間管理員  
 在 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為物件設置動畫時，是時間管理器來管理為時間表<xref:System.Windows.Media.MediaPlayer.Clock%2A>創建的物件。 時間管理員為 <xref:System.Windows.Media.MediaPlayer.Clock%2A> 物件樹狀目錄的根目錄，並控制該樹狀目錄中的時間流程。  系統會為每一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式自動建立時間管理員，而且應用程式開發人員看不到時間管理員。 時間管理員每一秒都會「滴答」許多次，每一秒發生的實際滴答數目會視可用的系統資源而有所不同。 在每個這些刻度期間，時間管理器計算計時樹中所有<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>物件的狀態。  
  
 下圖顯示了時間管理器和<xref:System.Windows.Media.Animation.AnimationClock>以及 和 和 之間的關係。  
  
 ![計時系統元件](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
以動畫顯示屬性  
  
 當時間管理器滴答作響時，它會更新應用程式中每個<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>時間的時間。 如果<xref:System.Windows.Media.Animation.Clock>為<xref:System.Windows.Media.Animation.AnimationClock>，則它使用<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>創建它<xref:System.Windows.Media.Animation.AnimationTimeline>的方法來計算其當前輸出值。 提供<xref:System.Windows.Media.Animation.AnimationClock><xref:System.Windows.Media.Animation.AnimationTimeline>當前本地時間 、輸入值（通常是屬性的基值）和預設目標值。 使用<xref:System.Windows.DependencyObject.GetValue%2A>方法或其 CLR 訪問器按屬性檢索動畫的值時，您將獲得其<xref:System.Windows.Media.Animation.AnimationClock>的輸出。  
  
#### <a name="clock-groups"></a>時鐘群組  
 上一節介紹了不同類型的時間表如何有不同類型的<xref:System.Windows.Media.Animation.Clock>物件。 下圖顯示了時間管理器<xref:System.Windows.Media.Animation.ClockGroup>、、和<xref:System.Windows.Media.Animation.AnimationClock>動畫依賴項屬性之間的關係。 為<xref:System.Windows.Media.Animation.ClockGroup>對其他時間表（如<xref:System.Windows.Media.Animation.Storyboard>類）進行分組的時間表（對動畫和其他時間表進行分組）創建。  
  
 ![計時系統元件](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
ClockGroup  
  
#### <a name="composition"></a>撰寫  
 您可以將多個時鐘與單一屬性進行關聯，此時每個時鐘都使用上述時鐘的輸出值做為其基底值。 下圖顯示了應用於同一<xref:System.Windows.Media.Animation.AnimationClock>屬性的三個物件。 Clock1 使用動畫屬性的基底值做為輸入，並使用它來產生輸出。 Clock2 會採用從 Clock1 的輸出做為輸入，並使用它來產生輸出。 Clock3 會採用從 Clock2 的輸出做為輸入，並使用它來產生輸出。 當多個時鐘同時影響同一個屬性時，就可以說是形成一個組合鏈結。  
  
 ![計時系統元件](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
組合鏈結  
  
 請注意，雖然在合成鏈中<xref:System.Windows.Media.Animation.AnimationClock>物件的輸入和輸出之間創建了關係，但它們的計時行為不受影響;<xref:System.Windows.Media.Animation.Clock>物件（包括<xref:System.Windows.Media.Animation.AnimationClock>物件）對其父<xref:System.Windows.Media.Animation.Clock>物件具有分層依賴關係。  
  
 要將多個時鐘應用於<xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior>同一<xref:System.Windows.Media.Animation.Storyboard>屬性，請使用 應用 的 動畫 或<xref:System.Windows.Media.Animation.AnimationClock>時使用 。  
  
#### <a name="ticks-and-event-consolidation"></a>滴答和事件彙總  
 除了計算輸出值，時間管理員也會在每次滴答時執行其他工作︰它會判斷每個時鐘的狀態並引發適當的事件。  
  
 雖然滴答經常發生，但在滴答之間有可能會發生很多事。 例如，可能停止<xref:System.Windows.Media.Animation.Clock>、啟動和再次停止 ， 在這種情況下，其<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>值將更改三次。 理論上，<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>該事件可以在一個刻度中多次引發;但是，計時引擎合併事件，以便每個刻度最多可以<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>引發一次事件。 對於所有計時事件也是如此：對於給定<xref:System.Windows.Media.Animation.Clock>物件，最多最多引發一個每種類型的事件。  
  
 當<xref:System.Windows.Media.Animation.Clock>切換狀態並在刻度之間返回到其原始狀態（例如從<xref:System.Windows.Media.Animation.ClockState.Active>到 和<xref:System.Windows.Media.Animation.ClockState.Stopped>返回<xref:System.Windows.Media.Animation.ClockState.Active>）之間時，關聯事件仍將發生。  
  
 如需計時事件的詳細資訊，請參閱[計時事件概觀](timing-events-overview.md)。  
  
<a name="currentvaluesbasevaluesofproperties"></a>
## <a name="current-values-and-base-values-of-properties"></a>屬性的目前值和基底值  
 可動畫的屬性可以有兩個值︰基底值和目前值。 使用其 CLR 訪問器或<xref:System.Windows.DependencyObject.SetValue%2A>方法設置屬性時，將設置其基值。 當屬性未以動畫顯示時，其基底值和目前值都相同。  
  
 為屬性設置動畫時，將<xref:System.Windows.Media.Animation.AnimationClock>設置該屬性的*當前*值。 通過其 CLR 訪問<xref:System.Windows.DependencyObject.GetValue%2A>器或 方法檢索屬性的值將返回<xref:System.Windows.Media.Animation.AnimationClock><xref:System.Windows.Media.Animation.AnimationClock>或<xref:System.Windows.Media.Animation.ClockState.Active>時 的輸出。 <xref:System.Windows.Media.Animation.ClockState.Filling> 可以使用<xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A>方法檢索屬性的基值。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [計時事件概觀](timing-events-overview.md)
- [計時行為概觀](timing-behaviors-overview.md)
