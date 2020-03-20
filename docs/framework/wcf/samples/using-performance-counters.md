---
title: 使用效能計數器
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143573"
---
# <a name="using-performance-counters"></a><span data-ttu-id="37947-102">使用效能計數器</span><span class="sxs-lookup"><span data-stu-id="37947-102">Using Performance Counters</span></span>
<span data-ttu-id="37947-103">此示例演示如何訪問 Windows 通信基礎 （WCF） 效能計數器以及如何創建使用者定義的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="37947-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="37947-104">此示例基於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="37947-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37947-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="37947-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="37947-106">在這個範例中，用戶端呼叫 `ICalculator` 服務的四個方法。</span><span class="sxs-lookup"><span data-stu-id="37947-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="37947-107">用戶端持續此操作，直到被使用者中斷為止。</span><span class="sxs-lookup"><span data-stu-id="37947-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="37947-108">服務維持不變。</span><span class="sxs-lookup"><span data-stu-id="37947-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="37947-109">效能計數器在用於服務的 Web.config 檔案之診斷區段中啟用，如下列範例組態中所示。</span><span class="sxs-lookup"><span data-stu-id="37947-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="37947-110">此任務也可以使用[配置編輯器工具 （SvcConfigEditor.exe）](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)完成。</span><span class="sxs-lookup"><span data-stu-id="37947-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="37947-111">啟用效能計數器後，將為服務啟用整個 WCF 效能計數器套件。</span><span class="sxs-lookup"><span data-stu-id="37947-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="37947-112">.NET Framework 自動在三個層級保有效能資料：`ServiceModelService`、`ServiceModelEndpoint` 和 `ServiceModelOperation`。</span><span class="sxs-lookup"><span data-stu-id="37947-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="37947-113">這些層級中的每個層級都有效能計數器，例如「呼叫」、「每秒的呼叫數」和「未授權的安全性呼叫數」。</span><span class="sxs-lookup"><span data-stu-id="37947-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37947-114">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="37947-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="37947-115">確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="37947-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="37947-116">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="37947-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="37947-117">要在單電腦或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。</span><span class="sxs-lookup"><span data-stu-id="37947-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="37947-118">若要檢視效能資料</span><span class="sxs-lookup"><span data-stu-id="37947-118">To view performance data</span></span>  
  
1. <span data-ttu-id="37947-119">通過按一下"**開始**、**運行..."、** 輸入`perfmon`並按一下"**確定"** 或"從控制台"啟動效能監視器工具，選擇 **"管理工具**"並按兩下 **"性能**"。</span><span class="sxs-lookup"><span data-stu-id="37947-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="37947-120">在範例程式碼執行後才能新增計數器。</span><span class="sxs-lookup"><span data-stu-id="37947-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="37947-121">選擇列出的效能計數器，然後按 Delete 鍵將它們刪除。</span><span class="sxs-lookup"><span data-stu-id="37947-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="37947-122">通過按右鍵圖形窗格並選擇 **"添加計數器**"來添加 WCF 計數器。</span><span class="sxs-lookup"><span data-stu-id="37947-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="37947-123">在 **"添加計數器"** 對話方塊中，在"性能"物件下拉式清單方塊中選擇 **"服務模型操作 3.0.0.0"、服務模型終結點 3.0.0.0 或"服務模型服務 3.0.0.0"。"** 下拉式清單方塊中。</span><span class="sxs-lookup"><span data-stu-id="37947-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="37947-124">從清單中選取您要檢視的計數器。</span><span class="sxs-lookup"><span data-stu-id="37947-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="37947-125">如果電腦上沒有運行 WCF 服務，則服務沒有 WCF 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="37947-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="37947-126">若要使用組態編輯器來啟用計數器</span><span class="sxs-lookup"><span data-stu-id="37947-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="37947-127">開啟 SvcConfigEditor.exe 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="37947-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="37947-128">在"檔"功能表上，按一下 **"打開"，** 然後按一下"**設定檔..."。**</span><span class="sxs-lookup"><span data-stu-id="37947-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="37947-129">巡覽至範例應用程式的服務資料夾，並開啟 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="37947-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="37947-130">按一下"配置樹上的**診斷**"。</span><span class="sxs-lookup"><span data-stu-id="37947-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="37947-131">在 **"診斷"** 視窗中切換**效能計數器**以顯示"全部"。</span><span class="sxs-lookup"><span data-stu-id="37947-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="37947-132">儲存組態檔並結束編輯器。</span><span class="sxs-lookup"><span data-stu-id="37947-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="37947-133">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="37947-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="37947-134">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="37947-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="37947-135">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="37947-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37947-136">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="37947-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="37947-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37947-137">See also</span></span>

- <span data-ttu-id="37947-138">[AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="37947-138">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
