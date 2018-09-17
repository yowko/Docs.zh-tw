---
title: XslTransform 類別實作 XSLT 處理器
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81d0ce4f697935908b8ad7084560bd1adacbdf2d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45653105"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>XslTransform 類別實作 XSLT 處理器
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。  
  
 <xref:System.Xml.Xsl.XslTransform> 類別是可實作 XSL 轉換 (XSLT) 1.0 版建議事項的 XSLT 處理器。 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法可尋找及讀取樣式表，而 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法則可轉換指定的來源文件。 任何實作 <xref:System.Xml.XPath.IXPathNavigable> 介面的存放區都可用來做為 <xref:System.Xml.Xsl.XslTransform> 的來源文件。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 目前可實作 <xref:System.Xml.XPath.IXPathNavigable>、<xref:System.Xml.XmlDocument> 和 <xref:System.Xml.XmlDataDocument> 上的 <xref:System.Xml.XPath.XPathDocument> 介面，因此它們都可用來做為轉換的輸入來源文件。  
  
 <xref:System.Xml.Xsl.XslTransform> 中的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件僅支援 XSLT 1.0 規格，此規格是以下列命名空間定義：  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法可用來將下列其中一個類別載入樣式表：  
  
-   XPathNavigator  
  
-   XmlReader  
  
-   表示 URL 的字串   
  
 上述每個輸入類別都有不同的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法。 有些方法會採用上述其中一個類別與 <xref:System.Xml.XmlResolver> 類別的組合，來做為引數。 <xref:System.Xml.XmlResolver> 會尋找樣式表中可發現之 `<xsl:import>` 或 `<xsl:include>` 所參考的資源。 下列幾種方法會採用字串 (<xref:System.Xml.XmlReader>) 或 <xref:System.Xml.XPath.XPathNavigator> 做為輸入。  
  
```vb  
Overloads Public Sub Load(String)  
```  
  
```csharp  
public void Load(string);  
```  
  
```vb  
Overloads Public Sub Load(String, XmlResolver)  
```  
  
```csharp  
public void Load(string, XmlResolver);  
```  
  
```vb  
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XmlReader, XmlResolver, Evidence);  
```  
  
```vb  
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XPathNavigator, XmlResolver, Evidence);  
```  
  
 上述 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法大多會以 <xref:System.Xml.XmlResolver> 做為參數。 <xref:System.Xml.XmlResolver> 可用來載入樣式表，以及 xsl:import 和 xsl:include 項目中所參考的任何樣式表。  
  
 大多數的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法也會以辨識項做為參數。 辨識項參數是指與樣式表關聯的 <xref:System.Security.Policy.Evidence>。 樣式表的安全性層級會影響它所參考之後續資源的安全性層級，例如它所包含的指令碼、所使用的任何 `document()` 函式，以及 <xref:System.Xml.Xsl.XsltArgumentList> 所使用的任何擴充物件。  
  
 如果使用 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法 (具有 URL 參數但未提供辨識項) 來載入樣式表，則會結合指定的 URL 與其網站和區域來計算樣式表的辨識項。  
  
 若未提供 URI 或辨識項，則樣式表的辨識項集合將完全受信任。 請勿從未受信任的來源載入樣式表，或者將未受信任的擴充物件加入 <xref:System.Xml.Xsl.XsltArgumentList> 中。  
  
 如需安全性層級、辨識項，以及辨識項將會如何影響指令碼的詳細資訊，請參閱[使用 \<msxsl:script> 的 XSLT 樣式表指令碼](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)。 如需安全性層級、辨識項，以及辨識項將會如何影響指令碼的詳細資訊，請參閱[樣式表參數和擴充物件的 XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)。  
  
 如需安全性層級、辨識項，以及辨識項將會如何影響 `document()` 函式的詳細資訊，請參閱[解析外部的 XSLT 樣式表和文件](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md) 。  
  
 可提供樣式表數個輸入參數。 樣式表也可以呼叫擴充物件上的函式。 參數和擴充物件都可透過 <xref:System.Xml.Xsl.XsltArgumentList> 類別提供給樣式表。 如需 <xref:System.Xml.Xsl.XsltArgumentList> 的詳細資訊，請參閱<xref:System.Xml.Xsl.XsltArgumentList>。  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a>建議的 XslTransform 類別安全使用法  
 樣式表的安全性權限取決於所提供的辨識項。 下表摘錄樣式表的位置，並針對應提供何種辨識項型別加以說明。  
  
-   XSLT 樣式表沒有外部參考，或者樣式表是來自您信任的程式碼基底。  
  
    -   從您的組件提供辨識項：  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   XSLT 樣式表來自外部來源。 已知來源的源頭，並且有可驗證的 URI。  
  
    -   使用 URI 建立辨識項。  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   XSLT 樣式表來自外部來源。 來源的源頭未知。  
  
    -   將辨識項設為 `null`。 不會處理指令碼區塊、不支援 XSLT `document()` 函式，且不允許已授權的擴充物件。  
  
         此外，您也可以將 `resolver` 參數設為 `null`，如此可確保不會處理 `xsl:import` 和 `xsl:include` 項目。  
  
-   XSLT 樣式表來自外部來源。 來源的源頭未知，但是您需要指令碼支援。  
  
    -   自呼叫端要求識別項。  
  
## <a name="transformation-of-xml-data"></a>XML 資料的轉換  
 載入樣式表後，即可呼叫其中一個 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法以及提供輸入來源文件來啟動轉換。 可多載化 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法，以提供不同的轉換輸出。 轉換可以產生下列輸出格式：  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   檔案的字串 URL  
  
 字串 URL 是最後一個格式，它經用於 URL 中的輸入文件轉換，以及將文件寫入輸出 URL 等作業案例中。 這項 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 是一項便利的方法，可從檔案載入 XML 文件，然後執行 XSLT 轉換，再將輸出寫入檔案中。 如此可以防止您必須建立和載入輸入來源文件，再寫入至檔案資料流。 下列程式碼範例將以字串 URL 做為輸入和輸出，以示範 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法的使用情形：  
  
```vb  
Dim xsltransform As XslTransform = New XslTransform()  
xsltransform.Load("favorite.xsl")  
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)  
```  
  
```csharp  
XslTransform xsltransform = new XslTransform();  
xsltransform.Load("favorite.xsl");  
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);  
```  
  
## <a name="transforming-a-section-of-an-xml-document"></a>轉換 XML 文件的段落  
 轉換是指套用到整個文件。 換言之，如果您要傳入的節點不是文件的根節點，則不會阻止轉換程序取得已載入文件中的所有節點。 若要轉換結果樹狀結構片段，則必須建立僅包含結果樹狀結構片段的 <xref:System.Xml.XmlDocument>，並將 <xref:System.Xml.XmlDocument> 傳遞至 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法中。 以下範例將執行結果樹狀片段的轉換。  
  
```vb  
Dim xslt As New XslTransform()  
xslt.Load("print_root.xsl")  
Dim doc As New XmlDocument()  
doc.Load("library.xml")  
' Create a new document containing just the result tree fragment.  
Dim testNode As XmlNode = doc.DocumentElement.FirstChild  
Dim tmpDoc As New XmlDocument()  
tmpDoc.LoadXml(testNode.OuterXml)  
' Pass the document containing the result tree fragment   
' to the Transform method.  
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))  
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)  
```  
  
```csharp  
XslTransform xslt = new XslTransform();       
xslt.Load("print_root.xsl");  
XmlDocument doc = new XmlDocument();  
doc.Load("library.xml");  
// Create a new document containing just the result tree fragment.  
XmlNode testNode = doc.DocumentElement.FirstChild;   
XmlDocument tmpDoc = new XmlDocument();   
tmpDoc.LoadXml(testNode.OuterXml);  
// Pass the document containing the result tree fragment   
// to the Transform method.  
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");  
xslt.Transform(tmpDoc, null, Console.Out, null);  
```  
  
 此範例使用 library.xml 和 print_root.xsl 檔案做為輸入，並且會將下列項目輸出到主控台。  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 library.xml  
  
```xml  
<library>  
  <book genre='novel' ISBN='1-861001-57-5'>  
     <title>Pride And Prejudice</title>  
  </book>  
  <book genre='novel' ISBN='1-81920-21-2'>  
     <title>Hook</title>  
  </book>  
</library>  
```  
  
 print_root.xsl  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>XSLT 從 .NET Framework 1.0 版到 .NET Framework 1.1 版的轉換  
 下列表格將針對 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 方法列出已過時的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版方法以及新的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 1.1 版方法。 新方法可讓您藉由指定辨識項來限制樣式表的使用權限。  
  
|.NET Framework 1.0 版過時的 Load 方法|.NET Framework 1.1 版替代的 Load 方法|  
|------------------------------------------------------|---------------------------------------------------------|  
|Load(XPathNavigator input);<br /><br /> Load(XPathNavigator input, XmlResolver resolver);|Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);|  
|Load(IXPathNavigable stylesheet);<br /><br /> Load(IXPathNavigable stylesheet, XmlResolver resolver);|Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);|  
|Load(XmlReader stylesheet);<br /><br /> Load(XmlReader stylesheet, XmlResolver resolver);|Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);|  
  
 下列表格將針對 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法列出已過時的方法和新的方法。 新方法採用的是 <xref:System.Xml.XmlResolver> 物件。  
  
|.NET Framework 1.0 版過時的 Transform 方法 |.NET Framework 1.1 版替代的 Transform 方法|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|XmlReader Transform(XPathNavigator input, XsltArgumentList args)|XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)|  
|XmlReader Transform(IXPathNavigable input, XsltArgumentList args)|XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)|  
|Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)|Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)|  
|Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)|Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)|  
|Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)|Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)|  
|Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)|Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)|  
|Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)|Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)|  
|Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)|Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)|  
|Void Transform(String input, String output);|Void Transform(String input, String output, XmlResolver resolver);|  
  
 <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> 屬性在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 版中已過時。 請改用新的 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 多載，它採用的是 <xref:System.Xml.XmlResolver> 物件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Xsl.XslTransform>  
- [使用 XslTransform 類別進行 XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [轉換中的 XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [轉換中的 XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [XslTransform 的 XPathDocument 輸入](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [XslTransform 的 XmlDataDocument 輸入](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [XslTransform 的 XmlDocument 輸入](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
