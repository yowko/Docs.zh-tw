---
title: msxsl:node-set() 函式的支援
ms.date: 03/30/2017
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 6c84e3789916e8d842e51e8417cb27505cb5cba6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673393"
---
# <a name="support-for-the-msxslnode-set-function"></a>msxsl:node-set() 函式的支援

`msxsl:node-set` 函式讓您可以將 result tree fragment 轉換為節點集。 產生的節點集永遠包含單一節點，且為樹狀結構的根節點。  
  
> [!NOTE]
> 在 .NET Framework 2.0 中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](migrating-from-the-xsltransform-class.md)。  
  
 `msxsl:node-set` 函式讓您可以將 result tree fragment 轉換為節點集。 產生的節點集永遠包含單一節點，且為樹狀結構的根節點。  
  
## <a name="example"></a>範例  

 下列範例中，`$books` 是樣式表內節點樹狀結構的變數。 for-each 陳述式和 `node-set` 函式結合，可讓使用者將這個節點樹狀結構當做節點集反覆查看。  
  
## <a name="nodesetxsl"></a>nodeset.xsl  
  
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
  
## <a name="output"></a>輸出  

 轉換的輸出為  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a>另請參閱

- [XslTransform 類別實作 XSLT 處理器](xsltransform-class-implements-the-xslt-processor.md)
