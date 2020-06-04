---
title: readonly 關鍵字 - C# 參考
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 66a096e8831f72a2216e8ba5dd9866046504624f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368617"
---
# <a name="readonly-c-reference"></a>readonly (C# 參考)

`readonly`關鍵字是可以在四個內容中使用的修飾詞：

- 在[欄位](#readonly-field-example)宣告中， `readonly` 表示對欄位的指派只會當做宣告的一部分，或在相同類別的函式中發生。 可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。
  
  在 `readonly` 此函式結束之後，無法指派欄位。 此規則對於實數值型別和參考型別有不同的含意：
  
  - 由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。
  - 由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。 該物件不變。 `readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。 不過，修飾詞並不會防止欄位的實例資料透過唯讀欄位進行修改。

  > [!WARNING]
  > 外部可見的類型若包含屬於可變動參考型別的外部可見唯讀欄位，可能會是安全性弱點，而且可能會觸發警告[CA2104](/visualstudio/code-quality/ca2104) ：「不要宣告唯讀的可變動參考型別」。

- 在 `readonly struct` 型別定義中， `readonly` 表示結構型別是不可變的。 如需詳細資訊，請參閱[結構類型](../builtin-types/struct.md)一文的[ `readonly` 結構](../builtin-types/struct.md#readonly-struct)一節。
- 在結構型別內的實例成員宣告中， `readonly` 表示實例成員不會修改結構的狀態。 如需詳細資訊，請參閱[結構類型](../builtin-types/struct.md)一文的[ `readonly` 實例成員](../builtin-types/struct.md#readonly-instance-members)一節。
- 在[ `ref readonly` 方法](#ref-readonly-return-example)傳回中， `readonly` 修飾詞表示方法會傳回參考，而且不允許寫入該參考。

`readonly struct`和內容 `ref readonly` 是以 c # 7.2 加入。 `readonly`結構成員已新增至 c # 8。0

## <a name="readonly-field-example"></a>唯讀欄位範例

在此範例中，即使在類別的函式中 `year` `ChangeYear` 已指派一個值，也無法在方法中變更欄位的值：

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

您只能在下列內容中將值指派給 `readonly` 欄位︰

- 在宣告中初始化變數時，例如︰

  ```csharp
  public readonly int y = 5;
  ```

- 在包含執行個體欄位宣告的類別執行個體建構函式。
- 在包含靜態欄位宣告的類別靜態建構函式。

這些「檢查程式內容」也是唯一有效傳遞 `readonly` 欄位做為[out](out-parameter-modifier.md)或[ref](ref.md)參數的內容。

> [!NOTE]
> `readonly` 關鍵字與 [const](const.md) 關鍵字不同。 `const` 欄位只能在欄位的宣告中初始化。 您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。 因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。 此外，當 `const` 欄位是編譯時間常數時， `readonly` 欄位可用於執行時間常數，如下列範例所示：
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

在上述範例中，如果您使用如下範例的陳述式：

```csharp
p2.y = 66;        // Error
```

您會收到編譯器錯誤訊息：

**無法指派 readonly 欄位（除非在函式或變數初始化運算式中）**

## <a name="ref-readonly-return-example"></a>參考唯讀傳回範例

`readonly`上的修飾詞 `ref return` 表示無法修改傳回的參考。 下列範例會傳回對來源的參考。 它會使用 `readonly` 修飾詞來表示呼叫端無法修改來源：

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

傳回的型別不一定得是 `readonly struct`。 可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

您也可以查看語言規格提案：

- [readonly ref 和 readonly 結構](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [readonly 結構成員](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 關鍵字](index.md)
- [修飾詞](index.md)
- [const](const.md)
- [欄位](../../programming-guide/classes-and-structs/fields.md)
