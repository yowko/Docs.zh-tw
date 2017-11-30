---
title: "計時事件概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f50923d9e314d2f677e26416cef59fdf380213e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="timing-events-overview"></a>計時事件概觀
本主題描述如何使用五個可用的計時事件<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>物件。  
  
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該了解如何建立及使用動畫。 若要開始使用動畫，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 有多種方法，以動畫方式顯示在屬性[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **使用分鏡腳本物件**（標記和程式碼）： 您可以使用<xref:System.Windows.Media.Animation.Storyboard>排列及散發至一個或多個物件的動畫物件。 如需範例，請參閱[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)。  
  
-   **使用本機動畫**（僅程式碼）： 您可以套用<xref:System.Windows.Media.Animation.AnimationTimeline>直接物件所建立動畫的屬性。 如需範例，請參閱[不使用分鏡腳本而建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
-   **使用時鐘** (僅程式碼)︰您可以明確管理時鐘的建立，並自行發佈動畫時鐘。  如需範例，請參閱[建立屬性的動畫使用 AnimationClock](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md)。  
  
 因為您可以利用這些標記和程式碼中，本概觀中的範例使用<xref:System.Windows.Media.Animation.Storyboard>物件。 不過，所述的概念也可以套用到其他建立屬性動畫的方法。  
  
### <a name="what-is-a-clock"></a>什麼是時鐘？  
 它是時間軸。單獨使用時，它除了描述一段時間之外沒有任何其他功能。 它是時間軸的<xref:System.Windows.Media.Animation.Clock>從事實際作業的物件： 其維持的時間軸與時間有關執行階段狀態。 在大部分情況下 (例如使用分鏡腳本時)，系統會自動為時間軸建立時鐘。 您也可以建立<xref:System.Windows.Media.Animation.Clock>明確地使用<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>方法。 如需有關<xref:System.Windows.Media.Animation.Clock>物件，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。  
  
## <a name="why-use-events"></a>為何要使用事件？  
 除了一個例外狀況 (對齊最後一個滴答的搜尋) 之外，所有互動式計時作業都是非同步的。 您無法得知它們會在何時執行。 當有其他程式碼需要依賴您的計時作業時，這會構成問題。 假設您要停止對矩形建立動畫的時間軸。 在該時間軸停止之後，您會變更該矩形的色彩。  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 在上述範例中，第二行的程式碼可能會在分鏡腳本停止前執行。 這是因為停止是一個非同步作業。 要求時間軸或時鐘停止，會建立某種「停止要求」，並需要等到計時引擎的下一個滴答才會處理該要求。  
  
 若要在時間軸完成之後執行命令，請使用計時事件。 在下列範例中，在分鏡腳本停止播放之後，會使用事件處理常式來變更矩形的色彩。  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 如需更完整的範例，請參閱[接收通知時時鐘的狀態變更](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md)。  
  
## <a name="public-events"></a>公用事件  
 <xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>這兩個類別會提供五個計時事件。 下表列出這些事件和觸發它們的條件。  
  
|事件|觸發互動式作業|其他觸發程序|  
|-----------|--------------------------------------|--------------------|  
|**Completed**|跳至填滿|時鐘完成。|  
|**CurrentGlobalSpeedInvalidated**|暫停、繼續、搜尋、設定速率、跳至填滿、停止|時鐘反轉、加速、啟動或停止。|  
|**CurrentStateInvalidated**|開始、跳至填滿、停止|時鐘啟動、停止或填滿。|  
|**CurrentTimeInvalidated**|開始、搜尋、跳至填滿、停止|時鐘進行。|  
|**RemoveRequested**|移除||  
  
## <a name="ticking-and-event-consolidation"></a>滴答和事件彙總  
 當您製作物件動畫中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，它是計時引擎，可管理您的動畫。 計時引擎會追蹤時間的進展，並計算每個動畫的狀態。 它在一秒內會做出許多這種評估處理。 這些評估處理稱為「滴答」。  
  
 雖然滴答經常發生，但在滴答之間有可能會發生很多事。 例如，時間軸可能會停止，啟動，然後再次停止，在此情況下，它的目前狀態已變更三次。 理論上，事件可以在單一滴答中引發很多次，不過，由於計時引擎會彙總事件，所以每個事件在每次滴答中最多只能引發一次。  
  
## <a name="registering-for-events"></a>註冊事件  
 有兩種方式可以註冊計時事件：使用時間軸來註冊，或使用從時間軸建立的時鐘來註冊。 使用時鐘直接註冊事件很簡單，但是只能透過程式碼來完成。 您可以透過標記或程式碼來使用時間軸註冊事件。 下節會說明使用時間軸註冊時鐘事件的方法。  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>使用時間軸註冊時鐘事件  
 雖然時間軸的<xref:System.Windows.Media.Animation.Timeline.Completed>， <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>， <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>， <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>，和<xref:System.Windows.Media.Animation.Timeline.RemoveRequested>事件似乎是相關聯時間軸，註冊的實際這些事件產生關聯的事件處理常式和<xref:System.Windows.Media.Animation.Clock>建立在時間軸。  
  
 當您註冊<xref:System.Windows.Media.Animation.Timeline.Completed>時間表上的事件，例如，您正在實際告訴系統註冊<xref:System.Windows.Media.Animation.Clock.Completed>事件的時間軸會建立每個時鐘。 程式碼中，您必須註冊此事件之前<xref:System.Windows.Media.Animation.Clock>建立的這個時間軸中; 否則您不會收到通知。 發生這種情況中自動[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; 剖析器會自動註冊的事件之前<xref:System.Windows.Media.Animation.Clock>建立。  
  
## <a name="see-also"></a>另請參閱  
 [動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [計時行為概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
