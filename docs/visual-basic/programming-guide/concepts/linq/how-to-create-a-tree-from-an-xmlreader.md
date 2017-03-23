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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a8dff4e518d8850b4050389e5677ac81ecd1e074
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>如何︰ 從 XmlReader (Visual Basic) 建立樹狀結構
本主題說明如何直接從<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>建立 XML 樹狀結構 若要建立<xref:System.Xml.Linq.XElement>從<xref:System.Xml.XmlReader>，您必須將<xref:System.Xml.XmlReader>項目節點上。</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader>會略過註解與處理指示，但是如果<xref:System.Xml.XmlReader>定位於文字節點上，將會擲回錯誤。</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> 若要避免這類錯誤，一律將<xref:System.Xml.XmlReader>您建立 XML 樹狀結構從<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>之前的項目上</xref:System.Xml.XmlReader>  
  
## <a name="example"></a>範例  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)。  
  
 下列程式碼會建立 `T:System.Xml.XmlReader` 物件，然後讀取節點，直到找到第一個項目節點為止。 它接著會載入<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 這個範例會產生下列輸出：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
