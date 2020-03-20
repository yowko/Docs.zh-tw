---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: b0660312f540a69911905edd08541ed70cf39bb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174312"
---
# <a name="linq-to-sql"></a><span data-ttu-id="c098c-102">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="c098c-102">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c098c-103">是 .NET Framework 版本 3.5 的一個元件，它提供了用於將關係資料作為物件管理的運行時基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c098c-103">is a component of .NET Framework version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c098c-104">關聯式資料會顯示為二維資料表 (「關聯」\*\* 或「一般檔案」\*\*) 的集合，其中通用資料行會與資料表彼此相關。</span><span class="sxs-lookup"><span data-stu-id="c098c-104">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="c098c-105">若要有效地使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您必須熟悉關聯式資料庫的基礎原則。</span><span class="sxs-lookup"><span data-stu-id="c098c-105">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="c098c-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。</span><span class="sxs-lookup"><span data-stu-id="c098c-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="c098c-107">執行應用程式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將物件模型中的 Language Integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫進行執行。</span><span class="sxs-lookup"><span data-stu-id="c098c-107">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="c098c-108">當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將結果轉譯回您可以在自己的程式語言中處理的物件。</span><span class="sxs-lookup"><span data-stu-id="c098c-108">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="c098c-109">使用 Visual Studio 的開發人員通常使用物件關係設計器，它提供了實現 的許多功能的[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]使用者介面。</span><span class="sxs-lookup"><span data-stu-id="c098c-109">Developers using Visual Studio typically use the Object Relational Designer, which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="c098c-110">這一版 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 隨附的文件會描述建置 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式所需的基本建置組塊、處理序和技巧。</span><span class="sxs-lookup"><span data-stu-id="c098c-110">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="c098c-111">您還可以搜索 Microsoft 文檔以查找特定問題，還可以參加[LINQ 論壇](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)，與專家詳細討論更複雜的主題。</span><span class="sxs-lookup"><span data-stu-id="c098c-111">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="c098c-112">最後[，LINQ 到 SQL：.NET 語言集成查詢關係資料](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10))白皮書詳細介紹了[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]技術，並附有視覺化基本和 C# 代碼示例。</span><span class="sxs-lookup"><span data-stu-id="c098c-112">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c098c-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="c098c-113">In This Section</span></span>  
 [<span data-ttu-id="c098c-114">快速入門</span><span class="sxs-lookup"><span data-stu-id="c098c-114">Getting Started</span></span>](getting-started.md)  
 <span data-ttu-id="c098c-115">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的扼要概觀，以及如何著手使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c098c-115">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="c098c-116">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c098c-116">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="c098c-117">提供對應、查詢、更新、偵錯和類似工作的步驟。</span><span class="sxs-lookup"><span data-stu-id="c098c-117">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="c098c-118">參考</span><span class="sxs-lookup"><span data-stu-id="c098c-118">Reference</span></span>](reference.md)  
 <span data-ttu-id="c098c-119">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 某些層面的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="c098c-119">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="c098c-120">主題包含 SQL-CLR 型別對應、標準查詢運算子轉譯等等。</span><span class="sxs-lookup"><span data-stu-id="c098c-120">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="c098c-121">樣品</span><span class="sxs-lookup"><span data-stu-id="c098c-121">Samples</span></span>](samples.md)  
 <span data-ttu-id="c098c-122">提供指向視覺化基本和 C# 示例的連結。</span><span class="sxs-lookup"><span data-stu-id="c098c-122">Provides links to Visual Basic and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c098c-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="c098c-123">Related Sections</span></span>  
 <span data-ttu-id="c098c-124">[語言集成查詢 （LINQ） - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="c098c-124">[Language-Integrated Query (LINQ) - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)</span></span>\
 <span data-ttu-id="c098c-125">在 C# 中提供 LINQ 技術的概述。</span><span class="sxs-lookup"><span data-stu-id="c098c-125">Provides overviews of LINQ technologies in C#.</span></span>

 [<span data-ttu-id="c098c-126">Language-Integrated Query (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c098c-126">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="c098c-127">在視覺化基礎知識中概述 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="c098c-127">Provides overviews of LINQ technologies in Visual Basic.</span></span>
  
 [<span data-ttu-id="c098c-128">LINQ</span><span class="sxs-lookup"><span data-stu-id="c098c-128">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="c098c-129">介紹視覺化基本使用者的 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="c098c-129">Describes LINQ technologies for Visual Basic users.</span></span>  
  
 [<span data-ttu-id="c098c-130">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c098c-130">LINQ and ADO.NET</span></span>](../../linq-and-ado-net.md)  
 <span data-ttu-id="c098c-131">指向ADO.NET門戶的連結。</span><span class="sxs-lookup"><span data-stu-id="c098c-131">Links to the ADO.NET portal.</span></span>  
  
 <span data-ttu-id="c098c-132">[LINQ to SQL 逐步解說](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c098c-132">[LINQ to SQL Walkthroughs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span></span>  
 <span data-ttu-id="c098c-133">列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可用的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="c098c-133">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="c098c-134">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="c098c-134">Downloading Sample Databases</span></span>](downloading-sample-databases.md)  
 <span data-ttu-id="c098c-135">描述如何下載文件中所用的範例程式庫。</span><span class="sxs-lookup"><span data-stu-id="c098c-135">Describes how to download sample databases used in the documentation.</span></span>  
  
 <span data-ttu-id="c098c-136">[LinqDataSource Web 服務器控制概述](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c098c-136">[LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span></span>  
 <span data-ttu-id="c098c-137">描述<xref:System.Web.UI.WebControls.LinqDataSource>控制項如何通過ASP.NET資料來源控制體系結構向 Web 開發人員公開語言集成查詢 （LINQ）。</span><span class="sxs-lookup"><span data-stu-id="c098c-137">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes Language-Integrated Query (LINQ) to Web developers through the ASP.NET data-source control architecture.</span></span>
