---
title: "計時事件概觀 | Microsoft Docs"
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
  - "Clock 類別"
  - "時鐘的類別"
  - "時刻表"
  - "計時事件"
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 計時事件概觀
本主題描述如何使用提供的五個計時事件<xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>物件。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
## <a name="prerequisites"></a>必要條件  
 若要了解本主題，您應該了解如何建立及使用動畫。 若要開始使用動畫，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 有多種方式可以建立屬性中的動畫[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **使用腳本物件**（標記和程式碼）︰ 您可以使用<xref:System.Windows.Media.Animation.Storyboard>排列及散發至一個或多個物件的動畫的物件。 如需範例，請參閱[使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)。  
  
-   **使用本機動畫**（僅程式碼）︰ 您可以套用<xref:System.Windows.Media.Animation.AnimationTimeline>直接加入它們顯示為動畫屬性的物件。 如需範例，請參閱[屬性而不使用腳本建立動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
-   **使用時鐘**（僅程式碼）︰ 您可以明確管理時鐘的建立並發佈您自己的動畫時鐘。  如需範例，請參閱[使用 AnimationClock 建立屬性動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md)。  
  
 因為您可以利用這些標記和程式碼中，本概觀中的範例將使用<xref:System.Windows.Media.Animation.Storyboard>物件。 不過，所述概念可以套用到的其他方法建立屬性動畫。  
  
### <a name="what-is-a-clock"></a>什麼是時鐘？  
 時間軸，單獨使用，實際上並不進行任何項目以外的其他說明一段時間。 它會在時間軸<xref:System.Windows.Media.Animation.Clock>物件且沒有實際的工作︰ 它會維護與時間有關執行階段狀態的時間軸。 在大部分情況下，例如當使用 分鏡腳本，時鐘會自動時刻表建立。 您也可以建立<xref:System.Windows.Media.Animation.Clock>明確地使用<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>方法。 如需詳細資訊<xref:System.Windows.Media.Animation.Clock>物件，請參閱[動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。  
  
## <a name="why-use-events"></a>使用事件的原因？  
 只有一個例外 （搜尋對齊與最後一個刻度），所有互動計時作業是非同步。 沒有任何方法，讓您知道確切時將會執行。 當您有其他程式碼，取決於您的計時作業時，這就是問題。 假設您想要停止建立矩形動畫時間軸。 時間軸停止之後，您可以變更矩形的色彩。  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 在上一個範例中，可能會在腳本停止之前執行程式碼的第二行。 這是因為停止是非同步作業。 通知時間軸或停止時鐘會建立 「 停止要求 」，它會等到下一個時脈週期時間引擎會處理。  
  
 若要在時刻表完成後，請執行命令，使用計時事件。 在下列範例中，事件處理常式用來變更矩形的色彩之後在腳本停止播放。  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 如需更完整範例，請參閱[收到通知時時鐘的狀態變更](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md)。  
  
## <a name="public-events"></a>公用事件  
 <xref:System.Windows.Media.Animation.Timeline>和<xref:System.Windows.Media.Animation.Clock>類別都提供五個計時事件。 下表列出這些事件和觸發條件。  
  
|事件|觸發互動作業|其他觸發程序|  
|-----------|--------------------------------------|--------------------|  
|**已完成**|跳至填滿|時鐘完成。|  
|**CurrentGlobalSpeedInvalidated**|暫停、 繼續、 搜尋、 設定速率，請跳至填滿、 停止|時鐘會反轉、 加速、 啟動或停止。|  
|**CurrentStateInvalidated**|開始，請跳至填滿、 停止|時鐘開始、 停止或填滿。|  
|**CurrentTimeInvalidated**|開始、 搜尋、 跳至填滿、 停止|時鐘進行中。|  
|**RemoveRequested**|移除||  
  
## <a name="ticking-and-event-consolidation"></a>跳動和事件彙總  
 當您製作物件動畫中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，它是管理動畫的計時引擎。 計時引擎會追蹤時間的進展，並計算每個動畫的狀態。 它讓許多這類的評估活動中的第二個。 這類評估活動稱為 「 跳動 」。  
  
 雖然跳動經常發生，可能會很多事項要刻度之間會發生此問題。 例如，時間軸可能會停止、 啟動，且又再度停止，在此情況下目前的狀態將會變更三次。 理論上，可能會引發事件多次中單一刻度。不過，時間引擎將彙總事件，可以一次產生每個事件，每個刻度。  
  
## <a name="registering-for-events"></a>註冊事件  
 計時事件註冊兩種方式︰ 您可以註冊與時間軸或建立時間軸的時鐘。 雖然它只能從程式碼，是很簡單，直接使用時鐘註冊事件。 您可以註冊的事件標記或程式碼從時間軸。 下一節說明如何註冊與時間軸的時鐘事件。  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>註冊以時間表的時鐘事件  
 雖然時間軸<xref:System.Windows.Media.Animation.Timeline.Completed>， <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>， <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>， <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>，和<xref:System.Windows.Media.Animation.Timeline.RemoveRequested>與時間軸，為這些事件實際上將相關聯的事件處理常式與註冊相關聯的事件會出現<xref:System.Windows.Media.Animation.Clock>建立時間軸。  
  
 當您註冊<xref:System.Windows.Media.Animation.Timeline.Completed>時間軸上的事件，例如，您實際上告訴系統註冊<xref:System.Windows.Media.Animation.Clock.Completed>事件的時間軸會建立每個時鐘。 程式碼中，您必須註冊此事件之前<xref:System.Windows.Media.Animation.Clock>建立的這個時間軸中; 否則您將不會收到通知。 發生這種情況中自動[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; 剖析器會自動為之前的事件註冊<xref:System.Windows.Media.Animation.Clock>建立。  
  
## <a name="see-also"></a>另請參閱  
 [動畫和計時系統概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [計時行為概觀](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)