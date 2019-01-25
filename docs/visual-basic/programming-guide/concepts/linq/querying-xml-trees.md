---
title: 查詢 XML 樹狀結構 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: bb0024a6cfb93be5f1f78f33ad29c22f3400de48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671378"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="63801-102">查詢 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63801-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="63801-103">本節提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="63801-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="63801-104">如需有關撰寫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢，請參閱[Getting Started with Visual Basic 中的 LINQ](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="63801-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="63801-105">具現化 XML 樹狀後，撰寫查詢是從樹狀擷取資料最有效的方式。</span><span class="sxs-lookup"><span data-stu-id="63801-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="63801-106">同時，結合功能結構的查詢可讓您從原始文件產生具有不同組織結構的新 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="63801-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63801-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="63801-107">In This Section</span></span>  
  
|<span data-ttu-id="63801-108">主題</span><span class="sxs-lookup"><span data-stu-id="63801-108">Topic</span></span>|<span data-ttu-id="63801-109">描述</span><span class="sxs-lookup"><span data-stu-id="63801-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="63801-110">基本查詢 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63801-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="63801-111">提供查詢 XML 樹狀的常見範例。</span><span class="sxs-lookup"><span data-stu-id="63801-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="63801-112">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63801-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="63801-113">提供從 XML 樹狀規劃與轉換 XML 樹狀的常見範例。</span><span class="sxs-lookup"><span data-stu-id="63801-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="63801-114">進階查詢技術 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63801-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="63801-115">提供適用於更進階案例的查詢技術。</span><span class="sxs-lookup"><span data-stu-id="63801-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="63801-116">LINQ to XML (Visual Basic) 的 XPath 使用者適用的</span><span class="sxs-lookup"><span data-stu-id="63801-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="63801-117">顯示數個 XPath 運算式和其 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 對等項目。</span><span class="sxs-lookup"><span data-stu-id="63801-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="63801-118">純功能性轉換 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63801-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="63801-119">顯示以功能性程式設計方式撰寫查詢的小型教學課程。</span><span class="sxs-lookup"><span data-stu-id="63801-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63801-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63801-120">See also</span></span>
- [<span data-ttu-id="63801-121">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63801-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
- [<span data-ttu-id="63801-122">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="63801-122">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
