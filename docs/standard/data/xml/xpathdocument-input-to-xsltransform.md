---
title: "XslTransform 的 XPathDocument 輸入"
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
ms.assetid: 7d1bbe8b-ed43-4e62-a5ba-d602d244f4ae
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 80708dfa60636bbb038c3a86e336709339d2ac55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xpathdocument-input-to-xsltransform"></a><span data-ttu-id="ac6f4-102">XslTransform 的 XPathDocument 輸入</span><span class="sxs-lookup"><span data-stu-id="ac6f4-102">XPathDocument Input to XslTransform</span></span>
<span data-ttu-id="ac6f4-103"><xref:System.Xml.XPath.XPathDocument> 是一種唯讀快取，可運用在透過 <xref:System.Xml.Xsl.XslTransform> 處理文件的作業中。</span><span class="sxs-lookup"><span data-stu-id="ac6f4-103">The <xref:System.Xml.XPath.XPathDocument> is a read-only cache, for processing documents with <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="ac6f4-104">它的結構與 XML 文件物件模型 (DOM) 類似，但它已透過 <xref:System.Xml.XPath.XPathNavigator> 上的 XPath 最佳化函式而獲得高度最佳化，可運用在可擴充樣式表語言轉換 (XSLT) 處理和 XML 路徑語言 (XPath) 資料模型上。</span><span class="sxs-lookup"><span data-stu-id="ac6f4-104">It is structurally similar to the XML Document Object Model (DOM), but it is highly optimized for Extensible Stylesheet Language for Transformations (XSLT) processing and the XML Path Language (XPath) data model using the XPath optimization functions on the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac6f4-105"><xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。</span><span class="sxs-lookup"><span data-stu-id="ac6f4-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="ac6f4-106">您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="ac6f4-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="ac6f4-107">請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[移轉從 XslTransform 類別](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ac6f4-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="ac6f4-108">下列程式碼範例會建立 <xref:System.Xml.XPath.XPathDocument> 做為轉換的輸入。</span><span class="sxs-lookup"><span data-stu-id="ac6f4-108">The following code sample creates an <xref:System.Xml.XPath.XPathDocument> as input to a transform.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac6f4-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac6f4-109">See Also</span></span>  
 [<span data-ttu-id="ac6f4-110">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="ac6f4-110">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
