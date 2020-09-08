---
title: 混合的宣告式/命令式程式碼 bug-LINQ to XML
description: 瞭解如何辨識和避免程式碼逐一查看進行變更時可能發生的問題。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 280bb62d15ff28d1fd09ca2d0c52c0a0c36d7282
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552217"
---
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a>混合的宣告式/命令式程式碼 bug (LINQ to XML) 

LINQ to XML 包含各種可讓您直接修改 XML 樹狀結構的方法。 您可以加入項目、刪除項目、變更項目的內容、加入屬性等等。 [修改 XML 樹狀](in-memory-xml-tree-modification-vs-functional-construction.md)結構中會說明這個程式設計介面。 如果您正在逐一查看其中一個軸（例如）， <xref:System.Xml.Linq.XContainer.Elements%2A> 而且您要在逐一查看軸時修改 XML 樹狀結構，最後可能會出現一些奇怪的錯誤。

這種問題有時候稱為「幽靈問題」。

當您使用可逐一查看集合的 LINQ 撰寫一些程式碼時，就是以宣告式樣式撰寫程式碼。 它比較類似于描述您想要的 *內容* ，而不是您想要 *如何* 完成。 如果您撰寫的程式碼可 1) 取得第一個項目、2) 針對某些條件進行測試、3) 加以修改，以及 4) 將其放回清單中，則這會是命令性程式碼。 您會告訴電腦 *如何* 執行您想要的動作。

在相同的運算中混用這些程式碼樣式就是導致問題發生的原因。 請考慮下列事項：

假設您有一個連結的清單，其中包含三個項目 (a、b 和 c)：

> a-> b-> c

現在，假設您要移動連結的清單，以加入三個新項目 (a'、b' 和 c')。 您希望所產生的連結清單如下所示：

 > a-> a '-> b-> b '-> c-> c '

因此，您可以撰寫逐一查看清單的程式碼，然後針對每個項目，將新項目加入到清單的後面。 結果是，您的程式碼將會先看到 `a` 項目，然後在其後插入 `a'`。 現在，您的程式碼會移至清單中的下一個節點（現在 `a'` ），因此它會在清單中加入新的專案到清單中！

您要如何解決這個問題？ 您可以複製原始的連結清單，然後建立一個全新的清單。 或者，如果您要撰寫單純的命令式程式碼，您可能會發現第一個專案，加入新的專案，然後在連結清單中前進兩次，然後在您剛加入的元素上前進。

## <a name="example-adding-while-iterating"></a>範例：反覆運算時加入

例如，假設您想要撰寫程式碼，以在樹狀結構中建立每個元素的重複專案：

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    root.Add(new XElement(e.Name, (string)e));
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    root.Add(New XElement(e.Name, e.Value))
Next
```

這個程式碼會進入無限的迴圈。 `foreach` 陳述式會逐一查看 `Elements()` 座標軸，並將新的項目加入到 `doc` 項目。 它也會透過剛才加入的項目結束反覆運算。 而且它會利用迴圈的每次反覆運算配置新物件，因此最終會消耗所有可用的記憶體。

您可以使用 <xref:System.Linq.Enumerable.ToList%2A> 標準查詢運算子將集合配置到記憶體，藉以修正這個問題，如下所示：

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    root.Add(new XElement(e.Name, (string)e));
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    root.Add(New XElement(e.Name, e.Value))
Next
Console.WriteLine(root)
```

現在，這個程式碼可以運作了。 所產生的 XML 樹狀結構如下所示：

```xml
<Root>
  <A>1</A>
  <B>2</B>
  <C>3</C>
  <A>1</A>
  <B>2</B>
  <C>3</C>
</Root>
```

## <a name="example-deleting-while-iterating"></a>範例：反覆運算時刪除

如果您要在特定的層級刪除所有節點，您可能想要撰寫如下的程式碼：

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    e.Remove()
Next
Console.WriteLine(root)
```

不過，這並不是您想要的。 在這種情況下，當您移除第一個專案（A）之後，它會從根目錄中包含的 XML 樹狀結構中移除，而 Elements 方法中執行反覆運算的程式碼則找不到下一個元素。

這個範例會產生下列輸出：

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

解決方案為呼叫 <xref:System.Linq.Enumerable.ToList%2A> 來具體化集合，如下所示：

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    e.Remove()
Next
Console.WriteLine(root)
```

這個範例會產生下列輸出：

```xml
<Root />
```

或者，您可以在父項目上呼叫 <xref:System.Xml.Linq.XElement.RemoveAll%2A>，一起排除反覆運算：

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
root.RemoveAll();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
root.RemoveAll()
Console.WriteLine(root)
```

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a>範例：為什麼 LINQ 無法自動處理這些問題

其中一個方法是，一律將所有項目放入記憶體，而不是進行延遲評估。 不過，關於效能和記憶體使用率，這將會高度耗費資源。 事實上，如果 LINQ 和 LINQ to XML 是採用這種方法，在真實世界的情況下會失敗。

另一個可能的方法是將某種形式的交易語法放到 LINQ 中，並讓編譯器嘗試分析程式碼，以判斷是否需要具體化任何特定的集合。 不過，嘗試判斷具有副作用的所有程式碼相當複雜。 請考慮下列程式碼：

```csharp
var z =
    from e in root.Elements()
    where TestSomeCondition(e)
    select DoMyProjection(e);
```

```vb
Dim z = _
    From e In root.Elements() _
    Where (TestSomeCondition(e)) _
    Select DoMyProjection(e)
```

此類分析程式碼必須分析 TestSomeCondition 和 DoMyProjection 方法，而且這些方法呼叫的所有方法都必須判斷任何程式碼是否有副作用。 但是，分析程式碼無法只尋找具有副作用的任何程式碼。 在此情況下，此分析程式碼必須僅針對 `root` 的子項目上，具有副作用的程式碼進行選取。

LINQ to XML 不會嘗試進行任何這類的分析。 您可以自行避免這些問題。

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a>範例：使用宣告式程式碼產生新的 XML 樹狀結構，而不是修改現有的樹狀結構

若要避免這類問題，請不要混用宣告式和命令式程式碼，即使您知道集合的語義以及修改 XML 樹狀結構的方法的語法也是一樣。 如果您撰寫可避免問題的程式碼，則您的程式碼未來將需要由其他開發人員維護，而這些程式碼可能不會對問題造成任何清楚的解決。 如果您混用宣告式與命令性編碼方式，您的程式碼將更不可靠。  如果您撰寫可具體化集合的程式碼，讓這些問題得以避免，請在程式碼中，以適當的註解方式記錄下來，負責維護的程式設計人員就可以了解這個問題。

如果效能和其他考慮允許，請只使用宣告式程式碼。 請勿修改您現有的 XML 樹狀結構。 請改為產生一個新的，如下列範例所示：

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
XElement newRoot = new XElement("Root",
    root.Elements(),
    root.Elements()
);
Console.WriteLine(newRoot);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
Dim newRoot As XElement = New XElement("Root", _
    root.Elements(), root.Elements())
Console.WriteLine(newRoot)
```
