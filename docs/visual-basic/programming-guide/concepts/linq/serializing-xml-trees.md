---
title: "序列化 XML 樹狀結構 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a63e875b1c1391ec1bb2b0ae64be9f9cff28d87d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="f52c2-102">序列化 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f52c2-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="f52c2-103">序列化 XML 樹狀結構表示從 XML 樹狀結構產生 XML。</span><span class="sxs-lookup"><span data-stu-id="f52c2-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="f52c2-104">您可以序列化到檔案中的具象<xref:System.IO.TextWriter>類別，或<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>的具體實作</xref:System.IO.TextWriter></span><span class="sxs-lookup"><span data-stu-id="f52c2-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="f52c2-105">您可以控制各方面的序列化。</span><span class="sxs-lookup"><span data-stu-id="f52c2-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="f52c2-106">例如，您可以控制是否要縮排序列化的 XML，以及是否要撰寫 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="f52c2-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f52c2-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f52c2-107">In This Section</span></span>  
  
|<span data-ttu-id="f52c2-108">主題</span><span class="sxs-lookup"><span data-stu-id="f52c2-108">Topic</span></span>|<span data-ttu-id="f52c2-109">描述</span><span class="sxs-lookup"><span data-stu-id="f52c2-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f52c2-110">序列化時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="f52c2-110">Preserving White Space While Serializing</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="f52c2-111">描述序列化 XML 樹狀時，如何控制空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="f52c2-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="f52c2-112">使用 XML 宣告 (Visual Basic) 進行序列化</span><span class="sxs-lookup"><span data-stu-id="f52c2-112">Serializing with an XML Declaration (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="f52c2-113">描述如何序列化包含 XML 宣告的 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="f52c2-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="f52c2-114">序列化至 File、TextWriter 和 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="f52c2-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="f52c2-115">描述如何序列化文件<xref:System.IO.File>、 <xref:System.IO.TextWriter>，或<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="f52c2-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="f52c2-116">序列化至 XmlReader (叫用 XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f52c2-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="f52c2-117">描述如何建立<xref:System.Xml.XmlReader>，可讓其他模組讀取 XML 樹狀結構的內容。</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="f52c2-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f52c2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f52c2-118">See Also</span></span>  
 [<span data-ttu-id="f52c2-119">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f52c2-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
