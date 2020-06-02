---
title: LINQ to SQL
description: LINQ to SQL 是 .NET Framework 的元件，可提供用來將關聯式資料當做物件管理的執行時間基礎結構。
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 13502bfee3ee24764d190dace1512bc958343973
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286310"
---
# <a name="linq-to-sql"></a><span data-ttu-id="9be8f-103">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9be8f-103">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9be8f-104">是 .NET Framework 版本3.5 的元件，可提供用來將關聯式資料當做物件管理的執行時間基礎結構。</span><span class="sxs-lookup"><span data-stu-id="9be8f-104">is a component of .NET Framework version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9be8f-105">關聯式資料會顯示為二維資料表 (「關聯」\*\* 或「一般檔案」\*\*) 的集合，其中通用資料行會與資料表彼此相關。</span><span class="sxs-lookup"><span data-stu-id="9be8f-105">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="9be8f-106">若要有效地使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您必須熟悉關聯式資料庫的基礎原則。</span><span class="sxs-lookup"><span data-stu-id="9be8f-106">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="9be8f-107">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。</span><span class="sxs-lookup"><span data-stu-id="9be8f-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="9be8f-108">執行應用程式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將物件模型中的 Language Integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫進行執行。</span><span class="sxs-lookup"><span data-stu-id="9be8f-108">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="9be8f-109">當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將結果轉譯回您可以在自己的程式語言中處理的物件。</span><span class="sxs-lookup"><span data-stu-id="9be8f-109">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="9be8f-110">使用 Visual Studio 的開發人員通常會使用物件關聯式設計工具，它會提供用來執行許多功能的使用者介面 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9be8f-110">Developers using Visual Studio typically use the Object Relational Designer, which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="9be8f-111">這一版 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 隨附的文件會描述建置 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式所需的基本建置組塊、處理序和技巧。</span><span class="sxs-lookup"><span data-stu-id="9be8f-111">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="9be8f-112">您也可以搜尋 Microsoft Docs 中的特定問題，而且您可以參與[LINQ 論壇](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)，您可以在其中詳細討論更複雜的主題。</span><span class="sxs-lookup"><span data-stu-id="9be8f-112">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="9be8f-113">最後， [LINQ to SQL：關聯式資料的 .Net 語言整合式查詢](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10))白皮書詳細說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術，並 Visual Basic 和 c # 程式碼範例完成。</span><span class="sxs-lookup"><span data-stu-id="9be8f-113">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9be8f-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="9be8f-114">In This Section</span></span>  
 [<span data-ttu-id="9be8f-115">快速入門</span><span class="sxs-lookup"><span data-stu-id="9be8f-115">Getting Started</span></span>](getting-started.md)  
 <span data-ttu-id="9be8f-116">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的扼要概觀，以及如何著手使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9be8f-116">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="9be8f-117">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9be8f-117">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="9be8f-118">提供對應、查詢、更新、偵錯和類似工作的步驟。</span><span class="sxs-lookup"><span data-stu-id="9be8f-118">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="9be8f-119">參考</span><span class="sxs-lookup"><span data-stu-id="9be8f-119">Reference</span></span>](reference.md)  
 <span data-ttu-id="9be8f-120">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 某些層面的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="9be8f-120">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="9be8f-121">主題包含 SQL-CLR 型別對應、標準查詢運算子轉譯等等。</span><span class="sxs-lookup"><span data-stu-id="9be8f-121">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="9be8f-122">範例</span><span class="sxs-lookup"><span data-stu-id="9be8f-122">Samples</span></span>](samples.md)  
 <span data-ttu-id="9be8f-123">提供 Visual Basic 和 c # 範例的連結。</span><span class="sxs-lookup"><span data-stu-id="9be8f-123">Provides links to Visual Basic and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9be8f-124">相關章節</span><span class="sxs-lookup"><span data-stu-id="9be8f-124">Related Sections</span></span>  
 <span data-ttu-id="9be8f-125">[語言整合式查詢（LINQ）-C#](../../../../../csharp/programming-guide/concepts/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="9be8f-125">[Language-Integrated Query (LINQ) - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)</span></span>\
 <span data-ttu-id="9be8f-126">概述 c # 中的 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="9be8f-126">Provides overviews of LINQ technologies in C#.</span></span>

 [<span data-ttu-id="9be8f-127">Language-Integrated Query (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9be8f-127">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="9be8f-128">概述 Visual Basic 中的 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="9be8f-128">Provides overviews of LINQ technologies in Visual Basic.</span></span>
  
 [<span data-ttu-id="9be8f-129">LINQ</span><span class="sxs-lookup"><span data-stu-id="9be8f-129">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="9be8f-130">描述 Visual Basic 使用者的 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="9be8f-130">Describes LINQ technologies for Visual Basic users.</span></span>  
  
 [<span data-ttu-id="9be8f-131">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9be8f-131">LINQ and ADO.NET</span></span>](../../linq-and-ado-net.md)  
 <span data-ttu-id="9be8f-132">ADO.NET 入口網站的連結。</span><span class="sxs-lookup"><span data-stu-id="9be8f-132">Links to the ADO.NET portal.</span></span>  
  
 <span data-ttu-id="9be8f-133">[LINQ to SQL 逐步解說](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9be8f-133">[LINQ to SQL Walkthroughs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span></span>  
 <span data-ttu-id="9be8f-134">列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可用的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="9be8f-134">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="9be8f-135">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="9be8f-135">Downloading Sample Databases</span></span>](downloading-sample-databases.md)  
 <span data-ttu-id="9be8f-136">描述如何下載文件中所用的範例程式庫。</span><span class="sxs-lookup"><span data-stu-id="9be8f-136">Describes how to download sample databases used in the documentation.</span></span>  
  
 <span data-ttu-id="9be8f-137">[LinqDataSource Web 服務器控制項總覽](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9be8f-137">[LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span></span>  
 <span data-ttu-id="9be8f-138">描述控制項如何 <xref:System.Web.UI.WebControls.LinqDataSource> 透過 ASP.NET 資料原始檔控制架構，將語言整合式查詢（LINQ）公開給 Web 開發人員。</span><span class="sxs-lookup"><span data-stu-id="9be8f-138">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes Language-Integrated Query (LINQ) to Web developers through the ASP.NET data-source control architecture.</span></span>
