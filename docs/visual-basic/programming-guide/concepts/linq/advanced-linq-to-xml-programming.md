---
title: "進階 LINQ to XML 程式設計 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 36018532-a55c-4538-8a27-98f475ea3415
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c4add52a2c195593fd44abf3728bde68fe8d4e1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="advanced-linq-to-xml-programming-visual-basic"></a><span data-ttu-id="694e8-102">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="694e8-102">Advanced LINQ to XML Programming (Visual Basic)</span></span>
<span data-ttu-id="694e8-103">本節提供的資訊將僅適用於某些 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 案例中的進階開發人員。</span><span class="sxs-lookup"><span data-stu-id="694e8-103">This section provides information that will only be applicable to advanced developers in certain [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="694e8-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="694e8-104">In This Section</span></span>  
  
|<span data-ttu-id="694e8-105">主題</span><span class="sxs-lookup"><span data-stu-id="694e8-105">Topic</span></span>|<span data-ttu-id="694e8-106">描述</span><span class="sxs-lookup"><span data-stu-id="694e8-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="694e8-107">LINQ to XML 註釋</span><span class="sxs-lookup"><span data-stu-id="694e8-107">LINQ to XML Annotations</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md)|<span data-ttu-id="694e8-108">描述如何將附註加入到 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 節點和屬性。</span><span class="sxs-lookup"><span data-stu-id="694e8-108">Describes how to add annotations to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] nodes and attributes.</span></span>|  
|[<span data-ttu-id="694e8-109">LINQ to XML 事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="694e8-109">LINQ to XML Events (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-events.md)|<span data-ttu-id="694e8-110">描述如何針對改變 XML 樹狀時發生的事件，撰寫事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="694e8-110">Describes how to write event handlers for events that occur when you alter an XML tree.</span></span>|  
|[<span data-ttu-id="694e8-111">程式設計的節點 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="694e8-111">Programming with Nodes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-with-nodes.md)|<span data-ttu-id="694e8-112">描述如何以比項目和屬性還要細微的位移單位等級來查詢與管理節點。</span><span class="sxs-lookup"><span data-stu-id="694e8-112">Describes how to query and manipulate nodes at a finer level of granularity than elements and attributes.</span></span>|  
|[<span data-ttu-id="694e8-113">宣告式程式碼/命令式混合程式碼 Bug (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="694e8-113">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)|<span data-ttu-id="694e8-114">描述您混用宣告式程式碼 (查詢) 與命令性程式碼 (修改 XML 樹狀結構的程式碼) 時所出現的問題。</span><span class="sxs-lookup"><span data-stu-id="694e8-114">Describes the problems that appear when you mix declarative code (queries) with imperative code (code that modifies the XML tree).</span></span>|  
|[<span data-ttu-id="694e8-115">如何︰ 傳送資料流 XML 片段並存取標頭資訊 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="694e8-115">How to: Stream XML Fragments with Access to Header Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)|<span data-ttu-id="694e8-116">描述如何串流 XML 片段，從<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="694e8-116">Describes how to stream XML fragments from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="694e8-117">您可以使用這個技術來控制您應用程式的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="694e8-117">You can use this technique to control the memory footprint of your application.</span></span>|  
|[<span data-ttu-id="694e8-118">如何︰ 執行大型 XML 文件 (Visual Basic) 的資料流轉換</span><span class="sxs-lookup"><span data-stu-id="694e8-118">How to: Perform Streaming Transform of Large XML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)|<span data-ttu-id="694e8-119">描述如何串流 XML <xref:System.Xml.XmlReader>、 轉換 XML 片段，並使用<xref:System.Xml.Linq.XStreamingElement>.</xref:System.Xml.Linq.XStreamingElement>的輸出資料流</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="694e8-119">Describes how to stream XML from an <xref:System.Xml.XmlReader>, transform the XML fragment, and stream the output using <xref:System.Xml.Linq.XStreamingElement>.</span></span>|  
|[<span data-ttu-id="694e8-120">如何︰ 讀取和寫入編碼的文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="694e8-120">How to: Read and Write an Encoded Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-read-and-write-an-encoded-document.md)|<span data-ttu-id="694e8-121">描述如何讀取與寫入編碼的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="694e8-121">Describes how to read and write XML documents that are encoded.</span></span>|  
|[<span data-ttu-id="694e8-122">使用 XSLT 轉換 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="694e8-122">Using XSLT to Transform an XML Tree (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/using-xslt-to-transform-an-xml-tree.md)|<span data-ttu-id="694e8-123">描述如何使用 XSLT 轉換 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="694e8-123">Describes how to transform an XML tree using XSLT.</span></span>|  
|[<span data-ttu-id="694e8-124">如何︰ 使用註釋將 LINQ to XML 樹狀結構中的 XSLT 樣式 (Visual Basic) 轉換</span><span class="sxs-lookup"><span data-stu-id="694e8-124">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md)|<span data-ttu-id="694e8-125">描述如何使用附註來簡化 XML 樹狀的轉換。</span><span class="sxs-lookup"><span data-stu-id="694e8-125">Describes how annotations can be used to facilitate transforms of an XML tree.</span></span>|  
|[<span data-ttu-id="694e8-126">序列化包含 XElement 物件 (Visual Basic) 的物件圖形</span><span class="sxs-lookup"><span data-stu-id="694e8-126">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-object-graphs-that-contain-xelement-objects.md)|<span data-ttu-id="694e8-127">描述如何序列化包含的物件圖形<xref:System.Xml.Linq.XElement>和<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="694e8-127">Describes how to serialize object graphs that contain <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|[<span data-ttu-id="694e8-128">WPF 資料繫結與 LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="694e8-128">WPF Data Binding with LINQ to XML</span></span>](https://docs.microsoft.com/visualstudio/designers/wpf-data-binding-with-linq-to-xml)|<span data-ttu-id="694e8-129">描述如何使用 LINQ to XML 做為 Windows Presentation Foundation 應用程式中資料繫結的資料來源。</span><span class="sxs-lookup"><span data-stu-id="694e8-129">Describes how to use LINQ to XML as the data source for data binding in Windows Presentation Foundation applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="694e8-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="694e8-130">See Also</span></span>  
 [<span data-ttu-id="694e8-131">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="694e8-131">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
