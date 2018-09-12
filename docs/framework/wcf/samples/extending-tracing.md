---
title: 擴充追蹤
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 02dfcc099883ed1d5e97b4f7b1a1f76d49b27a20
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494196"
---
# <a name="extending-tracing"></a><span data-ttu-id="05417-102">擴充追蹤</span><span class="sxs-lookup"><span data-stu-id="05417-102">Extending Tracing</span></span>
<span data-ttu-id="05417-103">此範例會示範如何擴充 Windows Communication Foundation (WCF) 追蹤功能，藉由在用戶端和服務的程式碼中撰寫使用者定義的活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="05417-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="05417-104">這樣可以讓使用者建立追蹤活動，並將追蹤分組成工作的邏輯單位 (Logical Unit)。</span><span class="sxs-lookup"><span data-stu-id="05417-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="05417-105">也可以透過傳輸 (在相同的端點內) 以及傳播 (跨端點) 方式來關聯活動。</span><span class="sxs-lookup"><span data-stu-id="05417-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="05417-106">在此範例中，用戶端與服務都會啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="05417-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="05417-107">如需如何在用戶端與服務組態檔中啟用追蹤的詳細資訊，請參閱[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="05417-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="05417-108">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="05417-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05417-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="05417-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05417-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="05417-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="05417-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="05417-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="05417-112">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="05417-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="05417-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="05417-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="05417-114">追蹤與活動傳播</span><span class="sxs-lookup"><span data-stu-id="05417-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="05417-115">使用者定義的活動追蹤 」 可讓使用者建立自己的 「 追蹤 」 活動來群組追蹤成邏輯單元的工作，讓透過傳輸和傳播的活動相互關聯並降低 （例如，成本的磁碟空間的 WCF 追蹤的效能成本記錄檔）。</span><span class="sxs-lookup"><span data-stu-id="05417-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="05417-116">新增自訂來源</span><span class="sxs-lookup"><span data-stu-id="05417-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="05417-117">使用者定義的追蹤可以同時新增至用戶端與服務程式碼。</span><span class="sxs-lookup"><span data-stu-id="05417-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="05417-118">新增這些自訂追蹤記錄並顯示在允許用戶端或服務組態檔的追蹤來源[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="05417-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="05417-119">下列程式碼示範如何將名為 `ServerCalculatorTraceSource` 之使用者定義的追蹤來源新增至組態檔。</span><span class="sxs-lookup"><span data-stu-id="05417-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a><span data-ttu-id="05417-120">關聯活動</span><span class="sxs-lookup"><span data-stu-id="05417-120">Correlating Activities</span></span>  
 <span data-ttu-id="05417-121">若要直接關聯跨端點的活動，在 `propagateActivity` 追蹤來源中的 `true` 屬性必須設定為 `System.ServiceModel`。</span><span class="sxs-lookup"><span data-stu-id="05417-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="05417-122">此外，若要傳播追蹤，而不經由 WCF 活動，ServiceModel 活動追蹤必須關閉。</span><span class="sxs-lookup"><span data-stu-id="05417-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="05417-123">這項設定將如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="05417-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05417-124">關閉 ServiceModel 活動追蹤的方式不同於指定追蹤層級 (以設定為 Off 的 `switchValue` 屬性表示)。</span><span class="sxs-lookup"><span data-stu-id="05417-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="05417-125">降低效能成本</span><span class="sxs-lookup"><span data-stu-id="05417-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="05417-126">將 `ActivityTracing` 追蹤來源中的 `System.ServiceModel` 設定為 Off 時會產生追蹤檔，其中只包含使用者定義的活動追蹤，而不包含任何 ServiceModel 活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="05417-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="05417-127">這樣會使記錄檔的大小變小許多。</span><span class="sxs-lookup"><span data-stu-id="05417-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="05417-128">不過，有機會將 WCF 處理追蹤相互關聯會遺失。</span><span class="sxs-lookup"><span data-stu-id="05417-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="05417-129">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="05417-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="05417-130">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="05417-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="05417-131">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="05417-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="05417-132">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="05417-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05417-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05417-133">See Also</span></span>  
 [<span data-ttu-id="05417-134">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="05417-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
