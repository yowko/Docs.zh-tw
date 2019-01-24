---
title: 預先同質化 XName 物件 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: 51670a23bf3e8b2896b866b0dd62346d8893aff7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520089"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>預先同質化 XName 物件 (LINQ to XML) (Visual Basic)
在 LINQ to XML 中，改善效能的其中一種方式就是預先不可部分完成 <xref:System.Xml.Linq.XName> 物件。 預先不可部分完成是表示，您先指派字串給 <xref:System.Xml.Linq.XName> 物件，然後再使用 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 類別 (Class) 的建構函式 (Constructor) 來建立 XML 樹狀結構。 接著，您會傳遞初始化的 <xref:System.Xml.Linq.XName> 物件，而非將字串傳遞至建構函式 (會使用隱含轉換，從字串轉換成 <xref:System.Xml.Linq.XName>)。  
  
 當您建立重複特定名稱的大型 XML 樹狀結構時，這樣做可以改善效能。 若要這樣做，請在建構 XML 樹狀結構之前宣告並初始化 <xref:System.Xml.Linq.XName> 物件，然後使用 <xref:System.Xml.Linq.XName> 物件，而非指定項目和屬性名稱的字串。 如果您使用相同的名稱來建立大量項目 (或屬性)，這項技巧可能會大幅提升效能。  
  
 您應該使用自己的案例來測試預先不可部分完成，以便決定是否應該使用此作業。  
  
## <a name="example"></a>範例  
 下列範例為其示範。  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 下列範例顯示 XML 文件位於命名空間中的相同技巧：  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 下列範例更類似於您可能會在真實世界中遇到的狀況。 在此範例中，項目的內容是由查詢提供：  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 上一則範例的執行效能比下列範例要好，因為其名稱並非預先不可部分完成：  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>另請參閱
- [效能 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [不可部分完成的 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
