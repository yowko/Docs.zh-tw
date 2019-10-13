---
title: 疑難排解相互關聯
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: d4b7b4ecd724416256cf0b2499d7180200f4e75c
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291559"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="ae083-102">疑難排解相互關聯</span><span class="sxs-lookup"><span data-stu-id="ae083-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="ae083-103">相互關聯用於讓工作流程服務訊息彼此之間產生關聯，以及讓工作流程服務訊息和正確的工作流程執行個體產生關聯，但是，如果設定錯誤，將不會收到訊息，而且應用程式將不會正確運作。</span><span class="sxs-lookup"><span data-stu-id="ae083-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="ae083-104">本主題提供數個疑難排解相互關聯問題方法的概觀，同時也列出使用相互關聯時可能發生的部分常見問題。</span><span class="sxs-lookup"><span data-stu-id="ae083-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="ae083-105">處理 UnknownMessageReceived 事件</span><span class="sxs-lookup"><span data-stu-id="ae083-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="ae083-106">當服務收到不明訊息 (包括無法與現有執行個體相互關聯的訊息) 時，會發生 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> 事件。</span><span class="sxs-lookup"><span data-stu-id="ae083-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="ae083-107">若是自我裝載的服務，此事件可以在主機應用程式中處理。</span><span class="sxs-lookup"><span data-stu-id="ae083-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="ae083-108">若是 Web 託管服務，此事件可以透過從 <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> 衍生類別，然後覆寫 <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A> 來處理。</span><span class="sxs-lookup"><span data-stu-id="ae083-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

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

 <span data-ttu-id="ae083-109">接著，您可以在服務的 <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> 檔案中指定這個自訂 `svc`。</span><span class="sxs-lookup"><span data-stu-id="ae083-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 <span data-ttu-id="ae083-110">叫用此處理常式時，可以使用 <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> 的 <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> 屬性擷取訊息，而且類似下列訊息。</span><span class="sxs-lookup"><span data-stu-id="ae083-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```xml
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

 <span data-ttu-id="ae083-111">檢查發送至 <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> 處理常式的訊息可能會提供訊息沒有與工作流程服務執行個體相互關聯之原因的線索。</span><span class="sxs-lookup"><span data-stu-id="ae083-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="ae083-112">使用追蹤功能監視工作流程的進度</span><span class="sxs-lookup"><span data-stu-id="ae083-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="ae083-113">追蹤功能提供一種監視工作流程進度的方式。</span><span class="sxs-lookup"><span data-stu-id="ae083-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="ae083-114">根據預設，系統會針對工作流程生命週期事件、活動生命週期事件、錯誤傳播與書籤繼續，發出追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ae083-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="ae083-115">此外，自訂活動可以發出自訂追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ae083-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="ae083-116">疑難排解相互關聯時，活動追蹤記錄、書籤繼續記錄，以及錯誤傳播記錄最實用。</span><span class="sxs-lookup"><span data-stu-id="ae083-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="ae083-117">活動追蹤記錄可用來判斷工作流程目前的進度，而且有助於識別目前正在等待訊息的訊息活動。</span><span class="sxs-lookup"><span data-stu-id="ae083-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="ae083-118">書籤繼續記錄的實用之處在於指出訊息已由工作流程收到，而錯誤傳播記錄則提供工作流程中任何錯誤的記錄。</span><span class="sxs-lookup"><span data-stu-id="ae083-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="ae083-119">若要啟用追蹤功能，請在 <xref:System.Activities.Tracking.TrackingParticipant> 的 <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> 中指定所需的 <xref:System.ServiceModel.Activities.WorkflowServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="ae083-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="ae083-120">在下列範例中，會使用預設的追蹤設定檔來設定 `ConsoleTrackingParticipant` （來自[自訂追蹤](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md)範例）。</span><span class="sxs-lookup"><span data-stu-id="ae083-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="ae083-121">追蹤參與者 (例如 ConsoleTrackingParticipant) 對於擁有主控台視窗的自我裝載工作流程服務相當實用。</span><span class="sxs-lookup"><span data-stu-id="ae083-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="ae083-122">若是 Web 裝載的服務，則應該使用將追蹤資訊記錄到長期存放區的追蹤參與者，例如內建的 <xref:System.Activities.Tracking.EtwTrackingParticipant>，或將資訊記錄到檔案的自訂追蹤參與者。</span><span class="sxs-lookup"><span data-stu-id="ae083-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="ae083-123">如需追蹤和設定 Web 主控工作流程服務之追蹤的詳細資訊，請參閱[工作流程追蹤和追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)、設定[工作流程的追蹤](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)，[以及&#91;追蹤 WF&#93;範例](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md)範例。</span><span class="sxs-lookup"><span data-stu-id="ae083-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="ae083-124">使用 WCF 追蹤</span><span class="sxs-lookup"><span data-stu-id="ae083-124">Use WCF Tracing</span></span>
 <span data-ttu-id="ae083-125">WCF 追蹤可追蹤進出工作流程服務的訊息流量。</span><span class="sxs-lookup"><span data-stu-id="ae083-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="ae083-126">疑難排解相互關聯問題 (特別是以內容為主的相互關聯) 時，這個追蹤資訊相當實用。</span><span class="sxs-lookup"><span data-stu-id="ae083-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="ae083-127">若要啟用追蹤功能，請在 `system.diagnostics` 檔案 (如果是 Web 裝載的工作流程服務) 或 `web.config` 檔案 (如果是自我裝載的工作流程服務) 的 `app.config` 區段中，指定所需的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="ae083-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="ae083-128">若要將訊息內容納入追蹤檔中，在 `true` 之 `logEntireMessage` 區段的 `messageLogging` 項目中，針對 `diagnostics` 指定 `system.serviceModel`。</span><span class="sxs-lookup"><span data-stu-id="ae083-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="ae083-129">在以下範例中，追蹤資訊 (包括訊息內容) 會設定為寫入名稱為 `service.svclog` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="ae083-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

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

 <span data-ttu-id="ae083-130">若要查看包含在 `service.svclog` 中的追蹤資訊，請使用[服務追蹤檢視器工具（svctraceviewer.exe .exe）](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) 。</span><span class="sxs-lookup"><span data-stu-id="ae083-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="ae083-131">疑難排解以內容為主的相互關聯問題時，這特別有用，因為您可以檢視訊息內容並正確地查看傳遞的內容，以及是否符合以內容為主之相互關聯的 <xref:System.ServiceModel.CorrelationQuery>。</span><span class="sxs-lookup"><span data-stu-id="ae083-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="ae083-132">如需 WCF 追蹤的詳細資訊，請參閱[服務追蹤檢視器工具（svctraceviewer.exe）](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)、設定[追蹤](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)，以及[使用追蹤來疑難排解您的應用程式](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ae083-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="ae083-133">常見的內容交換相互關聯問題</span><span class="sxs-lookup"><span data-stu-id="ae083-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="ae083-134">特定類型的相互關聯會要求使用特定的繫結類型，才能讓相互關聯正確運作。</span><span class="sxs-lookup"><span data-stu-id="ae083-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="ae083-135">範例包括要求-回覆相互關聯 (需要雙向繫結，例如 <xref:System.ServiceModel.BasicHttpBinding>) 與內容交換相互關聯 (需要以內容為主的繫結，例如 <xref:System.ServiceModel.BasicHttpContextBinding>)。</span><span class="sxs-lookup"><span data-stu-id="ae083-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="ae083-136">大部分的繫結都支援雙向作業，因此，這不是要求-回覆相互關聯的常見問題，但是只有少數以內容為主的繫結，包括 <xref:System.ServiceModel.BasicHttpContextBinding>、<xref:System.ServiceModel.WSHttpContextBinding> 和 <xref:System.ServiceModel.NetTcpContextBinding>。</span><span class="sxs-lookup"><span data-stu-id="ae083-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="ae083-137">如果未使用以上其中一個繫結，對工作流程服務的初始呼叫將會成功，但是後續的呼叫將會失敗，並產生下列 <xref:System.ServiceModel.FaultException>。</span><span class="sxs-lookup"><span data-stu-id="ae083-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="ae083-138">用於內容相互關聯的內容資訊可以透過 <xref:System.ServiceModel.Activities.SendReply> 傳回到 <xref:System.ServiceModel.Activities.Receive> 活動，使用雙向作業時，這個活動會初始化內容關聯；如果是單向作業，則可透過呼叫者指定這個活動。</span><span class="sxs-lookup"><span data-stu-id="ae083-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="ae083-139">如果內容不是透過呼叫者傳送，或者不是透過工作流程服務傳回，則在叫用後續的作業時，將會傳回先前所述的相同 <xref:System.ServiceModel.FaultException>。</span><span class="sxs-lookup"><span data-stu-id="ae083-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="ae083-140">常見的要求-回覆相互關聯問題</span><span class="sxs-lookup"><span data-stu-id="ae083-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="ae083-141">要求-回復相互關聯會與 <xref:System.ServiceModel.Activities.Receive> @ no__t-1 @ no__t-2 配對搭配使用，以在工作流程服務中執行雙向作業，並具有 <xref:System.ServiceModel.Activities.Send> @ no__t-4 @ no__t-5 組，會在另一個 Web 服務中叫用雙向作業。</span><span class="sxs-lookup"><span data-stu-id="ae083-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="ae083-142">在 WCF 服務中叫用雙向作業時，服務可以是傳統的命令式程式碼型 WCF 服務，或者它可以是工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="ae083-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="ae083-143">若要使用要求-回覆相互關聯，則必須使用雙向繫結，例如 <xref:System.ServiceModel.BasicHttpBinding>，而且必須是雙向作業。</span><span class="sxs-lookup"><span data-stu-id="ae083-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="ae083-144">如果工作流程服務以平行方式進行雙向作業，或重迭 <xref:System.ServiceModel.Activities.Receive> @ no__t-1 @ no__t-2 或 <xref:System.ServiceModel.Activities.Send> @ no__t-4 @ no__t-5 組，則 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 所提供的隱含相互關聯控制碼管理可能不足夠，特別是在高壓力中案例和訊息可能無法正確地路由傳送。</span><span class="sxs-lookup"><span data-stu-id="ae083-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="ae083-145">若要防止發生這個問題，建議您在使用要求-回覆相互關聯時，一律明確指定 <xref:System.ServiceModel.Activities.CorrelationHandle>。</span><span class="sxs-lookup"><span data-stu-id="ae083-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="ae083-146">在工作流程設計工具中，從 **工具箱** 的 訊息 區段使用  **sendandreceivereply**  和  **receiveandsendreply**  範本時，預設會明確設定 <xref:System.ServiceModel.Activities.CorrelationHandle>。</span><span class="sxs-lookup"><span data-stu-id="ae083-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="ae083-147">使用程式碼建立工作流程時，在配對中第一個活動的 <xref:System.ServiceModel.Activities.CorrelationHandle> 內，會指定 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>。</span><span class="sxs-lookup"><span data-stu-id="ae083-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="ae083-148">以下範例會設定 <xref:System.ServiceModel.Activities.Receive> 活動，並在 <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> 中指定明確的 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>。</span><span class="sxs-lookup"><span data-stu-id="ae083-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

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

 <span data-ttu-id="ae083-149">@No__t-0 @ no__t-1 @ no__t-2 組或 <xref:System.ServiceModel.Activities.Send> @ no__t-4 @ no__t-5 配對之間不允許持續性。</span><span class="sxs-lookup"><span data-stu-id="ae083-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="ae083-150">系統會建立不保存區域，這個區域會持續直到兩個活動都完成為止。</span><span class="sxs-lookup"><span data-stu-id="ae083-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="ae083-151">如果某個活動 (例如延遲活動) 位於這個不保存區域中，並且導致工作流程變成閒置，工作流程將不會保存，即使主機設定為在工作流程變成閒置時保存它們也一樣。</span><span class="sxs-lookup"><span data-stu-id="ae083-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="ae083-152">如果某個活動 (例如持續活動) 嘗試明確保存在不保存區域中，系統就會擲回嚴重的例外狀況、工作流程會中止，而且 <xref:System.ServiceModel.FaultException> 會傳回給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="ae083-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="ae083-153">嚴重的例外狀況訊息為 "InvalidOperationException：保存活動不能包含在無持續性區塊中。」。</span><span class="sxs-lookup"><span data-stu-id="ae083-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="ae083-154">此例外狀況不會傳回給呼叫端，不過如果啟用了追蹤，就可以觀察此例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ae083-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="ae083-155">傳回給呼叫端之 <xref:System.ServiceModel.FaultException> 的訊息為「無法執行作業，因為 WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' 已完成」。</span><span class="sxs-lookup"><span data-stu-id="ae083-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="ae083-156">如需有關要求-回復相互關聯的詳細資訊，請參閱[要求-回復](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)。</span><span class="sxs-lookup"><span data-stu-id="ae083-156">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="ae083-157">常見的內容相互關聯問題</span><span class="sxs-lookup"><span data-stu-id="ae083-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="ae083-158">當工作流程服務收到多個訊息，而且交換的訊息中有一個資料片段能夠識別所需的執行個體時，就會使用以內容為主的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="ae083-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="ae083-159">以內容為主的相互關聯會利用訊息中的此項資料 (例如客戶編號或訂單 ID)，將訊息路由至正確的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="ae083-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="ae083-160">本節描述使用以內容為主之相互關聯時可能會發生的數個常見問題。</span><span class="sxs-lookup"><span data-stu-id="ae083-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="ae083-161">請確認識別資料是唯一的</span><span class="sxs-lookup"><span data-stu-id="ae083-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="ae083-162">用於識別執行個體的資料會雜湊成為相互關聯索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ae083-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="ae083-163">請特別小心確認用於關聯的資料是否為唯一的資料，否則雜湊索引鍵中可能會發生衝突，導致訊息路由錯誤。</span><span class="sxs-lookup"><span data-stu-id="ae083-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="ae083-164">例如，只以客戶名稱為主的相互關聯可能會造成衝突，因為可能會有具有相同名稱的多位客戶。</span><span class="sxs-lookup"><span data-stu-id="ae083-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="ae083-165">用於相互關聯訊息的資料中不可包含冒號 (:)，因為冒號已用於分隔訊息查詢的索引鍵和值，以形成後續雜湊的字串。</span><span class="sxs-lookup"><span data-stu-id="ae083-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="ae083-166">如果使用持續性，請確認先前持續存在的執行個體尚未使用目前的識別資料。</span><span class="sxs-lookup"><span data-stu-id="ae083-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="ae083-167">暫時停用持續性有助於識別這個問題。</span><span class="sxs-lookup"><span data-stu-id="ae083-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="ae083-168">WCF 追蹤可用於檢視計算的相互關聯索引鍵，而且對於此種問題的偵錯相當實用。</span><span class="sxs-lookup"><span data-stu-id="ae083-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="ae083-169">追蹤條件</span><span class="sxs-lookup"><span data-stu-id="ae083-169">Race Conditions</span></span>
 <span data-ttu-id="ae083-170">在服務收到訊息和實際初始化相互關聯之間有些微的時間差距，在這段期間，將會忽略後續追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="ae083-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="ae083-171">如果工作流程服務使用用戶端透過單向作業傳遞的資料初始化以內容為主的相互關聯，而且呼叫者傳送立即的後續追蹤訊息，則在這段間隔內，將會忽略這些訊息。</span><span class="sxs-lookup"><span data-stu-id="ae083-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="ae083-172">您可以使用雙向作業初始化相互關聯，或使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 來避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="ae083-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="ae083-173">相互關聯查詢問題</span><span class="sxs-lookup"><span data-stu-id="ae083-173">Correlation Query Issues</span></span>
 <span data-ttu-id="ae083-174">相互關聯查詢用於指定訊息中用來相互關聯訊息的資料。</span><span class="sxs-lookup"><span data-stu-id="ae083-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="ae083-175">此資料是使用 XPath 查詢指定。</span><span class="sxs-lookup"><span data-stu-id="ae083-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="ae083-176">如果在即使一切似乎正確的情況下也沒有對服務發送訊息，其中一個疑難排解策略就是指定符合訊息資料值 (而非 XPath 查詢) 的常值。</span><span class="sxs-lookup"><span data-stu-id="ae083-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="ae083-177">若要指定常值，請使用 `string` 函式。</span><span class="sxs-lookup"><span data-stu-id="ae083-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="ae083-178">在以下範例中，<xref:System.ServiceModel.MessageQuerySet> 會設定為使用 `11445` 的常值 `OrderId`，而且會取消註解 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="ae083-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

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

 <span data-ttu-id="ae083-179">如果 XPath 查詢的設定不正確，因此不會抓取任何相互關聯資料，則會傳回錯誤，並顯示下列訊息：「相互關聯查詢產生空白的結果集。</span><span class="sxs-lookup"><span data-stu-id="ae083-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="ae083-180">請確定已正確設定端點的相互關聯查詢」。</span><span class="sxs-lookup"><span data-stu-id="ae083-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="ae083-181">其中一種快速疑難排解此問題的方式為，將 XPath 查詢取代成常值，如上一節所述。</span><span class="sxs-lookup"><span data-stu-id="ae083-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="ae083-182">如果您在 [**加入相互關聯初始化運算式**] 或 [ **CorrelatesOn 定義**] 對話方塊中使用 XPath 查詢產生器，而且您的工作流程服務使用訊息合約，就可能會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="ae083-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="ae083-183">在下列範例中，系統會定義訊息合約類別。</span><span class="sxs-lookup"><span data-stu-id="ae083-183">In the following example, a message contract class is defined.</span></span>

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

 <span data-ttu-id="ae083-184">此訊息合約是由工作流程中的 <xref:System.ServiceModel.Activities.Receive> 活動所使用。</span><span class="sxs-lookup"><span data-stu-id="ae083-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="ae083-185">訊息標頭中的 `CartId` 是用來讓訊息與正確的執行個體相互關聯。</span><span class="sxs-lookup"><span data-stu-id="ae083-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="ae083-186">如果擷取 `CartId` 的 XPath 查詢是使用工作流程設計工具中的相互關聯對話方塊來建立，就會產生下列不正確的 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="ae083-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="ae083-187">如果 <xref:System.ServiceModel.Activities.Receive> 活動針對資料使用了參數，此 XPath 查詢就會正確，但是因為它使用了訊息合約，所以仍然不正確。</span><span class="sxs-lookup"><span data-stu-id="ae083-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="ae083-188">下列 XPath 查詢是要從標頭中擷取 `CartId` 的正確 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="ae083-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="ae083-189">您可以透過檢查訊息的本文來確認這點。</span><span class="sxs-lookup"><span data-stu-id="ae083-189">This can be confirmed by examining the body of the message.</span></span>

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

<span data-ttu-id="ae083-190">下列範例會顯示針對使用先前訊息合約來接收資料之 <xref:System.ServiceModel.Activities.Receive> 作業所設定的 `AddItem` 活動。</span><span class="sxs-lookup"><span data-stu-id="ae083-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="ae083-191">此 XPath 查詢的設定正確無誤。</span><span class="sxs-lookup"><span data-stu-id="ae083-191">The XPath query is correctly configured.</span></span>

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
