---
title: XslCompiledTransform 類別的輸入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
ms.openlocfilehash: af529f1c6ccfe3abe761c7707772d6f9697c179d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733421"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a><span data-ttu-id="e0ed3-102">XslCompiledTransform 類別的輸入</span><span class="sxs-lookup"><span data-stu-id="e0ed3-102">Inputs to the XslCompiledTransform Class</span></span>

<span data-ttu-id="e0ed3-103"><xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法可接受來源文件的三種輸入型別：實作 <xref:System.Xml.XPath.IXPathNavigable> 介面的物件、讀取來源文件的 <xref:System.Xml.XmlReader> 物件，或是字串 URI。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-103">The <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method accepts three input types for the source document: an object that implements the <xref:System.Xml.XPath.IXPathNavigable> interface, an <xref:System.Xml.XmlReader> object that reads the source document, or a string URI.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0ed3-104">依預設，<xref:System.Xml.Xsl.XslCompiledTransform> 類別會保留泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class preserves white space by default.</span></span> <span data-ttu-id="e0ed3-105">這符合 [W3C XSLT 1.0 版建議事項的 3.4 節](https://www.w3.org/TR/xslt.html#strip) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-105">This is in accordance with [section 3.4 of the W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt.html#strip).</span></span>  
  
## <a name="ixpathnavigable-interface"></a><span data-ttu-id="e0ed3-106">IXPathNavigable 介面</span><span class="sxs-lookup"><span data-stu-id="e0ed3-106">IXPathNavigable Interface</span></span>  

 <span data-ttu-id="e0ed3-107"><xref:System.Xml.XPath.IXPathNavigable> 介面是在 <xref:System.Xml.XmlNode> 及 <xref:System.Xml.XPath.XPathDocument> 類別中實作的。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-107">The <xref:System.Xml.XPath.IXPathNavigable> interface is implemented in the <xref:System.Xml.XmlNode> and <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="e0ed3-108">這些類別代表 XML 資料的記憶體中快取。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-108">These classes represent an in-memory cache of XML data.</span></span>  
  
- <span data-ttu-id="e0ed3-109"><xref:System.Xml.XmlNode> 類別是以 W3C 文件物件模型 (DOM) 為基礎，並包含編輯功能。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-109">The <xref:System.Xml.XmlNode> class is based on the W3C Document Object Model (DOM) and includes editing capabilities.</span></span>  
  
- <span data-ttu-id="e0ed3-110"><xref:System.Xml.XPath.XPathDocument> 類別是以 XPath 資料模型為基礎的唯讀資料存放區。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-110">The <xref:System.Xml.XPath.XPathDocument> class is a read-only data store based on the XPath data model.</span></span> <span data-ttu-id="e0ed3-111"><xref:System.Xml.XPath.XPathDocument> 是建議用於 XSLT 處理的類別。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-111"><xref:System.Xml.XPath.XPathDocument> is the recommended class for XSLT processing.</span></span> <span data-ttu-id="e0ed3-112">與 <xref:System.Xml.XmlNode> 類別相比，它可提供更高的效能。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-112">It provides faster performance when compared to the <xref:System.Xml.XmlNode> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0ed3-113">轉換是指套用到整個文件。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-113">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="e0ed3-114">換言之，如果您要傳入的節點不是文件的根節點，則不會阻止轉換程序取得已載入文件中的所有節點。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-114">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="e0ed3-115">若要轉換節點片段，您必須建立只包含節點片段的物件，並將該物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-115">To transform a node fragment, you must create an object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="e0ed3-116">如需詳細資訊，請參閱[如何：轉換節點片段](how-to-transform-a-node-fragment.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-116">For more information, see [How to: Transform a Node Fragment](how-to-transform-a-node-fragment.md).</span></span>  
  
 <span data-ttu-id="e0ed3-117">下列範例使用 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> 方法，透過 transform.xsl 樣式表將 books.xml 檔案轉換為 books.html 檔案。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-117">The following example uses the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> method to transform the books.xml file to the books.html file using the transform.xsl style sheet.</span></span> <span data-ttu-id="e0ed3-118">本主題中可找到 books.xml 和 transform.xsl 檔案：[如何：使用組件執行 XSLT 轉換](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-118">The books.xml and transform.xsl files can be found in this topic: [How to: Perform an XSLT Transformation by Using an Assembly](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).</span></span>  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a><span data-ttu-id="e0ed3-119">XmlReader 物件</span><span class="sxs-lookup"><span data-stu-id="e0ed3-119">XmlReader Object</span></span>  

 <span data-ttu-id="e0ed3-120"><xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法會從 <xref:System.Xml.XmlReader> 的目前節點載入，並套用至其所有子系節點。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-120">The <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method loads from the current node of the <xref:System.Xml.XmlReader> through all its children.</span></span> <span data-ttu-id="e0ed3-121">如此您就能夠利用文件中的某些部份做為內容文件。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-121">This enables you to use a portion of a document as the context document.</span></span> <span data-ttu-id="e0ed3-122">傳回 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法後，<xref:System.Xml.XmlReader> 便定位於內容文件結尾之後的下一節點。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-122">After the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method returns, the <xref:System.Xml.XmlReader> is positioned on the next node after the end of the context document.</span></span> <span data-ttu-id="e0ed3-123">如果到達文件結尾，則 <xref:System.Xml.XmlReader> 會定位於檔案結尾 (EOF)。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-123">If the end of the document is reached, the <xref:System.Xml.XmlReader> is positioned at the end of file (EOF).</span></span>  
  
 <span data-ttu-id="e0ed3-124">下列範例使用 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> 方法，透過 transform.xsl 樣式表將 books.xml 檔案轉換為 books.html 檔案。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-124">The following example uses the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> method to transform the books.xml file to the books.html file using the transform.xsl style sheet.</span></span> <span data-ttu-id="e0ed3-125">本主題中可找到 books.xml 和 transform.xsl 檔案：[如何：使用組件執行 XSLT 轉換](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-125">The books.xml and transform.xsl files can be found in this topic: [How to: Perform an XSLT Transformation by Using an Assembly](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).</span></span>  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a><span data-ttu-id="e0ed3-126">字串 URI</span><span class="sxs-lookup"><span data-stu-id="e0ed3-126">String URI</span></span>  

 <span data-ttu-id="e0ed3-127">您也可以將來源文件 URI 指定為 XSLT 輸入。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-127">You can also specify the source document URI as your XSLT input.</span></span> <span data-ttu-id="e0ed3-128"><xref:System.Xml.XmlResolver> 可用於解析 URI。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-128">An <xref:System.Xml.XmlResolver> is used to resolve the URI.</span></span> <span data-ttu-id="e0ed3-129">您可以藉由將要使用的 <xref:System.Xml.XmlResolver> 傳遞給 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法，來對其進行指定。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-129">You can specify the <xref:System.Xml.XmlResolver> to use by passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="e0ed3-130">若未指定 <xref:System.Xml.XmlResolver>，則 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法會使用不含認證的預設 <xref:System.Xml.XmlUrlResolver>。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-130">If an <xref:System.Xml.XmlResolver> is not specified, the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method uses a default <xref:System.Xml.XmlUrlResolver> with no credentials.</span></span>  
  
 <span data-ttu-id="e0ed3-131">下列範例使用 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> 方法，透過 transform.xsl 樣式表將 books.xml 檔案轉換為 books.html 檔案。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-131">The following example uses the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> method to transform the books.xml file to the books.html file using the transform.xsl style sheet.</span></span> <span data-ttu-id="e0ed3-132">本主題中可找到 books.xml 和 transform.xsl 檔案：[如何：使用組件執行 XSLT 轉換](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-132">The books.xml and transform.xsl files can be found in this topic: [How to: Perform an XSLT Transformation by Using an Assembly](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).</span></span>  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 <span data-ttu-id="e0ed3-133">如需詳細資訊，請參閱 [XSLT 處理期間解析外部資源](resolving-external-resources-during-xslt-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="e0ed3-133">For more information, see [Resolving External Resources During XSLT Processing](resolving-external-resources-during-xslt-processing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ed3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0ed3-134">See also</span></span>

- [<span data-ttu-id="e0ed3-135">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="e0ed3-135">XSLT Transformations</span></span>](xslt-transformations.md)
