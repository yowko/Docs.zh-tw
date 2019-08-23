---
title: 靜態編譯的查詢 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f9e703e65b333c0fd0c2a3219d537466c686af10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961892"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>靜態編譯的查詢 (LINQ to XML) (Visual Basic)
相對於 <xref:System.Xml.XmlDocument> 而言，LINQ to XML 其中一個最重要的效能優勢在於，LINQ to XML 中的查詢是靜態編譯的查詢，而 XPath 查詢則必須在執行階段解譯。 由於這項功能是 LINQ to XML 內建的，所以您不需要進行額外步驟，即可運用此功能，但是在選擇這兩項技術時了解其差異會有所幫助。 本主題將說明兩者的差異。  
  
## <a name="statically-compiled-queries-vs-xpath"></a>靜態編譯查詢與XPath  
 下列範例將顯示如何取得具有指定之名稱以及具有指定值之屬性的子代項目。  
  
 下面是對等的 XPath 運算式：  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 這則範例中的查詢運算式由編譯器重新撰寫成以方法為基礎的查詢語法。 下列範例 (使用以方法為基礎的查詢語法所撰寫) 會與先前的範例產生相同的結果：  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <xref:System.Linq.Enumerable.Where%2A> 方法是擴充方法。 如需詳細資訊，請參閱[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。 由於 <xref:System.Linq.Enumerable.Where%2A> 是擴充方法，所以上述查詢會按照下列方式編譯：  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 這則範例會與先前兩則範例產生完全相同的結果。 這表示查詢實際上會編譯成靜態連結方法呼叫。 與 Iterator 的延後執行語意 (Semantics) 結合之後，便可改善效能。 如需反覆運算器延後執行語義的詳細資訊, 請參閱[LINQ to XML (Visual Basic) 中的延後執行和延遲評估](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。  
  
> [!NOTE]
> 這些範例是代表編譯器可能會撰寫的程式碼。 雖然實際的實作 (Implementation) 可能會與這些範例稍微不同，不過其效能與這些範例相同或相似。  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>使用 XmlDocument 來執行 XPath 運算式  
 下列範例會使用 <xref:System.Xml.XmlDocument> 來達成與先前範例相同的結果：  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 這個查詢與使用 LINQ to XML 的範例會傳回相同的輸出。唯一的差異是 LINQ to XML 會讓列印的 XML 縮排，而 <xref:System.Xml.XmlDocument> 則不會。  
  
 不過，<xref:System.Xml.XmlDocument> 方法的執行效能通常不如 LINQ to XML，因為每次呼叫 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法時，它就必須在內部執行下列作業：  
  
-   它會剖析包含 XPath 運算式的字串，並將此字串分割成語彙基元 (Token)。  
  
-   它會驗證這些語彙基元來確定 XPath 運算式是否有效。  
  
-   它會將此運算式轉譯成內部運算式樹狀架構。  
  
-   它會逐一查看這些節點，並且根據運算式的評估，適當地選取結果集的節點。  
  
 這點明顯比對應 LINQ to XML 查詢所完成的工作還多。 雖然特定效能差異會因不同類型的查詢而異，不過一般而言，相較於使用 <xref:System.Xml.XmlDocument> 來評估 XPath 運算式，LINQ to XML 查詢會進行較少工作，因此具有較佳的執行效能。  
  
## <a name="see-also"></a>另請參閱

- [效能 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
