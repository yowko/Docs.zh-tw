---
title: 如何：從 XmlReader 建立樹狀結構 (C#)
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 1a0f56655f2b328be5a6615088ef242061ddbd5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317267"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="f71f5-102">如何：從 XmlReader 建立樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="f71f5-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="f71f5-103">這個主題顯示如何從 <xref:System.Xml.XmlReader> 直接建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="f71f5-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="f71f5-104">若要從 <xref:System.Xml.Linq.XElement> 建立 <xref:System.Xml.XmlReader>，您必須將 <xref:System.Xml.XmlReader> 定位在項目節點上。</span><span class="sxs-lookup"><span data-stu-id="f71f5-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="f71f5-105"><xref:System.Xml.XmlReader> 將會略過註解與處理指示，但是，如果 <xref:System.Xml.XmlReader> 定位在文字節點上，則會擲出錯誤。</span><span class="sxs-lookup"><span data-stu-id="f71f5-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="f71f5-106">若要避免此類的錯誤，請務必將 <xref:System.Xml.XmlReader> 定位在項目上，然後再從 <xref:System.Xml.XmlReader> 建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="f71f5-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f71f5-107">範例</span><span class="sxs-lookup"><span data-stu-id="f71f5-107">Example</span></span>  
 <span data-ttu-id="f71f5-108">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="f71f5-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="f71f5-109">下列程式碼會建立 `T:System.Xml.XmlReader` 物件，然後讀取節點，直到找到第一個項目節點為止。</span><span class="sxs-lookup"><span data-stu-id="f71f5-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="f71f5-110">接著，它會載入 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="f71f5-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f71f5-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f71f5-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f71f5-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="f71f5-112">See Also</span></span>  
 [<span data-ttu-id="f71f5-113">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f71f5-113">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
