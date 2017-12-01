---
title: "XslCompiledTransform 類別的輸入"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 97d636583393ab856a9c17af4c974c53fbde5767
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>XslCompiledTransform 類別的輸入
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法可接受來源文件的三種輸入型別：實作 <xref:System.Xml.XPath.IXPathNavigable> 介面的物件、讀取來源文件的 <xref:System.Xml.XmlReader> 物件，或是字串 URI。  
  
> [!NOTE]
>  依預設，<xref:System.Xml.Xsl.XslCompiledTransform> 類別會保留泛空白字元。 這符合 W3C XSLT 1.0 版建議事項的 3.4 節 (3.4 節，http://www.w3.org/TR/xslt.html#strip)。  
  
## <a name="ixpathnavigable-interface"></a>IXPathNavigable 介面  
 <xref:System.Xml.XPath.IXPathNavigable> 介面是在 <xref:System.Xml.XmlNode> 及 <xref:System.Xml.XPath.XPathDocument> 類別中實作的。 這些類別代表 XML 資料的記憶體中快取。  
  
-   <xref:System.Xml.XmlNode> 類別是以 W3C 文件物件模型 (DOM) 為基礎，並包含編輯功能。  
  
-   <xref:System.Xml.XPath.XPathDocument> 類別是以 XPath 資料模型為基礎的唯讀資料存放區。 <xref:System.Xml.XPath.XPathDocument> 是建議用於 XSLT 處理的類別。 與 <xref:System.Xml.XmlNode> 類別相比，它可提供更高的效能。  
  
> [!NOTE]
>  轉換是指套用到整個文件。 換言之，如果您要傳入的節點不是文件的根節點，則不會阻止轉換程序取得已載入文件中的所有節點。 若要轉換節點片段，您必須建立只包含節點片段的物件，並將該物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。 如需詳細資訊，請參閱[How to： 轉換節點片段](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)。  
  
 下列範例使用 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> 方法，透過 transform.xsl 樣式表將 books.xml 檔案轉換為 books.html 檔案。 本主題中可以找到 books.xml 和 transform.xsl 檔案： [How to： 使用組件執行 XSLT 轉換](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)。  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>XmlReader 物件  
 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法會從 <xref:System.Xml.XmlReader> 的目前節點載入，並套用至其所有子系節點。 如此您就能夠利用文件中的某些部份做為內容文件。 傳回 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法後，<xref:System.Xml.XmlReader> 便定位於內容文件結尾之後的下一節點。 如果到達文件結尾，則 <xref:System.Xml.XmlReader> 會定位於檔案結尾 (EOF)。  
  
 下列範例使用 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> 方法，透過 transform.xsl 樣式表將 books.xml 檔案轉換為 books.html 檔案。 本主題中可以找到 books.xml 和 transform.xsl 檔案： [How to： 使用組件執行 XSLT 轉換](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)。  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>字串 URI  
 您也可以將來源文件 URI 指定為 XSLT 輸入。 <xref:System.Xml.XmlResolver> 可用於解析 URI。 您可以藉由將要使用的 <xref:System.Xml.XmlResolver> 傳遞給 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法，來對其進行指定。 若未指定 <xref:System.Xml.XmlResolver>，則 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法會使用不含認證的預設 <xref:System.Xml.XmlUrlResolver>。  
  
 下列範例使用 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> 方法，透過 transform.xsl 樣式表將 books.xml 檔案轉換為 books.html 檔案。 本主題中可以找到 books.xml 和 transform.xsl 檔案： [How to： 使用組件執行 XSLT 轉換](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)。  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 如需詳細資訊，請參閱[解析外部資源在 XSLT 處理](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)
