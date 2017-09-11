---
title: "投影和轉換 (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 297de224-b625-44cf-8c00-186b6189aa0e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 723685400aadbf883d7ad939e6a1dd5bdeb7ba09
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="projections-and-transformations-linq-to-xml-visual-basic"></a><span data-ttu-id="26af0-102">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26af0-102">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="26af0-103">本節提供的範例[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]投影和轉換。</span><span class="sxs-lookup"><span data-stu-id="26af0-103">This section provides examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] projections and transformations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26af0-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="26af0-104">In This Section</span></span>  
  
|<span data-ttu-id="26af0-105">主題</span><span class="sxs-lookup"><span data-stu-id="26af0-105">Topic</span></span>|<span data-ttu-id="26af0-106">描述</span><span class="sxs-lookup"><span data-stu-id="26af0-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="26af0-107">如何︰ 使用字典使用 LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26af0-107">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-work-with-dictionaries-using-linq-to-xml.md)|<span data-ttu-id="26af0-108">顯示如何將字典轉換為 XML，以及如何將 XML 轉換為字典。</span><span class="sxs-lookup"><span data-stu-id="26af0-108">Shows how to transform dictionaries to XML, and how to transform XML into dictionaries.</span></span>|  
|[<span data-ttu-id="26af0-109">如何︰ 轉換 XML 樹狀結構 (Visual Basic) 的圖形</span><span class="sxs-lookup"><span data-stu-id="26af0-109">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-transform-the-shape-of-an-xml-tree.md)|<span data-ttu-id="26af0-110">顯示如何轉換 XML 文件的組織結構。</span><span class="sxs-lookup"><span data-stu-id="26af0-110">Shows how to transform the shape of an XML document.</span></span>|  
|[<span data-ttu-id="26af0-111">如何︰ 控制投影 (Visual Basic) 的類型</span><span class="sxs-lookup"><span data-stu-id="26af0-111">How to: Control the Type of a Projection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)|<span data-ttu-id="26af0-112">顯示如何控制 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢的型別。</span><span class="sxs-lookup"><span data-stu-id="26af0-112">Shows how to control the type of a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="26af0-113">如何︰ 投影新類型 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26af0-113">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-a-new-type-linq-to-xml.md)|<span data-ttu-id="26af0-114">顯示如何從 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢規劃使用者定義型別的集合。</span><span class="sxs-lookup"><span data-stu-id="26af0-114">Shows how to project a collection of a user-defined type from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="26af0-115">如何︰ 投影物件圖形 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26af0-115">How to: Project an Object Graph (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-object-graph.md)|<span data-ttu-id="26af0-116">顯示如何從 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢規劃更複雜的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="26af0-116">Shows how to project a more complex object graph from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="26af0-117">如何︰ 投影匿名類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26af0-117">How to: Project an Anonymous Type (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-project-an-anonymous-type.md)|<span data-ttu-id="26af0-118">顯示如何從 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢規劃匿名物件的集合。</span><span class="sxs-lookup"><span data-stu-id="26af0-118">Shows how to project a collection of anonymous objects from a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query.</span></span>|  
|[<span data-ttu-id="26af0-119">如何︰ 從 XML (Visual Basic) 產生文字檔</span><span class="sxs-lookup"><span data-stu-id="26af0-119">How to: Generate Text Files from XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-text-files-from-xml.md)|<span data-ttu-id="26af0-120">顯示如何將 XML 檔案轉換為非 XML 的文字檔。</span><span class="sxs-lookup"><span data-stu-id="26af0-120">Shows how to transform an XML file to a non-XML text file.</span></span>|  
|[<span data-ttu-id="26af0-121">如何︰ 從 CSV 檔案 (Visual Basic) 中產生 XML</span><span class="sxs-lookup"><span data-stu-id="26af0-121">How to: Generate XML from CSV Files (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)|<span data-ttu-id="26af0-122">顯示如何使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 剖析 CSV 檔案並從其中產生 XML。</span><span class="sxs-lookup"><span data-stu-id="26af0-122">Shows how to use [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] to parse a CSV file and generate XML from it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26af0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26af0-123">See Also</span></span>  
 [<span data-ttu-id="26af0-124">查詢 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26af0-124">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
