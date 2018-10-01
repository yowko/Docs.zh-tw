---
title: 轉換中的 XPathNodeIterator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f71d409729707f4af93fd7f8d5b82a99404579b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232751"
---
# <a name="xpathnodeiterator-in-transformations"></a>轉換中的 XPathNodeIterator
<xref:System.Xml.XPath.XPathNodeIterator> 所提供的方法可讓您重複處理建立為 XML 路徑語言 (XPath) 查詢結果的節點集，或是利用節點集方法轉換成節點集的 Result Tree Fragment。 <xref:System.Xml.XPath.XPathNodeIterator> 可讓您重複處理該節點集內的節點。 擷取節點集之後，<xref:System.Xml.XPath.XPathNodeIterator> 類別即會提供唯讀且順向的資料指標給選取的節點集。 節點集以文件順序建立，因此呼叫這個方法將移至文件順序中的下一個節點。 <xref:System.Xml.XPath.XPathNodeIterator> 不會在節點集內建置所有節點的節點樹狀結構。 而是將單一節點視窗提供到資料內，讓您在樹狀結構中移動時，公開它所指到的基礎節點。 因使用 <xref:System.Xml.XPath.XPathNodeIterator> 類別而成為可用的方法與屬性，可讓您取得目前節點的相關資訊。 如需可用方法和屬性的清單，請參閱 <xref:System.Windows.Forms.ToolBar>。  
  
 <xref:System.Xml.XPath.XPathNodeIterator> 會在 XPath 查詢所建立的節點集上移動，且只能順向移動，因此必須使用 <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> 方法來移動。 這種方法傳回的型別是 `Boolean`，若它移到下一個選取的節點則傳回 `true`，若沒有其他選取的節點則傳回 `false`。 如果它傳回 `true`，下列清單顯示可用的屬性：  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 當您首次檢視節點集時，必須呼叫 <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A>，對所選節點集之第一個節點的 <xref:System.Xml.XPath.XPathNodeIterator> 進行定位。 這允許寫入 while 迴圈。  
  
 下列程式碼範例顯示如何在 <xref:System.Xml.XPath.XPathNodeIterator> 中，將 <xref:System.Xml.Xsl.XslTransform> 作為參數，傳遞到 <xref:System.Xml.Xsl.XsltArgumentList>。 程式碼的輸入為 **books.xml**，樣式表為 **text.xsl**。 **test.xml** 檔案為 <xref:System.Xml.XPath.XPathDocument>。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a>books.xml  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a>test.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>test.xml  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>輸出 (out.xml)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>另請參閱

- [XslTransform 類別實作 XSLT 處理器](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
