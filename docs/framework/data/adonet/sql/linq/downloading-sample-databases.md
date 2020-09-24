---
title: 取得範例 SQL Server 資料庫以 ADO.NET 程式碼範例
description: 下載 ADO.NET 檔中的程式碼範例所使用的範例 SQL Server 資料庫，以及 SQL Server 和管理工具
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: f7c0d1eb0089a6bfabc92e1deecf563c3e59cc6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156052"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="55ef1-103">取得 ADO.NET 程式碼範例的範例資料庫</span><span class="sxs-lookup"><span data-stu-id="55ef1-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="55ef1-104">檔中的一些範例和逐步解說會 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 使用範例 SQL Server 資料庫和 SQL Server Express。</span><span class="sxs-lookup"><span data-stu-id="55ef1-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="55ef1-105">您可以從 Microsoft 免費下載這些產品。</span><span class="sxs-lookup"><span data-stu-id="55ef1-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="55ef1-106">取得 SQL Server 的 Northwind 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="55ef1-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="55ef1-107">`instnwnd.sql`從下列 GitHub 存放庫下載腳本，以建立和載入 SQL Server 的 Northwind 範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="55ef1-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="55ef1-108">Microsoft SQL Server 的 Northwind 和 pubs 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="55ef1-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="55ef1-109">使用 Northwind 資料庫之前，您必須執行下載的腳本檔案， `instnwnd.sql` 以使用 [SQL Server Management Studio](#get_ssms) 或類似的工具，在 SQL Server 的實例上重新建立資料庫。</span><span class="sxs-lookup"><span data-stu-id="55ef1-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="55ef1-110">遵循存放庫中讀我檔案中的指示。</span><span class="sxs-lookup"><span data-stu-id="55ef1-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="55ef1-111">如果您要尋找適用于 Microsoft Access 的 Northwind 資料庫，請參閱 [安裝適用于 Microsoft access 的 northwind 範例資料庫](#northwind_access)。</span><span class="sxs-lookup"><span data-stu-id="55ef1-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a> <span data-ttu-id="55ef1-112">取得 Microsoft Access 的 Northwind 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="55ef1-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="55ef1-113">Microsoft 下載中心不提供適用于 Microsoft Access 的 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="55ef1-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="55ef1-114">若要直接從 Access 內安裝 Northwind，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="55ef1-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="55ef1-115">開啟存取權。</span><span class="sxs-lookup"><span data-stu-id="55ef1-115">Open Access.</span></span>

1. <span data-ttu-id="55ef1-116">在 [**搜尋線上範本**] 方塊中輸入**Northwind** ，然後選取**enter**。</span><span class="sxs-lookup"><span data-stu-id="55ef1-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="55ef1-117">在 [結果] 畫面上，選取 [ **Northwind**]。</span><span class="sxs-lookup"><span data-stu-id="55ef1-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="55ef1-118">新視窗隨即開啟，其中包含 Northwind 資料庫的描述。</span><span class="sxs-lookup"><span data-stu-id="55ef1-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="55ef1-119">在新視窗的 [ **檔案名** ] 文字方塊中，提供您的 Northwind 資料庫複本的檔案名。</span><span class="sxs-lookup"><span data-stu-id="55ef1-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="55ef1-120">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="55ef1-120">Select **Create**.</span></span> <span data-ttu-id="55ef1-121">存取會下載 Northwind 資料庫，並準備檔案。</span><span class="sxs-lookup"><span data-stu-id="55ef1-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="55ef1-122">當此程式完成時，資料庫會以歡迎畫面開啟。</span><span class="sxs-lookup"><span data-stu-id="55ef1-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="55ef1-123">取得 SQL Server 的 AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="55ef1-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="55ef1-124">從下列 GitHub 存放庫下載 SQL Server 的 AdventureWorks 範例資料庫：</span><span class="sxs-lookup"><span data-stu-id="55ef1-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="55ef1-125">AdventureWorks 範例資料庫</span><span class="sxs-lookup"><span data-stu-id="55ef1-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="55ef1-126">下載其中一個資料庫備份 (\* .bak) 檔案之後，請使用 SQL Server Management Studio (SSMS) ，將備份還原至 SQL Server 的實例。</span><span class="sxs-lookup"><span data-stu-id="55ef1-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="55ef1-127">請參閱 [Get SQL Server Management Studio](#get_ssms)。</span><span class="sxs-lookup"><span data-stu-id="55ef1-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a> <span data-ttu-id="55ef1-128">取得 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="55ef1-128">Get SQL Server Management Studio</span></span>

<span data-ttu-id="55ef1-129">如果您想要查看或修改已下載的資料庫，您可以使用 SQL Server Management Studio (SSMS) 。</span><span class="sxs-lookup"><span data-stu-id="55ef1-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="55ef1-130">從下列頁面下載 SSMS：</span><span class="sxs-lookup"><span data-stu-id="55ef1-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="55ef1-131">下載 SQL Server Management Studio (SSMS)</span><span class="sxs-lookup"><span data-stu-id="55ef1-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="55ef1-132">您也可以在 Visual Studio 整合式開發環境中， (IDE) 來查看及管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="55ef1-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="55ef1-133">在 [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)中，從 **SQL Server 物件總管**連接到資料庫，或在 **伺服器總管**中建立資料庫的資料連線。</span><span class="sxs-lookup"><span data-stu-id="55ef1-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="55ef1-134">從 [ **View** ] 功能表開啟這些 [explorer] 窗格。</span><span class="sxs-lookup"><span data-stu-id="55ef1-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a> <span data-ttu-id="55ef1-135">取得 SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="55ef1-135">Get SQL Server Express</span></span>

<span data-ttu-id="55ef1-136">SQL Server Express 是免費的入門版 SQL Server，可讓您隨應用程式一起轉散發。</span><span class="sxs-lookup"><span data-stu-id="55ef1-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="55ef1-137">從下列頁面下載 SQL Server Express：</span><span class="sxs-lookup"><span data-stu-id="55ef1-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="55ef1-138">SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="55ef1-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="55ef1-139">如果您使用 [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)，SQL Server Express LocalDB 會包含在 Visual Studio 的免費版和更高版本中。</span><span class="sxs-lookup"><span data-stu-id="55ef1-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="55ef1-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55ef1-140">See also</span></span>

- [<span data-ttu-id="55ef1-141">快速入門</span><span class="sxs-lookup"><span data-stu-id="55ef1-141">Getting Started</span></span>](getting-started.md)
