---
title: readonly 關鍵字 - C# 參考
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 165b6287e1610e013b289601e1535a08fdd3b5c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399354"
---
# <a name="readonly-c-reference"></a>readonly (C# 參考)

關鍵字`readonly`是可在四個上下文中使用的修飾符：

- 在[欄位聲明中](#readonly-field-example)，`readonly`指示對欄位的分配只能作為聲明的一部分或在同一類中的建構函式中進行。 可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。
  
  構造`readonly`函數退出後無法分配欄位。 此規則對數值型別和參考型別具有不同的含義：
  
  - 由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。
  - 由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。 那個物件不是不變的。 `readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。 但是，修改器不會阻止通過唯讀欄位修改欄位的實例資料。

  > [!WARNING]
  > 包含外部可見唯讀欄位（即可變參考型別）的外部可見類型可能是安全性漏洞，可能會觸發警告[CA2104："](/visualstudio/code-quality/ca2104)不要聲明唯讀可變參考型別。

- 在[`readonly struct`定義](#readonly-struct-example)`readonly`中 ，`struct`表示 不可變。
- 在[`readonly`成員定義](#readonly-member-examples)中`readonly`，指示 的成員`struct`不會更改結構的內部狀態。
- 在[`ref readonly`方法返回](#ref-readonly-return-example)中，`readonly`修飾符指示該方法返回引用，並且不允許寫入該引用。

和`readonly struct``ref readonly`上下文在 C# 7.2 中添加。 `readonly`在 C# 8.0 中添加了結構成員

## <a name="readonly-field-example"></a>唯讀欄位範例

在此示例中，無法在 方法`year``ChangeYear`中更改欄位的值，即使該欄位在類建構函式中分配了值：

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

您只能在下列內容中將值指派給 `readonly` 欄位︰

- 在宣告中初始化變數時，例如︰

  ```csharp
  public readonly int y = 5;
  ```

- 在包含執行個體欄位宣告的類別執行個體建構函式。
- 在包含靜態欄位宣告的類別靜態建構函式。

這些建構函式上下文也是將`readonly`欄位作為[out](out-parameter-modifier.md)或[ref](ref.md)參數傳遞的唯一上下文。

> [!NOTE]
> `readonly` 關鍵字與 [const](const.md) 關鍵字不同。 `const` 欄位只能在欄位的宣告中初始化。 您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。 因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。 此外，當`const`欄位是編譯時間常量時，該`readonly`欄位可用於運行時常量，如以下示例所示：
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

在上述範例中，如果您使用如下範例的陳述式：

```csharp
p2.y = 66;        // Error
```

你會得到編譯器錯誤訊息：

**不能將唯讀欄位分配給（建構函式或變數初始化器除外）**

## <a name="readonly-struct-example"></a>唯讀結構範例

`struct` 定義上的 `readonly` 修飾詞會宣告 struct 是**不可變**。 `struct` 的每個執行個體欄位必須標記為 `readonly`，如下列範例所示：

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

上述範例會使用[唯讀自動屬性](../../properties.md#read-only)來宣告其儲存體。 它會指示編譯器建立 `readonly` 支援這些屬性的欄位。 您也可以直接宣告 `readonly` 欄位：

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

新增未標記 `readonly` 的欄位會產生編譯器錯誤 `CS8340`：「唯讀結構的執行個體欄位必須為唯讀。」

## <a name="readonly-member-examples"></a>唯讀成員示例

其他時候，您可以創建支援突變的結構。 在這些情況下，幾個實例成員可能不會修改結構的內部狀態。 您可以使用`readonly`修飾符聲明這些實例成員。 編譯器強制執行您的意圖。 如果該成員直接修改狀態或訪問未使用`readonly`修飾符聲明的成員，則結果是編譯時間錯誤。 修改`readonly`器對成員有效`struct`，而不是`class``interface`對成員聲明有效。

通過將修改器應用於適用`readonly``struct`的方法，可以獲得兩個優勢。 最重要的是，編譯器強制執行您的意圖。 修改狀態的代碼在`readonly`方法中無效。 編譯器還可以使用`readonly`修改器來啟用性能優化。 當通過`struct``in`引用傳遞大型類型時，如果結構的狀態可能修改，編譯器必須生成防禦性副本。 如果僅`readonly`訪問成員，編譯器可能不會創建防禦性副本。

修飾`readonly`符對 中的大多數成員有效`struct`，包括重寫 中<xref:System.Object?displayProperty=nameWithType>聲明的方法的方法。 有一些限制：

- 不能聲明`readonly`靜態方法或屬性。
- 不能聲明`readonly`建構函式。

您可以將`readonly`修改器添加到屬性或索引子聲明：

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

您還可以將`readonly`修改器添加到屬性或索引子`get`的`set`單個或訪問器：

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

不能將`readonly`修改器添加到屬性和同一屬性的一個或多個訪問器。 同樣的限制也適用于索引子。

編譯器隱式將`readonly`修改器應用於編譯器實現的代碼不修改狀態的自動實現屬性。 它等效于以下聲明：

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

您可以在這些位置添加`readonly`修改器，但它將沒有有意義的效果。 不能將`readonly`修改器添加到自動實現的屬性設置器或讀/寫自動實現的屬性。

## <a name="ref-readonly-return-example"></a>參考唯讀傳回範例

上的`readonly`修飾符`ref return`指示無法修改返回的引用。 下列範例會傳回對來源的參考。 它使用`readonly`修改器指示調用方無法修改原點：

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
傳回的型別不一定得是 `readonly struct`。 可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

您還可以查看語言規範建議：

- [唯讀參考和唯讀結構](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [唯讀結構成員](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [修飾詞](index.md)
- [const](const.md)
- [領域](../../programming-guide/classes-and-structs/fields.md)
