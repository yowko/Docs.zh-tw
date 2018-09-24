---
title: XslTransform 的 XmlDocument 輸入
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e83cf82aee57b1f40f695700d8d0b38c12e0ac39
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583442"
---
# <a name="xmldocument-input-to-xsltransform"></a>XslTransform 的 XmlDocument 輸入
<xref:System.Xml.XmlDocument> 類別會提供 XML 文件的編輯功能。 如果在傳送到 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法前必須先編輯或修改 XML，請將 XML 載入 <xref:System.Xml.XmlDocument> 並加以編輯，然後再將它傳送到 <xref:System.Xml.Xsl.XslTransform>。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。  
  
 <xref:System.Xml.XmlDocument> 可實作 <xref:System.Xml.XPath.IXPathNavigable> 介面，以便文件在編輯後可傳遞至 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法。  
  
 由於 <xref:System.Xml.XmlDocument> 的編輯功能之故，使用 <xref:System.Xml.XmlDocument> 類別做為轉換的輸入，會比使用可延伸樣式表語言轉換 (XSLT) 轉換的 <xref:System.Xml.XPath.XPathDocument> 來得慢，因為 <xref:System.Xml.XPath.XPathDocument> 已因內部儲存而針對 XML 路徑語言 (XPath) 查詢進行過最佳化。  
  
## <a name="example"></a>範例  
 下列程式碼範例顯示如何將 <xref:System.Xml.XmlDocument> 提供給 <xref:System.Xml.Xsl.XslTransform>，並將輸出傳送至 <xref:System.Xml.XmlReader>。  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>  
- [使用 XslTransform 類別進行 XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [XslTransform 類別實作 XSLT 處理器](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [轉換中的 XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [轉換中的 XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [XslTransform 的 XPathDocument 輸入](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [XslTransform 的 XmlDataDocument 輸入](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
