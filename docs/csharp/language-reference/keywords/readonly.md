---
title: readonly 關鍵字 - C# 參考
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389050"
---
# <a name="readonly-c-reference"></a>readonly (C# 參考)

關鍵字`readonly`是可在四個上下文中使用的修飾元:

- 在[欄位聲明中](#readonly-field-example),`readonly`指示對欄位的分配只能作為聲明的一部分或在同一類中的構造函數中進行。 可以在欄位宣告及建構函式中指派及多次重新指派 readonly 欄位。
  
  建構`readonly`函數退出後無法分配欄位。 這個規則對值型態和參考類型具有不同的含義:
  
  - 由於實值型別會直接包含其資料，因此具有 `readonly` 實值型別的欄位是不可變的。
  - 由於參考型別包含針對其資料的參考，因此 `readonly` 參考型別的欄位必須一律參考相同的物件。 那個物件不是不變的。 `readonly` 修飾詞可防止欄位被不同的參考型別執行個體取代。 但是,修改器不會阻止通過唯讀欄位修改欄位的實例數據。

  > [!WARNING]
  > 包含外部可見唯讀欄位(即可變引用類型)的外部可見類型可能是安全漏洞,可能會觸發警告[CA2104:"](/visualstudio/code-quality/ca2104)不要聲明唯讀可變引用類型。

- 在類型`readonly struct`定義中`readonly`, 指示結構類型不可變。 有關詳細資訊,請參閱[`readonly`](../builtin-types/struct.md#readonly-struct)[結構類型](../builtin-types/struct.md)文章的結構部分。
- 在結構類型的實體成員聲明中,`readonly`指示實體成員不修改結構的狀態。 有關詳細資訊,請參閱[結構類型](../builtin-types/struct.md)文章的[`readonly`實例成員](../builtin-types/struct.md#readonly-instance-members)部分。
- 在[`ref readonly`方法返回](#ref-readonly-return-example)中`readonly`, 修飾符指示該方法返回引用,並且不允許寫入該引用。

和`readonly struct``ref readonly`上下文在 C# 7.2 中添加。 `readonly`在 C# 8.0 新增結構成員

## <a name="readonly-field-example"></a>唯讀欄位範例

此範例中,無法在方法`year``ChangeYear`中更改欄位的值,即使該欄位在類構造函數中分配了值:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

您只能在下列內容中將值指派給 `readonly` 欄位︰

- 在宣告中初始化變數時，例如︰

  ```csharp
  public readonly int y = 5;
  ```

- 在包含執行個體欄位宣告的類別執行個體建構函式。
- 在包含靜態欄位宣告的類別靜態建構函式。

這些建構函數上下文也是將`readonly`欄位作為[out](out-parameter-modifier.md)或[ref](ref.md)參數傳遞的唯一上下文。

> [!NOTE]
> `readonly` 關鍵字與 [const](const.md) 關鍵字不同。 `const` 欄位只能在欄位的宣告中初始化。 您可以在欄位宣告及任何建構函式中，多次指派 `readonly` 欄位。 因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。 此外,當`const`欄位是編譯時間常量時,`readonly`該 欄位可用於運行時常量,如以下範例所示:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

在上述範例中，如果您使用如下範例的陳述式：

```csharp
p2.y = 66;        // Error
```

你會得到編譯器錯誤訊息:

**無法將唯讀字段配置給(建構函數或變數初始化器除外)**

## <a name="ref-readonly-return-example"></a>參考唯讀傳回範例

上的`readonly`修飾符`ref return`指示無法修改返回的引用。 下列範例會傳回對來源的參考。 它使用`readonly`變更器指示呼叫者無法修改原點:

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

傳回的型別不一定得是 `readonly struct`。 可由 `ref` 傳回的任何類型，都可以由 `ref readonly` 傳回。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

您還可以檢視語言規格建議:

- [唯讀參考和唯讀結構](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [唯讀結構成員](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 編程指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [修飾詞](index.md)
- [const](const.md)
- [欄位](../../programming-guide/classes-and-structs/fields.md)
