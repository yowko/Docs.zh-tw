---
title: "查詢 XML 樹狀結構 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66028510b57981879412a1c2a161652adde340bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="cbb12-102">查詢 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="cbb12-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="cbb12-103">本節提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="cbb12-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="cbb12-104">如需撰寫 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的詳細資訊，請參閱[開始使用 C# 中的 LINQ](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="cbb12-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="cbb12-105">具現化 XML 樹狀後，撰寫查詢是從樹狀擷取資料最有效的方式。</span><span class="sxs-lookup"><span data-stu-id="cbb12-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="cbb12-106">同時，結合功能結構的查詢可讓您從原始文件產生具有不同組織結構的新 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="cbb12-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cbb12-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="cbb12-107">In This Section</span></span>  
  
|<span data-ttu-id="cbb12-108">主題</span><span class="sxs-lookup"><span data-stu-id="cbb12-108">Topic</span></span>|<span data-ttu-id="cbb12-109">描述</span><span class="sxs-lookup"><span data-stu-id="cbb12-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cbb12-110">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cbb12-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="cbb12-111">提供查詢 XML 樹狀的常見範例。</span><span class="sxs-lookup"><span data-stu-id="cbb12-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="cbb12-112">投影和轉換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cbb12-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="cbb12-113">提供從 XML 樹狀規劃與轉換 XML 樹狀的常見範例。</span><span class="sxs-lookup"><span data-stu-id="cbb12-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="cbb12-114">進階查詢技術 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cbb12-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="cbb12-115">提供適用於更進階案例的查詢技術。</span><span class="sxs-lookup"><span data-stu-id="cbb12-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="cbb12-116">XPath 使用者適用的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="cbb12-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="cbb12-117">顯示數個 XPath 運算式和其 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 對等項目。</span><span class="sxs-lookup"><span data-stu-id="cbb12-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="cbb12-118">XML 純功能性轉換 (C#)</span><span class="sxs-lookup"><span data-stu-id="cbb12-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="cbb12-119">顯示以功能性程式設計方式撰寫查詢的小型教學課程。</span><span class="sxs-lookup"><span data-stu-id="cbb12-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbb12-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbb12-120">See Also</span></span>  
 [<span data-ttu-id="cbb12-121">程式設計手冊 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cbb12-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="cbb12-122">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="cbb12-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
