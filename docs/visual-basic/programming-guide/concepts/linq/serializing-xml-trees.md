---
title: 序列化 XML 樹狀結構
ms.date: 07/20/2015
ms.assetid: 2c340695-a726-4030-85be-6975d8a149cf
ms.openlocfilehash: 640dc49134e869b60b4fa1fcd9a71fb1d61d39db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411814"
---
# <a name="serializing-xml-trees-visual-basic"></a><span data-ttu-id="dee5c-102">序列化 XML 樹狀結構（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="dee5c-102">Serializing XML Trees (Visual Basic)</span></span>
<span data-ttu-id="dee5c-103">序列化 XML 樹狀結構表示從 XML 樹狀結構產生 XML。</span><span class="sxs-lookup"><span data-stu-id="dee5c-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="dee5c-104">您可以序列化到檔案、<xref:System.IO.TextWriter> 類別的具體實作，或 <xref:System.Xml.XmlWriter> 的具體實作。</span><span class="sxs-lookup"><span data-stu-id="dee5c-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="dee5c-105">您可以控制各方面的序列化。</span><span class="sxs-lookup"><span data-stu-id="dee5c-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="dee5c-106">例如，您可以控制是否要縮排序列化的 XML，以及是否要撰寫 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="dee5c-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dee5c-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="dee5c-107">In This Section</span></span>  
  
|<span data-ttu-id="dee5c-108">主題</span><span class="sxs-lookup"><span data-stu-id="dee5c-108">Topic</span></span>|<span data-ttu-id="dee5c-109">說明</span><span class="sxs-lookup"><span data-stu-id="dee5c-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dee5c-110">序列化時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="dee5c-110">Preserving White Space While Serializing</span></span>](preserving-white-space-while-serializing.md)|<span data-ttu-id="dee5c-111">描述序列化 XML 樹狀時，如何控制空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="dee5c-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="dee5c-112">使用 XML 宣告序列化（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="dee5c-112">Serializing with an XML Declaration (Visual Basic)</span></span>](serializing-with-an-xml-declaration.md)|<span data-ttu-id="dee5c-113">描述如何序列化包含 XML 宣告的 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="dee5c-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="dee5c-114">序列化至 File、TextWriter 和 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="dee5c-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="dee5c-115">描述如何將文件序列化到 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="dee5c-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="dee5c-116">序列化至 XmlReader （叫用 XSLT）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="dee5c-116">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>](serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="dee5c-117">描述如何建立可讓其他模組讀取 XML 樹狀結構之內容的 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="dee5c-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dee5c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dee5c-118">See also</span></span>

- [<span data-ttu-id="dee5c-119">程式設計指南（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="dee5c-119">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](programming-guide-linq-to-xml.md)
