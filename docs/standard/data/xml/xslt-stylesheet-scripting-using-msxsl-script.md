---
title: "使用 &lt;msxsl:script&gt; 加入 XSLT 樣式表指令碼 | Microsoft Docs"
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
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 使用 &lt;msxsl:script&gt; 加入 XSLT 樣式表指令碼
<xref:System.Xml.Xsl.XslTransform> 類別支援使用 `script` 項目的內嵌指令碼。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。  您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 \(XSLT\)。  如需詳細資訊，請參閱 [使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) 和 [從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。  
  
 <xref:System.Xml.Xsl.XslTransform> 類別支援使用 `script` 項目的內嵌指令碼。  載入樣式表時，任何已定義的函式都會被包裝在類別定義內，而編譯成 Microsoft Intermediate Language \(MSIL\)，因此不會降低效能。  
  
 `<msxsl:script>` 項目的定義如下：  
  
```  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 其中 `msxsl` 是繫結至命名空間 `urn:schemas-microsoft-com:xslt` 的前置詞。  
  
 `language` 屬性並非必要項目，但若指定，則其值必須為下列其中一個值：C\#、VB、JScript、JavaScript、VisualBasic 或 CSharp。  如果沒有指定的話，語言預設為 JScript。  `language-name` 不區分大小寫，因此 'JavaScript' 和 'javascript' 是一樣的。  
  
 `implements-prefix` 屬性是必要的。  這個屬性用來宣告命名空間，並把它與指令碼區塊產生關聯。  這個屬性的值是表示命名空間的前置詞。  這個命名空間可以被定義在樣式表內的某處。  
  
 因為 `msxsl:script` 項目屬於命名空間 `urn:schemas-microsoft-com:xslt`，所以樣式表必須包含命名空間宣告 `xmlns:msxsl=urn:schemas-microsoft-com:xslt`。  
  
 如果指令碼的呼叫端沒有 [UnmanagedCode](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) 存取使用權限，則永遠不會編譯樣式表中的指令碼，且無法呼叫 <xref:System.Xml.Xsl.XslTransform.Load%2A>。  
  
 如果呼叫者端擁有 `UnmanagedCode` 使用權限，則會編譯指令碼，但是所允許的作業則取決於載入時所提供的辨識項。  
  
 如果使用其中一個採用 <xref:System.Xml.XmlReader> 或 <xref:System.Xml.XPath.XPathNavigator> 的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法來載入樣式表，則必須使用將 <xref:System.Security.Policy.Evidence> 參數做為它的其中一個引數的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 多載。  若要提供辨識項，呼叫端必須具有 [ControlEvidence](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic) 使用權限，才可提供指令碼組件的 `Evidence`。  如果呼叫端沒有這項使用權限，則可以將 `Evidence` 參數設為 `null`。  這樣 <xref:System.Xml.Xsl.XslTransform.Load%2A> 函式會在尋找指令碼時失敗。  `ControlEvidence` 使用權限被認為是功能非常強的使用權限，只能授與高度信任的程式碼。  
  
 若要從組件中取得辨識項，請使用 `this.GetType().Assembly.Evidence`。  若要從統一資源識別元 \(URI\) 取得辨識項，請使用 `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`。  
  
 如果使用的是採用 <xref:System.Xml.XmlResolver> 但不含 `Evidence` 的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法，則組件的安全性區域會預設為「完全信任」。  如需詳細資訊，請參閱 <xref:System.Security.SecurityZone> 和[具名使用權限集合](http://msdn.microsoft.com/zh-tw/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)。  
  
 函式可在 `msxsl:script` 項目內進行宣告。  下表顯示根據預設所支援的命名空間。  您可以使用所列之命名空間以外的類別。  不過這些類別必須是完整限定。  
  
|預設的命名空間|描述|  
|-------------|--------|  
|系統|系統類別。|  
|System.Collection|集合類別。|  
|System.Text|文字類別。|  
|System.Text.RegularExpressions|規則運算式類別。|  
|System.Xml|核心 XML 類別。|  
|System.Xml.Xsl|XSLT 類別。|  
|System.Xml.XPath|XML 路徑語言 \(XPath\) 類別。|  
|Microsoft.VisualBasic|Microsoft Visual Basic 指令碼的類別。|  
  
 宣告函式時，函式是包含在指令碼區塊內。  樣式表可以包含多個指令碼區塊，而每一個都會各自獨立運作。  這表示如果您在指令碼區塊內執行，您無法呼叫在另一個指令碼區塊內所定義的函式，除非它被宣告成有相同的命名空間和相同的指令碼語言。  因為每一個指令碼區塊都可以使用本身的語言，且這些區塊是根據該語言剖析器的文法規則進行剖析，因此您必須針對使用中的語言使用正確的語法。  例如，如果是在 C\# 指令碼區塊中，則在區塊中使用 XML 註解節點 `<!-- an XML comment -->` 就會產生錯誤。  
  
 指令碼函式所定義之提供的引數和傳回值，必須屬於全球資訊網協會 \(W3C\) XPath 或 XSLT 的其中一種型別。  下表列出對應的 W3C 型別、對等的 .NET Framework 類別 \(型別\)，以及 W3C 型別是 XPath 還是 XSLT 型別。  
  
|類型|對等的 .NET Framework 類別 \(型別\)|XPath 型別或 XSLT 型別|  
|--------|----------------------------------|-----------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|數字|System.Double|XPath|  
|Result Tree Fragment|System.Xml.XPath.XPathNavigator|XSLT|  
|Node Set|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 如果指令碼函式使用下列其中一個數字型別：Int16、UInt16、Int32、UInt32、Int64、UInt64、Single 或 Decimal，則會將這些型別強制成 Double \(其對應至 W3C XPath 型別數值\)。  所有其他型別會透過呼叫 `ToString` 方法而強制轉成字串。  
  
 如果指令碼函式使用前述以外的型別，或將樣式表載入 <xref:System.Xml.Xsl.XslTransform> 物件時未編譯函式，則會擲回例外狀況。  
  
 使用 `msxsl:script` 項目時，無論所使用的語言為何，都強烈建議將指令碼置於 CDATA 區段內。  例如，下例 XML 顯示您的程式碼所在的 CDATA 區段的範本。  
  
```  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 建議將所有指令碼內容置於 CDATA 區段內，因為指定之語言的運算子、識別項或分隔符號有可能會被錯譯為 XML。  下列範例顯示在指令碼中使用邏輯 AND 運算子。  
  
```  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 這將擲回例外狀況，因為未逸出連字號。  會將這份文件載入為 XML，且對  `msxsl:script` 項目標記之間的文字並未採取特別的處置。  
  
## 範例  
 下列範例會使用內嵌指令碼來計算圓周 \(假設已經知道其半徑\)。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.               
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
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
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.               
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }   
}  
```  
  
## 輸入  
 number.xml  
  
```  
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
  
 calc.xsl  
  
```  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius){  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">    
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>   
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## 輸出  
  
```  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>    
```  
  
## 請參閱  
 [XslTransform 類別實作 XSLT 處理器](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)