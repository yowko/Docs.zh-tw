---
title: LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c68e00930b518a637a42e99c422e4acf7982f5f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-sql"></a><span data-ttu-id="09924-102">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="09924-102">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="09924-103"> 為 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 3.5 版的元件，它所提供的執行階段基礎結構可將關聯式資料當作物件管理。</span><span class="sxs-lookup"><span data-stu-id="09924-103"> is a component of [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09924-104">關聯式資料會顯示為二維資料表 (「關聯」或「一般檔案」) 的集合，其中通用資料行會與資料表彼此相關。</span><span class="sxs-lookup"><span data-stu-id="09924-104">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="09924-105">若要有效地使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您必須熟悉關聯式資料庫的基礎原則。</span><span class="sxs-lookup"><span data-stu-id="09924-105">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="09924-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。</span><span class="sxs-lookup"><span data-stu-id="09924-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="09924-107">執行應用程式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將物件模型中的 Language Integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫進行執行。</span><span class="sxs-lookup"><span data-stu-id="09924-107">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="09924-108">當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將結果轉譯回您可以在自己的程式語言中處理的物件。</span><span class="sxs-lookup"><span data-stu-id="09924-108">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="09924-109">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員通常會使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]，它可提供用以實作多項 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 功能的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="09924-109">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="09924-110">這一版 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 隨附的文件會描述建置 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式所需的基本建置組塊、處理序和技巧。</span><span class="sxs-lookup"><span data-stu-id="09924-110">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="09924-111">您也可以搜尋特定問題，Microsoft 文件，而且可以參與[LINQ 論壇](http://go.microsoft.com/fwlink/?LinkId=76488)，您可以在其中討論與專家更複雜的主題的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="09924-111">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="09924-112">最後，[LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) (LINQ to SQL：關聯式資料的 .NET Language-Integrated Query) 白皮書會詳述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術，其中包含 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 和 C# 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="09924-112">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09924-113">本章節內容</span><span class="sxs-lookup"><span data-stu-id="09924-113">In This Section</span></span>  
 [<span data-ttu-id="09924-114">快速入門</span><span class="sxs-lookup"><span data-stu-id="09924-114">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 <span data-ttu-id="09924-115">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的扼要概觀，以及如何著手使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="09924-115">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="09924-116">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="09924-116">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="09924-117">提供對應、查詢、更新、偵錯和類似工作的步驟。</span><span class="sxs-lookup"><span data-stu-id="09924-117">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="09924-118">參考</span><span class="sxs-lookup"><span data-stu-id="09924-118">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 <span data-ttu-id="09924-119">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 某些層面的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="09924-119">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="09924-120">主題包含 SQL-CLR 型別對應、標準查詢運算子轉譯等等。</span><span class="sxs-lookup"><span data-stu-id="09924-120">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="09924-121">範例</span><span class="sxs-lookup"><span data-stu-id="09924-121">Samples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 <span data-ttu-id="09924-122">提供 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 和 C# 範例的連結。</span><span class="sxs-lookup"><span data-stu-id="09924-122">Provides links to [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09924-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="09924-123">Related Sections</span></span>  
 [<span data-ttu-id="09924-124">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="09924-124">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 <span data-ttu-id="09924-125">提供 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 技術的概觀。</span><span class="sxs-lookup"><span data-stu-id="09924-125">Provides an overview of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies.</span></span>  
  
 [<span data-ttu-id="09924-126">LINQ</span><span class="sxs-lookup"><span data-stu-id="09924-126">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="09924-127">針對 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 使用者描述 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 技術。</span><span class="sxs-lookup"><span data-stu-id="09924-127">Describes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologies for [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] users.</span></span>  
  
 [<span data-ttu-id="09924-128">LINQ to ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09924-128">LINQ to ADO.NET</span></span>](http://msdn.microsoft.com/en-us/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 <span data-ttu-id="09924-129">[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] 入口網站的連結。</span><span class="sxs-lookup"><span data-stu-id="09924-129">Links to the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portal.</span></span>  
  
 [<span data-ttu-id="09924-130">LINQ to SQL 逐步解說</span><span class="sxs-lookup"><span data-stu-id="09924-130">LINQ to SQL Walkthroughs</span></span>](http://msdn.microsoft.com/en-us/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 <span data-ttu-id="09924-131">列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可用的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="09924-131">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="09924-132">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="09924-132">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 <span data-ttu-id="09924-133">描述如何下載文件中所用的範例程式庫。</span><span class="sxs-lookup"><span data-stu-id="09924-133">Describes how to download sample databases used in the documentation.</span></span>  
  
 [<span data-ttu-id="09924-134">LinqDataSource 技術概觀</span><span class="sxs-lookup"><span data-stu-id="09924-134">LinqDataSource Technology Overview</span></span>](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136)  
 <span data-ttu-id="09924-135">描述 <xref:System.Web.UI.WebControls.LinqDataSource> 控制項如何透過 [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] 資料來源控制項架構，將 [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] 公開給 Web 程式開發人員。</span><span class="sxs-lookup"><span data-stu-id="09924-135">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] to Web developers through the [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] data-source control architecture.</span></span>
