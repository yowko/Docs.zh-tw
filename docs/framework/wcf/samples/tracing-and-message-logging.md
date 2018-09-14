---
title: 追蹤和訊息記錄
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 7f729e845fe552d523a46a1783404baf4e0bbfca
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569407"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="1c247-102">追蹤和訊息記錄</span><span class="sxs-lookup"><span data-stu-id="1c247-102">Tracing and Message Logging</span></span>
<span data-ttu-id="1c247-103">這個範例示範如何啟用追蹤和訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="1c247-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="1c247-104">產生的追蹤和訊息記錄則會使用檢視[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1c247-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="1c247-105">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="1c247-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c247-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="1c247-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="1c247-107">追蹤</span><span class="sxs-lookup"><span data-stu-id="1c247-107">Tracing</span></span>  
 <span data-ttu-id="1c247-108">Windows Communication Foundation (WCF) 會使用在定義的追蹤機制<xref:System.Diagnostics>命名空間。</span><span class="sxs-lookup"><span data-stu-id="1c247-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="1c247-109">在這個追蹤模型中，應用程式實作的追蹤來源會產生追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="1c247-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="1c247-110">每個來源都是以名稱來識別。</span><span class="sxs-lookup"><span data-stu-id="1c247-110">Each source is identified by a name.</span></span> <span data-ttu-id="1c247-111">追蹤消費者會為他們要擷取資訊的追蹤來源建立追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="1c247-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="1c247-112">若要接收追蹤資料，就必須建立追蹤來源的接聽項。</span><span class="sxs-lookup"><span data-stu-id="1c247-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="1c247-113">在 WCF 中，做法是藉由將下列程式碼新增至服務或用戶端的組態檔中，藉由設定服務模型追蹤來源`switchValue`:</span><span class="sxs-lookup"><span data-stu-id="1c247-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="1c247-114">如需詳細的追蹤來源的詳細資訊，請參閱中的追蹤來源 > 一節[設定追蹤](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)主題。</span><span class="sxs-lookup"><span data-stu-id="1c247-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="1c247-115">活動追蹤和傳播</span><span class="sxs-lookup"><span data-stu-id="1c247-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="1c247-116">擁有`ActivityTracing`啟用並`propagateActivity`設為`true`在`system.ServiceModel`用戶端和服務的追蹤來源會提供追蹤的處理 （活動），邏輯單位內的相互關聯跨端點 （內的活動透過活動傳輸），以及跨多個端點 （透過活動識別碼傳播） 活動。</span><span class="sxs-lookup"><span data-stu-id="1c247-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="1c247-117">這三種機制 (活動、傳輸和傳播) 可以協助您使用 [服務追蹤檢閱器] 工具，迅速找到錯誤的根本原因。</span><span class="sxs-lookup"><span data-stu-id="1c247-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="1c247-118">如需詳細資訊，請參閱 <<c0> [ 使用服務追蹤檢視器檢視相互關聯的追蹤和疑難排解](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="1c247-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="1c247-119">您可以建立使用者定義的活動追蹤，來延伸 ServiceModel 所提供的追蹤。</span><span class="sxs-lookup"><span data-stu-id="1c247-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="1c247-120">使用者定義的活動追蹤允許使用者建立追蹤活動，以進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="1c247-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
-   <span data-ttu-id="1c247-121">將追蹤集合成工作邏輯單位的群組。</span><span class="sxs-lookup"><span data-stu-id="1c247-121">Group traces into logical units of work.</span></span>  
  
-   <span data-ttu-id="1c247-122">透過傳輸和傳播將活動相互關聯。</span><span class="sxs-lookup"><span data-stu-id="1c247-122">Correlate activities through transfers and propagation.</span></span>  
  
-   <span data-ttu-id="1c247-123">降低 （例如，記錄檔的磁碟空間成本） 的 WCF 追蹤的效能成本。</span><span class="sxs-lookup"><span data-stu-id="1c247-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="1c247-124">如需有關使用者定義的活動追蹤的詳細資訊，請參閱[擴充追蹤](../../../../docs/framework/wcf/samples/extending-tracing.md)範例。</span><span class="sxs-lookup"><span data-stu-id="1c247-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="1c247-125">訊息記錄</span><span class="sxs-lookup"><span data-stu-id="1c247-125">Message Logging</span></span>  
 <span data-ttu-id="1c247-126">用戶端和服務的任何 WCF 應用程式，可以啟用訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="1c247-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="1c247-127">若要啟用訊息記錄，您必須將下列程式碼新增至用戶端或服務：</span><span class="sxs-lookup"><span data-stu-id="1c247-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1c247-128">記錄訊息時，追蹤類型將依據是在用戶端或在伺服器上追蹤而定。</span><span class="sxs-lookup"><span data-stu-id="1c247-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="1c247-129">例如，在用戶端，傳送給用戶端的「新增」訊息會受到 "TransportWrite" 類型的追蹤，然而在服務上，相同的訊息則會受到 "TransportRead" 類型的追蹤。</span><span class="sxs-lookup"><span data-stu-id="1c247-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="1c247-130">設定追蹤接聽項，方式是將下列程式碼新增至用戶端的 App.config 檔案或服務的 Web.config 檔案的 <xref:System.Diagnostics> 區段：</span><span class="sxs-lookup"><span data-stu-id="1c247-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="1c247-131">在組態檔內指定的目標目錄中，會使用 XML 格式來記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="1c247-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c247-132">如果一開始並未建立記錄目錄，就不會建立追蹤檔。</span><span class="sxs-lookup"><span data-stu-id="1c247-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="1c247-133">請確定目錄 C:\logs\ 存在，不然就在接聽項組態中指定其他記錄目錄。</span><span class="sxs-lookup"><span data-stu-id="1c247-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="1c247-134">如需詳細資訊，請參閱本文件結尾的初始安裝指示。</span><span class="sxs-lookup"><span data-stu-id="1c247-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="1c247-135">如需訊息記錄的詳細資訊，請參閱[設定訊息記錄](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)主題。</span><span class="sxs-lookup"><span data-stu-id="1c247-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1c247-136">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="1c247-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1c247-137">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1c247-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1c247-138">在執行追蹤和訊息記錄範例前，請先建立可供服務將 .svclog 檔寫入的 C:\logs\ 目錄。</span><span class="sxs-lookup"><span data-stu-id="1c247-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="1c247-139">這個目錄名稱會在組態檔中定義為所要記錄之追蹤和訊息的路徑，而您可以變更此名稱。</span><span class="sxs-lookup"><span data-stu-id="1c247-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="1c247-140">請提供使用者對記錄目錄的網路服務寫入權限。</span><span class="sxs-lookup"><span data-stu-id="1c247-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3.  <span data-ttu-id="1c247-141">若要建置方案的 C#、 c + + 或 Visual Basic.NET 版本，請依照下列中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1c247-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="1c247-142">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1c247-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1c247-143">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1c247-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1c247-144">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="1c247-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1c247-145">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="1c247-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1c247-146">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="1c247-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="1c247-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c247-147">See Also</span></span>  
 [<span data-ttu-id="1c247-148">追蹤</span><span class="sxs-lookup"><span data-stu-id="1c247-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1c247-149">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="1c247-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
