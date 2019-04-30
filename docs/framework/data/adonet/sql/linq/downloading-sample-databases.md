---
title: 取得範例 SQL Server 資料庫的 ADO.NET 程式碼範例
description: 下載 ADO.NET 文件，以及 SQL Server 和管理工具的程式碼範例中所使用的 SQL Server 範例資料庫
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 5580f06f3d28ed6d70f75b619498ac8de7bc3326
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037930"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="63fd6-103">取得範例資料庫的 ADO.NET 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="63fd6-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="63fd6-104">許多範例和逐步解說中的[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文件使用的 SQL Server 範例資料庫和 SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="63fd6-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="63fd6-105">您可以從 Microsoft 下載這些免費的產品。</span><span class="sxs-lookup"><span data-stu-id="63fd6-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="63fd6-106">取得 SQL Server 的 Northwind 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="63fd6-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="63fd6-107">下載指令碼`instnwnd.sql`從下列的 GitHub 存放庫，來建立和載入適用於 SQL Server 的 Northwind 範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="63fd6-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="63fd6-108">Microsoft SQL server 的 Northwind 和 pubs 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="63fd6-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="63fd6-109">您可以使用 Northwind 資料庫之前，您必須執行已下載`instnwnd.sql`重新建立 SQL Server 執行個體上的資料庫所使用的指令碼檔案[SQL Server Management Studio](#get_ssms)或類似的工具。</span><span class="sxs-lookup"><span data-stu-id="63fd6-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="63fd6-110">請遵循存放庫中的讀我檔案中的指示。</span><span class="sxs-lookup"><span data-stu-id="63fd6-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="63fd6-111">如果您想為 Microsoft Access Northwind 資料庫，請參閱[安裝 Microsoft Access Northwind 範例資料庫](#northwind_access)。</span><span class="sxs-lookup"><span data-stu-id="63fd6-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="northwind_access"></a> <span data-ttu-id="63fd6-112">取得 Microsoft Access Northwind 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="63fd6-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="63fd6-113">Microsoft Download Center 上，不可以使用 Microsoft access Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="63fd6-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="63fd6-114">若要安裝在 Access 中的直接從 Northwind，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="63fd6-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="63fd6-115">開啟 [存取]。</span><span class="sxs-lookup"><span data-stu-id="63fd6-115">Open Access.</span></span>

1. <span data-ttu-id="63fd6-116">Enter **Northwind**中**搜尋線上範本**方塊，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="63fd6-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="63fd6-117">在 [結果] 畫面中，選取**Northwind**。</span><span class="sxs-lookup"><span data-stu-id="63fd6-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="63fd6-118">新的視窗會開啟 Northwind 資料庫的描述。</span><span class="sxs-lookup"><span data-stu-id="63fd6-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="63fd6-119">在新視窗中，在**檔案名**文字中，提供檔案名稱，為您的 Northwind 資料庫的副本。</span><span class="sxs-lookup"><span data-stu-id="63fd6-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="63fd6-120">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="63fd6-120">Select **Create**.</span></span> <span data-ttu-id="63fd6-121">存取下載 Northwind 資料庫，並準備此檔案。</span><span class="sxs-lookup"><span data-stu-id="63fd6-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="63fd6-122">完成此程序時，資料庫便會開啟 歡迎使用畫面。</span><span class="sxs-lookup"><span data-stu-id="63fd6-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="63fd6-123">取得 SQL Server 的 AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="63fd6-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="63fd6-124">適用於 SQL Server，從下列 GitHub 儲存機制下載 AdventureWorks 範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="63fd6-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="63fd6-125">AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="63fd6-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="63fd6-126">下載其中一個資料庫備份之後 (\*.bak) 檔案，使用 SQL Server Management Studio (SSMS) 將備份還原到 SQL Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="63fd6-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="63fd6-127">請參閱[取得 SQL Server Management Studio](#get_ssms)。</span><span class="sxs-lookup"><span data-stu-id="63fd6-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_ssms"></a> <span data-ttu-id="63fd6-128">取得 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="63fd6-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="63fd6-129">如果您想要檢視或修改的資料庫，您已下載，您可以使用 SQL Server Management Studio (SSMS)。</span><span class="sxs-lookup"><span data-stu-id="63fd6-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="63fd6-130">下載 SSMS，從下列頁面：</span><span class="sxs-lookup"><span data-stu-id="63fd6-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="63fd6-131">下載 SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="63fd6-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="63fd6-132">您也可以檢視和管理 Visual Studio 整合式的開發環境 (IDE) 中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="63fd6-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="63fd6-133">在[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，連接到資料庫**SQL Server 物件總管**，或建立的資料庫中的資料連接**伺服器總管**。</span><span class="sxs-lookup"><span data-stu-id="63fd6-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="63fd6-134">開啟這些檔案總管 窗格，從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="63fd6-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="63fd6-135">Get SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="63fd6-135">Get SQL Server Express</span></span>

<span data-ttu-id="63fd6-136">SQL Server Express 是免費的入門級的 SQL Server 版本，您可以重新發佈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="63fd6-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="63fd6-137">下載 SQL Server Express 從下列頁面：</span><span class="sxs-lookup"><span data-stu-id="63fd6-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="63fd6-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="63fd6-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="63fd6-139">如果您使用[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，SQL Server Express LocalDB 納入的 Visual Studio 中，免費的 Community edition，以及專業和更高版本。</span><span class="sxs-lookup"><span data-stu-id="63fd6-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="63fd6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63fd6-140">See also</span></span>

- [<span data-ttu-id="63fd6-141">快速入門</span><span class="sxs-lookup"><span data-stu-id="63fd6-141">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
