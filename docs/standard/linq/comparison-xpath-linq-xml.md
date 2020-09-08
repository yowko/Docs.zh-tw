---
title: XPath 和 LINQ to XML LINQ to XML 的比較
description: XPath 和 LINQ to XML 查詢都可以查詢 XML 樹狀結構。 本文將比較這兩個選項，並尋找 LINQ to XML 的查詢，這些都是最強大、多用途、更快速、更方便的選擇。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552248"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>XPath 和 LINQ to XML 的比較

XPath 和 LINQ to XML 在某些方面很類似。 兩者都可用於查詢 XML 樹狀結構，將此類結果當做項目的集合、屬性的集合、節點的集合，以及項目或屬性的值傳回。 不過，這兩個選項之間有顯著的差異。

## <a name="differences-between-xpath-and-linq-to-xml"></a>XPath 與 LINQ to XML 之間的差異

XPath 不允許投影新的類型。 它只能從樹狀結構傳回節點的集合，而 LINQ to XML 可以執行查詢並評估新圖案中的物件圖形或 XML 樹狀結構。 LINQ to XML 查詢可以比 XPath 運算式更多。

XPath 運算式存在於字串內的隔離中。 C # 編譯器無法在編譯時期協助剖析 XPath 運算式。 相較之下，C# 編譯器會剖析與編譯 LINQ to XML 查詢。 編譯器可能會攔截許多查詢錯誤。

XPath 結果不是強型別。 在許多情況下，評估 XPath 運算式的結果是一個物件，而開發人員可以決定適當的類型，並視需要轉換結果。 相較之下，LINQ to XML 查詢的評估為強型別。

## <a name="result-ordering"></a>結果排序

XPath 1.0 建議事項指出評估 XPath 運算式結果的集合未排序。

不過，逐一查看由 LINQ to XML XPath 軸方法傳回的集合時，會以文件順序傳回集合中的節點。 即使在存取 XPath 軸 (其中的述詞會根據反向的文件順序表示，例如，`preceding` 和 `preceding-sibling`) 時，也是如此。

相較之下，大部分的 LINQ to XML 軸會以檔順序傳回集合。 但是，其中的兩個 <xref:System.Xml.Linq.XNode.Ancestors%2A> 和會 <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> 以反向檔順序傳回集合。 下表列舉座標軸，並指出每個軸的收集順序：

|LINQ to XML 軸|排序|
|----------------------|--------------|
|XContainer.DescendantNodes|文件順序|
|XContainer.Descendants|文件順序|
|XContainer.Elements|文件順序|
|XContainer.Nodes|文件順序|
|XContainer.NodesAfterSelf|文件順序|
|XContainer.NodesBeforeSelf|文件順序|
|XElement.AncestorsAndSelf|反向的文件順序|
|XElement.Attributes|文件順序|
|XElement.DescendantNodesAndSelf|文件順序|
|XElement.DescendantsAndSelf|文件順序|
|XNode.Ancestors|反向的文件順序|
|XNode.ElementsAfterSelf|文件順序|
|XNode.ElementsBeforeSelf|文件順序|
|XNode.NodesAfterSelf|文件順序|
|XNode.NodesBeforeSelf|文件順序|

## <a name="positional-predicates"></a>位置述詞

在 XPath 運算式中，位置述詞會以檔順序表示許多座標軸，但以反向軸的反向檔順序表示。 反向軸如下： `preceding` 、 `preceding-sibling` 、 `ancestor` 和 `ancestor-or-self` 。 例如，XPath 運算式 `preceding-sibling::*[1]` 會傳回正前面的同層級。 即使最後的結果集會以文件順序呈現，也是如此。

相較之下，LINQ to XML 中的所有位置性述詞都一律會以座標軸的順序表示。 例如，`anElement.ElementsBeforeSelf().ElementAt(0)` 會傳回所查詢項目之父代的第一個子項目，而非正前面的同層級。 另一個範例：`anElement.Ancestors().ElementAt(0)` 會傳回父項目。

如果您要在 LINQ to XML 中尋找正前面的項目，您可以撰寫下列運算式：

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a>效能差異

在 LINQ to XML 中使用 XPath 功能的 XPath 查詢將會比 LINQ to XML 查詢慢。

## <a name="comparison-of-composition"></a>組合的比較

LINQ to XML 查詢的組合類似于 XPath 運算式的組合，但是語法非常不同。

例如，如果您在名為的變數中有一個專案 `customers` ，而您想要在名為的所有子項目底下尋找名為的孫元素 `CompanyName` `Customer` ，您可以撰寫此 XPath 運算式：

```csharp
customers.XPathSelectElements("./Customer/CompanyName")
```

```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

對等的 LINQ to XML 查詢為：

```csharp
customers.Elements("Customer").Elements("CompanyName")
```

```vb
customers.Elements("Customer").Elements("CompanyName")
```

每個 XPath 座標軸都有類似的項目。

|XPath 座標軸|LINQ to XML 軸|
|----------------|----------------------|
|child (預設軸)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|
|Parent (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|
|attribute 軸 (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|ancestor 軸|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|ancestor-or-self 軸|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|descendant 軸 (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|following-sibling|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|preceding-sibling|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> 或<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|following|沒有直接的對等。|
|preceding|沒有直接的對等。|
