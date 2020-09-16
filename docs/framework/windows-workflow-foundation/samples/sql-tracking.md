---
title: SQL 追蹤
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 916c04b03dee296b7e6f5c792f0c4e50fb4203c0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559346"
---
# <a name="sql-tracking"></a><span data-ttu-id="42ec4-102">SQL 追蹤</span><span class="sxs-lookup"><span data-stu-id="42ec4-102">SQL tracking</span></span>

<span data-ttu-id="42ec4-103">這個範例會示範如何撰寫自訂的 SQL 追蹤參與者，將追蹤記錄寫入至 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="42ec4-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="42ec4-104">Windows Workflow Foundation (WF) 提供工作流程追蹤，以瞭解工作流程實例的執行。</span><span class="sxs-lookup"><span data-stu-id="42ec4-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="42ec4-105">追蹤執行階段會在工作流程執行期間發出工作流程追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="42ec4-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="42ec4-106">如需工作流程追蹤的詳細資訊，請參閱 [工作流程追蹤和追蹤](../workflow-tracking-and-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="42ec4-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="42ec4-107">使用範例</span><span class="sxs-lookup"><span data-stu-id="42ec4-107">Use the sample</span></span>

1. <span data-ttu-id="42ec4-108">確定您已安裝 SQL Server 2008、SQL Server 2008 Express 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="42ec4-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="42ec4-109">隨範例封裝的指令碼假定在本機電腦上使用 SQL Express 執行個體。</span><span class="sxs-lookup"><span data-stu-id="42ec4-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="42ec4-110">如果您有不同的執行個體，在執行範例之前請先修改資料庫相關指令碼。</span><span class="sxs-lookup"><span data-stu-id="42ec4-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="42ec4-111">執行指令碼目錄 (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 中的 Trackingsetup.cmd，建立 SQL Server 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="42ec4-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="42ec4-112">這會建立名為 TrackingSample 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="42ec4-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="42ec4-113">指令碼會在 SQL Express 預設執行個體上建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="42ec4-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="42ec4-114">如果您想要安裝在不同的資料庫執行個體上，請編輯 Trackingsetup.cmd 指令碼。</span><span class="sxs-lookup"><span data-stu-id="42ec4-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="42ec4-115">在 Visual Studio 2010 中開啟 SqlTrackingSample .sln。</span><span class="sxs-lookup"><span data-stu-id="42ec4-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="42ec4-116">按**Ctrl** + **Shift** + **B**以建立解決方案。</span><span class="sxs-lookup"><span data-stu-id="42ec4-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="42ec4-117">按 **F5** 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="42ec4-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="42ec4-118">瀏覽器視窗隨即開啟並顯示應用程式的目錄清單。</span><span class="sxs-lookup"><span data-stu-id="42ec4-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="42ec4-119">在瀏覽器中，按一下 StockPriceService.xamlx。</span><span class="sxs-lookup"><span data-stu-id="42ec4-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="42ec4-120">瀏覽器隨即顯示 StockPriceService 頁面，其中包含本機服務 WSDL 位址。</span><span class="sxs-lookup"><span data-stu-id="42ec4-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="42ec4-121">複製此位址。</span><span class="sxs-lookup"><span data-stu-id="42ec4-121">Copy this address.</span></span>

   <span data-ttu-id="42ec4-122">本機服務 WSDL 位址的範例是 `http://localhost:65193/StockPriceService.xamlx?wsdl` 。</span><span class="sxs-lookup"><span data-stu-id="42ec4-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="42ec4-123">使用檔案總管， ( # A0) 執行 WCF 測試用戶端。</span><span class="sxs-lookup"><span data-stu-id="42ec4-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="42ec4-124">它位於 *Microsoft Visual Studio 10.0 \ Common7\IDE 目錄*中。</span><span class="sxs-lookup"><span data-stu-id="42ec4-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="42ec4-125">在 WCF 測試用戶端中，按一下 [檔案 **] 功能表，** 然後選取 [ **加入服務**]。</span><span class="sxs-lookup"><span data-stu-id="42ec4-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="42ec4-126">將本機服務位址貼至文字方塊。</span><span class="sxs-lookup"><span data-stu-id="42ec4-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="42ec4-127">按一下 **[確定]** 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="42ec4-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="42ec4-128">在 WCF 測試用戶端中，按兩下 [ **GetStockPrice**]。</span><span class="sxs-lookup"><span data-stu-id="42ec4-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="42ec4-129">這會開啟 `GetStockPrice` 接受一個參數的作業，輸入值，然後按一下 [叫用] `Contoso` 。 **Invoke**</span><span class="sxs-lookup"><span data-stu-id="42ec4-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="42ec4-130">發出的追蹤記錄會寫入至 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="42ec4-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="42ec4-131">若要檢視追蹤記錄，請在 SQL Management Studio 中開啟 TrackingSample 資料庫並巡覽至資料表。</span><span class="sxs-lookup"><span data-stu-id="42ec4-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="42ec4-132">在資料表上執行 Select 查詢，會顯示個別資料表中所儲存的追蹤記錄資料。</span><span class="sxs-lookup"><span data-stu-id="42ec4-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="42ec4-133">如需 SQL Server Management Studio 的詳細資訊，請參閱 [SQL Server Management Studio 簡介](/sql/ssms/sql-server-management-studio-ssms)。</span><span class="sxs-lookup"><span data-stu-id="42ec4-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="42ec4-134">[在這裡](https://aka.ms/ssmsfullsetup)下載 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="42ec4-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="42ec4-135">卸載範例</span><span class="sxs-lookup"><span data-stu-id="42ec4-135">Uninstall the sample</span></span>

1. <span data-ttu-id="42ec4-136"> (*\WF\Basic\Tracking\SqlTracking*) 中執行範例目錄中的 theTrackingcleanup .cmd 腳本。</span><span class="sxs-lookup"><span data-stu-id="42ec4-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="42ec4-137">Trackingcleanup.cmd 會嘗試刪除本機電腦 SQL Express 中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="42ec4-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="42ec4-138">如果您使用另一個 SQL Server 執行個體，請編輯 Trackingcleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="42ec4-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="42ec4-139">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="42ec4-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="42ec4-140">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="42ec4-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="42ec4-141">如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="42ec4-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="42ec4-142">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="42ec4-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="42ec4-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42ec4-143">See also</span></span>

- <span data-ttu-id="42ec4-144">[AppFabric 監控範例](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="42ec4-144">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
