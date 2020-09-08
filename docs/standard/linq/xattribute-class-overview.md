---
title: System.xml.linq.xattribute> 類別總覽
description: System.xml.linq.xattribute> 類別代表 XML 屬性。 使用 LINQ to XML 中的屬性類似于使用元素。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552114"
---
# <a name="xattribute-class-overview"></a>System.xml.linq.xattribute> 類別總覽

屬性是與專案相關聯的成對名稱/值。 <xref:System.Xml.Linq.XAttribute> 類別表示 XML 屬性。

使用 LINQ to XML 中的屬性類似于使用元素。 其建構函式類似。 您用來擷取其集合的方法也類似。 屬性集合的 LINQ 查詢運算式看起來類似于元素集合的 LINQ 查詢運算式。

系統會保留將屬性加入到項目的順序。 也就是說，當您逐一查看屬性時，您會看到加入這些屬性的相同順序。

## <a name="the-xattribute-constructor"></a>System.xml.linq.xattribute> 函式

下列類別的函式 <xref:System.Xml.Linq.XAttribute> 是您最常使用的類別：

|建構函式|描述|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|建立 <xref:System.Xml.Linq.XAttribute> 物件。 `name` 引數會指定屬性的名稱；`content` 會指定屬性的內容。|

## <a name="example-create-an-element-with-an-attribute"></a>範例：建立具有屬性的元素

下列範例顯示建立包含屬性之元素的一般工作。

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

這個範例會產生下列輸出：

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a>範例：屬性的功能結構

您可以 <xref:System.Xml.Linq.XAttribute> 使用物件的結構，以內嵌方式建立物件 <xref:System.Xml.Linq.XElement> ，如下列範例所示：

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

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
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

## <a name="attributes-arent-nodes"></a>屬性不是節點

屬性和項目有一些差異。 <xref:System.Xml.Linq.XAttribute> 物件不是 XML 樹狀結構中的節點。 它們是與 XML 元素相關聯的名稱/值配對。 相較於文件物件模型 (DOM)，這在反映 XML 的結構時，更為接近。 雖然 <xref:System.Xml.Linq.XAttribute> 物件實際上不是 XML 樹狀結構中的節點，但使用物件的方式類似于使用 <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> 物件。

這個區別只有對於撰寫可在節點層級使用 XML 樹狀結構之程式碼的開發人員特別重要。 許多開發人員都不在意這種差異。

## <a name="see-also"></a>另請參閱

- [LINQ to XML 總覽](linq-xml-overview.md)
