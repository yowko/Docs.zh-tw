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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186249"
---
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="34526-102">轉換中的 XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="34526-102">XPathNodeIterator in Transformations</span></span>
<span data-ttu-id="34526-103"><xref:System.Xml.XPath.XPathNodeIterator> 所提供的方法可讓您重複處理建立為 XML 路徑語言 (XPath) 查詢結果的節點集，或是利用節點集方法轉換成節點集的 Result Tree Fragment。</span><span class="sxs-lookup"><span data-stu-id="34526-103">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="34526-104"><xref:System.Xml.XPath.XPathNodeIterator> 可讓您重複處理該節點集內的節點。</span><span class="sxs-lookup"><span data-stu-id="34526-104">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="34526-105">擷取節點集之後，<xref:System.Xml.XPath.XPathNodeIterator> 類別即會提供唯讀且順向的資料指標給選取的節點集。</span><span class="sxs-lookup"><span data-stu-id="34526-105">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="34526-106">節點集以文件順序建立，因此呼叫這個方法將移至文件順序中的下一個節點。</span><span class="sxs-lookup"><span data-stu-id="34526-106">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="34526-107"><xref:System.Xml.XPath.XPathNodeIterator> 不會在節點集內建置所有節點的節點樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="34526-107"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="34526-108">而是將單一節點視窗提供到資料內，讓您在樹狀結構中移動時，公開它所指到的基礎節點。</span><span class="sxs-lookup"><span data-stu-id="34526-108">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="34526-109">因使用 <xref:System.Xml.XPath.XPathNodeIterator> 類別而成為可用的方法與屬性，可讓您取得目前節點的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="34526-109">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="34526-110">如需可用方法和屬性的清單，請參閱 <xref:System.Windows.Forms.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="34526-110">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="34526-111"><xref:System.Xml.XPath.XPathNodeIterator> 會在 XPath 查詢所建立的節點集上移動，且只能順向移動，因此必須使用 <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> 方法來移動。</span><span class="sxs-lookup"><span data-stu-id="34526-111">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="34526-112">這種方法傳回的型別是 `Boolean`，若它移到下一個選取的節點則傳回 `true`，若沒有其他選取的節點則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="34526-112">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="34526-113">如果它傳回 `true`，下列清單顯示可用的屬性：</span><span class="sxs-lookup"><span data-stu-id="34526-113">If it returns `true`, the following list shows the properties available:</span></span>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="34526-114">當您首次檢視節點集時，必須呼叫 <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A>，對所選節點集之第一個節點的 <xref:System.Xml.XPath.XPathNodeIterator> 進行定位。</span><span class="sxs-lookup"><span data-stu-id="34526-114">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="34526-115">這允許寫入 while 迴圈。</span><span class="sxs-lookup"><span data-stu-id="34526-115">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="34526-116">下列程式碼範例顯示如何在 <xref:System.Xml.XPath.XPathNodeIterator> 中，將 <xref:System.Xml.Xsl.XslTransform> 作為參數，傳遞到 <xref:System.Xml.Xsl.XsltArgumentList>。</span><span class="sxs-lookup"><span data-stu-id="34526-116">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="34526-117">程式碼的輸入為 **books.xml**，樣式表為 **text.xsl**。</span><span class="sxs-lookup"><span data-stu-id="34526-117">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="34526-118">**test.xml** 檔案為 <xref:System.Xml.XPath.XPathDocument>。</span><span class="sxs-lookup"><span data-stu-id="34526-118">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
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
  
## <a name="booksxml"></a><span data-ttu-id="34526-119">books.xml</span><span class="sxs-lookup"><span data-stu-id="34526-119">books.xml</span></span>  
  
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
  
## <a name="testxsl"></a><span data-ttu-id="34526-120">test.xsl</span><span class="sxs-lookup"><span data-stu-id="34526-120">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="34526-121">test.xml</span><span class="sxs-lookup"><span data-stu-id="34526-121">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="34526-122">輸出 (out.xml)</span><span class="sxs-lookup"><span data-stu-id="34526-122">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34526-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34526-123">See also</span></span>

- [<span data-ttu-id="34526-124">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="34526-124">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
