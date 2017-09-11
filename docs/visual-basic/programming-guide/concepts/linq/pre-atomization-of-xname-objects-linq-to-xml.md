---
title: "預先同質化 XName 物件 (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4871fab18d04ce9d715299fd06138c493e666466
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="19589-102">預先同質化 XName 物件 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19589-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="19589-103">若要改善效能，LINQ to XML 中的之一是預先不可部分完成<xref:System.Xml.Linq.XName>物件。</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="19589-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="19589-104">預先同質化表示您指派字串給<xref:System.Xml.Linq.XName>物件使用的建構函式建立 XML 樹狀結構之前<xref:System.Xml.Linq.XElement>和<xref:System.Xml.Linq.XAttribute>類別。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="19589-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="19589-105">然後，而非將字串傳遞至建構函式，它會使用隱含轉換，從字串到<xref:System.Xml.Linq.XName>，您會傳遞初始化<xref:System.Xml.Linq.XName>物件。</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="19589-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="19589-106">當您建立重複特定名稱的大型 XML 樹狀結構時，這樣做可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="19589-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="19589-107">若要這樣做，宣告及初始化<xref:System.Xml.Linq.XName>物件之前建構 XML 樹狀結構中，然後使用<xref:System.Xml.Linq.XName>物件，而非指定的項目和屬性名稱的字串。</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="19589-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="19589-108">如果您使用相同的名稱來建立大量項目 (或屬性)，這項技巧可能會大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="19589-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="19589-109">您應該使用自己的案例來測試預先不可部分完成，以便決定是否應該使用此作業。</span><span class="sxs-lookup"><span data-stu-id="19589-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19589-110">範例</span><span class="sxs-lookup"><span data-stu-id="19589-110">Example</span></span>  
 <span data-ttu-id="19589-111">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="19589-111">The following example demonstrates this.</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="19589-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="19589-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="19589-113">下列範例顯示 XML 文件位於命名空間中的相同技巧：</span><span class="sxs-lookup"><span data-stu-id="19589-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="19589-114">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="19589-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="19589-115">下列範例更類似於您可能會在真實世界中遇到的狀況。</span><span class="sxs-lookup"><span data-stu-id="19589-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="19589-116">在此範例中，項目的內容是由查詢提供：</span><span class="sxs-lookup"><span data-stu-id="19589-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 <span data-ttu-id="19589-117">上一則範例的執行效能比下列範例要好，因為其名稱並非預先不可部分完成：</span><span class="sxs-lookup"><span data-stu-id="19589-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="19589-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19589-118">See Also</span></span>  
 <span data-ttu-id="19589-119">[效能 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="19589-119">[Performance (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md) </span></span>  
<span data-ttu-id="19589-120"> [不可部分完成的 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="19589-120"> [Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)</span></span>
