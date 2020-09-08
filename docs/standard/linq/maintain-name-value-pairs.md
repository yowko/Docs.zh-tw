---
title: 維護名稱/值組-LINQ to XML
description: 瞭解如何使用 LINQ to XML 方法來維護一組名稱/值配對。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 681df91d42f8bdb403dcf6f735104301c4a0c9ba
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552218"
---
# <a name="maintain-name-value-pairs-linq-to-xml"></a>維護名稱/值組 (LINQ to XML) 

許多應用程式都必須維護最適合作為成對名稱/值的資訊。 這類資訊可能是組態或全域設定的相關資訊。 LINQ to XML 包含的方法，可讓您輕鬆地維護一組名稱/值配對。 您可以將該資訊保存為屬性或一組子項目。

將資訊保存為屬性或子項目的其中一個差異在於，屬性所擁有的條件約束中，僅能有一個具有項目之特定名稱的屬性。 這項限制不適用於子項目。

## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue 和 SetElementValue

有助於將名稱/值配對保持在一起的兩個方法為 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 和 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 。 這些兩個方法具有類似的語意 (Semantics)。

<xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 可以加入、修改和移除專案的屬性。

- 如果您 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 使用不存在的屬性名稱進行呼叫，此方法會建立新的屬性，並將它加入至指定的元素。
- 如果您呼叫的 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 具有現有屬性的名稱以及某些指定的內容，屬性的內容會取代為指定的內容。
- 如果您 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 使用現有屬性的名稱來呼叫，並指定 `null` 內容的，則會從其父系中移除該屬性。

<xref:System.Xml.Linq.XElement.SetElementValue%2A> 可以加入、修改和移除專案的子項目。

- 如果您 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 使用不存在的子專案名稱來呼叫，此方法會建立新的專案，並將其加入至指定的元素。
- 如果您呼叫的 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 具有現有項目的名稱以及某些指定的內容，項目的內容會取代為指定的內容。
- 如果您使用現有專案的名稱來呼叫 <xref:System.Xml.Linq.XElement.SetElementValue%2A> ，並 `null` 為內容指定，則會從其父系中移除該元素。

## <a name="example-use-setattributevalue-to-create-and-maintain-a-list-of-name-value-pairs"></a>範例：用 `SetAttributeValue` 來建立及維護成對的名稱/值組清單

下列範例會建立沒有屬性的項目。 然後，它會使用 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 方法來建立和維護成對的名稱/值組清單。

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22);
root.SetAttributeValue("Left", 20);
root.SetAttributeValue("Bottom", 122);
root.SetAttributeValue("Right", 300);
root.SetAttributeValue("DefaultColor", "Color.Red");
Console.WriteLine(root);

// Replace the value of Top.
root.SetAttributeValue("Top", 10);
Console.WriteLine(root);

// Remove DefaultColor.
root.SetAttributeValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22)
root.SetAttributeValue("Left", 20)
root.SetAttributeValue("Bottom", 122)
root.SetAttributeValue("Right", 300)
root.SetAttributeValue("DefaultColor", "Color.Red")
Console.WriteLine(root)

' Replace the value of Top.
root.SetAttributeValue("Top", 10)
Console.WriteLine(root)

' Remove DefaultColor.
root.SetAttributeValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

這個範例會產生下列輸出：

```xml
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" />
```

## <a name="example-use-setelementvalue-to-create-and-maintain-a-list-of-name-value-pairs"></a>範例：用 `SetElementValue` 來建立及維護成對的名稱/值組清單

下列範例會建立沒有子項目的項目。 然後，它會使用 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 方法來建立和維護成對的名稱/值組清單。

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22);
root.SetElementValue("Left", 20);
root.SetElementValue("Bottom", 122);
root.SetElementValue("Right", 300);
root.SetElementValue("DefaultColor", "Color.Red");
Console.WriteLine(root);
Console.WriteLine("----");

// Replace the value of Top.
root.SetElementValue("Top", 10);
Console.WriteLine(root);
Console.WriteLine("----");

// Remove DefaultColor.
root.SetElementValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22)
root.SetElementValue("Left", 20)
root.SetElementValue("Bottom", 122)
root.SetElementValue("Right", 300)
root.SetElementValue("DefaultColor", "Color.Red")
Console.WriteLine(root)
Console.WriteLine("----")

' Replace the value of Top.
root.SetElementValue("Top", 10)
Console.WriteLine(root)
Console.WriteLine("----")

' Remove DefaultColor.
root.SetElementValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Top>22</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
</Root>
```

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
