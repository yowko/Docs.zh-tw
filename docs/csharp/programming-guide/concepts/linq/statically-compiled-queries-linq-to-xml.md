---
title: "靜態編譯的查詢 (LINQ to XML) (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 10e4df75be88dc5609e0ca15666042a0354824bc
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017


---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>靜態編譯的查詢 (LINQ to XML) (C#)
相對於 <xref:System.Xml.XmlDocument> 而言，LINQ to XML 其中一個最重要的效能優勢在於，LINQ to XML 中的查詢是靜態編譯的查詢，而 XPath 查詢則必須在執行階段進行解譯。 由於這項功能是 LINQ to XML 內建的，所以您不需要進行額外步驟，即可運用此功能，但是在選擇這兩項技術時了解其差異會有所幫助。 本主題將說明兩者的差異。  
  
## <a name="statically-compiled-queries-vs-xpath"></a>靜態編譯查詢與XPath  
 下列範例將顯示如何取得具有指定之名稱以及具有指定值之屬性的子代項目。  
  
 下面是對等的 XPath 運算式：  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 這則範例中的查詢運算式由編譯器重新撰寫成以方法為基礎的查詢語法。 下列範例 (使用以方法為基礎的查詢語法所撰寫) 會與先前的範例產生相同的結果：  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A> 方法是擴充方法。 如需詳細資訊，請參閱[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。 因為 <xref:System.Linq.Enumerable.Where%2A> 是擴充方法，所以上述查詢會依照下列方式編譯：  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 這則範例會與先前兩則範例產生完全相同的結果。 這表示查詢實際上會編譯成靜態連結方法呼叫。 與 Iterator 的延後執行語意 (Semantics) 結合之後，便可改善效能。 如需迭代器之延後執行語意的詳細資訊，請參閱 [LINQ to XML 中的延後執行和延遲評估 (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。  
  
> [!NOTE]
>  這些範例是代表編譯器可能會撰寫的程式碼。 雖然實際的實作 (Implementation) 可能會與這些範例稍微不同，不過其效能與這些範例相同或相似。  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>使用 XmlDocument 來執行 XPath 運算式  
 下列範例會使用 <xref:System.Xml.XmlDocument> 來達成與先前範例相同的結果：  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 這個查詢會傳回與使用 LINQ to XML 之範例相同的輸出；唯一的差異是 LINQ to XML 會讓列印的 XML 縮排，<xref:System.Xml.XmlDocument> 則不會。  
  
 不過，<xref:System.Xml.XmlDocument> 方法的執行效能通常不如 LINQ to XML，因為每次呼叫 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法時，它就必須在內部執行下列作業：  
  
-   它會剖析包含 XPath 運算式的字串，並將此字串分割成語彙基元 (Token)。  
  
-   它會驗證這些語彙基元來確定 XPath 運算式是否有效。  
  
-   它會將此運算式轉譯成內部運算式樹狀架構。  
  
-   它會逐一查看這些節點，並且根據運算式的評估，適當地選取結果集的節點。  
  
 這點明顯比對應 LINQ to XML 查詢所完成的工作還多。 雖然特定效能差異會因不同類型的查詢而異，不過一般而言，相較於使用 <xref:System.Xml.XmlDocument> 來評估 XPath 運算式，LINQ to XML 查詢會進行較少工作，因此具有較佳的執行效能。  
  
## <a name="see-also"></a>另請參閱  
 [效能 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
