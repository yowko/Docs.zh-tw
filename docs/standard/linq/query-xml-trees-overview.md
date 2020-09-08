---
title: 查詢 XML 樹狀結構總覽-LINQ to XML
description: 瞭解如何查詢 XML 樹狀結構，以及如何結合查詢和功能結構來調整樹狀結構。
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 3529650aa5ee0575331653f5714c841d1fc1dfb5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552737"
---
# <a name="query-xml-trees-overview-linq-to-xml"></a><span data-ttu-id="99f8e-103">查詢 XML 樹狀結構總覽 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="99f8e-103">Query XML trees overview (LINQ to XML)</span></span>

<span data-ttu-id="99f8e-104">在您具現化 XML 樹狀結構之後，撰寫查詢是從樹狀目錄中解壓縮資料最有效的方式。</span><span class="sxs-lookup"><span data-stu-id="99f8e-104">After you've instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="99f8e-105">同時，結合功能結構的查詢可讓您從原始文件產生具有不同組織結構的新 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="99f8e-105">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>

<span data-ttu-id="99f8e-106">如需 LINQ 查詢的背景資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="99f8e-106">For background information about LINQ queries, see:</span></span>

- [<span data-ttu-id="99f8e-107">LINQ 查詢簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="99f8e-107">Introduction to LINQ Queries (C#)</span></span>](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="99f8e-108">撰寫第一個 LINQ 查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99f8e-108">Writing Your First LINQ Query (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)

## <a name="in-this-section"></a><span data-ttu-id="99f8e-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="99f8e-109">In this section</span></span>

<span data-ttu-id="99f8e-110">這一節的文章會提供有關 LINQ to XML 查詢的資訊，包括範例。</span><span class="sxs-lookup"><span data-stu-id="99f8e-110">This section of articles provides information, including examples, about LINQ to XML queries.</span></span> <span data-ttu-id="99f8e-111">它包含下列小節：</span><span class="sxs-lookup"><span data-stu-id="99f8e-111">It comprises the following subsections:</span></span>

|<span data-ttu-id="99f8e-112">發行項</span><span class="sxs-lookup"><span data-stu-id="99f8e-112">Article</span></span>|<span data-ttu-id="99f8e-113">描述</span><span class="sxs-lookup"><span data-stu-id="99f8e-113">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="99f8e-114">基本查詢</span><span class="sxs-lookup"><span data-stu-id="99f8e-114">Basic queries</span></span>](find-element-specific-attribute.md)|<span data-ttu-id="99f8e-115">提供查詢 XML 樹狀的常見範例。</span><span class="sxs-lookup"><span data-stu-id="99f8e-115">Provides common examples of querying XML trees.</span></span>|
|[<span data-ttu-id="99f8e-116">投影和轉換</span><span class="sxs-lookup"><span data-stu-id="99f8e-116">Projections and transformations</span></span>](work-dictionaries-linq-xml.md)|<span data-ttu-id="99f8e-117">提供從 XML 樹狀規劃與轉換 XML 樹狀的常見範例。</span><span class="sxs-lookup"><span data-stu-id="99f8e-117">Provides common examples of projecting from and transforming XML trees.</span></span>|
|[<span data-ttu-id="99f8e-118">先進的查詢技術</span><span class="sxs-lookup"><span data-stu-id="99f8e-118">Advanced query techniques</span></span>](join-two-collections.md)|<span data-ttu-id="99f8e-119">提供適用於更進階案例的查詢技術。</span><span class="sxs-lookup"><span data-stu-id="99f8e-119">Provides query techniques that are useful in more advanced scenarios.</span></span>|
|[<span data-ttu-id="99f8e-120">XPath 使用者的 LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="99f8e-120">LINQ to XML for XPath users</span></span>](comparison-xpath-linq-xml.md)|<span data-ttu-id="99f8e-121">提供許多 XPath 運算式及其 LINQ to XML 對等專案。</span><span class="sxs-lookup"><span data-stu-id="99f8e-121">Presents a number of XPath expressions and their LINQ to XML equivalents.</span></span>|
|[<span data-ttu-id="99f8e-122">純功能性轉換簡介</span><span class="sxs-lookup"><span data-stu-id="99f8e-122">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)|<span data-ttu-id="99f8e-123">顯示以功能性程式設計方式撰寫查詢的小型教學課程。</span><span class="sxs-lookup"><span data-stu-id="99f8e-123">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|

## <a name="see-also"></a><span data-ttu-id="99f8e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99f8e-124">See also</span></span>

- [<span data-ttu-id="99f8e-125">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="99f8e-125">Language-Integrated Query (LINQ) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="99f8e-126">LINQ 查詢簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="99f8e-126">Introduction to LINQ Queries (C#)</span></span>](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="99f8e-127">Visual Basic 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="99f8e-127">LINQ in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="99f8e-128">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99f8e-128">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="99f8e-129">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="99f8e-129">Getting Started with LINQ in Visual Basic</span></span>](../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="99f8e-130">撰寫第一個 LINQ 查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99f8e-130">Writing Your First LINQ Query (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)
