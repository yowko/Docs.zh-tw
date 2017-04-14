---
title: "處理和引發事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式開發 [.NET Framework], 事件"
  - "事件的委派模型"
  - "事件 [.NET Framework]"
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# 處理和引發事件
在 .NET Framework 中的事件是以委派模型為基礎   授權模型遵守觀察者設計模式，可讓訂閱者向提供者註冊並且接收通知。  事件發送者的推播通知事件發生，而事件接收器接收告知並定義對它的回應。  本文說明委派模型的主要元件，如何在應用程式消滅事件和如何實作事件程式碼。  
  
 如需 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中處理事件的詳細資訊，請參閱 [事件和路由事件概觀 \(Windows 存放應用程式\)](http://go.microsoft.com/fwlink/p/?LinkId=261485)。  
  
## 事件  
 事件是由物件傳送用來表示發生某種動作的訊息。  這個動作可能由使用者互動造成，例如按一下按鈕，也可能是由其他程式邏輯引發，例如變更屬性值。  引發事件的物件稱為 *事件傳送者*。  事件的寄件者不知道哪個物件或方法會接收\(處理\) 其引發的事件。  事件通常是事件傳送者的成員；例如， <xref:System.Web.UI.WebControls.Button.Click> 事件是 <xref:System.Web.UI.WebControls.Button> 類別的成員，因此， <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件是實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面之類別的成員。  
  
 若要定義事件，則事件的簽章使用 `event` \(C\#\) 或 `Event` \(Visual Basic\) 關鍵字，並為事件指定委派的型別。  委派將在下一節中說明。  
  
 一般而言，若要引發事件，您將標記為 `protected` 和 `virtual` 的方法 \(在 C\# 中\) 或 `Protected` 和 `Overridable` \(在 Visual Basic 中\)加入方法中。  將這個 `On`*EventName*方法命名；例如， `OnDataReceived`。  此方法應該採用指定事件資料物件的參數。  您提供這個方法可讓衍生類別覆寫引發的事件邏輯。  衍生類別一定要呼叫基底類別的 `On`*EventNameEventName* 方法，以確保註冊的委派可以接收事件。  
  
 下面的範例顯示如何宣告名為 `ThresholdReached` 的事件：  事件與<xref:System.EventHandler>委派有關，且發生於名為`OnThresholdReached`的方法中。  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## 委派  
 委派是保存方法之參考的類別。  委派透過方法所參考、顯示傳回型別和參數方法的簽章宣告，而且可以保留只符合其簽章方法的參考。  所以委派相當於型別安全函式指標或者回呼 \(Callback\)。  委派宣告已足以定義委派類別。  
  
 在.NET Framework 中委派有許多用途 。  在事件中，委派是在事件來源和處理事件的程式碼之間的媒介 \(或類似指標的機制\) 。  您將該委派與事件藉由包括委派輸入產生關聯，如上一節中的範例所示事件宣告。  如需委派的詳細資訊，請參閱<xref:System.Delegate>類別。  
  
 .NET Framework 提供 <xref:System.EventHandler> 和 <xref:System.EventHandler%601> 委派來支援大多數事件案例。  為所有布包含式件資料的事件使用 <xref:System.EventHandler> 委派。  為包含事件相關資料的事件使用 <xref:System.EventHandler%601> 委派。  這些委派沒有任何傳回型別值並採用兩個參數 \(事件來源的物件和事件資料的物件\)。  
  
 事件委派為多點傳送，這表示它們可以存有對一個以上事件處理方法的參考。  如需詳細資訊，請參閱 <xref:System.Delegate> 參考頁面。  委派可以讓事件處理更彈性和有精細的控制。  委派可藉由維持事件之已註冊事件處理常式的清單，扮演引發事件之類別的事件分派者。  
  
 對於 <xref:System.EventHandler> 和 <xref:System.EventHandler%601> 委派無法運作的情形，您可以定義委派。  要求您定義委派的情況非常罕見，例如，當您必須使用無法辨識泛型的程式碼時。  您將有 `delegate` \(C\# 中的子句\) 和宣告中的 `Delegate` \(在 Visual Basic 中為\) 關鍵字標記為委派。  下列範例示範如何定義名為 `ThresholdReachedEventHandler` 的委派。  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## 事件資料  
 與事件有關連的資料可以透過事件資料類別提供。  .NET Framework 提供您許多在應用程式中使用的事件資料類別。  例如， <xref:System.IO.Ports.SerialDataReceivedEventArgs> 類別是 <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=fullName> 事件的事件資料類別。  .NET Framework 遵循利用`EventArgs`關閉所有事件資料型態命名模式。  您判斷哪個事件資料類別會與事件有關藉由查看事件的委派。  例如， <xref:System.IO.Ports.SerialDataReceivedEventHandler> 委派包含 <xref:System.IO.Ports.SerialDataReceivedEventArgs> 類別做為其中一個參數。  
  
 <xref:System.EventArgs> 類別是所有事件資料類別的基底型別。  <xref:System.EventArgs> 也是當事件無任何資料與它相關您使用的類別。  當您建立只會通知其他類別事情發生且不需要傳遞任何資料的事件時，將 <xref:System.EventArgs> 類別引入做為第二個委派中的參數。  如果未提供資料時，您可以透過 <xref:System.EventArgs.Empty?displayProperty=fullName> 值傳遞資料。  <xref:System.EventHandler> 委派包含 <xref:System.EventArgs> 類別做為參數。  
  
 當您要建立自訂事件資料類別時，請建立衍生自 <xref:System.EventArgs>的類別，然後提供所有需要傳遞與事件相關的資料的成員。  一般而言，您應該使用如同 .NET Framework 一樣的命名模式並結束您的 `EventArgs`使用事件資料類別名稱。  
  
 下列範例顯示名為`ThresholdReachedEventArgs` 的事件資料。  它包含專屬於所引發之事件的屬性。  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## 事件處理常式  
 若要回應事件，您在事件接收器中定義事件處理常式方法。  這個方法必須符合您處理事件的委派簽章。  在事件處理常式，當事件引發時您執行必要的動作，例如在使用者按一下按鈕後收集使用者輸入。  在發生事件時若要接收告知，事件處理常式方法必須訂閱事件。  
  
 下列範例會顯示符合 <xref:System.EventHandler> 委派簽章的事件處理常式方法名稱為 `c_ThresholdReached` 。  方法訂閱 `ThresholdReached` 事件。  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## 靜態和動態事件處理常式  
 .NET Framework 允許訂閱者靜態或動態註冊事件通知。  靜態事件處理常式會在處理其事件之類別的整個週期持續作用中。  動態事件處理常式則會在程式執行期間明確地啟用和停用，以回應某些條件式程式邏輯。  例如，如果只有在某些情況下才需要事件通知，或者應用程式提供多個事件處理常式，並且執行階段狀況會決定適用的事件處理常式，則可以使用動態事件處理常式。  在前幾節中的範例示範如何以動態方式加入事件處理常式。  如需詳細資訊，請參閱[Events](../Topic/Events%20\(Visual%20Basic\).md)與[事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)。  
  
## 引發多個事件  
 如果您的類別會引發多個事件，編譯器產生每個事件委派執行個體欄位。  如果事件的數目很多，每一委派一個欄位的儲存取成本可能是無法接受的。  對於這些情況，.NET Framework 提供了一種稱為事件屬性的建構，可以搭配您所選的其他資料結構用來儲存事件委派。  
  
 事件屬性是由事件宣告加上事件存取子 \(Accessor\) 所組成。  事件存取子是您定義用來將事件委派執行個體加入資料結構儲存區或從其中移除的方法。  請注意，事件屬性會比事件欄位來得慢些，因為每個事件委派都必須先被擷取，然後才能夠被呼叫。  因此在記憶體和速度之間必須有所取捨。  如果您的類別定義了許多不常被引發的事件，您應該實作事件屬性。  如需詳細資訊，請參閱[如何：使用事件屬性處理多個事件](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)。  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[如何：引發和使用事件](../../../docs/standard/events/how-to-raise-and-consume-events.md)|包含引發和使用事件的範例。|  
|[如何：使用事件屬性處理多個事件](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|示範如何使用事件屬性來處理多個事件。|  
|[觀察器設計模式](../../../docs/standard/events/observer-design-pattern.md)|描述設計模式可讓訂閱者向提供者註冊，並且接收通知。|  
|[如何：使用 Web Form 應用程式中的事件](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|示範如何處理 Web Form 控制項所引發的事件。|  
  
## 請參閱  
 <xref:System.EventHandler>   
 <xref:System.EventHandler%601>   
 <xref:System.EventArgs>   
 <xref:System.Delegate>   
 [事件和路由事件概觀 \(Windows 存放應用程式\)](http://go.microsoft.com/fwlink/?LinkId=261485)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)   
 [事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)