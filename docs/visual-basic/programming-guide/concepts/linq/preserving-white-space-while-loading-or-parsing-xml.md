---
title: "載入或剖析 XML2 時保留空白字元"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d99cea37bb9817c40a6d3876b72ccdbd84d7e7ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="4fce1-102">載入或剖析 XML 時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="4fce1-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="4fce1-103">這個主題描述如何控制 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="4fce1-103">This topic describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="4fce1-104">常見的案例為讀取縮排的 XML、建立沒有任何空白字元文字節點 (也就是不保留空白字元) 的記憶體中 XML 樹狀結構、在 XML 上執行某些作業，然後儲存包含縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="4fce1-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="4fce1-105">當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="4fce1-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="4fce1-106">這是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="4fce1-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="4fce1-107">其他常見案例為讀取與修改已經過刻意縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="4fce1-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="4fce1-108">您可能不想用任何方式變更這個縮排。</span><span class="sxs-lookup"><span data-stu-id="4fce1-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="4fce1-109">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，如果您在載入或剖析 XML 時保留空白字元，並在序列化 XML 時停用格式化，就可以達到這個效果。</span><span class="sxs-lookup"><span data-stu-id="4fce1-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="4fce1-110">這個主題描述填入 XML 樹狀之方法的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="4fce1-110">This topic describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="4fce1-111">如需序列化 XML 樹狀結構時控制空白字元的資訊，請參閱[序列化時保留空白字元](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)。</span><span class="sxs-lookup"><span data-stu-id="4fce1-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="4fce1-112">填入 XML 樹狀之方法的行為</span><span class="sxs-lookup"><span data-stu-id="4fce1-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="4fce1-113">下列 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 類別中的方法會填入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4fce1-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="4fce1-114">您可以從檔案、<xref:System.IO.TextReader>、<xref:System.Xml.XmlReader> 或字串填入 XML 樹狀結構：</span><span class="sxs-lookup"><span data-stu-id="4fce1-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="4fce1-115">如果此方法不採用 <xref:System.Xml.Linq.LoadOptions> 當做引數，該方法將不會保留有效的空白字元。</span><span class="sxs-lookup"><span data-stu-id="4fce1-115">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="4fce1-116">在大部分的情況下，如果此方法採用 <xref:System.Xml.Linq.LoadOptions> 當做引數，您可以選擇性地保留有效空白字元當做 XML 樹狀結構中的文字節點。</span><span class="sxs-lookup"><span data-stu-id="4fce1-116">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="4fce1-117">不過，如果此方法是從 <xref:System.Xml.XmlReader> 載入 XML，<xref:System.Xml.XmlReader> 會決定是否要保留空白字元。</span><span class="sxs-lookup"><span data-stu-id="4fce1-117">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="4fce1-118">設定 <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> 不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="4fce1-118">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>  
  
 <span data-ttu-id="4fce1-119">利用這些方法，如果保留空白字元，會將有效的空白字元插入到 XML 樹狀結構中，當做 <xref:System.Xml.Linq.XText> 節點。</span><span class="sxs-lookup"><span data-stu-id="4fce1-119">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="4fce1-120">如果不保留空白字元，則不會插入文字節點。</span><span class="sxs-lookup"><span data-stu-id="4fce1-120">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="4fce1-121">您可以使用 <xref:System.Xml.XmlWriter> 來建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4fce1-121">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="4fce1-122">寫入到 <xref:System.Xml.XmlWriter> 中的節點會填入樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="4fce1-122">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="4fce1-123">不過，當您使用這個方法建置 XML 樹狀時，不管節點是否為空白字元，也不管空白字元是否有效，都會保留所有節點。</span><span class="sxs-lookup"><span data-stu-id="4fce1-123">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fce1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fce1-124">See Also</span></span>  
 [<span data-ttu-id="4fce1-125">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fce1-125">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
