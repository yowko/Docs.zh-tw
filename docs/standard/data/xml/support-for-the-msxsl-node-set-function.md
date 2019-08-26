---
title: msxsl:node-set() 函式的支援
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3670803ff20351fd9ff6892a0cef48b9caa70199
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939528"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="f83e4-102">msxsl:node-set() 函式的支援</span><span class="sxs-lookup"><span data-stu-id="f83e4-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="f83e4-103">`msxsl:node-set` 函式讓您可以將 result tree fragment 轉換為節點集。</span><span class="sxs-lookup"><span data-stu-id="f83e4-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="f83e4-104">產生的節點集永遠包含單一節點，且為樹狀結構的根節點。</span><span class="sxs-lookup"><span data-stu-id="f83e4-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f83e4-105">在 .NET Framework 2.0 中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。</span><span class="sxs-lookup"><span data-stu-id="f83e4-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="f83e4-106">您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="f83e4-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f83e4-107">如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。</span><span class="sxs-lookup"><span data-stu-id="f83e4-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="f83e4-108">`msxsl:node-set` 函式讓您可以將 result tree fragment 轉換為節點集。</span><span class="sxs-lookup"><span data-stu-id="f83e4-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="f83e4-109">產生的節點集永遠包含單一節點，且為樹狀結構的根節點。</span><span class="sxs-lookup"><span data-stu-id="f83e4-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f83e4-110">範例</span><span class="sxs-lookup"><span data-stu-id="f83e4-110">Example</span></span>  
 <span data-ttu-id="f83e4-111">下列範例中，`$var` 是樣式表內節點樹狀結構的變數。</span><span class="sxs-lookup"><span data-stu-id="f83e4-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="f83e4-112">for-each 陳述式和 `node-set` 函式結合，可讓使用者將這個節點樹狀結構當做節點集反覆查看。</span><span class="sxs-lookup"><span data-stu-id="f83e4-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="f83e4-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="f83e4-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="f83e4-114">Output</span><span class="sxs-lookup"><span data-stu-id="f83e4-114">Output</span></span>  
 <span data-ttu-id="f83e4-115">轉換的輸出為</span><span class="sxs-lookup"><span data-stu-id="f83e4-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f83e4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f83e4-116">See also</span></span>

- [<span data-ttu-id="f83e4-117">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="f83e4-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
