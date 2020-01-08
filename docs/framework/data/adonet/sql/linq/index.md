---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 4553be9eeab8792197503d0b1de872f4494277b6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634621"
---
# <a name="linq-to-sql"></a><span data-ttu-id="53172-102">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="53172-102">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="53172-103">是 .NET Framework 3.5 版的元件，它會提供執行時間基礎結構，以便將關聯式資料當做物件來管理。</span><span class="sxs-lookup"><span data-stu-id="53172-103">is a component of .NET Framework version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53172-104">關聯式資料會顯示為二維資料表 (「關聯」或「一般檔案」) 的集合，其中通用資料行會與資料表彼此相關。</span><span class="sxs-lookup"><span data-stu-id="53172-104">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="53172-105">若要有效地使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您必須熟悉關聯式資料庫的基礎原則。</span><span class="sxs-lookup"><span data-stu-id="53172-105">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="53172-106">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，關聯式資料庫的資料模型會對應至以開發人員的程式設計語言表示的物件模型。</span><span class="sxs-lookup"><span data-stu-id="53172-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="53172-107">執行應用程式時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將物件模型中的 Language Integrated Query (LINQ) 轉譯成 SQL，並將這些查詢傳送至資料庫進行執行。</span><span class="sxs-lookup"><span data-stu-id="53172-107">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="53172-108">當資料庫傳回結果時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將結果轉譯回您可以在自己的程式語言中處理的物件。</span><span class="sxs-lookup"><span data-stu-id="53172-108">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="53172-109">使用 Visual Studio 的開發人員通常會使用物件關聯式設計工具，它會提供一個使用者介面來執行 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]的許多功能。</span><span class="sxs-lookup"><span data-stu-id="53172-109">Developers using Visual Studio typically use the Object Relational Designer, which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="53172-110">這一版 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 隨附的文件會描述建置 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式所需的基本建置組塊、處理序和技巧。</span><span class="sxs-lookup"><span data-stu-id="53172-110">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="53172-111">您也可以搜尋 Microsoft Docs 中的特定問題，而且您可以參與[LINQ 論壇](https://go.microsoft.com/fwlink/?LinkId=76488)，您可以在其中詳細討論更複雜的主題。</span><span class="sxs-lookup"><span data-stu-id="53172-111">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="53172-112">最後， [LINQ to SQL：關聯式資料的 .Net 語言整合式查詢](https://go.microsoft.com/fwlink/?LinkId=93205)白皮書詳細說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術，完成 Visual Basic 和C#程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="53172-112">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53172-113">本章節內容</span><span class="sxs-lookup"><span data-stu-id="53172-113">In This Section</span></span>  
 [<span data-ttu-id="53172-114">使用者入門</span><span class="sxs-lookup"><span data-stu-id="53172-114">Getting Started</span></span>](getting-started.md)  
 <span data-ttu-id="53172-115">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的扼要概觀，以及如何著手使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="53172-115">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="53172-116">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="53172-116">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="53172-117">提供對應、查詢、更新、偵錯和類似工作的步驟。</span><span class="sxs-lookup"><span data-stu-id="53172-117">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="53172-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="53172-118">Reference</span></span>](reference.md)  
 <span data-ttu-id="53172-119">提供 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 某些層面的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="53172-119">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="53172-120">主題包含 SQL-CLR 型別對應、標準查詢運算子轉譯等等。</span><span class="sxs-lookup"><span data-stu-id="53172-120">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="53172-121">範例</span><span class="sxs-lookup"><span data-stu-id="53172-121">Samples</span></span>](samples.md)  
 <span data-ttu-id="53172-122">提供 Visual Basic 和C#範例的連結。</span><span class="sxs-lookup"><span data-stu-id="53172-122">Provides links to Visual Basic and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="53172-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="53172-123">Related Sections</span></span>  
 <span data-ttu-id="53172-124">[語言整合式查詢（LINQ）- C# ](../../../../../csharp/programming-guide/concepts/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="53172-124">[Language-Integrated Query (LINQ) - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)</span></span>\
 <span data-ttu-id="53172-125">概述中C#的 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="53172-125">Provides overviews of LINQ technologies in C#.</span></span>
 
 [<span data-ttu-id="53172-126">Language-Integrated Query (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53172-126">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="53172-127">概述 Visual Basic 中的 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="53172-127">Provides overviews of LINQ technologies in Visual Basic.</span></span>
  
 [<span data-ttu-id="53172-128">LINQ</span><span class="sxs-lookup"><span data-stu-id="53172-128">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="53172-129">描述 Visual Basic 使用者的 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="53172-129">Describes LINQ technologies for Visual Basic users.</span></span>  
  
 [<span data-ttu-id="53172-130">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="53172-130">LINQ and ADO.NET</span></span>](../../linq-and-ado-net.md)  
 <span data-ttu-id="53172-131">ADO.NET 入口網站的連結。</span><span class="sxs-lookup"><span data-stu-id="53172-131">Links to the ADO.NET portal.</span></span>  
  
 <span data-ttu-id="53172-132">[LINQ to SQL 逐步解說](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="53172-132">[LINQ to SQL Walkthroughs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span></span>  
 <span data-ttu-id="53172-133">列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可用的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="53172-133">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="53172-134">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="53172-134">Downloading Sample Databases</span></span>](downloading-sample-databases.md)  
 <span data-ttu-id="53172-135">描述如何下載文件中所用的範例程式庫。</span><span class="sxs-lookup"><span data-stu-id="53172-135">Describes how to download sample databases used in the documentation.</span></span>  
  
 <span data-ttu-id="53172-136">[LinqDataSource Web 服務器控制項總覽](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53172-136">[LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span></span>  
 <span data-ttu-id="53172-137">描述 <xref:System.Web.UI.WebControls.LinqDataSource> 控制項如何透過 ASP.NET 資料原始檔控制架構，向 Web 開發人員公開語言整合式查詢（LINQ）。</span><span class="sxs-lookup"><span data-stu-id="53172-137">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes Language-Integrated Query (LINQ) to Web developers through the ASP.NET data-source control architecture.</span></span>
