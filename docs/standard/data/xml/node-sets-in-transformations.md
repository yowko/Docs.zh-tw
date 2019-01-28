---
title: 轉換中的節點集
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23632a5df10c1ab2d1afa654d5438a4ebd903d5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603036"
---
# <a name="node-sets-in-transformations"></a><span data-ttu-id="c86fb-102">轉換中的節點集</span><span class="sxs-lookup"><span data-stu-id="c86fb-102">Node Sets in Transformations</span></span>
<span data-ttu-id="c86fb-103">節點集是 XML 路徑語言 (XPath) 運算式傳回的四種基本資料型別之一。</span><span class="sxs-lookup"><span data-stu-id="c86fb-103">Node sets are one of four basic data types that are returned from XML Path Language (XPath) expressions.</span></span> <span data-ttu-id="c86fb-104">節點集是一個沒有順序、不重複的節點集合，它依據文件的順序建立，可以指定給樣式表中的變數。</span><span class="sxs-lookup"><span data-stu-id="c86fb-104">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c86fb-105"><xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。</span><span class="sxs-lookup"><span data-stu-id="c86fb-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="c86fb-106">您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="c86fb-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c86fb-107">如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。</span><span class="sxs-lookup"><span data-stu-id="c86fb-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="c86fb-108">節點集是 XPath 運算式傳回的四種基本資料型別之一。</span><span class="sxs-lookup"><span data-stu-id="c86fb-108">Node sets are one of four basic data types that are returned from XPath expressions.</span></span> <span data-ttu-id="c86fb-109">節點集是一個沒有順序、不重複的節點集合，它依據文件的順序建立，可以指定給樣式表中的變數。</span><span class="sxs-lookup"><span data-stu-id="c86fb-109">A node set, which is an unordered collection of nodes without duplicates, created in document order, can be assigned to a variable in a style sheet.</span></span> <span data-ttu-id="c86fb-110">這個節點集是轉換中 `select` 屬性所使用之 XPath 運算式的結果，具有與 XML 文件物件模型 (DOM) 的節點集相同的行為。</span><span class="sxs-lookup"><span data-stu-id="c86fb-110">This node set, which is a result of an XPath expression used in a `select` attribute in a transformation, has the same behavior as a node set from the XML Document Object Model (DOM).</span></span> <span data-ttu-id="c86fb-111">您可以使用[使用 XPathNavigator 巡覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)中所顯示的一組方法來巡覽節點集，而不需像 result tree fragment 一樣使用 <xref:System.Xml.XPath.XPathNodeIterator> 進行巡覽。</span><span class="sxs-lookup"><span data-stu-id="c86fb-111">You can navigate a node set using a set of methods shown in [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), unlike a result tree fragment or result tree fragment, which uses the <xref:System.Xml.XPath.XPathNodeIterator> for navigation.</span></span>  
  
 <span data-ttu-id="c86fb-112">下列程式碼範例說明，當樣式表中的 `variable` 或 `parameter` 項目評估為節點集時，應該如何反覆查看節點集。</span><span class="sxs-lookup"><span data-stu-id="c86fb-112">The following code sample shows how to iterate over a node set when a `variable` or `parameter` element in a style sheet evaluates to a node set.</span></span>  
  
## <a name="style-sheet"></a><span data-ttu-id="c86fb-113">樣式表</span><span class="sxs-lookup"><span data-stu-id="c86fb-113">Style Sheet</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a><span data-ttu-id="c86fb-114">輸入</span><span class="sxs-lookup"><span data-stu-id="c86fb-114">Input</span></span>  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a><span data-ttu-id="c86fb-115">輸出</span><span class="sxs-lookup"><span data-stu-id="c86fb-115">Output</span></span>  
  
```  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a><span data-ttu-id="c86fb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c86fb-116">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="c86fb-117">使用 XslTransform 類別進行 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="c86fb-117">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="c86fb-118">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="c86fb-118">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
