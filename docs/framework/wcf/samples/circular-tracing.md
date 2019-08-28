---
title: 循環追蹤
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: ad3e4acca7e4bce24c839e71381bf321365a4b2e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045684"
---
# <a name="circular-tracing"></a><span data-ttu-id="ba8d0-102">循環追蹤</span><span class="sxs-lookup"><span data-stu-id="ba8d0-102">Circular Tracing</span></span>

<span data-ttu-id="ba8d0-103">這個範例會示範循環緩衝區追蹤接聽項的實作。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="ba8d0-104">實際執行服務的常見案例是產生可長時間使用的服務以及可在低階進行的追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="ba8d0-105">這些服務會耗用大量的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="ba8d0-106">在進行服務疑難排解時，追蹤記錄中最近的資料往往最切合問題的解決。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="ba8d0-107">這個範例將示範實作循環緩衝區追蹤接聽項，其中會將最近的追蹤保存在磁碟上，最多到某個可設定的資料數量。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="ba8d0-108">這個範例是以[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎, 並包含自訂的追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="ba8d0-109">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ba8d0-110">這個範例假設您已熟悉[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)範例, 並已閱讀為[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)範例提供的檔。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="ba8d0-111">循環緩衝區追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="ba8d0-111">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="ba8d0-112">實作「循環緩衝區追蹤接聽項」的基本概念是產生兩個檔案，而這兩個檔案可以各自儲存多達追蹤記錄資料總共所需數量的一半。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="ba8d0-113">接聽項會先建立一個檔案，再寫入該檔案直到資料大小上限的一半為止，然後於此時切換到第二個檔案。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="ba8d0-114">當接聽項寫入到達第二個檔案的限制時，便會將新的追蹤覆寫到第一個檔案。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="ba8d0-115">此接聽程式衍生自`XmlWriteTraceListener` , 並可讓您使用[服務追蹤檢視器工具 (svctraceviewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)來查看記錄。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="ba8d0-116">當您嘗試檢視記錄時，只要在 [服務追蹤檢視器] 工具中同時開啟這兩個記錄檔，就可以輕易地將兩個記錄檔重新合併。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="ba8d0-117">[服務追蹤檢視器] 工具會自動排序追蹤，讓它們依照正確的順序出現。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="ba8d0-118">組態</span><span class="sxs-lookup"><span data-stu-id="ba8d0-118">Configuration</span></span>

<span data-ttu-id="ba8d0-119">您可以為接聽項與來源項目新增下列程式碼，以便將服務設定為使用循環緩衝區追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="ba8d0-120">在循環追蹤接聽項的組態中設定 `maxFileSizeKB` 屬性，可以指定檔案大小的上限。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="ba8d0-121">這點會在下列程式碼中示範。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-121">This is demonstrated in the following code.</span></span>

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">
      <listeners>
        <add name="CircularTraceListener" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />
  </sharedListeners>
  <trace autoflush="true" />
</system.diagnostics>
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ba8d0-122">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ba8d0-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ba8d0-123">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ba8d0-124">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="ba8d0-125">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba8d0-126">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ba8d0-127">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ba8d0-128">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba8d0-129">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ba8d0-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="ba8d0-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba8d0-130">See also</span></span>

- [<span data-ttu-id="ba8d0-131">AppFabric 監視範例</span><span class="sxs-lookup"><span data-stu-id="ba8d0-131">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
