---
title: 擴充追蹤
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: f2b9deb346077609193ec08c2c01b10a3ad9357b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556508"
---
# <a name="extend-tracing"></a><span data-ttu-id="f32e1-102">擴充追蹤</span><span class="sxs-lookup"><span data-stu-id="f32e1-102">Extend tracing</span></span>

<span data-ttu-id="f32e1-103">這個範例示範如何在用戶端和服務程式代碼中撰寫使用者定義的活動追蹤，以擴充 Windows Communication Foundation (WCF) 追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="f32e1-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="f32e1-104">撰寫使用者定義的活動追蹤可讓使用者建立追蹤活動，並將追蹤群組至工作的邏輯單元。</span><span class="sxs-lookup"><span data-stu-id="f32e1-104">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="f32e1-105">也可以透過傳輸 (在相同的端點內) 以及傳播 (跨端點) 方式來關聯活動。</span><span class="sxs-lookup"><span data-stu-id="f32e1-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="f32e1-106">在此範例中，用戶端與服務都會啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="f32e1-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="f32e1-107">如需如何在用戶端和服務設定檔中啟用追蹤的詳細資訊，請參閱 [追蹤和訊息記錄](tracing-and-message-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="f32e1-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="f32e1-108">這個範例是以 [消費者入門](getting-started-sample.md)為基礎。</span><span class="sxs-lookup"><span data-stu-id="f32e1-108">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f32e1-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="f32e1-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f32e1-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f32e1-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f32e1-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f32e1-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f32e1-112">如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="f32e1-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f32e1-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f32e1-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="f32e1-114">追蹤與活動傳播</span><span class="sxs-lookup"><span data-stu-id="f32e1-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="f32e1-115">使用者定義的活動追蹤可讓使用者建立自己的追蹤活動，將追蹤分組為工作的邏輯單元、透過傳輸和傳播來使活動相互關聯，以及降低 WCF 追蹤 (的效能成本，例如記錄檔) 的磁碟空間成本。</span><span class="sxs-lookup"><span data-stu-id="f32e1-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="f32e1-116">新增自訂來源</span><span class="sxs-lookup"><span data-stu-id="f32e1-116">Add custom sources</span></span>  
 <span data-ttu-id="f32e1-117">使用者定義的追蹤可以同時新增至用戶端與服務程式碼。</span><span class="sxs-lookup"><span data-stu-id="f32e1-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="f32e1-118">將追蹤來源新增至用戶端或服務設定檔，可讓您在 [服務追蹤檢視器工具 ( # A0) ](../service-trace-viewer-tool-svctraceviewer-exe.md)中記錄和顯示這些自訂追蹤。</span><span class="sxs-lookup"><span data-stu-id="f32e1-118">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="f32e1-119">下列程式碼示範如何將名為 `ServerCalculatorTraceSource` 之使用者定義的追蹤來源新增至組態檔。</span><span class="sxs-lookup"><span data-stu-id="f32e1-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="f32e1-120">關聯活動</span><span class="sxs-lookup"><span data-stu-id="f32e1-120">Correlate activities</span></span>  
 <span data-ttu-id="f32e1-121">若要直接關聯跨端點的活動，在 `propagateActivity` 追蹤來源中的 `true` 屬性必須設定為 `System.ServiceModel`。</span><span class="sxs-lookup"><span data-stu-id="f32e1-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="f32e1-122">此外，若要在不經過 WCF 活動的情況下傳播追蹤，必須關閉 [System.servicemodel 活動追蹤]。</span><span class="sxs-lookup"><span data-stu-id="f32e1-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="f32e1-123">這項設定將如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="f32e1-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f32e1-124">關閉 ServiceModel 活動追蹤的方式不同於指定追蹤層級 (以設定為 Off 的 `switchValue` 屬性表示)。</span><span class="sxs-lookup"><span data-stu-id="f32e1-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="f32e1-125">降低效能成本</span><span class="sxs-lookup"><span data-stu-id="f32e1-125">Lessen performance cost</span></span>  
 <span data-ttu-id="f32e1-126">將 `ActivityTracing` 追蹤來源中的 `System.ServiceModel` 設定為 Off 時會產生追蹤檔，其中只包含使用者定義的活動追蹤，而不包含任何 ServiceModel 活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="f32e1-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="f32e1-127">排除 System.servicemodel 活動追蹤會導致較小的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f32e1-127">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="f32e1-128">但是，將 WCF 處理追蹤相互關聯的機會會遺失。</span><span class="sxs-lookup"><span data-stu-id="f32e1-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="f32e1-129">設定、建立及執行範例</span><span class="sxs-lookup"><span data-stu-id="f32e1-129">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f32e1-130">確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f32e1-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f32e1-131">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="f32e1-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f32e1-132">若要在單一或跨電腦的設定中執行範例，請遵循執行 [Windows Communication Foundation 範例](running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="f32e1-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32e1-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f32e1-133">See also</span></span>

- <span data-ttu-id="f32e1-134">[AppFabric 監控範例](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f32e1-134">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
