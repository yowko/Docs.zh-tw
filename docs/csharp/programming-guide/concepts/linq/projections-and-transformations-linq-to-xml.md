---
title: "投影和轉換 (LINQ to XML) (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bb0457ab-1823-47e6-9d2d-c93c958cc913
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9dc3f97281f2cd13a44e52c441b537e9e2c640a6
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="projections-and-transformations-linq-to-xml-c"></a><span data-ttu-id="6d6e4-102">投影和轉換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-102">Projections and Transformations (LINQ to XML) (C#)</span></span>
<span data-ttu-id="6d6e4-103">本節提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 投影和轉換的範例。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d6e4-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="6d6e4-104">In This Section</span></span>  
  
|<span data-ttu-id="6d6e4-105">主題</span><span class="sxs-lookup"><span data-stu-id="6d6e4-105">Topic</span></span>|<span data-ttu-id="6d6e4-106">描述</span><span class="sxs-lookup"><span data-stu-id="6d6e4-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6d6e4-107">如何：利用 LINQ to XML 使用字典 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-107">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="6d6e4-108">顯示如何將字典轉換為 XML，以及如何將 XML 轉換為字典。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="6d6e4-109">如何：轉換 XML 樹狀結構的組織結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-109">How to: Transform the Shape of an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="6d6e4-110">顯示如何轉換 XML 文件的組織結構。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="6d6e4-111">如何：控制投影的類型 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-111">How to: Control the Type of a Projection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="6d6e4-112">顯示如何控制 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的型別。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="6d6e4-113">如何：投影新類型 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-113">How to: Project a New Type (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="6d6e4-114">顯示如何從 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢規劃使用者定義型別的集合。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="6d6e4-115">如何：投影物件圖形 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-115">How to: Project an Object Graph (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="6d6e4-116">顯示如何從 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢規劃更複雜的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="6d6e4-117">如何：投影匿名型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-117">How to: Project an Anonymous Type (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="6d6e4-118">顯示如何從 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢規劃匿名物件的集合。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="6d6e4-119">如何：從 XML 產生文字檔 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-119">How to: Generate Text Files from XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="6d6e4-120">顯示如何將 XML 檔案轉換為非 XML 的文字檔。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="6d6e4-121">如何：從 CSV 檔案產生 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-121">How to: Generate XML from CSV Files (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="6d6e4-122">顯示如何使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 剖析 CSV 檔案並從其中產生 XML。</span><span class="sxs-lookup"><span data-stu-id="6d6e4-122">Shows how to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d6e4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d6e4-123">See Also</span></span>  
 [<span data-ttu-id="6d6e4-124">查詢 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d6e4-124">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)

