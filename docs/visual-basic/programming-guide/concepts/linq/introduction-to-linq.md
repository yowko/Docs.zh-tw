---
title: "(Visual Basic) 的 LINQ 簡介 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d2c02daacc2674da31715e5fda027b97e6b7bc97
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="50464-102">(Visual Basic) 的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="50464-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="50464-103">語言整合查詢 (LINQ) 是一項創新技術引進.NET Framework 3.5 版中該橋接器世界的物件與世界的資料之間的差距。</span><span class="sxs-lookup"><span data-stu-id="50464-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="50464-104">傳統上，對資料執行查詢被以簡單的字串，不具型別檢查在編譯時間或 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="50464-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="50464-105">此外，您必須了解每個資料來源類型的不同的查詢語言︰ SQL 資料庫、 XML 文件、 不同的 Web 服務等等。</span><span class="sxs-lookup"><span data-stu-id="50464-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="50464-106">LINQ 可讓*查詢*在 Visual Basic 中的第一級語言建構。</span><span class="sxs-lookup"><span data-stu-id="50464-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="50464-107">您可以使用語言關鍵字和熟悉的運算子，以撰寫強型別的物件集合的查詢。</span><span class="sxs-lookup"><span data-stu-id="50464-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="50464-108">您可以在 Visual Basic 中撰寫 LINQ 查詢，SQL Server 資料庫、 XML 文件、 ADO.NET 資料集和任何支援的物件集合<xref:System.Collections.IEnumerable>或泛型<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="50464-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="50464-109">協力廠商也被提供 LINQ 支援許多 Web 服務和其他資料庫實作。</span><span class="sxs-lookup"><span data-stu-id="50464-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="50464-110">在新的專案，或與現有的專案中的非 LINQ 查詢，您可以使用 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="50464-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="50464-111">唯一的需求是將專案目標.NET Framework 3.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="50464-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="50464-112">從 Visual Studio 下的圖顯示的部分完成 LINQ 查詢對 SQL Server 資料庫在 C# 和 Visual Basic 中使用完整的型別檢查和 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="50464-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="50464-113">![具有 Intellisense 的 LINQ 查詢](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="50464-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="50464-114">後續步驟</span><span class="sxs-lookup"><span data-stu-id="50464-114">Next Steps</span></span>  
 <span data-ttu-id="50464-115">若要了解更多詳細 LINQ，開始熟悉入門 」 一節中的某些基本概念[在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)，然後讀取您感興趣的 LINQ 技術的文件︰</span><span class="sxs-lookup"><span data-stu-id="50464-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="50464-116">SQL Server 資料庫︰ [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span><span class="sxs-lookup"><span data-stu-id="50464-116">SQL Server databases: [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)</span></span>  
  
-   <span data-ttu-id="50464-117">XML 文件︰ [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="50464-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="50464-118">ADO.NET 資料集︰ [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)</span><span class="sxs-lookup"><span data-stu-id="50464-118">ADO.NET Datasets: [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)</span></span>  
  
-   <span data-ttu-id="50464-119">.NET 集合、 檔案、 字串等等︰ [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="50464-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50464-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50464-120">See Also</span></span>  
 [<span data-ttu-id="50464-121">語言整合查詢 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50464-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
