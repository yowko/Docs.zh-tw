---
title: 序列化 XML 樹狀結構 (C#)
ms.date: 07/20/2015
ms.assetid: b3937e54-4ce9-4236-ac96-14e7972aa594
ms.openlocfilehash: 8f372a05bd69b801085cba9d9a3b11ae01841a2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338347"
---
# <a name="serializing-xml-trees-c"></a><span data-ttu-id="888a9-102">序列化 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="888a9-102">Serializing XML Trees (C#)</span></span>
<span data-ttu-id="888a9-103">序列化 XML 樹狀結構表示從 XML 樹狀結構產生 XML。</span><span class="sxs-lookup"><span data-stu-id="888a9-103">Serializing an XML tree means generating XML from the XML tree.</span></span> <span data-ttu-id="888a9-104">您可以序列化到檔案、<xref:System.IO.TextWriter> 類別的具體實作，或 <xref:System.Xml.XmlWriter> 的具體實作。</span><span class="sxs-lookup"><span data-stu-id="888a9-104">You can serialize to a file, to a concrete implementation of the <xref:System.IO.TextWriter> class, or to a concrete implementation of an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="888a9-105">您可以控制各方面的序列化。</span><span class="sxs-lookup"><span data-stu-id="888a9-105">You can control various aspects of serialization.</span></span> <span data-ttu-id="888a9-106">例如，您可以控制是否要縮排序列化的 XML，以及是否要撰寫 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="888a9-106">For example, you can control whether to indent the serialized XML, and whether to write an XML declaration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="888a9-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="888a9-107">In This Section</span></span>  
  
|<span data-ttu-id="888a9-108">主題</span><span class="sxs-lookup"><span data-stu-id="888a9-108">Topic</span></span>|<span data-ttu-id="888a9-109">描述</span><span class="sxs-lookup"><span data-stu-id="888a9-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="888a9-110">序列化時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="888a9-110">Preserving White Space While Serializing</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)|<span data-ttu-id="888a9-111">描述序列化 XML 樹狀時，如何控制空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="888a9-111">Describes how to control white space behavior when you serialize XML trees.</span></span>|  
|[<span data-ttu-id="888a9-112">使用 XML 宣告序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="888a9-112">Serializing with an XML Declaration (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-with-an-xml-declaration.md)|<span data-ttu-id="888a9-113">描述如何序列化包含 XML 宣告的 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="888a9-113">Describes how to serialize an XML tree that includes an XML declaration.</span></span>|  
|[<span data-ttu-id="888a9-114">序列化至 File、TextWriter 和 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="888a9-114">Serializing to Files, TextWriters, and XmlWriters</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-files-textwriters-and-xmlwriters.md)|<span data-ttu-id="888a9-115">描述如何將文件序列化到 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="888a9-115">Describes how to serialize a document to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="888a9-116">序列化至 XmlReader (叫用 XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="888a9-116">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-to-an-xmlreader-invoking-xslt.md)|<span data-ttu-id="888a9-117">描述如何建立可讓其他模組讀取 XML 樹狀結構之內容的 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="888a9-117">Describes how to create a <xref:System.Xml.XmlReader> that enables another module to read the contents of an XML tree.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="888a9-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="888a9-118">See Also</span></span>  
 [<span data-ttu-id="888a9-119">程式設計手冊 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="888a9-119">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
