---
title: 取得 ADO.NET 程式碼範例的範例 SQL Server 資料庫
description: 下載 ADO.NET 檔中程式碼範例所使用的範例 SQL Server 資料庫，以及 SQL Server 和管理工具
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 60566041ff4f99e96c9aee052dbcc17b5e5da9e5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794037"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="be27b-103">取得 ADO.NET 程式碼範例的範例資料庫</span><span class="sxs-lookup"><span data-stu-id="be27b-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="be27b-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]檔中的一些範例和逐步解說會使用範例 SQL Server 資料庫和 SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="be27b-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="be27b-105">您可以從 Microsoft 免費下載這些產品。</span><span class="sxs-lookup"><span data-stu-id="be27b-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="be27b-106">取得適用于 SQL Server 的 Northwind 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="be27b-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="be27b-107">從下列 GitHub `instnwnd.sql`存放庫下載腳本，以建立和載入 SQL Server 的 Northwind 範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="be27b-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="be27b-108">適用于 Microsoft SQL Server 的 Northwind 和 pubs 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="be27b-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="be27b-109">在您可以使用 Northwind 資料庫之前，您必須先執行下載`instnwnd.sql`的腳本檔案，使用[SQL Server Management Studio](#get_ssms)或類似的工具，在 SQL Server 的實例上重新建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="be27b-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="be27b-110">遵循存放庫中的讀我檔案中的指示。</span><span class="sxs-lookup"><span data-stu-id="be27b-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="be27b-111">如果您要尋找適用于 Microsoft Access 的 Northwind 資料庫，請參閱[安裝適用于 Microsoft access 的 northwind 範例資料庫](#northwind_access)。</span><span class="sxs-lookup"><span data-stu-id="be27b-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="northwind_access"></a><span data-ttu-id="be27b-112">取得適用于 Microsoft Access 的 Northwind 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="be27b-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="be27b-113">Microsoft 下載中心不提供適用于 Microsoft Access 的 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="be27b-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="be27b-114">若要直接從存取中安裝 Northwind，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="be27b-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="be27b-115">開啟 [存取]。</span><span class="sxs-lookup"><span data-stu-id="be27b-115">Open Access.</span></span>

1. <span data-ttu-id="be27b-116">在 [**搜尋線上範本**] 方塊中輸入**Northwind** ，然後選取**Enter**。</span><span class="sxs-lookup"><span data-stu-id="be27b-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="be27b-117">在 [結果] 畫面上，選取 [ **Northwind**]。</span><span class="sxs-lookup"><span data-stu-id="be27b-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="be27b-118">新視窗隨即開啟，其中含有 Northwind 資料庫的描述。</span><span class="sxs-lookup"><span data-stu-id="be27b-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="be27b-119">在新視窗的 [**檔案名**] 文字方塊中，為您的 Northwind 資料庫複本提供檔案名。</span><span class="sxs-lookup"><span data-stu-id="be27b-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="be27b-120">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="be27b-120">Select **Create**.</span></span> <span data-ttu-id="be27b-121">Access 會下載 Northwind 資料庫，並準備檔案。</span><span class="sxs-lookup"><span data-stu-id="be27b-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="be27b-122">當此程式完成時，資料庫就會開啟並顯示 [歡迎使用] 畫面。</span><span class="sxs-lookup"><span data-stu-id="be27b-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="be27b-123">取得適用于 SQL Server 的 AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="be27b-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="be27b-124">從下列 GitHub 存放庫下載適用于 SQL Server 的 AdventureWorks 範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="be27b-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="be27b-125">AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="be27b-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="be27b-126">在您下載其中一個資料庫備份（\*.bak）檔案之後，請使用 SQL Server Management Studio （SSMS）將備份還原到 SQL Server 的實例。</span><span class="sxs-lookup"><span data-stu-id="be27b-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="be27b-127">請參閱[取得 SQL Server Management Studio](#get_ssms)。</span><span class="sxs-lookup"><span data-stu-id="be27b-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get_ssms"></a><span data-ttu-id="be27b-128">取得 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="be27b-128">Get SQL Server Management Studio</span></span>
<span data-ttu-id="be27b-129">如果您想要查看或修改已下載的資料庫，您可以使用 SQL Server Management Studio （SSMS）。</span><span class="sxs-lookup"><span data-stu-id="be27b-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="be27b-130">從下列頁面下載 SSMS：</span><span class="sxs-lookup"><span data-stu-id="be27b-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="be27b-131">下載 SQL Server Management Studio （SSMS）</span><span class="sxs-lookup"><span data-stu-id="be27b-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms) 

<span data-ttu-id="be27b-132">您也可以在 Visual Studio 整合式開發環境（IDE）中查看和管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="be27b-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="be27b-133">在[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)中，從**SQL Server 物件總管**連接到資料庫，或在**伺服器總管**中建立資料庫的資料連線。</span><span class="sxs-lookup"><span data-stu-id="be27b-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="be27b-134">從 [ **View** ] 功能表開啟這些 [瀏覽器] 窗格。</span><span class="sxs-lookup"><span data-stu-id="be27b-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get_sql"></a><span data-ttu-id="be27b-135">取得 SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="be27b-135">Get SQL Server Express</span></span>

<span data-ttu-id="be27b-136">SQL Server Express 是免費的入門版的 SQL Server，可讓您隨著應用程式轉散發。</span><span class="sxs-lookup"><span data-stu-id="be27b-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="be27b-137">從下列頁面下載 SQL Server Express：</span><span class="sxs-lookup"><span data-stu-id="be27b-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="be27b-138">SQL Server Express 版本</span><span class="sxs-lookup"><span data-stu-id="be27b-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="be27b-139">如果您使用的是[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)，SQL Server Express LocalDB 會包含在免費的 Visual Studio 的社區版本中，以及 Professional 和更高版本中。</span><span class="sxs-lookup"><span data-stu-id="be27b-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="be27b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be27b-140">See also</span></span>

- [<span data-ttu-id="be27b-141">快速入門</span><span class="sxs-lookup"><span data-stu-id="be27b-141">Getting Started</span></span>](getting-started.md)
