---
title: LINQ 簡介 (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: ea17de41bbbc03158179f207aa0bc9fc9cceb863
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410689"
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="d0411-102">LINQ 簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0411-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="d0411-103">Language-Integrated Query (LINQ) 是 .NET Framework 3.5 版中引進的創新技術，用來填補許多物件與資料之間的缺口。</span><span class="sxs-lookup"><span data-stu-id="d0411-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="d0411-104">傳統上，針對資料的查詢是以簡單字串表示，而不會在編譯期間進行型別檢查，或提供 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="d0411-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="d0411-105">此外，您還必須了解每種資料來源類型的不同查詢語言：SQL 資料庫、XML 文件、各種 Web 服務等。</span><span class="sxs-lookup"><span data-stu-id="d0411-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="d0411-106">LINQ 會在 C# 中將「查詢」設為第一類語言建構。</span><span class="sxs-lookup"><span data-stu-id="d0411-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="d0411-107">您可以使用語言關鍵字和熟悉的運算子，針對強型別的物件集合撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="d0411-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="d0411-108">您可以使用 C# 針對下列項目撰寫 LINQ 查詢：SQL Server 資料庫、XML 文件、ADO.NET 資料集，以及支援 <xref:System.Collections.IEnumerable> 或泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面的任何物件集合。</span><span class="sxs-lookup"><span data-stu-id="d0411-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="d0411-109">也有協力廠商針對許多 Web 服務和其他資料庫實作提供 LINQ 支援。</span><span class="sxs-lookup"><span data-stu-id="d0411-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="d0411-110">您可以在新的專案中使用 LINQ 查詢，也可以與現有專案中的非 LINQ 查詢一起使用。</span><span class="sxs-lookup"><span data-stu-id="d0411-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="d0411-111">唯一的必要條件是專案要以 .NET Framework 3.5 或更新版本為目標。</span><span class="sxs-lookup"><span data-stu-id="d0411-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="d0411-112">下圖顯示 Visual Studio 中針對 SQL Server 資料庫以 C# 和 Visual Basic 撰寫之部分完成的 LINQ 查詢，其中有完整的類型檢查和 IntelliSense 支援：</span><span class="sxs-lookup"><span data-stu-id="d0411-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support:</span></span>  
  
 ![顯示具有 Intellisense 的 LINQ 查詢的圖表。](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="d0411-114">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d0411-114">Next Steps</span></span>  
 <span data-ttu-id="d0411-115">若要深入了解 LINQ 的詳細資料，請先參閱[開始使用 C# 中的 LINQ](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) 的＜使用者入門＞一節以熟悉一些基本概念，然後閱讀您感興趣的 LINQ 技術文件：</span><span class="sxs-lookup"><span data-stu-id="d0411-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="d0411-116">SQL Server 資料庫：[LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="d0411-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="d0411-117">XML 文件：[LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="d0411-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="d0411-118">ADO.NET 資料集：[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="d0411-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="d0411-119">.NET 集合、檔案、字串等：[LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="d0411-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0411-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0411-120">See also</span></span>

- [<span data-ttu-id="d0411-121">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d0411-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
