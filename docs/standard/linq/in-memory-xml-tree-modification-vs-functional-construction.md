---
title: 記憶體中 XML 樹狀結構修改與功能結構 LINQ to XML
description: 請參閱修改 XML 樹狀結構的兩種不同方法的範例。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552123"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a>記憶體中的 XML 樹狀結構修改與功能結構 (LINQ to XML) 

就地修改 XML 樹狀結構是變更 XML 文件組織結構的傳統方式。 一般的應用程式會將檔載入至資料存放區，例如 DOM 或 LINQ to XML;使用程式設計介面插入或刪除節點，或變更其內容;然後將 XML 儲存至檔案，或透過網路傳輸。

LINQ to XML 啟用在許多案例中有用的另一種方法： *功能結構*。 功能結構會將修改資料視為轉換的問題，而不是資料存放區的詳細管理。 如果您可以表示資料，並將其有效地從一個表單轉換到另一個表單，結果會與您取得一個資料存放區，然後以相同的方式管理該資料存放區取得其他組織結構相同。 功能結構方法的關鍵在於將查詢結果傳遞到 <xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 建構函式。

在許多情況下，您可以在運算元據存放區所需的時間內撰寫轉換程式碼，而產生的程式碼會更穩定且更容易維護。 在這些情況下，即使轉換方法可能需要更多處理能力，也是修改資料的有效方式。 如果開發人員熟悉功能性方法，在許多情況下產生的程式碼會更容易瞭解，而且很容易就能找到修改樹狀結構每個部分的程式碼。

對許多 DOM 程式設計師來說，您修改 XML 樹狀結構的方法比較熟悉，而使用功能性方法撰寫的程式碼可能看起來不熟悉該方法的開發人員。 如果您必須針對大型 XML 樹狀結構進行小小的修改，您就地修改樹狀結構的方法在大部分的情況下，將會需要較少的 CPU 時間。

本文提供這兩種方法的範例。 假設您想要修改下列簡單的 XML 檔，讓屬性成為元素：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

下列範例中的第一個範例會使用傳統的就地修改方法，而第二個範例會使用功能結構方法。

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a>範例：使用傳統的就地方法將屬性轉換成元素

您可以撰寫特定的程序性程式碼以便從屬性建立項目，然後刪除該屬性，如下所示：

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a>範例：使用功能結構方法將屬性轉換成元素

相較之下，功能性方法是由程式碼組成，以形成新的樹狀結構、挑選和選擇來源樹狀結構中的專案和屬性，以及在新增至新樹狀結構時適當地轉換它們。

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

這個範例會與第一個範例輸出相同的 XML。 但是請注意，您實際上可以用功能性方法查看所產生的新 XML 結構。 您可以查看 `Root` 項目的建立、從來源樹狀結構提取 `Child1` 項目的程式碼，以及將屬性從來源樹狀結構轉換到新樹狀結構中的項目之程式碼。

在此情況下，此功能範例的長度不會比第一個範例還簡單。 但是，如果您對 XML 樹狀結構進行了許多變更，則程式化方法會變得相當複雜，而且有點遲鈍。 相反地，使用功能性方法時，您仍然可以在適當地內嵌查詢和運算式，只形成所需的 XML，以便在所需的內容中提取。 功能性方法會產生容易維護的程式碼。

請注意，在這個情況下，功能性方法可能不會實際與樹狀結構管理方法一起執行。 主要的問題是，功能性方法會建立更多短期的物件。 不過，如果使用功能性方法能讓程式設計人員的產能更大，進行取捨是有效的方法。

這是非常簡單的範例，但是它有助於顯示兩種方法間的觀點差異。 功能性方法在轉換大型 XML 文件時，會產生較大的產能。
