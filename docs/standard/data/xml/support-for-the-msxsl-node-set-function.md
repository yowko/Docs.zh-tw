---
title: msxsl:node-set() 函式的支援
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3eb24d76ffb07b36b837056ffa5cde0cbd37f5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570523"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="2a333-102">msxsl:node-set() 函式的支援</span><span class="sxs-lookup"><span data-stu-id="2a333-102">Support for the msxsl:node-set() Function</span></span>
<span data-ttu-id="2a333-103">`msxsl:node-set` 函式讓您可以將 result tree fragment 轉換為節點集。</span><span class="sxs-lookup"><span data-stu-id="2a333-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="2a333-104">產生的節點集永遠包含單一節點，且為樹狀結構的根節點。</span><span class="sxs-lookup"><span data-stu-id="2a333-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a333-105"><xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。</span><span class="sxs-lookup"><span data-stu-id="2a333-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="2a333-106">您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="2a333-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="2a333-107">如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。</span><span class="sxs-lookup"><span data-stu-id="2a333-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="2a333-108">`msxsl:node-set` 函式讓您可以將 result tree fragment 轉換為節點集。</span><span class="sxs-lookup"><span data-stu-id="2a333-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="2a333-109">產生的節點集永遠包含單一節點，且為樹狀的根節點。</span><span class="sxs-lookup"><span data-stu-id="2a333-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a333-110">範例</span><span class="sxs-lookup"><span data-stu-id="2a333-110">Example</span></span>  
 <span data-ttu-id="2a333-111">下列範例中，`$var` 是樣式表內節點樹狀結構的變數。</span><span class="sxs-lookup"><span data-stu-id="2a333-111">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="2a333-112">for-each 陳述式和 `node-set` 函式結合，可讓使用者將這個節點樹狀結構當做節點集反覆查看。</span><span class="sxs-lookup"><span data-stu-id="2a333-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="2a333-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="2a333-113">nodeset.xsl</span></span>  
  
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
                <author><xsl:value-of select="@author"/)</author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="2a333-114">輸出</span><span class="sxs-lookup"><span data-stu-id="2a333-114">Output</span></span>  
 <span data-ttu-id="2a333-115">轉換的輸出為</span><span class="sxs-lookup"><span data-stu-id="2a333-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a333-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a333-116">See Also</span></span>  
 [<span data-ttu-id="2a333-117">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="2a333-117">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
