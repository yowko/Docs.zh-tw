---
title: 將元素、屬性和節點加入至 XML 樹狀結構-LINQ to XML
description: 瞭解如何將內容 (元素、屬性、批註、處理指示、文字和 CDATA) 加入至 XML 樹狀結構。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 5225560a3f3c94dcb7d4c65e66accddcead84b70
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552288"
---
# <a name="add-elements-attributes-and-nodes-to-an-xml-tree-linq-to-xml"></a>將元素、屬性和節點加入至 XML 樹狀結構 (LINQ to XML) 

您可以將內容 (元素、屬性、批註、處理指示、文字和 CDATA) 加入至 XML 樹狀結構。

## <a name="methods-for-adding-content"></a>加入內容的方法

下列方法會將子內容加入到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>：

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Linq.XContainer.Add%2A>|將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的結尾。|
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|將內容加入到 <xref:System.Xml.Linq.XContainer> 之子內容的開頭。|

下列方法會加入內容，做為 <xref:System.Xml.Linq.XNode> 的同層級節點。 雖然您可以將有效的同層級內容加入到節點的其他型別 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XText>)，但是您加入同層級內容的最常見目標節點為 <xref:System.Xml.Linq.XComment>。

|方法|描述|
|------------|-----------------|
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|將內容加入到 <xref:System.Xml.Linq.XNode> 之後。|
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|將內容加入到 <xref:System.Xml.Linq.XNode> 之前。|

## <a name="example-create-two-xml-trees-and-modify-one-of-them"></a>範例：建立兩個 XML 樹狀結構並修改其中一個

下列範例會建立兩個 XML 樹狀結構，然後修改其中一個。

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element1", 1),
    new XElement("Element2", 2),
    new XElement("Element3", 3),
    new XElement("Element4", 4),
    new XElement("Element5", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child1", 1),
    new XElement("Child2", 2),
    new XElement("Child3", 3),
    new XElement("Child4", 4),
    new XElement("Child5", 5)
);
xmlTree.Add(new XElement("NewChild", "new content"));
xmlTree.Add(
    from el in srcTree.Elements()
    where (int)el > 3
    select el
);
// Even though Child9 doesn't exist in srcTree, the following statement won't
// throw an exception, and nothing will be added to xmlTree.
xmlTree.Add(srcTree.Element("Child9"));
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element1>1</Element1>
        <Element2>2</Element2>
        <Element3>3</Element3>
        <Element4>4</Element4>
        <Element5>5</Element5>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child2>2</Child2>
        <Child3>3</Child3>
        <Child4>4</Child4>
        <Child5>5</Child5>
    </Root>

xmlTree.Add(<NewChild>new content</NewChild>)
xmlTree.Add( _
    From el In srcTree.Elements() _
    Where CInt(el) > 3 _
    Select el)

' Even though Child9 doesn't exist in srcTree, the following statement
' won't throw an exception, and nothing will be added to xmlTree.
xmlTree.Add(srcTree.Element("Child9"))
Console.WriteLine(xmlTree)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Child1>1</Child1>
  <Child2>2</Child2>
  <Child3>3</Child3>
  <Child4>4</Child4>
  <Child5>5</Child5>
  <NewChild>new content</NewChild>
  <Element4>4</Element4>
  <Element5>5</Element5>
</Root>
```
