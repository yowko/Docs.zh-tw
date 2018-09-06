---
title: SQL 追蹤
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 5f8d7bbd57965b4d7399373416caea87d4d84187
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779139"
---
# <a name="sql-tracking"></a><span data-ttu-id="547d0-102">SQL 追蹤</span><span class="sxs-lookup"><span data-stu-id="547d0-102">SQL Tracking</span></span>
<span data-ttu-id="547d0-103">此範例示範如何撰寫自訂的 SQL 追蹤參與者，將追蹤記錄寫入至 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="547d0-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> <span data-ttu-id="547d0-104">Windows Workflow Foundation (WF) 提供工作流程追蹤來查看執行工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="547d0-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="547d0-105">追蹤執行階段會在工作流程執行期間發出工作流程追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="547d0-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="547d0-106">如需有關工作流程追蹤的詳細資訊，請參閱 <<c0> [ 工作流程追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="547d0-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="547d0-107">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="547d0-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="547d0-108">確定您已安裝 SQL Server 2008、SQL Server 2008 Express 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="547d0-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="547d0-109">隨範例封裝的指令碼假定在本機電腦上使用 SQL Express 執行個體。</span><span class="sxs-lookup"><span data-stu-id="547d0-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="547d0-110">如果您有不同的執行個體，在執行範例之前請先修改資料庫相關指令碼。</span><span class="sxs-lookup"><span data-stu-id="547d0-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>  
  
2.  <span data-ttu-id="547d0-111">執行指令碼目錄 (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 中的 Trackingsetup.cmd，建立 SQL Server 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="547d0-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="547d0-112">這會建立名為 TrackingSample 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="547d0-112">This creates a database called TrackingSample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="547d0-113">指令碼會在 SQL Express 預設執行個體上建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="547d0-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="547d0-114">如果您想要安裝在不同的資料庫執行個體上，請編輯 Trackingsetup.cmd 指令碼。</span><span class="sxs-lookup"><span data-stu-id="547d0-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3.  <span data-ttu-id="547d0-115">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 SqlTrackingSample.sln。</span><span class="sxs-lookup"><span data-stu-id="547d0-115">Open SqlTrackingSample.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="547d0-116">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="547d0-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="547d0-117">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="547d0-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="547d0-118">瀏覽器視窗隨即開啟並顯示應用程式的目錄清單。</span><span class="sxs-lookup"><span data-stu-id="547d0-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6.  <span data-ttu-id="547d0-119">在瀏覽器中，按一下 StockPriceService.xamlx。</span><span class="sxs-lookup"><span data-stu-id="547d0-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7.  <span data-ttu-id="547d0-120">瀏覽器隨即顯示 StockPriceService 頁面，其中包含本機服務 WSDL 位址。</span><span class="sxs-lookup"><span data-stu-id="547d0-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="547d0-121">複製此位址。</span><span class="sxs-lookup"><span data-stu-id="547d0-121">Copy this address.</span></span>  
  
     <span data-ttu-id="547d0-122">本機服務 WSDL 位址的範例是 http://localhost:65193/StockPriceService.xamlx?wsdl。</span><span class="sxs-lookup"><span data-stu-id="547d0-122">An example of the local service WSDL address is http://localhost:65193/StockPriceService.xamlx?wsdl.</span></span>  
  
8.  <span data-ttu-id="547d0-123">使用 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] 來執行 WCF 測試用戶端 (WcfTestClient.exe)。</span><span class="sxs-lookup"><span data-stu-id="547d0-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="547d0-124">它是位於 Microsoft Visual Studio 10.0\Common7\IDE 目錄中。</span><span class="sxs-lookup"><span data-stu-id="547d0-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="547d0-125">在 WCF 測試用戶端中，按一下**檔案**功能表，然後選取**加入服務**。</span><span class="sxs-lookup"><span data-stu-id="547d0-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="547d0-126">將本機服務位址貼至文字方塊。</span><span class="sxs-lookup"><span data-stu-id="547d0-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="547d0-127">按一下 **確定**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="547d0-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="547d0-128">在 WCF 測試用戶端中，按兩下**GetStockPrice**。</span><span class="sxs-lookup"><span data-stu-id="547d0-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="547d0-129">這會開啟`GetStockPrice`作業會採用一個參數，在值中的型別`Contoso`然後按一下**叫用**。</span><span class="sxs-lookup"><span data-stu-id="547d0-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="547d0-130">發出的追蹤記錄會寫入至 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="547d0-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="547d0-131">若要檢視追蹤記錄，請在 SQL Management Studio 中開啟 TrackingSample 資料庫並巡覽至資料表。</span><span class="sxs-lookup"><span data-stu-id="547d0-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="547d0-132">如需有關 SQL Server Management Studio 的詳細資訊，請參閱 < [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645)。</span><span class="sxs-lookup"><span data-stu-id="547d0-132">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="547d0-133">您可以下載 SQL Server 2008 Management Studio Express[此處](https://go.microsoft.com/fwlink/?LinkId=180520)。</span><span class="sxs-lookup"><span data-stu-id="547d0-133">SQL Server 2008 Management Studio Express can be downloaded [here](https://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="547d0-134">在資料表上執行 Select 查詢，會顯示個別資料表中所儲存的追蹤記錄資料。</span><span class="sxs-lookup"><span data-stu-id="547d0-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="547d0-135">若要解除安裝範例</span><span class="sxs-lookup"><span data-stu-id="547d0-135">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="547d0-136">執行範例目錄 (\WF\Basic\Tracking\SqlTracking) 中的 theTrackingcleanup.cmd 指令碼。</span><span class="sxs-lookup"><span data-stu-id="547d0-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="547d0-137">Trackingcleanup.cmd 會嘗試刪除本機電腦 SQL Express 中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="547d0-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="547d0-138">如果您使用另一個 SQL Server 執行個體，請編輯 Trackingcleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="547d0-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="547d0-139">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="547d0-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="547d0-140">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="547d0-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="547d0-141">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="547d0-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="547d0-142">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="547d0-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="547d0-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="547d0-143">See Also</span></span>  
 [<span data-ttu-id="547d0-144">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="547d0-144">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
