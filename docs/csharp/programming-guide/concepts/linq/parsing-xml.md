---
title: 剖析 XML (C#)
ms.date: 07/20/2015
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
ms.openlocfilehash: 876cfdf7bd5a82aba75d456d6d5cda57e080fdf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="parsing-xml-c"></a><span data-ttu-id="4d80f-102">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4d80f-102">Parsing XML (C#)</span></span>
<span data-ttu-id="4d80f-103">本節中的主題描述如何剖析 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="4d80f-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d80f-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="4d80f-104">In This Section</span></span>  
  
|<span data-ttu-id="4d80f-105">主題</span><span class="sxs-lookup"><span data-stu-id="4d80f-105">Topic</span></span>|<span data-ttu-id="4d80f-106">描述</span><span class="sxs-lookup"><span data-stu-id="4d80f-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4d80f-107">如何：剖析字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="4d80f-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="4d80f-108">顯示如何剖析字串以建立 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="4d80f-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="4d80f-109">如何：從檔案載入 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4d80f-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="4d80f-110">顯示如何使用 <xref:System.Xml.Linq.XElement.Load%2A> 方法，從 URI 載入 XML。</span><span class="sxs-lookup"><span data-stu-id="4d80f-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="4d80f-111">載入或剖析 XML 時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="4d80f-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="4d80f-112">描述如何在載入 XML 樹狀結構時，控制 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="4d80f-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="4d80f-113">如何：攔截剖析錯誤 (C#)</span><span class="sxs-lookup"><span data-stu-id="4d80f-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="4d80f-114">顯示如何偵測格式錯誤或無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="4d80f-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="4d80f-115">如何：從 XmlReader 建立樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="4d80f-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="4d80f-116">顯示如何從 <xref:System.Xml.XmlReader> 直接建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4d80f-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="4d80f-117">如何：從 XmlReader 串流 XML 片段 (C#)</span><span class="sxs-lookup"><span data-stu-id="4d80f-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="4d80f-118">顯示如何使用 <xref:System.Xml.XmlReader> 串流 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="4d80f-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="4d80f-119">當您必須處理非常大的 XML 檔案時，可能無法將整個 XML 樹狀結構載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="4d80f-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="4d80f-120">但是，您可以串流 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="4d80f-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d80f-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d80f-121">See Also</span></span>  
 [<span data-ttu-id="4d80f-122">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="4d80f-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
