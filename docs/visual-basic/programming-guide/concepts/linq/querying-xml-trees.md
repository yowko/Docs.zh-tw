---
title: "查詢 XML 樹狀結構 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1516cdc58effaa3e738210b948b43d7ed170890a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="32aba-102">查詢 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32aba-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="32aba-103">本節提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="32aba-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="32aba-104">如需有關撰寫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢，請參閱[在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="32aba-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="32aba-105">具現化 XML 樹狀後，撰寫查詢是從樹狀擷取資料最有效的方式。</span><span class="sxs-lookup"><span data-stu-id="32aba-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="32aba-106">同時，結合功能結構的查詢可讓您從原始文件產生具有不同組織結構的新 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="32aba-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32aba-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="32aba-107">In This Section</span></span>  
  
|<span data-ttu-id="32aba-108">主題</span><span class="sxs-lookup"><span data-stu-id="32aba-108">Topic</span></span>|<span data-ttu-id="32aba-109">說明</span><span class="sxs-lookup"><span data-stu-id="32aba-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="32aba-110">基本查詢 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32aba-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="32aba-111">提供查詢 XML 樹狀的常見範例。</span><span class="sxs-lookup"><span data-stu-id="32aba-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="32aba-112">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32aba-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="32aba-113">提供從 XML 樹狀規劃與轉換 XML 樹狀的常見範例。</span><span class="sxs-lookup"><span data-stu-id="32aba-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="32aba-114">進階查詢技術 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32aba-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="32aba-115">提供適用於更進階案例的查詢技術。</span><span class="sxs-lookup"><span data-stu-id="32aba-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="32aba-116">LINQ to XML (Visual Basic) 的 XPath 使用者適用的</span><span class="sxs-lookup"><span data-stu-id="32aba-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="32aba-117">顯示數個 XPath 運算式和其 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 對等項目。</span><span class="sxs-lookup"><span data-stu-id="32aba-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="32aba-118">純功能性轉換 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32aba-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="32aba-119">顯示以功能性程式設計方式撰寫查詢的小型教學課程。</span><span class="sxs-lookup"><span data-stu-id="32aba-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32aba-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32aba-120">See Also</span></span>  
 [<span data-ttu-id="32aba-121">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32aba-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="32aba-122">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="32aba-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
