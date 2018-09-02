---
title: 處理和引發事件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET Framework], events
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 623700161ae4587daeb2c7348055d413512f7c87
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43452738"
---
# <a name="handling-and-raising-events"></a>處理和引發事件
.NET Framework 中的事件是以委派模型為基礎。 遵循觀察者設計模式的委派模型，它可讓訂閱者向提供者註冊，並且接收通知。 事件發送者會推播事件已發生的通知，而事件接收器會收到該通告並定義對它的回應。 本文將描述委派模型的主要元件、如何在應用程式中使用事件，以及如何在程式碼中實作事件。  
  
 如需處理 Windows 8.x Microsoft Store 應用程式中事件的詳細資訊，請參閱[事件和路由事件概觀](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10))。  
  
## <a name="events"></a>事件  
 事件是由物件傳送的訊息，用以表示發生動作。 這個動作可能是因使用者互動所造成，例如按一下按鈕，也可能是由其他程式邏輯所引發，例如變更屬性值。 引發事件的物件稱為「事件發送者」。 事件發送者並不清楚哪個物件或方法會接收 (處理) 它所引發的事件。 事件通常是事件發送者的成員，例如，<xref:System.Web.UI.WebControls.Button.Click> 事件是 <xref:System.Web.UI.WebControls.Button> 類別的成員，而 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件是實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面之類別的成員。  
  
 若要定義事件，您可以在事件類別的簽章中使用 `event` (C#) 或 `Event` (Visual Basic) 關鍵字，並且為事件指定委派的類型。 委派將在下一節中描述。  
  
 一般而言，若要引發事件，您會加入標記為 `protected` 和 `virtual` (C#) 或 `Protected` 和 `Overridable` (Visual Basic) 的方法。 為這個 `On`*EventName* 方法命名，例如 `OnDataReceived`。 這個方法應該採用一個指定事件資料物件的參數。 您可以提供這個方法讓衍生類別覆寫引發事件的邏輯。 衍生類別一定要呼叫基底類別的 `On`*EventName* 方法，以確保註冊的委派收到事件。  
  
 下列範例將示範如何宣告名為 `ThresholdReached` 的事件。 事件與 <xref:System.EventHandler> 委派有關，而且會在名為 `OnThresholdReached` 的方法中引發。  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>委派  
 委派是保存方法之參考的類型。 委派是透過簽章宣告，該簽章會顯示所參考方法的傳回類型和參數，而且委派只能保留符合其簽章之方法的參考。 委派因此相當於 type-safe 函式指標或回呼。 委派宣告不足以定義委派類別。  
  
 委派在 .NET Framework 中有多種用途。 在事件中，委派是事件來源和處理事件的程式碼之間的媒介 (或類似指標的機制)。 將委派類型加入事件宣告中就可以讓委派與事件產生關聯，如上一節的範例所示。 如需委派的詳細資訊，請參閱 <xref:System.Delegate> 類別。  
  
 .NET Framework 提供了 <xref:System.EventHandler> 和 <xref:System.EventHandler%601> 委派來支援大多數事件案例。 請針對所有沒有事件資料的事件使用 <xref:System.EventHandler> 委派。 請針對有事件相關資料的事件使用 <xref:System.EventHandler%601> 委派。 這些委派沒有傳回類型值，而且會採用兩個參數 (事件來源的物件和事件資料的物件)。  
  
 委派為多點傳送，這表示它們可以存有對一個以上事件處理方法的參考。 如需詳細資訊，請參閱 <xref:System.Delegate> 參考頁面。 委派可讓事件處理更彈性並進行精細的控制。 委派會維護事件的已註冊事件處理常式清單，進而做為引發事件之類別的事件分派者。  
  
 對於無法使用 <xref:System.EventHandler> 和 <xref:System.EventHandler%601> 委派的情況，您可以定義委派。 需要定義委派的情況非常少見，例如，當您必須使用無法辨識泛型的程式碼時。 您會在宣告中以 `delegate` (C#) 和 `Delegate` (Visual Basic) 關鍵字標記委派。 下列範例將示範如何宣告名為 `ThresholdReachedEventHandler` 的委派。  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>事件資料  
 與事件相關聯的資料可以透過事件資料類別提供。 .NET Framework 提供了許多事件資料類別，可讓您在應用程式中使用。 例如，<xref:System.IO.Ports.SerialDataReceivedEventArgs> 類別是 <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> 事件的事件資料類別。 .NET Framework 會遵循以 `EventArgs` 結束所有事件資料類型的命名模式。 您可以藉由查看事件的委派，判斷與事件相關聯的事件資料類別。 例如，<xref:System.IO.Ports.SerialDataReceivedEventHandler> 委派會包含 <xref:System.IO.Ports.SerialDataReceivedEventArgs> 類別做為其中一個參數。  
  
 <xref:System.EventArgs> 類別是所有事件資料類別的基底類型。 <xref:System.EventArgs> 也是您在事件沒有任何相關資料時使用的類別。 如果您建立的事件主要工作只是通知其他類別有事件發生，而不需要傳遞任何資料，請在委派中加入 <xref:System.EventArgs> 類別做為第二個參數。 您可以在未提供資料時傳遞 <xref:System.EventArgs.Empty?displayProperty=nameWithType> 值。 <xref:System.EventHandler> 委派會包含 <xref:System.EventArgs> 類別做為參數。  
  
 當您要建立自訂事件資料類別時，請建立衍生自 <xref:System.EventArgs> 的類別，然後提供傳遞事件相關資料所需的所有成員。 一般而言，您應該使用與 .NET Framework 相同的命名模式，並且以 `EventArgs` 結束事件資料類別名稱。  
  
 下列範例將示範名為 `ThresholdReachedEventArgs` 的事件資料類別。 其中包含所引發事件專屬的屬性。  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>事件處理常式  
 若要回應事件，請在事件接收器中定義事件處理常式方法。 這個方法必須符合您要處理之事件的委派簽章。 在事件處理常式中，您會在事件引發時執行必要的動作，例如，在使用者按一下按鈕後收集使用者輸入。 若要在事件發生時收到通告，則事件處理常式方法必須訂閱事件。  
  
 下列範例將示範名為 `c_ThresholdReached` 的事件處理常式方法，該方法會比對 <xref:System.EventHandler> 委派的簽章。 方法會訂閱 `ThresholdReached` 事件。  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>靜態和動態事件處理常式  
 .NET Framework 可讓訂閱者以靜態或動態方式註冊事件通知。 靜態事件處理常式在其處理事件之類別的整個生命週期內都有效。 動態事件處理常式會在程式執行期間明確地啟動及停用，通常是為了回應某些條件式邏輯。 比方說，如果只有在某些情況下才需要事件通知，或如果應用程式提供多個事件處理常式且執行階段條件會定義一個要使用的適當處理常式，即可使用動態事件處理常式。 上一節中的範例示範了如何以動態方式加入事件處理常式。 如需詳細資訊，請參閱[事件](../../visual-basic/programming-guide/language-features/events/index.md)和[事件](../../csharp/programming-guide/events/index.md)。  
  
## <a name="raising-multiple-events"></a>引發多個事件  
 如果您的類別會引發多個事件，編譯器將會為每個事件委派執行個體產生一個欄位。 如果事件數目很大，則可能無法接受每個委派一個欄位的儲存成本。 對於這些情況，.NET Framework 提供了事件屬性，可以搭配您選擇的另一種資料結構來儲存事件委派。  
  
 事件屬性是由事件存取子伴隨的事件宣告所組成。 事件存取子是您定義用來將事件委派執行個體加入儲存區資料結構或從其中移除的方法。 請注意，事件屬性會比事件欄位來得慢些，因為每個事件委派都必須先擷取，然後才能夠叫用。 記憶體和速度之間會有所折衷。 如果您的類別定義許多不常引發的事件，您會想要實作事件屬性。 如需詳細資訊，請參閱[如何：使用事件屬性處理多個事件](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[如何：引發和使用事件](../../../docs/standard/events/how-to-raise-and-consume-events.md)|包含引發和使用事件的範例。|  
|[如何：使用事件屬性處理多個事件](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|示範如何使用事件屬性處理多個事件。|  
|[觀察者設計模式](../../../docs/standard/events/observer-design-pattern.md)|描述設計模式，可讓訂閱者向提供者註冊，並且接收通知。|  
|[如何：使用 Web Form 應用程式中的事件](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|示範如何處理 Web Form 控制項所引發的事件。|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.EventHandler>  
 <xref:System.EventHandler%601>  
 <xref:System.EventArgs>  
 <xref:System.Delegate>  
 [事件和路由事件概觀 (UWP 應用程式)](/windows/uwp/xaml-platform/events-and-routed-events-overview)  
 [事件 (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)  
 [事件 (C# 程式設計手冊)](../../csharp/programming-guide/events/index.md)
