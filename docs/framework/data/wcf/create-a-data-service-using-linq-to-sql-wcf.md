---
title: "如何：使用 LINQ to SQL 資料來源建立資料服務 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52529689242342afa8920a7b01b532a24337f562
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="31706-102">如何：使用 LINQ to SQL 資料來源建立資料服務 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="31706-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="31706-103"> 會將實體資料公開為資料服務。</span><span class="sxs-lookup"><span data-stu-id="31706-103"> exposes entity data as a data service.</span></span> <span data-ttu-id="31706-104">反映提供者可讓您定義資料模型為基礎的任何類別所公開的成員，會傳回<xref:System.Linq.IQueryable%601>實作。</span><span class="sxs-lookup"><span data-stu-id="31706-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="31706-105">若要可以更新資料來源的資料，這些類別也必須實作 <xref:System.Data.Services.IUpdatable> 介面。</span><span class="sxs-lookup"><span data-stu-id="31706-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="31706-106">如需詳細資訊，請參閱[資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="31706-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="31706-107">本主題說明如何使用反映提供者，建立存取 Northwind 範例資料庫的 LINQ to SQL 類別以及如何根據這些資料類別，建立資料服務。</span><span class="sxs-lookup"><span data-stu-id="31706-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="31706-108">將 LINQ to SQL 類別加入至專案</span><span class="sxs-lookup"><span data-stu-id="31706-108">To add LINQ to SQL classes to a project</span></span>  
  
1.  <span data-ttu-id="31706-109">從在 Visual Basic 或 C# 應用程式上**專案**功能表上，按一下 **加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="31706-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="31706-110">按一下**LINQ to SQL 類別**範本。</span><span class="sxs-lookup"><span data-stu-id="31706-110">Click the **LINQ to SQL Classes** template.</span></span>  
  
3.  <span data-ttu-id="31706-111">將名稱變更為**Northwind.dbml**。</span><span class="sxs-lookup"><span data-stu-id="31706-111">Change the name to **Northwind.dbml**.</span></span>  
  
4.  <span data-ttu-id="31706-112">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="31706-112">Click **Add**.</span></span>  
  
     <span data-ttu-id="31706-113">Northwind.dbml 檔案會加入至專案，且會開啟 [物件關聯式設計工具] (O/R 設計工具)。</span><span class="sxs-lookup"><span data-stu-id="31706-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>  
  
5.  <span data-ttu-id="31706-114">在**伺服器**/**資料庫總管**，Northwind 下方，展開 **資料表**拖曳`Customers`資料表拖曳至 物件關聯式設計工具 (O/R設計工具）。</span><span class="sxs-lookup"><span data-stu-id="31706-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>  
  
     <span data-ttu-id="31706-115">隨即建立 `Customer` 實體類別，並出現在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="31706-115">A `Customer` entity class is created and appears on the design surface.</span></span>  
  
6.  <span data-ttu-id="31706-116">針對 `Orders`、`Order_Details` 和 `Products` 資料表，重複步驟 6。</span><span class="sxs-lookup"><span data-stu-id="31706-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>  
  
7.  <span data-ttu-id="31706-117">以滑鼠右鍵按一下表示 LINQ to SQL 類別，然後按一下新.dbml 檔案**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="31706-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>  
  
     <span data-ttu-id="31706-118">這樣會建立名為 Northwind.cs 的新程式碼後置頁面，其中包含繼承自 <xref:System.Data.Linq.DataContext> 類別的部分類別定義，在此案例中是 `NorthwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="31706-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>  
  
8.  <span data-ttu-id="31706-119">以下列程式碼取代 Northwind.cs 程式碼檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="31706-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="31706-120">此程式碼透過延伸 LINQ to SQL 產生的 <xref:System.Data.Linq.DataContext> 和資料類別，實作反映提供者：</span><span class="sxs-lookup"><span data-stu-id="31706-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="31706-121">使用 LINQ to SQL 架構資料模組建立資料服務</span><span class="sxs-lookup"><span data-stu-id="31706-121">To create a data service by using a LINQ to SQL-based data model</span></span>  
  
1.  <span data-ttu-id="31706-122">在**方案總管 中**，以滑鼠右鍵按一下您的 ASP.NET 專案的名稱，然後按一下**加入新項目**。</span><span class="sxs-lookup"><span data-stu-id="31706-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="31706-123">在**加入新項目**對話方塊中，選取**WCF 資料服務**。</span><span class="sxs-lookup"><span data-stu-id="31706-123">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="31706-124">提供服務的名稱，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="31706-124">Supply a name for the service, and then click **OK**.</span></span>  
  
     <span data-ttu-id="31706-125">Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="31706-125">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="31706-126">根據預設，程式碼編輯器視窗隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="31706-126">By default, the code-editor window opens.</span></span>  
  
4.  <span data-ttu-id="31706-127">在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindDataContext`。</span><span class="sxs-lookup"><span data-stu-id="31706-127">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>  
  
5.  <span data-ttu-id="31706-128">在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：</span><span class="sxs-lookup"><span data-stu-id="31706-128">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     <span data-ttu-id="31706-129">如此可讓已授權用戶端存取三個指定實體集的資源。</span><span class="sxs-lookup"><span data-stu-id="31706-129">This enables authorized clients to access resources for the three specified entity sets.</span></span>  
  
6.  <span data-ttu-id="31706-130">若要使用網頁瀏覽器測試 Northwind.svc 資料服務，請遵循本主題中的指示[從網頁瀏覽器存取服務](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="31706-130">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31706-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31706-131">See Also</span></span>  
 [<span data-ttu-id="31706-132">如何： 建立使用 ADO.NET Entity Framework 資料來源的資料服務</span><span class="sxs-lookup"><span data-stu-id="31706-132">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [<span data-ttu-id="31706-133">如何： 建立資料服務，使用反映提供者</span><span class="sxs-lookup"><span data-stu-id="31706-133">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [<span data-ttu-id="31706-134">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="31706-134">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
