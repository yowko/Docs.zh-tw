---
title: 剖析 XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
ms.openlocfilehash: ec9df29c239d2780b4fc13bb101a22c54eb43da5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832748"
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="0a9da-102">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a9da-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="0a9da-103">本節中的主題描述如何剖析 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="0a9da-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a9da-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="0a9da-104">In This Section</span></span>  
  
|<span data-ttu-id="0a9da-105">主題</span><span class="sxs-lookup"><span data-stu-id="0a9da-105">Topic</span></span>|<span data-ttu-id="0a9da-106">描述</span><span class="sxs-lookup"><span data-stu-id="0a9da-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0a9da-107">如何：剖析字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a9da-107">How to: Parse a String (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="0a9da-108">顯示如何剖析字串以建立 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="0a9da-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="0a9da-109">如何：載入 XML 檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a9da-109">How to: Load XML from a File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="0a9da-110">顯示如何使用 <xref:System.Xml.Linq.XElement.Load%2A> 方法，從 URI 載入 XML。</span><span class="sxs-lookup"><span data-stu-id="0a9da-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="0a9da-111">載入或剖析 XML 時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="0a9da-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="0a9da-112">描述如何在載入 XML 樹狀結構時，控制 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="0a9da-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="0a9da-113">如何：攔截剖析錯誤 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a9da-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="0a9da-114">顯示如何偵測格式錯誤或無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="0a9da-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="0a9da-115">如何：建立樹狀結構從 XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a9da-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="0a9da-116">顯示如何從 <xref:System.Xml.XmlReader> 直接建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="0a9da-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="0a9da-117">如何：Stream XML 片段，從 XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a9da-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="0a9da-118">顯示如何使用 <xref:System.Xml.XmlReader> 串流 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="0a9da-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="0a9da-119">當您必須處理非常大的 XML 檔案時，可能無法將整個 XML 樹狀結構載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="0a9da-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="0a9da-120">但是，您可以串流 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="0a9da-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a9da-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a9da-121">See also</span></span>

- [<span data-ttu-id="0a9da-122">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a9da-122">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
