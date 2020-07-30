---
title: '如何從 XmlReader 建立樹狀結構（c #）'
description: 瞭解如何直接從 XmlReader 建立 XML 樹狀結構。 請參閱示範如何建立 T:System.Xml.XmlReader 物件的範例。
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 3801177e664d142652d38748d44eaf3f274239dd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302655"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="372b0-104">如何從 XmlReader 建立樹狀結構（c #）</span><span class="sxs-lookup"><span data-stu-id="372b0-104">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="372b0-105">這個主題顯示如何從 <xref:System.Xml.XmlReader> 直接建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="372b0-105">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="372b0-106">若要從 <xref:System.Xml.Linq.XElement> 建立 <xref:System.Xml.XmlReader>，您必須將 <xref:System.Xml.XmlReader> 定位在項目節點上。</span><span class="sxs-lookup"><span data-stu-id="372b0-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="372b0-107"><xref:System.Xml.XmlReader> 將會略過註解與處理指示，但是，如果 <xref:System.Xml.XmlReader> 定位在文字節點上，則會擲出錯誤。</span><span class="sxs-lookup"><span data-stu-id="372b0-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="372b0-108">若要避免此類的錯誤，請務必將 <xref:System.Xml.XmlReader> 定位在項目上，然後再從 <xref:System.Xml.XmlReader> 建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="372b0-108">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="372b0-109">範例</span><span class="sxs-lookup"><span data-stu-id="372b0-109">Example</span></span>  
 <span data-ttu-id="372b0-110">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="372b0-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="372b0-111">下列程式碼會建立 `T:System.Xml.XmlReader` 物件，然後讀取節點，直到找到第一個項目節點為止。</span><span class="sxs-lookup"><span data-stu-id="372b0-111">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="372b0-112">接著，它會載入 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="372b0-112">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="372b0-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="372b0-113">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="372b0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="372b0-114">See also</span></span>

- [<span data-ttu-id="372b0-115">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="372b0-115">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
