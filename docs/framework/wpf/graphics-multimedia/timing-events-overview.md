---
title: 計時事件概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
ms.openlocfilehash: 1b0355758c7ba07d8cc1322dc165ac797e980498
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625671"
---
# <a name="timing-events-overview"></a>計時事件概觀
本主題描述如何使用提供的五個計時事件<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>物件。  
  
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該了解如何建立及使用動畫。 若要開始使用動畫，請參閱[動畫概觀](animation-overview.md)。  
  
 有多種方式可用來以動畫顯示屬性在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- **使用分鏡腳本物件**（標記和程式碼）：您可以使用<xref:System.Windows.Media.Animation.Storyboard>排列及散發至一或多個物件的動畫的物件。 如需範例，請參閱[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)。  
  
- **使用本機動畫**（僅程式碼）：您可以套用<xref:System.Windows.Media.Animation.AnimationTimeline>直接向它們要建立動畫之屬性的物件。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
- **使用時鐘**（僅程式碼）：您可以明確管理時鐘的建立，並自行發佈動畫時鐘。  如需範例，請參閱[藉由使用 AnimationClock 建立屬性的動畫](how-to-animate-a-property-by-using-an-animationclock.md)。  
  
 因為您可以使用這些標記和程式碼，此概觀中的範例使用<xref:System.Windows.Media.Animation.Storyboard>物件。 不過，所述的概念也可以套用到其他建立屬性動畫的方法。  
  
### <a name="what-is-a-clock"></a>什麼是時鐘？  
 它是時間軸。單獨使用時，它除了描述一段時間之外沒有任何其他功能。 它是時間軸的<xref:System.Windows.Media.Animation.Clock>實際執行工作的物件： 它會維護的時間軸的計時相關執行階段狀態。 在大部分情況下 (例如使用分鏡腳本時)，系統會自動為時間軸建立時鐘。 您也可以建立<xref:System.Windows.Media.Animation.Clock>明確地使用<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>方法。 如需詳細資訊<xref:System.Windows.Media.Animation.Clock>物件，請參閱[動畫和計時系統概觀](animation-and-timing-system-overview.md)。  
  
## <a name="why-use-events"></a>為何要使用事件？  
 除了一個例外狀況 (對齊最後一個滴答的搜尋) 之外，所有互動式計時作業都是非同步的。 您無法得知它們會在何時執行。 當有其他程式碼需要依賴您的計時作業時，這會構成問題。 假設您要停止對矩形建立動畫的時間軸。 在該時間軸停止之後，您會變更該矩形的色彩。  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 在上述範例中，第二行的程式碼可能會在分鏡腳本停止前執行。 這是因為停止是一個非同步作業。 要求時間軸或時鐘停止，會建立某種「停止要求」，並需要等到計時引擎的下一個滴答才會處理該要求。  
  
 若要在時間軸完成之後執行命令，請使用計時事件。 在下列範例中，在分鏡腳本停止播放之後，會使用事件處理常式來變更矩形的色彩。  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 如需更完整的範例，請參閱 <<c0> [ 收到通知時在時鐘的狀態變更](how-to-receive-notification-when-clock-state-changes.md)。  
  
## <a name="public-events"></a>公用事件  
 <xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>類別都提供五個計時事件。 下表列出這些事件和觸發它們的條件。  
  
|Event - 事件|觸發互動式作業|其他觸發程序|  
|-----------|--------------------------------------|--------------------|  
|**Completed**|跳至填滿|時鐘完成。|  
|**CurrentGlobalSpeedInvalidated**|暫停、繼續、搜尋、設定速率、跳至填滿、停止|時鐘反轉、加速、啟動或停止。|  
|**CurrentStateInvalidated**|開始、跳至填滿、停止|時鐘啟動、停止或填滿。|  
|**CurrentTimeInvalidated**|開始、搜尋、跳至填滿、停止|時鐘進行。|  
|**RemoveRequested**|移除||  
  
## <a name="ticking-and-event-consolidation"></a>滴答和事件彙總  
 當您以動畫顯示物件在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，它會管理您動畫計時引擎。 計時引擎會追蹤時間的進展，並計算每個動畫的狀態。 它在一秒內會做出許多這種評估處理。 這些評估處理稱為「滴答」。  
  
 雖然滴答經常發生，但在滴答之間有可能會發生很多事。 例如，時間軸可能會停止，啟動，然後再次停止，在此情況下，它的目前狀態已變更三次。 理論上，事件可以在單一滴答中引發很多次，不過，由於計時引擎會彙總事件，所以每個事件在每次滴答中最多只能引發一次。  
  
## <a name="registering-for-events"></a>註冊事件  
 有兩種方式可以註冊計時事件：使用時間軸來註冊，或使用從時間軸建立的時鐘來註冊。 使用時鐘直接註冊事件很簡單，但是只能透過程式碼來完成。 您可以透過標記或程式碼來使用時間軸註冊事件。 下節會說明使用時間軸註冊時鐘事件的方法。  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>使用時間軸註冊時鐘事件  
 雖然時間軸<xref:System.Windows.Media.Animation.Timeline.Completed>， <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>， <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>， <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>，並<xref:System.Windows.Media.Animation.Timeline.RemoveRequested>註冊這些事件實際上會將事件處理常式在時間軸與相關聯的事件會出現<xref:System.Windows.Media.Animation.Clock>建立時間軸。  
  
 當您註冊<xref:System.Windows.Media.Animation.Timeline.Completed>時間軸上的事件，例如，您實際上告訴系統註冊針對<xref:System.Windows.Media.Animation.Clock.Completed>事件的時間軸會建立每個時鐘。 程式碼中，您必須註冊此活動之前<xref:System.Windows.Media.Animation.Clock>已經為這個時刻表; 否則您將不會收到通知。 發生這種情況中自動[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; 剖析器會自動註冊的事件之前<xref:System.Windows.Media.Animation.Clock>建立。  
  
## <a name="see-also"></a>另請參閱

- [動畫和計時系統概觀](animation-and-timing-system-overview.md)
- [動畫概觀](animation-overview.md)
- [計時行為概觀](timing-behaviors-overview.md)
