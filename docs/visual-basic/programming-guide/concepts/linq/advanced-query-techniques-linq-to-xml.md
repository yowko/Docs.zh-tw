---
title: "進階查詢技術 (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 79be877c-fadc-4dfb-9f03-426082b13656
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6983fa5b9637210bb3c56e8f693eb4f956dab0a8
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="advanced-query-techniques-linq-to-xml-visual-basic"></a><span data-ttu-id="5ffe5-102">進階查詢技術 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-102">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5ffe5-103">本節提供更進階的 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢技術範例。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ffe5-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5ffe5-104">In This Section</span></span>  
  
|<span data-ttu-id="5ffe5-105">主題</span><span class="sxs-lookup"><span data-stu-id="5ffe5-105">Topic</span></span>|<span data-ttu-id="5ffe5-106">描述</span><span class="sxs-lookup"><span data-stu-id="5ffe5-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5ffe5-107">如何︰ 聯結兩個集合 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-107">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="5ffe5-108">顯示如何利用 `Join` 子句來使用 XML 資料中的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="5ffe5-109">如何︰ 使用群組 (Visual Basic) 建立階層</span><span class="sxs-lookup"><span data-stu-id="5ffe5-109">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="5ffe5-110">顯示如何群組資料，然後根據該群組產生 XML。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="5ffe5-111">如何︰ 查詢 LINQ to XML 使用 XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-111">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="5ffe5-112">顯示如何根據 XPath 查詢擷取集合。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="5ffe5-113">如何︰ 撰寫 LINQ to XML 軸心方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-113">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="5ffe5-114">顯示如何撰寫 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-114">Shows how to write a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axis method.</span></span>|  
|[<span data-ttu-id="5ffe5-115">如何︰ 列出樹狀結構 (Visual Basic) 中的所有節點</span><span class="sxs-lookup"><span data-stu-id="5ffe5-115">How to: List All Nodes in a Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="5ffe5-116">呈現列出 XML 樹狀中所有節點的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-116">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="5ffe5-117">這在為修改 XML 樹狀結構的程式碼偵錯時相當實用。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-117">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="5ffe5-118">如何︰ 從 Office Open XML 文件 (Visual Basic) 擷取段落</span><span class="sxs-lookup"><span data-stu-id="5ffe5-118">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="5ffe5-119">呈現的程式碼可開啟 Office Open XML 文件、擷取 XElement 物件集合中的段落、段落的文字與段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-119">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="5ffe5-120">如何︰ 修改 Office Open XML 文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-120">How to: Modify an Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="5ffe5-121">呈現會開啟、修改與儲存 Office Open XML 文件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-121">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="5ffe5-122">如何︰ 填入 XML 樹狀結構從檔案系統 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-122">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="5ffe5-123">呈現從檔案系統建立 XML 樹狀結構的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ffe5-123">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ffe5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ffe5-124">See Also</span></span>  
 [<span data-ttu-id="5ffe5-125">查詢 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-125">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
