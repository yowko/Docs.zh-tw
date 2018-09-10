---
title: 函數式建構 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: c2579da6e3cdfea6469742d29935b0137e320bbb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44191010"
---
# <a name="functional-construction-linq-to-xml-c"></a>函數式建構 (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供一種強大的方式來建立 XML 元素，稱為「函數式建構」。 功能結構是在單一陳述式中建立 XML 樹狀結構的能力。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 程式介面有數種主要功能可以使用功能結構：  
  
-   <xref:System.Xml.Linq.XElement> 建構函式會針對內容採用各種引數類型。 例如，您可以傳遞變成子項目的其他 <xref:System.Xml.Linq.XElement> 物件。 您可以傳遞變成項目屬性的 <xref:System.Xml.Linq.XAttribute> 物件。 或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。  
  
-   <xref:System.Xml.Linq.XElement> 建構函式會採用 `params` 類型的 <xref:System.Object> 陣列，讓您可以將任何數目的物件傳遞到建構函式。 這可讓您建立包含複雜內容的項目。  
  
-   如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。 如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。 這是非常重要的，因為這可讓您將 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的結果傳遞到建構函式中。  
  
 這些功能可讓您撰寫程式碼來建立 XML 樹狀結構。 以下是一個範例：  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 建立 XML 樹狀結構時，這些功能也可讓您撰寫使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢結果的程式碼，如下所示：  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>請參閱

- [建立 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
