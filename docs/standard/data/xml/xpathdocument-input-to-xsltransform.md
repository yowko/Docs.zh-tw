---
title: XslTransform 的 XPathDocument 輸入
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
ms.openlocfilehash: 66cdbae8b52ca1b7ed46e8f040fcbf51c969dea2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282970"
---
# <a name="xpathdocument-input-to-xsltransform"></a>XslTransform 的 XPathDocument 輸入
<xref:System.Xml.XPath.XPathDocument> 是一種唯讀快取，可運用在透過 <xref:System.Xml.Xsl.XslTransform> 處理文件的作業中。 它的結構與 XML 文件物件模型 (DOM) 類似，但它已透過 <xref:System.Xml.XPath.XPathNavigator> 上的 XPath 最佳化函式而獲得高度最佳化，可運用在可擴充樣式表語言轉換 (XSLT) 處理和 XML 路徑語言 (XPath) 資料模型上。  
  
> [!NOTE]
> 在 .NET Framework 2.0 中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](migrating-from-the-xsltransform-class.md)。  
  
 下列程式碼範例會建立 <xref:System.Xml.XPath.XPathDocument> 做為轉換的輸入。  
  
```vb  
Dim xslt as XslTransform = new XslTransform()  
Xslt.Load(someStylesheet)  
Dim doc as XPathDocument = New XPathDocument("books.xml")  
Dim fs as StringWriter = new StringWriter()  
Xslt.Transform(doc, Nothing, fs, Nothing);  
```  
  
```csharp  
XslTransform xslt = new XslTransform();  
Xslt.Load(someStylesheet);  
XPathDocument doc = XPathDocument("books.xml");  
StringWriter fs = new StringWriter();  
Xslt.Transform(doc, null, fs, null);  
```  
  
## <a name="see-also"></a>另請參閱

- [XslTransform 類別實作 XSLT 處理器](xsltransform-class-implements-the-xslt-processor.md)
