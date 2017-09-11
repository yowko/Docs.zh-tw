---
title: "如何︰ 從 XmlReader (Visual Basic) 建立樹狀結構 |Microsoft 文件"
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
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a60b5cb3557016bba7bae9be6e0b9c9a448c1284
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="54403-102">如何︰ 從 XmlReader (Visual Basic) 建立樹狀結構</span><span class="sxs-lookup"><span data-stu-id="54403-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="54403-103">本主題說明如何直接從<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="54403-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="54403-104">若要建立<xref:System.Xml.Linq.XElement>從<xref:System.Xml.XmlReader>，您必須將<xref:System.Xml.XmlReader>項目節點上。</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="54403-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="54403-105"><xref:System.Xml.XmlReader>會略過註解與處理指示，但是如果<xref:System.Xml.XmlReader>定位於文字節點上，將會擲回錯誤。</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="54403-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="54403-106">若要避免這類錯誤，一律將<xref:System.Xml.XmlReader>您建立 XML 樹狀結構從<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>之前的項目上</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="54403-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54403-107">範例</span><span class="sxs-lookup"><span data-stu-id="54403-107">Example</span></span>  
 <span data-ttu-id="54403-108">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="54403-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="54403-109">下列程式碼會建立 `T:System.Xml.XmlReader` 物件，然後讀取節點，直到找到第一個項目節點為止。</span><span class="sxs-lookup"><span data-stu-id="54403-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="54403-110">它接著會載入<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="54403-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="54403-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="54403-111">This example produces the following output:</span></span>  
  
```xml  
<Catalog>  
   <Book id="bk101">  
      <Author>Garghentini, Davide</Author>  
      <Title>XML Developer's Guide</Title>  
      <Genre>Computer</Genre>  
      <Price>44.95</Price>  
      <PublishDate>2000-10-01</PublishDate>  
      <Description>An in-depth look at creating applications   
      with XML.</Description>  
   </Book>  
   <Book id="bk102">  
      <Author>Garcia, Debra</Author>  
      <Title>Midnight Rain</Title>  
      <Genre>Fantasy</Genre>  
      <Price>5.95</Price>  
      <PublishDate>2000-12-16</PublishDate>  
      <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
   </Book>  
</Catalog>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54403-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54403-112">See Also</span></span>  
 [<span data-ttu-id="54403-113">剖析 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54403-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
