---
title: 在 C# 中建立 XML 樹狀 (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 98bad6bfc3b563b39f9e58eadbff673f202646c1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502280"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a>在 C# 中建立 XML 樹狀結構 (LINQ to XML)
本節提供在 C# 中建立 XML 樹狀的相關資訊。  
  
 如需使用 LINQ 查詢的結果作為 <xref:System.Xml.Linq.XElement> 內容的資訊，請參閱[函數式建構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)。  
  
## <a name="constructing-elements"></a>建構項目
 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 建構函式的簽章可讓您傳遞項目或屬性的內容，當做建構函式的引數。 由於其中一個建構函式採用多個引數，因此，您可以傳遞任何數目的子項目。 當然，這些子項目中的每個子項目都可以包含其自己的子項目。 對於任何項目，您可以加入任何數目的屬性。  
  
 加入 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。 如果新內容已經成為父代，或是其他 XML 樹狀的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀。 本主題中的最後一個範例會示範這個情況。  
  
 若要建立 `contacts`<xref:System.Xml.Linq.XElement>，您可以使用下列程式碼：  
  
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
  
 如果縮排正確，建構 <xref:System.Xml.Linq.XElement> 物件的程式碼會非常接近基礎 XML 的結構。  
  
## <a name="xelement-constructors"></a>XElement 建構函式  
 <xref:System.Xml.Linq.XElement> 類別會將下列建構函式用於功能結構。 請注意，<xref:System.Xml.Linq.XElement> 還有其他建構函式，但是它們不用於功能結構，因此未在此處列出。  
  
|建構函式|描述|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|建立 <xref:System.Xml.Linq.XElement>。 `name` 參數會指定項目的名稱；`content` 會指定項目的內容。|  
|`XElement(XName name)`|在將其 <xref:System.Xml.Linq.XElement> 初始化為指定之名稱的情況下，建立 <xref:System.Xml.Linq.XName>。|  
|`XElement(XName name, params object[] content)`|在將其 <xref:System.Xml.Linq.XElement> 初始化為指定之名稱的情況下，建立 <xref:System.Xml.Linq.XName>。 系統會從參數清單的內容建立屬性和/或子項目。|  
  
 `content` 參數非常有彈性。 它支援物件為 <xref:System.Xml.Linq.XElement> 之有效子系的任何型別。 下列規則適用於傳入此參數的不同型別物件：  
  
-   字串當做文字內容加入。  
  
-   <xref:System.Xml.Linq.XElement> 當做子項目加入。  
  
-   <xref:System.Xml.Linq.XAttribute> 當做屬性加入。  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> 或 <xref:System.Xml.Linq.XText> 當做子內容加入。  
  
-   系統會列舉 <xref:System.Collections.IEnumerable>，並將這些規則遞迴地套用到結果。  
  
-   若是其他任何型別，則會呼叫其 `ToString` 方法，並將結果當做文字內容加入。  
  
### <a name="creating-an-xelement-with-content"></a>建立包含內容的 XElement  
 您可以建立包含具有單一方法呼叫之簡單內容的 <xref:System.Xml.Linq.XElement>。 如果要這樣做，請將內容指定為第二個參數，如下所示：  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 您可以傳遞任何型別的物件當做內容。 例如，下列程式碼會建立包含浮點數的項目當做內容：  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 浮點數為 Boxed 而且會傳入建構函式。 Boxed 數字會轉換為字串，並當做項目的內容使用。  
  
### <a name="creating-an-xelement-with-a-child-element"></a>建立包含子項目的 XElement  
 如果您要針對內容引數傳遞 <xref:System.Xml.Linq.XElement> 類別的執行個體，建構函式會建立包含子項目的項目：  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a>建立包含多個子項目的 XElement  
 您可以針對內容傳入多個 <xref:System.Xml.Linq.XElement> 物件。 每個 <xref:System.Xml.Linq.XElement> 物件都會當做子項目包含在內。  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 藉由延伸以上的範例，您可以建立完整的 XML 樹狀結構，如下所示：  
  
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
Console.WriteLine(contacts);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  
  
### <a name="creating-an-empty-element"></a>建立空項目  
 若要建立空的 <xref:System.Xml.Linq.XElement>，您不用將任何內容傳遞到建構函式。 下列範例會建立空項目：  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a>附加與複製  
 如先前所述，加入 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement>) 或 <xref:System.Xml.Linq.XAttribute> 物件時，如果新內容沒有父代，這些物件只會附加到 XML 樹狀結構。 如果新內容已經成為父代，或是其他 XML 樹狀的一部分，則會複製新內容，而且新複製的內容會附加到 XML 樹狀。  

下列範例示範將成為父代的項目加入到樹狀結構時，以及將沒有父代的項目加入樹狀結構時的行為。

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a>請參閱

- [建立 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
