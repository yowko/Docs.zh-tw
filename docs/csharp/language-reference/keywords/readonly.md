---
title: readonly 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 8ecf399e48da12a9dee19bb217b8668c6a53d3ad
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191866"
---
# <a name="readonly-c-reference"></a>readonly (C# 參考)

`readonly` 關鍵字是可以在四個內容中使用的修飾詞：

- 在[欄位宣告](#readonly-field-example)中，`readonly` 表示只有在宣告中或相同類別的建構函式中，才能對欄位進行指派。 可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。 
  
  在此函式結束之後，無法指派 `readonly` 欄位。 此規則對於實數值型別和參考型別有不同的含意：
  
  - 由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。 
  - 由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。 該物件不變。 `readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。 不過，修飾詞並不會防止欄位的實例資料透過唯讀欄位進行修改。

  > [!WARNING]
  > 外部可見的類型若包含屬於可變動參考型別的外部可見唯讀欄位，可能會是安全性弱點，而且可能會觸發警告[CA2104](/visualstudio/code-quality/ca2104) ：「不要宣告唯讀的可變動參考型別」。

- 在 [`readonly struct` 定義](#readonly-struct-example)中，`readonly` 表示 `struct` 是不可變的。
- 在[`readonly` 成員定義](#readonly-member-examples)中，`readonly` 表示 `struct` 的成員不會改變結構的內部狀態。
- 在[`ref readonly` 方法](#ref-readonly-return-example)傳回中，`readonly` 修飾詞表示方法會傳回參考，而且不允許寫入該參考。

`readonly sturct` 和 `ref readonly` 內容已在7.2 中C#新增。 已在8.0 中C#新增 `readonly` 結構成員

## <a name="readonly-field-example"></a>唯讀欄位範例

在此範例中，即使在類別的函式中已指派值，也無法在方法 `ChangeYear`中變更欄位 `year` 的值：

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

您只能在下列內容中將值指派給 `readonly` 欄位︰

- 在宣告中初始化變數時，例如︰

  ```csharp
  public readonly int y = 5;
  ```

- 在包含執行個體欄位宣告的類別執行個體建構函式。
- 在包含靜態欄位宣告的類別靜態建構函式。

這些「檢查程式內容」也是唯一有效傳遞 `readonly` 欄位做為[out](out-parameter-modifier.md)或[ref](ref.md)參數的內容。

> [!NOTE]
> `readonly` 關鍵字與 [const](const.md) 關鍵字不同。 `const` 欄位只能在欄位的宣告中初始化。 您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。 因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。 此外，雖然 `const` 欄位是編譯時間常數，但是 `readonly` 欄位可用於執行階段常數，如下列範例所示：
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

在上述範例中，如果您使用如下範例的陳述式：

```csharp
p2.y = 66;        // Error
```

您會收到編譯器錯誤訊息：

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

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

## <a name="readonly-member-examples"></a>Readonly 成員範例

有時候，您可以建立支援變動的結構。 在這些情況下，有數個實例成員可能不會修改結構的內部狀態。 您可以使用 `readonly` 修飾詞來宣告這些實例成員。 編譯器會強制執行您的意圖。 如果該成員直接修改狀態，或存取未使用 `readonly` 修飾詞宣告的成員，則結果會是編譯時期錯誤。 `readonly` 修飾詞在 `struct` 成員上有效，而不是 `class` 或 `interface` 成員宣告。

將 `readonly` 修飾詞套用至適用的 `struct` 方法，即可獲得兩個優點。 最重要的是，編譯器會強制執行您的意圖。 修改狀態的程式碼在 `readonly` 方法中無效。 編譯器也可以使用 `readonly` 修飾詞來啟用效能優化。 `in` 參考傳遞大型 `struct` 類型時，如果結構的狀態可能會遭到修改，則編譯器必須產生防禦性複本。 如果只存取 `readonly` 的成員，編譯器可能不會建立防禦性複本。

`readonly` 修飾詞在 `struct`的大多數成員上有效，包括覆寫 <xref:System.Object?displayProperty=nameWithType>中宣告之方法的方法。 有一些限制：

- 您不能宣告 `readonly` 的靜態成員。
- 您不能宣告 `readonly` 的函式。

您可以將 `readonly` 修飾詞加入至屬性或索引子宣告：

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

您也可以將 `readonly` 修飾詞新增至屬性或索引子的個別 `get` 或 `set` 存取子：

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

您不能將 `readonly` 修飾詞加入屬性，以及該相同屬性存取子的一個或多個。 相同的限制適用于索引子。

編譯器會隱含地將 `readonly` 修飾詞套用至自動實作用的屬性，其中編譯器所執行的程式碼不會修改狀態。 它相當於下列宣告：

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

您可以在這些位置加入 `readonly` 修飾詞，但不會有任何意義的效果。 您不能將 `readonly` 修飾詞加入自動執行的屬性 setter 或讀取/寫入自動實作為屬性。

## <a name="ref-readonly-return-example"></a>參考唯讀傳回範例

`ref return` 上的 `readonly` 修飾詞表示無法修改傳回的參考。 下列範例會傳回對來源的參考。 它會使用 `readonly` 修飾詞來指出呼叫端無法修改來源：

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
傳回的型別不一定得是 `readonly struct`。 可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

您也可以查看語言規格提案：

- [readonly ref 和 readonly 結構](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [readonly 結構成員](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [修飾詞](modifiers.md)
- [const](const.md)
- [欄位](../../programming-guide/classes-and-structs/fields.md)
