---
title: 單位類型
description: F#瞭解「單位」類型通常用來存放語言語法在不需要任何值或需要時需要值的位置。
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424035"
---
# <a name="unit-type"></a>單位類型

`unit` 類型是表示沒有特定值的類型。`unit` 類型只有單一值，當沒有其他值存在或需要時，它會作為預留位置。

## <a name="syntax"></a>語法

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>備註

每F#個運算式都必須評估為值。 若為不會產生相關值的運算式，則會使用 `unit` 類型的值。 `unit` 類型類似于C#和C++等語言中的 `void` 類型。

`unit` 類型具有單一值，且該值是由權杖 `()`所表示。

`unit` 類型的值通常用來進行程式F#設計，以保存語言語法需要值的位置，但不需要任何值或需要時。 範例可能是 `printf` 函數的傳回值。 因為 `printf` 作業的重要動作會在函式中發生，所以函式不需要傳回實際的值。 因此，傳回值的類型為 `unit`。

某些結構預期會有 `unit` 值。 例如，`do` 系結或模組最上層的任何程式碼，都應該評估為 `unit` 值。 當模組最上層的 `do` 系結或程式碼產生的結果不是未使用的 `unit` 值時，編譯器會報告警告，如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

此警告是功能性程式設計的特性;它不會出現在其他 .NET 程式設計語言中。 在純粹功能的程式中，函式沒有任何副作用，最後傳回的值是函式呼叫的唯一結果。 因此，忽略結果時，可能是程式設計錯誤。 雖然F#不是純粹的功能性程式設計語言，但最好是盡可能遵循功能性程式設計風格。

## <a name="see-also"></a>請參閱

- [橢圓](basic-types.md)
- [F# 語言參考](index.md)
