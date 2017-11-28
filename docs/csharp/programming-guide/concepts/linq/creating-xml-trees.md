---
title: "建立 XML 樹狀結構 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bccc3e0a-c08c-468e-9d30-e075670fdace
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23b19593774b5a010b453e3fe755e21386afd015
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="creating-xml-trees-c"></a><span data-ttu-id="d7384-102">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="d7384-102">Creating XML Trees (C#)</span></span>
<span data-ttu-id="d7384-103">其中一個最常見的 XML 工做為建構 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d7384-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="d7384-104">本節描述數種建立這些樹狀結構的方式。</span><span class="sxs-lookup"><span data-stu-id="d7384-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7384-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d7384-105">In This Section</span></span>  
  
|<span data-ttu-id="d7384-106">主題</span><span class="sxs-lookup"><span data-stu-id="d7384-106">Topic</span></span>|<span data-ttu-id="d7384-107">描述</span><span class="sxs-lookup"><span data-stu-id="d7384-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d7384-108">函數式建構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d7384-108">Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="d7384-109">提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的功能結構概觀。</span><span class="sxs-lookup"><span data-stu-id="d7384-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="d7384-110">功能結構可讓您利用單一陳述式建立所有或部分 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d7384-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="d7384-111">這個主題也顯示如何在建構 XML 樹狀時內嵌查詢。</span><span class="sxs-lookup"><span data-stu-id="d7384-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="d7384-112">在 C# 中建立 XML 樹狀結構 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d7384-112">Creating XML Trees in C# (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md)|<span data-ttu-id="d7384-113">顯示如何在 C# 中建立樹狀。</span><span class="sxs-lookup"><span data-stu-id="d7384-113">Shows how to create trees in C#.</span></span>|  
|[<span data-ttu-id="d7384-114">複製與附加 (C#)</span><span class="sxs-lookup"><span data-stu-id="d7384-114">Cloning vs. Attaching (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/cloning-vs-attaching.md)|<span data-ttu-id="d7384-115">示範從現有 XML 樹狀結構加入節點 (系統會複製節點然後再加入) 以及加入沒有父代之節點 (只是附加這些節點) 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="d7384-115">Demonstrates the difference between adding nodes from an existing XML tree (nodes are cloned and then added) and adding nodes with no parent (they are simply attached).</span></span>|  
|[<span data-ttu-id="d7384-116">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d7384-116">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="d7384-117">顯示如何從各種來源剖析 XML。</span><span class="sxs-lookup"><span data-stu-id="d7384-117">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d7384-118"> 的層級位於用來剖析 XML 的 <xref:System.Xml.XmlReader> 頂端。</span><span class="sxs-lookup"><span data-stu-id="d7384-118"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="d7384-119">如何：使用 XmlWriter 填入 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d7384-119">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="d7384-120">顯示如何使用 <xref:System.Xml.XmlWriter> 填入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d7384-120">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="d7384-121">如何：使用 XSD 進行驗證 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d7384-121">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="d7384-122">顯示如何使用 XSD 驗證 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="d7384-122">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="d7384-123">XElement 和 XDocument 物件的有效內容</span><span class="sxs-lookup"><span data-stu-id="d7384-123">Valid Content of XElement and XDocument Objects</span></span>](../../../../csharp/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects3.md)|<span data-ttu-id="d7384-124">說明可以傳遞給用於將內容加入至項目和文件之建構函式和方法的有效引數。</span><span class="sxs-lookup"><span data-stu-id="d7384-124">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7384-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7384-125">See Also</span></span>  
 [<span data-ttu-id="d7384-126">程式設計手冊 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d7384-126">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
