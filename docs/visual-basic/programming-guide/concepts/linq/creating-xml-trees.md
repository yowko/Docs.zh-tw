---
title: "建立 XML 樹狀結構 (Visual Basic) |Microsoft 文件"
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
ms.assetid: e86ba12b-17de-4579-81bb-66322b84cfbe
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c60746a3da6255e4c245febf55151b41186a75b7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="creating-xml-trees-visual-basic"></a><span data-ttu-id="6a714-102">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a714-102">Creating XML Trees (Visual Basic)</span></span>
<span data-ttu-id="6a714-103">其中一個最常見的 XML 工做為建構 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="6a714-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="6a714-104">本節描述數種建立這些樹狀結構的方式。</span><span class="sxs-lookup"><span data-stu-id="6a714-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a714-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="6a714-105">In This Section</span></span>  
  
|<span data-ttu-id="6a714-106">主題</span><span class="sxs-lookup"><span data-stu-id="6a714-106">Topic</span></span>|<span data-ttu-id="6a714-107">描述</span><span class="sxs-lookup"><span data-stu-id="6a714-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6a714-108">功能建構 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a714-108">Functional Construction (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="6a714-109">提供 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中的功能結構概觀。</span><span class="sxs-lookup"><span data-stu-id="6a714-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span> <span data-ttu-id="6a714-110">功能結構可讓您利用單一陳述式建立所有或部分 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="6a714-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="6a714-111">這個主題也顯示如何在建構 XML 樹狀時內嵌查詢。</span><span class="sxs-lookup"><span data-stu-id="6a714-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="6a714-112">在 Visual Basic XML 常值簡介</span><span class="sxs-lookup"><span data-stu-id="6a714-112">Introduction to XML Literals in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md)|<span data-ttu-id="6a714-113">提供建立樹狀結構中的快速簡介[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="6a714-113">Provides a quick introduction to creating trees in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] by using XML literals.</span></span> <span data-ttu-id="6a714-114">本主題包含指向 XML 常值之 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 文件的連結。</span><span class="sxs-lookup"><span data-stu-id="6a714-114">This topic includes links to the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] documentation of XML literals.</span></span>|  
|[<span data-ttu-id="6a714-115">複製與附加 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a714-115">Cloning vs. Attaching (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="6a714-116">示範從現有 XML 樹狀結構加入節點 (系統會複製節點然後再加入) 以及加入沒有父代之節點 (只是附加這些節點) 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="6a714-116">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="6a714-117">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a714-117">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="6a714-118">顯示如何從各種來源剖析 XML。</span><span class="sxs-lookup"><span data-stu-id="6a714-118">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="6a714-119">這因為最上層的<xref:System.Xml.XmlReader>，用來剖析 XML。</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="6a714-119"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="6a714-120">如何︰ 填入 XML 樹狀結構使用 XmlWriter (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a714-120">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="6a714-121">示範如何藉由使用<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>填入 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="6a714-121">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="6a714-122">如何︰ 使用 XSD (LINQ to XML) 進行驗證 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a714-122">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="6a714-123">顯示如何使用 XSD 驗證 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="6a714-123">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="6a714-124">XElement 和 XDocument 物件的有效內容</span><span class="sxs-lookup"><span data-stu-id="6a714-124">Valid Content of XElement and XDocument Objects</span></span>](../../../../visual-basic/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects.md)|<span data-ttu-id="6a714-125">說明可以傳遞給用於將內容加入至項目和文件之建構函式和方法的有效引數。</span><span class="sxs-lookup"><span data-stu-id="6a714-125">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a714-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a714-126">See Also</span></span>  
 [<span data-ttu-id="6a714-127">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a714-127">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
