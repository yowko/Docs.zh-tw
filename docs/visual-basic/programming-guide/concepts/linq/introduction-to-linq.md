---
title: LINQ 簡介
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 58613281d79769bfb5515f1291feb9b502a1e846
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549963"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="be74e-102">LINQ 簡介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be74e-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="be74e-103">Language-Integrated Query (LINQ) 是 .NET Framework 3.5 版中引進的創新技術，用來填補許多物件與資料之間的缺口。</span><span class="sxs-lookup"><span data-stu-id="be74e-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="be74e-104">傳統上，資料查詢是以簡單的字串表示，既不會在編譯時進行類型檢查，也不支援 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="be74e-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="be74e-105">此外，您還必須針對每種資料來源類型學習不同的查詢語言：SQL 資料庫、XML 文件、各種 Web 服務等等。</span><span class="sxs-lookup"><span data-stu-id="be74e-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="be74e-106">LINQ 會讓 *查詢* 成為 Visual Basic 中的第一級語言結構。</span><span class="sxs-lookup"><span data-stu-id="be74e-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="be74e-107">您可以使用語言關鍵字和熟悉的運算子，針對強型別的物件集合撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="be74e-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="be74e-108">您可以在 Visual Basic 中撰寫 SQL Server 資料庫、XML 檔、ADO.NET 資料集，以及任何支援或泛型介面之物件集合的 LINQ 查詢 <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="be74e-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="be74e-109">也有協力廠商針對許多 Web 服務和其他資料庫實作提供 LINQ 支援。</span><span class="sxs-lookup"><span data-stu-id="be74e-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="be74e-110">您可以在新的專案中使用 LINQ 查詢，也可以與現有專案中的非 LINQ 查詢一起使用。</span><span class="sxs-lookup"><span data-stu-id="be74e-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="be74e-111">唯一的必要條件是專案要以 .NET Framework 3.5 或更新版本為目標。</span><span class="sxs-lookup"><span data-stu-id="be74e-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="be74e-112">下圖顯示 Visual Studio 中針對 SQL Server 資料庫以 C# 和 Visual Basic 撰寫之部分完成的 LINQ 查詢，其中有完整的類型檢查和 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="be74e-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![顯示具有 Intellisense 的 LINQ 查詢的圖表。](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="be74e-114">後續步驟</span><span class="sxs-lookup"><span data-stu-id="be74e-114">Next Steps</span></span>  
 <span data-ttu-id="be74e-115">若要深入瞭解 LINQ 的詳細資訊，請先熟悉消費者入門一節中的一些基本概念， [消費者入門在 Visual Basic 中使用 linq](getting-started-with-linq.md)，然後閱讀您感興趣的 linq 技術檔：</span><span class="sxs-lookup"><span data-stu-id="be74e-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="be74e-116">SQL Server 資料庫：[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="be74e-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="be74e-117">XML 檔： [LINQ to XML (Visual Basic) ](../../../../standard/linq/linq-xml-overview.md)</span><span class="sxs-lookup"><span data-stu-id="be74e-117">XML documents: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span></span>  
  
- <span data-ttu-id="be74e-118">ADO.NET 資料集：[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="be74e-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="be74e-119">.NET 集合、檔案、字串等等： [LINQ to Objects (Visual Basic) ](linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="be74e-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be74e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be74e-120">See also</span></span>

- [<span data-ttu-id="be74e-121">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be74e-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
