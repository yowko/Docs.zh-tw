---
title: 取得ADO.NET代碼範例的範例 SQL Server 資料庫
description: 下載ADO.NET文件中程式碼範例使用的範例 SQL Server 資料庫,以及 SQL Server 和管理工具
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 3449f502834f449f5023bd52457d45ffaf9b0fa1
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607980"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="f3a97-103">取得ADO.NET代碼範例的範例資料庫</span><span class="sxs-lookup"><span data-stu-id="f3a97-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="f3a97-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文檔中的一些範例和演練使用範例 SQL Server 資料庫和 SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="f3a97-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="f3a97-105">你可以從微軟免費下載這些產品。</span><span class="sxs-lookup"><span data-stu-id="f3a97-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="f3a97-106">取得 SQL Server 的北風範例資料庫</span><span class="sxs-lookup"><span data-stu-id="f3a97-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="f3a97-107">從以下`instnwnd.sql`GitHub 儲存函式庫下載文稿,以建立並載入 SQL Server 的北風範例資料庫:</span><span class="sxs-lookup"><span data-stu-id="f3a97-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="f3a97-108">Northwind 和 pubs 範例資料庫為 Microsoft SQL 伺服器</span><span class="sxs-lookup"><span data-stu-id="f3a97-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="f3a97-109">在使用 Northwind 資料庫之前,必須執行`instnwnd.sql`下載的文稿檔,以便使用 SQL Server[管理工作室](#get_ssms)或類似工具在 SQL Server 實例上重新創建資料庫。</span><span class="sxs-lookup"><span data-stu-id="f3a97-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="f3a97-110">按照存儲庫中的 Readme 檔中的說明進行操作。</span><span class="sxs-lookup"><span data-stu-id="f3a97-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="f3a97-111">如果您要尋找適用於 Microsoft Access 的北風資料庫,請參閱[安裝 Microsoft Access 的北風範例資料庫](#northwind_access)。</span><span class="sxs-lookup"><span data-stu-id="f3a97-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a><span data-ttu-id="f3a97-112">取得適用於 Microsoft 存取的北風範例資料庫</span><span class="sxs-lookup"><span data-stu-id="f3a97-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="f3a97-113">微軟訪問的北風示例資料庫在Microsoft下載中心不可用。</span><span class="sxs-lookup"><span data-stu-id="f3a97-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="f3a97-114">要直接從 Access 內部安裝北風,請執行以下操作:</span><span class="sxs-lookup"><span data-stu-id="f3a97-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="f3a97-115">打開訪問。</span><span class="sxs-lookup"><span data-stu-id="f3a97-115">Open Access.</span></span>

1. <span data-ttu-id="f3a97-116">在 **「搜尋連線範本」** 框中輸入**北風**,然後選擇「**輸入**」。</span><span class="sxs-lookup"><span data-stu-id="f3a97-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="f3a97-117">在結果螢幕上,選擇**北風**。</span><span class="sxs-lookup"><span data-stu-id="f3a97-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="f3a97-118">將打開一個新視窗,其中說明北風資料庫。</span><span class="sxs-lookup"><span data-stu-id="f3a97-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="f3a97-119">在新視窗中,在 **「檔名**」文字框中,為北風資料庫的副本提供檔名。</span><span class="sxs-lookup"><span data-stu-id="f3a97-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="f3a97-120">選取 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="f3a97-120">Select **Create**.</span></span> <span data-ttu-id="f3a97-121">訪問下載北風資料庫並準備檔。</span><span class="sxs-lookup"><span data-stu-id="f3a97-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="f3a97-122">此過程完成後,資料庫將打開,並帶有"歡迎"螢幕。</span><span class="sxs-lookup"><span data-stu-id="f3a97-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="f3a97-123">取得 SQL Server 的 AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="f3a97-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="f3a97-124">從以下 GitHub 儲存函式庫下載 SQL Server 的 AdventureWorks 範例資料庫:</span><span class="sxs-lookup"><span data-stu-id="f3a97-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="f3a97-125">AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="f3a97-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="f3a97-126">下載其中一個資料庫備份 (.bak)\*檔案後,請使用 SQL Server 管理工作室 (SSMS) 將備份還原到 SQL Server 實例。</span><span class="sxs-lookup"><span data-stu-id="f3a97-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="f3a97-127">請參考[SQL 伺服器管理工作室](#get_ssms)。</span><span class="sxs-lookup"><span data-stu-id="f3a97-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a><span data-ttu-id="f3a97-128">取得 SQL 伺服器管理工作室</span><span class="sxs-lookup"><span data-stu-id="f3a97-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="f3a97-129">如果要查看或修改已下載的資料庫,可以使用 SQL 伺服器管理工作室 (SSMS)。</span><span class="sxs-lookup"><span data-stu-id="f3a97-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="f3a97-130">從以下頁面下載 SSMS:</span><span class="sxs-lookup"><span data-stu-id="f3a97-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="f3a97-131">下載 SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="f3a97-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="f3a97-132">您還可以在可視化工作室集成開發環境 (IDE) 中查看和管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="f3a97-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="f3a97-133">在[可視化工作室](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)中,從 SQL**伺服器物件資源管理器**連接到資料庫,或在**伺服器資源管理器**中創建到資料庫的數據連接。</span><span class="sxs-lookup"><span data-stu-id="f3a97-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="f3a97-134">從 **「檢視」** 選單開啟這些資源管理器窗格。</span><span class="sxs-lookup"><span data-stu-id="f3a97-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a><span data-ttu-id="f3a97-135">取得 SQL 伺服器快速</span><span class="sxs-lookup"><span data-stu-id="f3a97-135">Get SQL Server Express</span></span>

<span data-ttu-id="f3a97-136">SQL Server Express 是一個免費的入門級 SQL Server 版本,您可以使用應用程式重新分發。</span><span class="sxs-lookup"><span data-stu-id="f3a97-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="f3a97-137">從以下頁面下載 SQL 伺服器快速服務:</span><span class="sxs-lookup"><span data-stu-id="f3a97-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="f3a97-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="f3a97-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="f3a97-139">如果您使用的是[Visual Studio,SQL](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)Server Express 本地DB 包含在 Visual Studio 的免費社區版以及專業版和更高版本中。</span><span class="sxs-lookup"><span data-stu-id="f3a97-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="f3a97-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3a97-140">See also</span></span>

- [<span data-ttu-id="f3a97-141">快速入門</span><span class="sxs-lookup"><span data-stu-id="f3a97-141">Getting Started</span></span>](getting-started.md)
