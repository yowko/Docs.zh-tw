---
title: "載入或剖析 XML2 時保留空白字元 |Microsoft 文件"
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
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
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
ms.openlocfilehash: a2872c1e2354c0a0bd106f7fb945542ce37e7774
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a><span data-ttu-id="48b24-102">載入或剖析 XML 時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="48b24-102">Preserving White Space while Loading or Parsing XML</span></span>
<span data-ttu-id="48b24-103">這個主題描述如何控制 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="48b24-103">This topic describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="48b24-104">常見的案例為讀取縮排的 XML、建立沒有任何空白字元文字節點 (也就是不保留空白字元) 的記憶體中 XML 樹狀結構、在 XML 上執行某些作業，然後儲存包含縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="48b24-104">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="48b24-105">當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="48b24-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="48b24-106">這是 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="48b24-106">This is the default behavior for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="48b24-107">其他常見案例為讀取與修改已經過刻意縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="48b24-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="48b24-108">您可能不想用任何方式變更這個縮排。</span><span class="sxs-lookup"><span data-stu-id="48b24-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="48b24-109">在 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 中，如果您在載入或剖析 XML 時保留空白字元，並在序列化 XML 時停用格式化，就可以達到這個效果。</span><span class="sxs-lookup"><span data-stu-id="48b24-109">To do this in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
 <span data-ttu-id="48b24-110">這個主題描述填入 XML 樹狀之方法的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="48b24-110">This topic describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="48b24-111">序列化 XML 樹狀結構時控制空白字元的相關資訊，請參閱[保留泛空白字元時序列化](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)。</span><span class="sxs-lookup"><span data-stu-id="48b24-111">For information about controlling white space when you serialize XML trees, see [Preserving White Space While Serializing](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="48b24-112">填入 XML 樹狀之方法的行為</span><span class="sxs-lookup"><span data-stu-id="48b24-112">Behavior of Methods that Populate XML Trees</span></span>  
 <span data-ttu-id="48b24-113">下列方法<xref:System.Xml.Linq.XElement>和<xref:System.Xml.Linq.XDocument>類別會填入 XML 樹狀結構。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="48b24-113">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="48b24-114">您可以填入 XML 樹狀結構從檔案、 <xref:System.IO.TextReader>、 <xref:System.Xml.XmlReader>，或字串︰</xref:System.Xml.XmlReader> </xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="48b24-114">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>  
  
-   <span data-ttu-id="48b24-115"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="48b24-115"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="48b24-116"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="48b24-116"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="48b24-117"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="48b24-117"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="48b24-118"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="48b24-118"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="48b24-119">如果此方法不採用<xref:System.Xml.Linq.LoadOptions>做為引數，此方法將不會保留不顯著泛空白字元。</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="48b24-119">If the method does not take <xref:System.Xml.Linq.LoadOptions> as an argument, the method will not preserve insignificant white space.</span></span>  
  
 <span data-ttu-id="48b24-120">在大部分情況下，如果此方法採用<xref:System.Xml.Linq.LoadOptions>做為引數，您可以選擇性地保留有效空白字元當做 XML 樹狀結構中的文字節點。</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="48b24-120">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="48b24-121">不過，如果此方法來從 XML 載入<xref:System.Xml.XmlReader>，然後在<xref:System.Xml.XmlReader>決定是否將會保留泛空白字元。</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="48b24-121">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="48b24-122">設定<xref:System.Xml.Linq.LoadOptions>會有任何作用。</xref:System.Xml.Linq.LoadOptions></span><span class="sxs-lookup"><span data-stu-id="48b24-122">Setting <xref:System.Xml.Linq.LoadOptions> will have no effect.</span></span>  
  
 <span data-ttu-id="48b24-123">利用這些方法，會保留泛空白字元，如果不顯著泛空白字元插入到 XML 樹狀結構當做<xref:System.Xml.Linq.XText>節點。</xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="48b24-123">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="48b24-124">如果不保留空白字元，則不會插入文字節點。</span><span class="sxs-lookup"><span data-stu-id="48b24-124">If white space is not preserved, text nodes are not inserted.</span></span>  
  
 <span data-ttu-id="48b24-125">您可以使用<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="48b24-125">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="48b24-126">節點寫入<xref:System.Xml.XmlWriter>樹狀目錄中會填入。</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="48b24-126">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="48b24-127">不過，當您使用這個方法建置 XML 樹狀時，不管節點是否為空白字元，也不管空白字元是否有效，都會保留所有節點。</span><span class="sxs-lookup"><span data-stu-id="48b24-127">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b24-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48b24-128">See Also</span></span>  
 [<span data-ttu-id="48b24-129">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48b24-129">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
