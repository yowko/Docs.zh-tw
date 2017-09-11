---
title: "查詢 XDocument 與查詢 xelement 的比較 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 93f0f7f50ad305540a6afef2374d4b948de48705
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="0dc84-102">查詢 XDocument 與查詢 xelement 的比較 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dc84-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="0dc84-103">當您載入文件<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>，您會注意到，您必須撰寫查詢稍有不同於載入透過<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>時</xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>透過</span><span class="sxs-lookup"><span data-stu-id="0dc84-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="0dc84-104">XDocument.Load 和 XElement.Load 之比較</span><span class="sxs-lookup"><span data-stu-id="0dc84-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="0dc84-105">當您載入到 XML 文件<xref:System.Xml.Linq.XElement>透過<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XElement>根目錄中的 XML 樹狀結構會包含已載入文件的根項目。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="0dc84-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="0dc84-106">不過，當您載入相同的 XML 文件<xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>樹狀結構的根<xref:System.Xml.Linq.XDocument>節點，然後載入文件的根項目是一個允許的子<xref:System.Xml.Linq.XElement>節點的<xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> ，</xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>透過</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="0dc84-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="0dc84-107">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 座標軸會相對於根節點進行運算。</span><span class="sxs-lookup"><span data-stu-id="0dc84-107">The [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="0dc84-108">這個第一個範例會載入使用<xref:System.Xml.Linq.XElement.Load%2A>.</xref:System.Xml.Linq.XElement.Load%2A> XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="0dc84-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="0dc84-109">接著，它會針對樹狀結構根目錄的子項目進行查詢。</span><span class="sxs-lookup"><span data-stu-id="0dc84-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="0dc84-110">這個範例預期會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0dc84-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="0dc84-111">下列範例是上述，使用例外狀況的 XML 樹狀結構載入<xref:System.Xml.Linq.XDocument>而不是<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>相同</span><span class="sxs-lookup"><span data-stu-id="0dc84-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="0dc84-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0dc84-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="0dc84-113">請注意，相同的查詢會傳回一個 `Root` 節點，而非三個子節點。</span><span class="sxs-lookup"><span data-stu-id="0dc84-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="0dc84-114">其中一種處理方式是使用<xref:System.Xml.Linq.XDocument.Root%2A>屬性，才能存取座標軸方法，如下︰</xref:System.Xml.Linq.XDocument.Root%2A></span><span class="sxs-lookup"><span data-stu-id="0dc84-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="0dc84-115">這個查詢會執行在同一個查詢樹狀結構的方式起源於<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="0dc84-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="0dc84-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0dc84-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dc84-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dc84-117">See Also</span></span>  
 [<span data-ttu-id="0dc84-118">基本查詢 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dc84-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
