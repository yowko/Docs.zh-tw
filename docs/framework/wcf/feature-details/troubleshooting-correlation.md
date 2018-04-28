---
title: 疑難排解相互關聯
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5bdf111e6802692aef893cf9dcae88f0f51aa467
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="troubleshooting-correlation"></a>疑難排解相互關聯
相互關聯用於讓工作流程服務訊息彼此之間產生關聯，以及讓工作流程服務訊息和正確的工作流程執行個體產生關聯，但是，如果設定錯誤，將不會收到訊息，而且應用程式將不會正確運作。 本主題提供數個疑難排解相互關聯問題方法的概觀，同時也列出使用相互關聯時可能發生的部分常見問題。  
  
## <a name="handle-the-unknownmessagereceived-event"></a>處理 UnknownMessageReceived 事件  
 當服務收到不明訊息 (包括無法與現有執行個體相互關聯的訊息) 時，會發生 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> 事件。 若是自我裝載的服務，此事件可以在主機應用程式中處理。  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 若是 Web 託管服務，此事件可以透過從 <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> 衍生類別，然後覆寫 <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A> 來處理。  
  
```csharp  
class CustomFactory : WorkflowServiceHostFactory  
{  
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)  
    {  
        // Create the WorkflowServiceHost.  
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);  
  
        // Handle the UnknownMessageReceived event.  
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
        {  
            Console.WriteLine("Unknown Message Received:");  
            Console.WriteLine(e.Message);  
        };  
  
        return host;  
    }  
}  
```  
  
 接著，您可以在服務的 <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> 檔案中指定這個自訂 `svc`。  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 叫用此處理常式時，可以使用 <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> 的 <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> 屬性擷取訊息，而且類似下列訊息。  
  
```Output  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
  </s:Header>  
  <s:Body>  
    <AddItem xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItem>  
  </s:Body>  
</s:Envelope>  
```  
  
 檢查發送至 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> 處理常式的訊息可能會提供訊息沒有與工作流程服務執行個體相互關聯之原因的線索。  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a>使用追蹤功能監視工作流程的進度  
 追蹤功能提供一種監視工作流程進度的方式。 根據預設，系統會針對工作流程生命週期事件、活動生命週期事件、錯誤傳播與書籤繼續，發出追蹤記錄。 此外，自訂活動可以發出自訂追蹤記錄。 疑難排解相互關聯時，活動追蹤記錄、書籤繼續記錄，以及錯誤傳播記錄最實用。 活動追蹤記錄可用來判斷工作流程目前的進度，而且有助於識別目前正在等待訊息的訊息活動。 書籤繼續記錄的實用之處在於指出訊息已由工作流程收到，而錯誤傳播記錄則提供工作流程中任何錯誤的記錄。 若要啟用追蹤功能，請在 <xref:System.Activities.Tracking.TrackingParticipant> 的 <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> 中指定所需的 <xref:System.ServiceModel.Activities.WorkflowServiceHost>。 在下列範例中， `ConsoleTrackingParticipant` (從[自訂追蹤](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md)範例) 使用預設的追蹤設定檔所設定。  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 追蹤參與者 (例如 ConsoleTrackingParticipant) 對於擁有主控台視窗的自我裝載工作流程服務相當實用。 Web 主控服務中，對長期存放區會將追蹤資訊記錄的追蹤參與者應該使用，例如內建<xref:System.Activities.Tracking.EtwTrackingParticipant>，或自訂追蹤參與者，可將資訊記錄至檔案，例如`TextWriterTrackingParticpant`從[追蹤使用文字檔](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md)範例。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 追蹤及設定追蹤 Web 裝載的工作流程服務，請參閱[工作流程追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)，[流程設定追蹤](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)，而[追蹤&#91;WF範例&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md)範例。  
  
## <a name="use-wcf-tracing"></a>使用 WCF 追蹤  
 WCF 追蹤可追蹤進出工作流程服務的訊息流量。 疑難排解相互關聯問題 (特別是以內容為主的相互關聯) 時，這個追蹤資訊相當實用。 若要啟用追蹤功能，請在 `system.diagnostics` 檔案 (如果是 Web 裝載的工作流程服務) 或 `web.config` 檔案 (如果是自我裝載的工作流程服務) 的 `app.config` 區段中，指定所需的追蹤接聽項。 若要將訊息內容納入追蹤檔中，在 `true` 之 `logEntireMessage` 區段的 `messageLogging` 項目中，針對 `diagnostics` 指定 `system.serviceModel`。 在以下範例中，追蹤資訊 (包括訊息內容) 會設定為寫入名稱為 `service.svclog` 的檔案。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
    </sources>  
  
    <sharedListeners>  
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging logEntireMessage="true" logMalformedMessages="false"  
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">  
      </messageLogging>  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 若要檢視追蹤資訊包含在`service.svclog`、[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)用。 疑難排解以內容為主的相互關聯問題時，這特別有用，因為您可以檢視訊息內容並正確地查看傳遞的內容，以及是否符合以內容為主之相互關聯的 <xref:System.ServiceModel.CorrelationQuery>。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] WCF 追蹤，請參閱[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)，[設定追蹤](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)，和[使用追蹤疑難排解您的應用程式](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。  
  
## <a name="common-context-exchange-correlation-issues"></a>常見的內容交換相互關聯問題  
 特定類型的相互關聯會要求使用特定的繫結類型，才能讓相互關聯正確運作。 範例包括要求-回覆相互關聯 (需要雙向繫結，例如 <xref:System.ServiceModel.BasicHttpBinding>) 與內容交換相互關聯 (需要以內容為主的繫結，例如 <xref:System.ServiceModel.BasicHttpContextBinding>)。 大部分的繫結都支援雙向作業，因此，這不是要求-回覆相互關聯的常見問題，但是只有少數以內容為主的繫結，包括 <xref:System.ServiceModel.BasicHttpContextBinding>、<xref:System.ServiceModel.WSHttpContextBinding> 和 <xref:System.ServiceModel.NetTcpContextBinding>。 如果未使用以上其中一個繫結，對工作流程服務的初始呼叫將會成功，但是後續的呼叫將會失敗，並產生下列 <xref:System.ServiceModel.FaultException>。  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 用於內容相互關聯的內容資訊可以透過 <xref:System.ServiceModel.Activities.SendReply> 傳回到 <xref:System.ServiceModel.Activities.Receive> 活動，使用雙向作業時，這個活動會初始化內容關聯；如果是單向作業，則可透過呼叫者指定這個活動。 如果內容不是透過呼叫者傳送，或者不是透過工作流程服務傳回，則在叫用後續的作業時，將會傳回先前所述的相同 <xref:System.ServiceModel.FaultException>。  
  
 如需詳細資訊，請參閱[Context Exchange](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)。  
  
## <a name="common-request-reply-correlation-issues"></a>常見的要求-回覆相互關聯問題  
 要求-回覆相互關聯會搭配<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組用來實作雙向作業，在工作流程服務與<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>叫用雙向作業中另一個 Web 組服務。 在 WCF 服務中叫用雙向作業時，服務可以是傳統的命令式程式碼架構 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，或是工作流程服務。 若要使用要求-回覆相互關聯，則必須使用雙向繫結，例如 <xref:System.ServiceModel.BasicHttpBinding>，而且必須是雙向作業。  
  
 如果工作流程服務的雙向作業在平行或重疊<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>或<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>組，則隱含的相互關聯控制代碼管理提供<xref:System.ServiceModel.Activities.WorkflowServiceHost>可能不夠，特別是在高壓力的情況下，訊息可能不會正確路由和。 若要防止發生這個問題，建議您在使用要求-回覆相互關聯時，一律明確指定 <xref:System.ServiceModel.Activities.CorrelationHandle>。 當使用**SendAndReceiveReply**和**ReceiveAndSendReply**從傳訊 區段的範本**工具箱**中工作流程設計工具中， <xref:System.ServiceModel.Activities.CorrelationHandle>明確預設設定。 使用程式碼建立工作流程時，在配對中第一個活動的 <xref:System.ServiceModel.Activities.CorrelationHandle> 內，會指定 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>。 以下範例會設定 <xref:System.ServiceModel.Activities.Receive> 活動，並在 <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> 中指定明確的 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>。  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = ... // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 之間，不允許持續性<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組或<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>組。 系統會建立不保存區域，這個區域會持續直到兩個活動都完成為止。 如果某個活動 (例如延遲活動) 位於這個不保存區域中，並且導致工作流程變成閒置，工作流程將不會保存，即使主機設定為在工作流程變成閒置時保存它們也一樣。 如果某個活動 (例如持續活動) 嘗試明確保存在不保存區域中，系統就會擲回嚴重的例外狀況、工作流程會中止，而且 <xref:System.ServiceModel.FaultException> 會傳回給呼叫端。 嚴重的例外狀況訊息為「System.InvalidOperationException: 持續活動不能包含在無持續性區塊中」。 此例外狀況不會傳回給呼叫端，不過如果啟用了追蹤，就可以觀察此例外狀況。 傳回給呼叫端之 <xref:System.ServiceModel.FaultException> 的訊息為「無法執行作業，因為 WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' 已完成」。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 要求-回覆相互關聯，請參閱[要求-回覆](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)。  
  
## <a name="common-content-correlation-issues"></a>常見的內容相互關聯問題  
 當工作流程服務收到多個訊息，而且交換的訊息中有一個資料片段能夠識別所需的執行個體時，就會使用以內容為主的相互關聯。 以內容為主的相互關聯會利用訊息中的此項資料 (例如客戶編號或訂單 ID)，將訊息路由至正確的工作流程執行個體。 本節描述使用以內容為主之相互關聯時可能會發生的數個常見問題。  
  
### <a name="ensure-the-identifying-data-is-unique"></a>請確認識別資料是唯一的  
 用於識別執行個體的資料會雜湊成為相互關聯索引鍵。 請特別小心確認用於關聯的資料是否為唯一的資料，否則雜湊索引鍵中可能會發生衝突，導致訊息路由錯誤。 例如，只以客戶名稱為主的相互關聯可能會造成衝突，因為可能會有具有相同名稱的多位客戶。 用於相互關聯訊息的資料中不可包含冒號 (:)，因為冒號已用於分隔訊息查詢的索引鍵和值，以形成後續雜湊的字串。 如果使用持續性，請確認先前持續存在的執行個體尚未使用目前的識別資料。 暫時停用持續性有助於識別這個問題。 WCF 追蹤可用於檢視計算的相互關聯索引鍵，而且對於此種問題的偵錯相當實用。  
  
### <a name="race-conditions"></a>追蹤條件  
 在服務收到訊息和實際初始化相互關聯之間有些微的時間差距，在這段期間，將會忽略後續追蹤訊息。 如果工作流程服務使用用戶端透過單向作業傳遞的資料初始化以內容為主的相互關聯，而且呼叫者傳送立即的後續追蹤訊息，則在這段間隔內，將會忽略這些訊息。 您可以使用雙向作業初始化相互關聯，或使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 來避免這個問題。  
  
### <a name="correlation-query-issues"></a>相互關聯查詢問題  
 相互關聯查詢用於指定訊息中用來相互關聯訊息的資料。 此資料是使用 XPath 查詢指定。 如果在即使一切似乎正確的情況下也沒有對服務發送訊息，其中一個疑難排解策略就是指定符合訊息資料值 (而非 XPath 查詢) 的常值。 若要指定常值，請使用 `string` 函式。 在以下範例中，<xref:System.ServiceModel.MessageQuerySet> 會設定為使用 `11445` 的常值 `OrderId`，而且會取消註解 XPath 查詢。  
  
```csharp  
MessageQuerySet = new MessageQuerySet  
{  
    {  
        "OrderId",   
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")  
        new XPathMessageQuery("string('11445')")  
    }  
}  
```  
  
 如果 XPath 查詢的設定不正確，因而無法擷取任何相互關聯資料，系統就會傳回錯誤並顯示下列訊息：「相互關聯查詢產生空白的結果集。 請確定已正確設定端點的相互關聯查詢」。 其中一種快速疑難排解此問題的方式為，將 XPath 查詢取代成常值，如上一節所述。 如果您使用 XPath 查詢產生器中的，會發生此問題**加入相互關聯初始設定式**或**CorrelatesOn 定義**對話方塊和工作流程服務使用訊息合約。 在下列範例中，系統會定義訊息合約類別。  
  
```csharp  
[MessageContract]  
public class AddItemMessage  
{  
    [MessageHeader]  
    public string CartId;  
  
    [MessageBodyMember]  
    public string Item;  
}  
```  
  
 此訊息合約是由工作流程中的 <xref:System.ServiceModel.Activities.Receive> 活動所使用。 訊息標頭中的 `CartId` 是用來讓訊息與正確的執行個體相互關聯。 如果擷取 `CartId` 的 XPath 查詢是使用工作流程設計工具中的相互關聯對話方塊來建立，就會產生下列不正確的 XPath 查詢。  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 如果 <xref:System.ServiceModel.Activities.Receive> 活動針對資料使用了參數，此 XPath 查詢就會正確，但是因為它使用了訊息合約，所以仍然不正確。 下列 XPath 查詢是要從標頭中擷取 `CartId` 的正確 XPath 查詢。  
  
```  
sm:header()/tempuri:CartId  
```  
  
 您可以透過檢查訊息的本文來確認這點。  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>  
  </s:Header>  
  <s:Body>  
    <AddItemMessage xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItemMessage>  
  </s:Body>  
</s:Envelope>  
```  
  
 下列範例會顯示針對使用先前訊息合約來接收資料之 <xref:System.ServiceModel.Activities.Receive> 作業所設定的 `AddItem` 活動。 此 XPath 查詢的設定正確無誤。  
  
```xaml  
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">  
  <Receive.CorrelatesOn>  
    <XPathMessageQuery x:Key="key1">  
      <XPathMessageQuery.Namespaces>  
        <ssx:XPathMessageContextMarkup>  
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>  
        </ssx:XPathMessageContextMarkup>  
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>  
  </Receive.CorrelatesOn>  
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">  
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>  
  </ReceiveMessageContent>  
</Receive>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 以內容為基礎的相互關聯，請參閱[內容基礎](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)和[相互關聯計算機](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)範例。
