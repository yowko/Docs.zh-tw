---
title: XAttribute 類別概觀 (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 79ef00aa79be0c743423cfba1a911b238ff9a7ca
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590922"
---
# <a name="xattribute-class-overview-c"></a>XAttribute 類別概觀 (C#)
屬性是與項目相關聯的成對名稱/值。 <xref:System.Xml.Linq.XAttribute> 類別表示 XML 屬性。  
  
## <a name="overview"></a>總覽  
 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中使用屬性的方式類似於使用項目。 其建構函式類似。 您用來擷取其集合的方法也類似。 屬性集合的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式看起來非常類似項目集合的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢運算式。  
  
 系統會保留將屬性加入到項目的順序。 也就是說，當您逐一查看屬性時，您會看到加入這些屬性的相同順序。  
  
## <a name="the-xattribute-constructor"></a>XAttribute 建構函式  
 下列 <xref:System.Xml.Linq.XAttribute> 類別的建構函式就是您常用的建構函式：  
  
|建構函式|說明|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|建立 <xref:System.Xml.Linq.XAttribute> 物件。 `name` 引數會指定屬性的名稱；`content` 會指定屬性的內容。|  
  
### <a name="creating-an-element-with-an-attribute"></a>建立具有屬性的項目  
 下列程式碼顯示建立包含屬性之項目的一般工作：  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>屬性的功能結構  
 您無法建構內嵌 <xref:System.Xml.Linq.XAttribute> 物件之結構的 <xref:System.Xml.Linq.XElement> 物件，如下所示：  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>屬性不是節點  
 屬性和項目有一些差異。 <xref:System.Xml.Linq.XAttribute> 物件在 XML 樹狀結構中不是節點。 它們是與 XML 項目相關聯的成對名稱/值。 相較於文件物件模型 (DOM)，這在反映 XML 的結構時，更為接近。 雖然 <xref:System.Xml.Linq.XAttribute> 物件實際上在 XML 樹狀結構中不是節點，但是使用 <xref:System.Xml.Linq.XAttribute> 物件的方式與使用 <xref:System.Xml.Linq.XElement> 物件的方式非常類似。  
  
 這個區別只有對於撰寫可在節點層級使用 XML 樹狀結構之程式碼的開發人員特別重要。 這個區別與許多開發人員都無關。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to XML 程式設計概觀 (C#)](./linq-to-xml-overview.md)
