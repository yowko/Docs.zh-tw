---
title: '如何從檔案載入 XML （c #）'
description: '瞭解如何在 c # 中使用 System.xml.linq.xelement> 方法，從 URI 載入 XML。 這個範例會載入 XML 檔案，並將 XML 樹狀結構列印到主控台。'
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 29de914139d1e9abcda2097addca9219d44d2696
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104960"
---
# <a name="how-to-load-xml-from-a-file-c"></a>如何從檔案載入 XML （c #）
這個主題顯示如何使用 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 方法，從 URI 載入 XML。  
  
## <a name="example"></a>範例  
 下列範例顯示如何從檔案載入 XML 文件。 下列範例會載入 books.xml，並將 XML 樹狀輸出到主控台。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 此程式碼會產生下列輸出：  
  
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
  