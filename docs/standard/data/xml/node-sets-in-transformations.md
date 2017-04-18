---
title: "轉換中的節點集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# 轉換中的節點集
節點集是 XML 路徑語言 \(XPath\) 運算式傳回的四種基本資料型別之一。 節點集是一個沒有順序、不重複的節點集合，它依據文件的順序建立，可以指定給樣式表中的變數。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 \(XSLT\)。 如需詳細資訊，請參閱 [使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) 和 [從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。  
  
 節點集是 XPath 運算式傳回的四種基本資料型別之一。 節點集是一個沒有順序、不重複的節點集合，它依據文件的順序建立，可以指定給樣式表中的變數。 這個節點集是轉換中 `select` 屬性所使用之 XPath 運算式的結果，具有與 XML 文件物件模型 \(DOM\) 的節點集相同的行為。 您可以使用[使用 XPathNavigator 巡覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)中所顯示的一組方法來導覽節點集，而不需像 result tree fragment 一樣使用 <xref:System.Xml.XPath.XPathNodeIterator> 進行導覽。  
  
 下列程式碼範例說明，當樣式表中的 `variable` 或 `parameter` 項目評估為節點集時，應該如何反覆查看節點集。  
  
## 樣式表  
  
```  
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
  
## 輸入  
  
```  
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
  
## 輸出  
  
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
  
## 請參閱  
 <xref:System.Xml.XPath.XPathNodeIterator>   
 [使用 XslTransform 類別進行 XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)   
 [XslTransform 類別實作 XSLT 處理器](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)