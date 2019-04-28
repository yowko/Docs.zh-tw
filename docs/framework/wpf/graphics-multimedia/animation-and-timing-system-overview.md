---
title: 動畫和計時系統概觀
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: f64431e7804ba6e068a3d05f512c6ead089d7712
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020339"
---
# <a name="animation-and-timing-system-overview"></a>動畫和計時系統概觀
本主題描述計時系統如何使用動畫<xref:System.Windows.Media.Animation.Timeline>，和<xref:System.Windows.Media.Animation.Clock>類別以動畫顯示屬性。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您可以如[動畫概觀](animation-overview.md)中所述，使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫來以動畫顯示屬性。 這也有助於熟悉相依性屬性。如需詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>時間軸和時鐘  
 [動畫概觀](animation-overview.md)所述方式<xref:System.Windows.Media.Animation.Timeline>代表一段時間，以及動畫是一種<xref:System.Windows.Media.Animation.Timeline>，會產生輸出值。 本身<xref:System.Windows.Media.Animation.Timeline>，不會執行任何以外單純描述一段時間。 它是時間軸的<xref:System.Windows.Media.Animation.Clock>實際執行工作的物件。 同樣地，動畫不會實際以動畫顯示屬性︰ 動畫類別描述如何應該計算輸出值，但它是<xref:System.Windows.Media.Animation.Clock>所建立的驅使動畫輸出並將其套用至屬性的動畫。  
  
 A<xref:System.Windows.Media.Animation.Clock>是一種特殊類型的物件，維護的計時相關執行階段狀態<xref:System.Windows.Media.Animation.Timeline>。 它會提供資訊的三個動畫和計時系統不可或缺的位元： <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>， <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>，和<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>。 A<xref:System.Windows.Media.Animation.Clock>判斷其目前的時間、 進度和狀態使用所描述的計時行為及其<xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>， <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>， <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>，依此類推。  
  
 在大部分情況下，<xref:System.Windows.Media.Animation.Clock>為時間軸會自動建立。 當您使用建立的動畫<xref:System.Windows.Media.Animation.Storyboard>或<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法中，時鐘會自動為您的時間軸和動畫建立並套用到其目標的屬性。 您也可以建立<xref:System.Windows.Media.Animation.Clock>明確地利用<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>方法的程式<xref:System.Windows.Media.Animation.Timeline>。 <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType>方法建立的適當型別的時鐘<xref:System.Windows.Media.Animation.Timeline>的呼叫。 如果<xref:System.Windows.Media.Animation.Timeline>包含子時間表，它會建立<xref:System.Windows.Media.Animation.Clock>以及它們的物件。 產生<xref:System.Windows.Media.Animation.Clock>物件會排列在符合的結構的樹狀結構<xref:System.Windows.Media.Animation.Timeline>所建立的物件樹狀結構。  
  
 不同類型的時間軸有不同類型的時鐘。 下表顯示<xref:System.Windows.Media.Animation.Clock>對應至一些不同的型別<xref:System.Windows.Media.Animation.Timeline>型別。  
  
|時間軸型別|時鐘類型|時鐘用途|  
|-------------------|----------------|-------------------|  
|動畫 (繼承自<xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|產生相依性屬性的輸出值。|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|處理媒體檔案。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|分組，並控制它的子系<xref:System.Windows.Media.Animation.Clock>物件|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|分組，並控制它的子系<xref:System.Windows.Media.Animation.Clock>物件|  
  
 您可以套用任何<xref:System.Windows.Media.Animation.AnimationClock>物件使用建立相容的相依性屬性<xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A>方法。  
  
 在耗用大量效能的情況下，例如以動畫顯示大量類似物件，管理您自己<xref:System.Windows.Media.Animation.Clock>使用可提供效能優勢。  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>時鐘和時間管理員  
 當您以動畫顯示中的物件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，它是時間管理員在管理<xref:System.Windows.Media.MediaPlayer.Clock%2A>針對時間表建立的物件。 時間管理員為 <xref:System.Windows.Media.MediaPlayer.Clock%2A> 物件樹狀目錄的根目錄，並控制該樹狀目錄中的時間流程。  系統會為每一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式自動建立時間管理員，而且應用程式開發人員看不到時間管理員。 時間管理員每一秒都會「滴答」許多次，每一秒發生的實際滴答數目會視可用的系統資源而有所不同。 在每一個滴答期間時間管理員會計算所有的狀態<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>計時樹狀結構中的物件。  
  
 下圖顯示時間管理員之間的關聯性和<xref:System.Windows.Media.Animation.AnimationClock>，和動畫的相依性屬性。  
  
 ![計時系統元件](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
以動畫顯示屬性  
  
 當時間管理員滴答時，它會更新的時間每隔<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>應用程式中。 如果<xref:System.Windows.Media.Animation.Clock>已<xref:System.Windows.Media.Animation.AnimationClock>，它會使用<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>方法<xref:System.Windows.Media.Animation.AnimationTimeline>從它建立的 若要計算其目前的輸出值。 <xref:System.Windows.Media.Animation.AnimationClock>提供<xref:System.Windows.Media.Animation.AnimationTimeline>使用目前的當地時間、 輸入的值，通常是屬性的基底值和預設目的值。 當您擷取值的動畫屬性使用<xref:System.Windows.DependencyObject.GetValue%2A>方法或其 CLR 存取子，您會得到的輸出其<xref:System.Windows.Media.Animation.AnimationClock>。  
  
#### <a name="clock-groups"></a>時鐘群組  
 上一節所述方式有不同類型的<xref:System.Windows.Media.Animation.Clock>的時間軸的不同類型的物件。 下圖顯示時間管理員之間的關聯性<xref:System.Windows.Media.Animation.ClockGroup>、 <xref:System.Windows.Media.Animation.AnimationClock>，和動畫的相依性屬性。 A<xref:System.Windows.Media.Animation.ClockGroup>分組其他時間軸，例如建立<xref:System.Windows.Media.Animation.Storyboard>動畫與其他時間軸分組的類別。  
  
 ![計時系統元件](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
ClockGroup  
  
#### <a name="composition"></a>組合  
 您可以將多個時鐘與單一屬性進行關聯，此時每個時鐘都使用上述時鐘的輸出值做為其基底值。 下圖顯示三個<xref:System.Windows.Media.Animation.AnimationClock>套用至相同屬性的物件。 Clock1 使用動畫屬性的基底值做為輸入，並使用它來產生輸出。 Clock2 會採用從 Clock1 的輸出做為輸入，並使用它來產生輸出。 Clock3 會採用從 Clock2 的輸出做為輸入，並使用它來產生輸出。 當多個時鐘同時影響同一個屬性時，就可以說是形成一個組合鏈結。  
  
 ![計時系統元件](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
組合鏈結  
  
 請注意，雖然在輸入和輸出之間建立關聯性<xref:System.Windows.Media.Animation.AnimationClock>組合鏈結中的物件其計時行為不受影響;<xref:System.Windows.Media.Animation.Clock>物件 (包括<xref:System.Windows.Media.Animation.AnimationClock>物件) 在其父代上有階層式相依性<xref:System.Windows.Media.Animation.Clock>物件。  
  
 若要將多個時鐘套用至相同的屬性中，使用<xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior>套用時<xref:System.Windows.Media.Animation.Storyboard>，動畫或<xref:System.Windows.Media.Animation.AnimationClock>。  
  
#### <a name="ticks-and-event-consolidation"></a>滴答和事件彙總  
 除了計算輸出值，時間管理員也會在每次滴答時執行其他工作︰它會判斷每個時鐘的狀態並引發適當的事件。  
  
 雖然滴答經常發生，但在滴答之間有可能會發生很多事。 例如，<xref:System.Windows.Media.Animation.Clock>可能會停止，啟動，並同樣地，在此情況下停止其<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>值卻已變更三次。 理論上，<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>可以引發多次一個滴答中; 不過，計時引擎會彙總事件，以便<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>可以一次引發事件，每個刻度。 這適用於所有的計時事件： 引發最多一個事件的每個型別指定<xref:System.Windows.Media.Animation.Clock>物件。  
  
 當<xref:System.Windows.Media.Animation.Clock>切換狀態並回到其原始狀態傳回滴答之間 (例如從<xref:System.Windows.Media.Animation.ClockState.Active>來<xref:System.Windows.Media.Animation.ClockState.Stopped>，再回到<xref:System.Windows.Media.Animation.ClockState.Active>)，相關聯的事件還是會發生。  
  
 如需計時事件的詳細資訊，請參閱[計時事件概觀](timing-events-overview.md)。  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>屬性的目前值和基底值  
 可動畫的屬性可以有兩個值︰基底值和目前值。 當您將使用的 CLR 存取子的屬性或<xref:System.Windows.DependencyObject.SetValue%2A>方法，將其基底值。 當屬性未以動畫顯示時，其基底值和目前值都相同。  
  
 當您建立屬性，動畫<xref:System.Windows.Media.Animation.AnimationClock>設定的屬性*目前*值。 擷取透過的 CLR 存取子屬性的值或<xref:System.Windows.DependencyObject.GetValue%2A>方法傳回的輸出<xref:System.Windows.Media.Animation.AnimationClock>當<xref:System.Windows.Media.Animation.AnimationClock>是<xref:System.Windows.Media.Animation.ClockState.Active>或<xref:System.Windows.Media.Animation.ClockState.Filling>。 您可以使用，以擷取屬性的基底值<xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A>方法。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [計時事件概觀](timing-events-overview.md)
- [計時行為概觀](timing-behaviors-overview.md)
