---
title: 樣式表參數和擴充物件的 XsltArgumentList
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11cf0b694d75836ad903edeafc79a55ec4612b45
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586459"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>樣式表參數和擴充物件的 XsltArgumentList
<xref:System.Xml.Xsl.XsltArgumentList> 類別包含可擴充樣式表語言轉換 (XSLT) 參數和 XSLT 擴充物件。 傳入 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法後，就可從樣式表叫用這些參數和擴充物件。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> 和 <xref:System.Xml.Xsl.XsltArgumentList> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行 XSLT 轉換。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。  
  
 <xref:System.Xml.Xsl.XsltArgumentList> 類別包含 XSLT 參數和 XSLT 擴充物件。 傳入 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法後，就可從樣式表叫用這些參數和擴充物件。  
  
 下列是傳遞物件，而不是使用內嵌指令碼的優點：  
  
- 提供較佳的類別封裝和重複使用。  
  
- 允許樣式表更簡潔且更易於維護。  
  
- 除了支援的 <xref:System> 命名空間集內所定義的命名空間以外，支援在其他命名空間的類別上呼叫方法。  
  
- 支援使用 <xref:System.Xml.XPath.XPathNodeIterator> 將結果樹狀結構片段傳遞給樣式表。  
  
## <a name="xslt-style-sheet-parameters"></a>XSLT 樣式表參數  
 XSLT 參數可使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法加入至 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>。 限定名稱和命名空間統一資源識別元 (URI) 會在此時與參數物件產生關聯。  
  
 參數物件應對應至全球資訊網協會 (W3C) 型別。 下表說明對應的 W3C 型別、對等的 .NET Framework 類別 (型別)，以及 W3C 型別是 XML 路徑語言 (XPath) 型別還是 XSLT 型別。  
  
|W3C 型別|對等的 .NET Framework 類別 (型別)|XPath 型別或 XSLT 型別|  
|--------------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|number|System.Double|XPath|  
|Result Tree Fragment|System.Xml.XPath.XPathNavigator|XSLT|  
|Node Set|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 如果參數物件不是以上類別之一，它會被強制成合適的 Double 或 String。 Int16、UInt16、Int32、UInt32、Int64、UInt64、Single 和 Decimal 型別被強制成 Double。 所有其他型別都會透過 `ToString` 方法而強制轉換為 String。  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>若要使用 XSLT 參數，使用者必須執行以下作業：  
  
1. 使用 <xref:System.Xml.Xsl.XsltArgumentList> 來建立 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>，並加入物件。  
  
2. 從樣式表呼叫參數。  
  
3. 將 <xref:System.Xml.Xsl.XsltArgumentList> 傳遞至 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法。  
  
### <a name="example"></a>範例  
 下列範例使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 方法來建立參數，以保留計算的折扣日期。 折扣日期計算為從訂購日期起的 20 天。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a>輸入  
 order.xml  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 discount.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a>Output  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a>XSLT 擴充物件  
 使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法，將 XSLT 擴充物件加入至 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>。 限定名稱和命名空間 URI 於當時與擴充物件產生關聯。  
  
 加入物件時，<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 的呼叫端必須在安全性原則中完全受信任。 如果呼叫端並非完全受信任，則無法加入。  
  
 雖然物件成功加入，但不保證會成功執行。 呼叫 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法時，即會針對 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間所提供的辨識項計算使用權限，接著將該使用權限集指派給整個轉換程序。 如果擴充物件企圖啟始需要權限集中找不到的使用權限的動作，將擲回例外狀況。  
  
 從擴充物件中傳回的資料型別，是數字、字串、布林和節點集這四種基本 XPath 資料型別的其中一種。  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>若要使用 XSLT 擴充物件，使用者必須執行以下作業：  
  
1. 使用 <xref:System.Xml.Xsl.XsltArgumentList> 來建立 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>，並加入擴充物件。  
  
2. 從樣式表叫用擴充物件。  
  
3. 將 <xref:System.Xml.Xsl.XsltArgumentList> 傳遞至 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法。  
  
### <a name="example"></a>範例  
 以下範例計算圓的圓周 (假設已經知道其半徑)。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a>輸入  
 number.xml  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>    
```  
  
 circle.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>          
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a>Output  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a>另請參閱

- [XslTransform 類別實作 XSLT 處理器](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
