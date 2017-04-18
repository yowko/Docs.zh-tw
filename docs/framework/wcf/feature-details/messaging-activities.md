---
title: "訊息活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# 訊息活動
訊息傳遞活動允許工作流程傳送和接收 WCF 訊息。藉由將訊息傳遞活動加入至工作流程，您就可以製作任何複雜訊息交換模式 \(MEP\) 的模型。  
  
## 訊息交換模式  
 有三種基本的訊息交換模式：  
  
-   **資料包** \- 使用資料包 MEP 時，用戶端會將訊息傳送至服務，但是服務不會回應。這種模式有時稱為「射後不理」\(Fire And Forget\)。射後不理交換是需要超出範圍確認成功傳遞的交換。訊息可能會在傳輸時遺失而永遠無法抵達服務。即使用戶端成功傳送訊息，也不會保證服務收到訊息。資料包是訊息的基本建置組塊，您可以在資料包的最上層建立自己的 MEP。  
  
-   **要求\-回應** \- 使用要求\-回應 MEP 時，用戶端會將訊息傳送至服務，服務會執行必要的處理，然後將回應傳回至用戶端。此模式是由要求\-回應組合所構成。遠端程序呼叫 \(Remote Procedure Call，RPC\) 與瀏覽器 GET 要求就是要求\-回應呼叫的例子。這個模式又稱為半雙工。  
  
-   **雙工** \- 使用雙工 MEP 時，用戶端和服務會依任意順序傳送訊息給彼此。雙工 MEP 就像是電話交談，談話中說出的每個字都是一則訊息。  
  
 訊息傳遞活動可讓您實作上述任何基本 MEP 以及各種複雜的 MEP。  
  
## 訊息傳遞活動  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 會定義下列訊息傳遞活動：  
  
-   <xref:System.ServiceModel.Activities.Send>\- 使用 <xref:System.ServiceModel.Activities.Send> 活動傳送訊息。  
  
-   <xref:System.ServiceModel.Activities.SendReply> \- 使用 <xref:System.ServiceModel.Activities.SendReply> 活動傳送對所收到訊息的回應。此活動是工作流程服務在實作要求\/回覆 MEP 時使用。  
  
-   <xref:System.ServiceModel.Activities.Receive>\- 使用 <xref:System.ServiceModel.Activities.Receive> 活動接收訊息。  
  
-   <xref:System.ServiceModel.Activities.ReceiveReply> \- 使用 <xref:System.ServiceModel.Activities.ReceiveReply> 活動接收回覆訊息。此活動是工作流程服務用戶端在實作要求\/回覆 MEP 時使用。  
  
## 訊息傳遞活動和訊息交換模式  
 資料包 MEP 包含傳送訊息的用戶端，以及接收訊息的服務。如果用戶端是工作流程，請使用 <xref:System.ServiceModel.Activities.Send> 活動傳送訊息。若要在工作流程中接收訊息，請使用 <xref:System.ServiceModel.Activities.Receive> 活動。<xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.Receive> 活動各有一個名為 `Content` 的屬性。此屬性包含要傳送或接收的資料。實作要求\-回應 MEP 時，用戶端和服務都會使用多組活動。用戶端會使用 <xref:System.ServiceModel.Activities.Send> 活動傳送訊息，並且使用 <xref:System.ServiceModel.Activities.ReceiveReply> 活動接收來自服務的回應。這兩種活動之間是透過 <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 屬性建立關聯。此屬性會設定為傳送原始訊息的 <xref:System.ServiceModel.Activities.Send> 活動。服務也會使用一組關聯的活動：<xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply>。這兩種活動之間是透過 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 屬性建立關聯。此屬性會設定為接收原始訊息的 <xref:System.ServiceModel.Activities.Receive> 活動。<xref:System.ServiceModel.Activities.ReceiveReply> 和 <xref:System.ServiceModel.Activities.SendReply> 活動就像 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.Receive>，可讓您傳送 <xref:System.ServiceModel.Channels.Message> 執行個體或訊息合約型別。  
  
 由於工作流程會長時間執行，因此雙向通訊模式必須也支援長時間執行的對話。若要支援長時間執行的對話，初始化對話的用戶端必須讓服務可在之後資料能夠使用時回呼。例如，訂單要求提交讓管理員核准之後，可能經過一天、一週甚至一年都未處理；管理訂單核准的工作流程必須知道要在核准之後繼續執行。使用相互關聯的工作流程中可支援這種雙向通訊模式。若要實作雙工模式，請使用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.Receive> 活動。在 <xref:System.ServiceModel.Activities.Receive> 活動上，使用特殊的 <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A> 索引鍵值初始化相互關聯。在 <xref:System.ServiceModel.Activities.Send> 活動上，將該相互關聯控制代碼設定為 <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> 屬性值。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][永久性雙工](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md).  
  
> [!NOTE]
>  使用回呼相互關聯 \(「永久性雙工」\) 之工作流程的雙工實作主要用於長時間執行的對話。這與採用回呼合約的 WCF 雙工不同，後者會處理短時間執行 \(通道的存留期\) 的對話。  
  
## 訊息格式和訊息傳遞活動  
 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動都有一個名為 `Content` 的屬性。此屬性的型別為 <xref:System.ServiceModel.Activities.ReceiveContent>，並且表示 <xref:System.ServiceModel.Activities.Receive> 或 <xref:System.ServiceModel.Activities.ReceiveReply> 活動接收的資料。.NET Framework 會定義分別稱為 <xref:System.ServiceModel.Activities.RecieveMessageContent> 和 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 的兩個相關類別，兩者都是衍生自 <xref:System.ServiceModel.Activities.ReceiveContent>。將 <xref:System.ServiceModel.Activities.Receive> 或 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的 `Content` 屬性設定為其中一種型別的執行個體，即可在工作流程服務中接收資料。要使用的型別是依據活動接收的資料型別而定。如果活動接收 `Message` 物件或訊息合約型別，則使用 <xref:System.ServiceModel.Activities.ReceiveMessageContent>。如果活動接收一組可序列化的資料合約或 XML 型別，則使用 <xref:System.ServiceModel.Activities.ReceiveParametersContent>。<xref:System.ServiceModel.Activities.ReceiveParametersContent> 可讓您傳送多個參數，而 <xref:System.ServiceModel.Activities.ReceiveMessageContent> 只能讓您傳送一個物件，也就是訊息 \(或訊息合約型別\)。  
  
> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent> 也可以搭配可序列化的單一資料合約或 XML 型別使用。使用 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 搭配單一參數與直接傳遞至 <xref:System.ServiceModel.Activities.RecieveMessageContent> 的物件之間的差異在於 Wire 格式。參數的內容是以對應於作業名稱的 XML 項目包裝，而序列化物件是以使用參數名稱的 XML 項目包裝 \(例如 `<Echo><msg>Hello, World</msg></Echo>`\)。訊息內容不會由作業名稱包裝。但是序列化物件會放置在使用 XML 限定型別名稱的 XML 項目內 \(例如 `<string>Hello, World</string>`\)。  
  
 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.SendReply> 活動也有一個名為 `Content` 的屬性。此屬性的型別為 <xref:System.ServiceModel.Activities.SendContent>，並且表示 <xref:System.ServiceModel.Activities.Send> 或 <xref:System.ServiceModel.Activities.SendReply> 活動傳送的資料。.NET Framework 會定義分別稱為 <xref:System.ServiceModel.Activities.SendMessageContent> 和 <xref:System.ServiceModel.Activities.SendParametersContent> 的兩個相關型別，兩者都是衍生自 <xref:System.ServiceModel.Activities.SendContent>。將 <xref:System.ServiceModel.Activities.Send> 或 <xref:System.ServiceModel.Activities.SendReply> 活動的 `Content` 屬性設定為其中一種型別的執行個體，即可從工作流程服務傳送資料。要使用的類型是依據活動傳送的資料型別而定。如果活動傳送 `Message` 物件或訊息合約型別，則使用 <xref:System.ServiceModel.Activities.SendMessageContent>。如果活動傳送資料合約型別，則使用 <xref:System.ServiceModel.Activities.SendParametersContent>。<xref:System.ServiceModel.Activities.SendParametersContent> 可讓您傳送多個參數，而 <xref:System.ServiceModel.Activities.SendMessageContent> 只能讓您傳送一個物件，也就是訊息 \(或訊息合約型別\)。  
  
 以命令方式程式設計訊息傳遞活動時，可使用泛型 <xref:System.ServiceModel.Activities.InArgument%601> 和 <xref:System.ServiceModel.Activities.OutArgument%601> 包裝您指派給訊息的物件，或 <xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.SendReply>、<xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動的參數屬性。針對 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.SendReply> 活動使用 <xref:System.ServiceModel.Activities.InArgument%601>，並且針對 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動使用 <xref:System.ServiceModel.Activities.OutArgument%601>。`In` 引數會搭配傳送活動使用，因為資料會傳遞至活動內。`Out` 引數則搭配接收活動使用，因為資料會從活動傳出，如下列範例中所示。  
  
```  
Receive reserveSeat = new Receive  
{   
    ...   
    Content = new ReceiveParametersContent  
    {  
        Parameters =  
        {  
            { "ReservationInfo", new OutArgument<ReservationRequest>(reservationInfo) }  
        }  
    }  
};  
SendReply reserveSeat = new SendReply  
{   
    ...   
    Request = reserveSeat,  
    Content = new SendParametersContent  
    {  
        Parameters =  
        {  
            { "ReservationId", new InArgument<string>(reservationId) }  
        }  
    },  
};  
```  
  
 實作定義以傳回 Void 之要求\/回應作業的工作流程服務時，您必須具現化 <xref:System.ServiceModel.Activities.SendReply> 活動，並且將 <xref:System.ServiceModel.Activities.SendReply.Content%2A> 屬性設定為其中一個內容型別 \(<xref:System.ServiceModel.Activities.SendMesageContent> 或 <xref:System.ServiceModel.Activities.SendParametersContent>\) 的空執行個體，如下列範例中所示。  
  
```  
Receive rcv = new Receive()  
{  
ServiceContractName = "IService",  
OperationName = "NullReturningContract",  
Content = new ReceiveParametersContent( new Dictionary<string, OutArgument>() { { "message", new OutArgument<string>() } } )  
};  
SendReply sr = new SendReply()  
{  
Request = rcv  
   Content = new SendParametersContent();  
};  
  
```  
  
## 加入服務參考  
 從工作流程應用程式呼叫工作流程服務時，[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 會產生自訂訊息傳遞活動，這些活動會封裝要求\/回覆 MEP 中常用的 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動。若要使用此功能，請以滑鼠右鍵按一下 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中的用戶端專案，並選取 \[**加入服務參考**\]。在位址方塊中輸入服務的基底位址，然後按一下 \[移至\]。可用的服務會在 \[**服務:**\] 方塊中顯示。展開服務節點，即可顯示支援的合約。選取您要呼叫的合約，可用作業的清單就會出現在 \[**作業**\] 方塊中。然後您可以為產生的活動指定命名空間，並且按一下 \[**確定**\]。接著您會看見一個對話方塊，說明作業已成功完成，而且在您重建專案之後，產生的自訂活動會位於工具方塊內。服務合約中會針對每一項作業定義一個活動。重建專案之後，您可以拖放自訂活動至工作流程，並且在 \[屬性\] 視窗中設定任何必要的屬性。  
  
## 訊息傳遞活動範本  
 為了讓您更容易在用戶端和服務上設定要求\/回應 MEP，[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 提供兩個訊息傳遞活動範本。<xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> 會在服務上使用，<xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> 則在用戶端使用。這兩種情況下，範本都會將適當的訊息傳遞活動加入至您的工作流程。在服務上，<xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> 會加入 <xref:System.ServiceModel.Activities.Receive> 活動，後面接著 <xref:System.ServiceModel.Activities.SendReply> 活動。<xref:System.ServiceModel.Activities.SendReply.Request> 屬性會自動設定為 <xref:System.ServiceModel.Activities.Receive> 活動。在用戶端上，<xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> 會加入 <xref:System.ServiceModel.Activities.Send> 活動，後面接著 <xref:System.ServiceModel.Activities.ReceiveReply>。<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> 屬性會自動設定為 <xref:System.ServiceModel.Activities.Send> 活動。若要使用這兩個範本，只要將適當的範本拖放至您的工作流程即可。  
  
## 訊息傳遞活動和交易  
 呼叫工作流程服務時，您可能想要讓交易流向服務作業。若要執行這項操作，請將 <xref:System.ServiceModel.Activities.Receive> 活動放置到 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動內。<xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動包含 `Receive` 活動和主體。流向服務的交易會在執行 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 主體的整個過程中維持環境。當主體執行完成時，交易也會完成。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]工作流程和交易的詳細資料，請參閱[工作流程交易](../../../../docs/framework/windows-workflow-foundation//workflow-transactions.md)。  
  
## 請參閱  
 [如何在工作流程服務中傳送和接收錯誤](http://go.microsoft.com/fwlink/?LinkId=189151)   
 [建立長期執行的工作流程服務](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)