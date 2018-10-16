---
title: 取得範例資料庫的 ADO.NET 程式碼範例
description: 下載範例資料庫中的 ADO.NET 文件，以及 SQL Server 和管理工具的程式碼範例使用
ms.date: 10/12/2018
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 75ae1895d683b669f51b33130fc2f47010e39814
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347496"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="fae4a-103">取得範例資料庫的 ADO.NET 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="fae4a-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="fae4a-104">許多範例和逐步解說中的[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文件使用範例資料庫和 SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="fae4a-104">A number of samples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample databases and SQL Server Express.</span></span> <span data-ttu-id="fae4a-105">您可以從 Microsoft 下載這些免費的產品。</span><span class="sxs-lookup"><span data-stu-id="fae4a-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-adventureworks-sample-database"></a><span data-ttu-id="fae4a-106">取得 AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="fae4a-106">Get the AdventureWorks sample database</span></span>

<span data-ttu-id="fae4a-107">從下列 GitHub 儲存機制下載 AdventureWorks 範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="fae4a-107">Download the AdventureWorks sample database from the following GitHub repository:</span></span>

[<span data-ttu-id="fae4a-108">AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="fae4a-108">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="fae4a-109">下載其中一個資料庫備份之後 (\*.bak) 檔案，使用 SQL Server Management Studio (SSMS) 將備份還原到 SQL Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fae4a-109">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="fae4a-110">請參閱[取得 SQL Server Management Studio](#get_ssms)。</span><span class="sxs-lookup"><span data-stu-id="fae4a-110">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-the-northwind-sample-database"></a><span data-ttu-id="fae4a-111">取得 Northwind 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="fae4a-111">Get the Northwind sample database</span></span>

<span data-ttu-id="fae4a-112">從 Microsoft 下載中心中的下列頁面下載 Northwind 範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="fae4a-112">Download the Northwind sample database from the following page in the Microsoft Download Center:</span></span>

[<span data-ttu-id="fae4a-113">Northwind 和 Pubs 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="fae4a-113">Northwind and Pubs Sample Databases</span></span>](https://go.microsoft.com/fwlink?linkid=64296)

<span data-ttu-id="fae4a-114">下載檔案之後，連按兩下該檔案以解壓縮資料庫與指令碼。</span><span class="sxs-lookup"><span data-stu-id="fae4a-114">After the file has downloaded, double-click the file to extract the databases and scripts.</span></span> <span data-ttu-id="fae4a-115">根據預設，檔案會安裝在資料夾`<drive>:\SQL Server 2000 Sample Databases`。</span><span class="sxs-lookup"><span data-stu-id="fae4a-115">By default, the files are installed in the folder `<drive>:\SQL Server 2000 Sample Databases`.</span></span>

<span data-ttu-id="fae4a-116">您可以使用 Northwind 資料庫之前，您必須執行下列事項之一：</span><span class="sxs-lookup"><span data-stu-id="fae4a-116">Before you can use the Northwind database, you have to do one of the following things:</span></span>

- <span data-ttu-id="fae4a-117">重新建立資料庫的 SQL Server 執行個體上執行`instnwnd.sql`安裝資料夾中的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="fae4a-117">Recreate the database on an instance of SQL Server by running the `instnwnd.sql` script file in the installation folder.</span></span>

- <span data-ttu-id="fae4a-118">附加`northwnd.mdf`與其對應的檔案`*.ldf`的 SQL Server 執行個體的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fae4a-118">Attach the `northwnd.mdf` file with its corresponding `*.ldf` log file to an instance of SQL Server.</span></span>

## <a name="get_sql"></a> <span data-ttu-id="fae4a-119">取得 SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="fae4a-119">Get SQL Server Express</span></span>

<span data-ttu-id="fae4a-120">SQL Server Express 是免費的入門級的 SQL Server 版本，您可以重新發佈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fae4a-120">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="fae4a-121">下載 SQL Server Express 從下列頁面：</span><span class="sxs-lookup"><span data-stu-id="fae4a-121">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="fae4a-122">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="fae4a-122">SQL Server Express Editions</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="fae4a-123">如果您使用[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，SQL Server Express LocalDB 納入 Community edition，以及專業和更高版本。</span><span class="sxs-lookup"><span data-stu-id="fae4a-123">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the Community edition as well as the Professional and higher editions.</span></span>  

## <a name="get_ssms"></a> <span data-ttu-id="fae4a-124">取得 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fae4a-124">Get SQL Server Management Studio</span></span>
<span data-ttu-id="fae4a-125">如果您想要檢視或修改的資料庫，您已下載，您可以使用 SQL Server Management Studio (SSMS)。</span><span class="sxs-lookup"><span data-stu-id="fae4a-125">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="fae4a-126">下載 SSMS，從下列頁面：</span><span class="sxs-lookup"><span data-stu-id="fae4a-126">Download SSMS from the following page:</span></span>

[<span data-ttu-id="fae4a-127">下載 SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="fae4a-127">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="fae4a-128">您也可以檢視和管理 Visual Studio 整合式的開發環境 (IDE) 中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fae4a-128">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="fae4a-129">在[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，連接到資料庫**SQL Server 物件總管**，或建立的資料庫中的資料連接**伺服器總管**。</span><span class="sxs-lookup"><span data-stu-id="fae4a-129">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="fae4a-130">開啟這些檔案總管 窗格，從**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="fae4a-130">Open these explorer panes from the **View** menu.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fae4a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fae4a-131">See also</span></span>

- [<span data-ttu-id="fae4a-132">快速入門</span><span class="sxs-lookup"><span data-stu-id="fae4a-132">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
