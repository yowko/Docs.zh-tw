---
title: HOW TO：使用 LINQ to SQL 資料來源建立資料服務（WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 7a1075b680ec3310e1bd8d712579872333c6ebed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791059"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="b4192-102">HOW TO：使用 LINQ to SQL 資料來源建立資料服務（WCF Data Services）</span><span class="sxs-lookup"><span data-stu-id="b4192-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="b4192-103">WCF Data Services 會將實體資料公開為數據服務。</span><span class="sxs-lookup"><span data-stu-id="b4192-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="b4192-104">反映提供者可讓您定義以任何類別為基礎的資料模型，其會公開傳回實作為<xref:System.Linq.IQueryable%601>的成員。</span><span class="sxs-lookup"><span data-stu-id="b4192-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="b4192-105">若要可以更新資料來源的資料，這些類別也必須實作 <xref:System.Data.Services.IUpdatable> 介面。</span><span class="sxs-lookup"><span data-stu-id="b4192-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="b4192-106">如需詳細資訊，請參閱[資料服務提供者](data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b4192-106">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="b4192-107">本主題說明如何使用反映提供者，建立存取 Northwind 範例資料庫的 LINQ to SQL 類別以及如何根據這些資料類別，建立資料服務。</span><span class="sxs-lookup"><span data-stu-id="b4192-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="b4192-108">將 LINQ to SQL 類別加入至專案</span><span class="sxs-lookup"><span data-stu-id="b4192-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="b4192-109">從 Visual Basic 或C#應用程式中，按一下 [**專案**] 功能表上的 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="b4192-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="b4192-110">按一下 [ **LINQ to SQL 類別**] 範本。</span><span class="sxs-lookup"><span data-stu-id="b4192-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="b4192-111">將名稱變更為**Northwind. .dbml**。</span><span class="sxs-lookup"><span data-stu-id="b4192-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="b4192-112">按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="b4192-112">Click **Add**.</span></span>

     <span data-ttu-id="b4192-113">Northwind.dbml 檔案會加入至專案，且會開啟 [物件關聯式設計工具] (O/R 設計工具)。</span><span class="sxs-lookup"><span data-stu-id="b4192-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="b4192-114">在 **伺服器**/**資料庫總管**的 Northwind 底下，展開  `Customers` **資料表** ，然後將資料表拖曳至 物件關聯式設計工具（O/R 設計工具）。</span><span class="sxs-lookup"><span data-stu-id="b4192-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="b4192-115">隨即建立 `Customer` 實體類別，並出現在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="b4192-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="b4192-116">針對 `Orders`、`Order_Details` 和 `Products` 資料表，重複步驟 6。</span><span class="sxs-lookup"><span data-stu-id="b4192-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="b4192-117">以滑鼠右鍵按一下代表 LINQ to SQL 類別的新 .dbml 檔案，然後按一下 [**查看程式碼**]。</span><span class="sxs-lookup"><span data-stu-id="b4192-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="b4192-118">這樣會建立名為 Northwind.cs 的新程式碼後置頁面，其中包含繼承自 <xref:System.Data.Linq.DataContext> 類別的部分類別定義，在此案例中是 `NorthwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="b4192-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="b4192-119">以下列程式碼取代 Northwind.cs 程式碼檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="b4192-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="b4192-120">此程式碼透過延伸 LINQ to SQL 產生的 <xref:System.Data.Linq.DataContext> 和資料類別，實作反映提供者：</span><span class="sxs-lookup"><span data-stu-id="b4192-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="b4192-121">使用 LINQ to SQL 架構資料模組建立資料服務</span><span class="sxs-lookup"><span data-stu-id="b4192-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="b4192-122">在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案的名稱，然後按一下 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="b4192-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="b4192-123">在 [**加入新專案**] 對話方塊中，從 [ **Web** ] 類別選取 [ **WCF 資料服務**] 範本。</span><span class="sxs-lookup"><span data-stu-id="b4192-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Visual Studio 2015 中的 WCF 資料服務專案範本](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="b4192-125">**WCF 資料服務**範本可在 Visual Studio 2015 中取得，但 Visual Studio 2017 則不提供。</span><span class="sxs-lookup"><span data-stu-id="b4192-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="b4192-126">提供服務的名稱，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b4192-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="b4192-127">Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="b4192-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="b4192-128">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="b4192-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="b4192-129">在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="b4192-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="b4192-130">在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：</span><span class="sxs-lookup"><span data-stu-id="b4192-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="b4192-131">如此可讓已授權用戶端存取三個指定實體集的資源。</span><span class="sxs-lookup"><span data-stu-id="b4192-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="b4192-132">若要使用網頁瀏覽器測試 Northwind 資料服務，請依照[從網頁瀏覽器存取服務](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)主題中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="b4192-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4192-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4192-133">See also</span></span>

- [<span data-ttu-id="b4192-134">如何：使用 ADO.NET Entity Framework 資料來源建立資料服務</span><span class="sxs-lookup"><span data-stu-id="b4192-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="b4192-135">如何：使用反映提供者建立資料服務</span><span class="sxs-lookup"><span data-stu-id="b4192-135">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="b4192-136">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="b4192-136">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
