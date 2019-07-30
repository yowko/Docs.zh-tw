---
title: 單位類型
description: F#瞭解「單位」類型通常用來存放語言語法在不需要任何值或需要時需要值的位置。
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630170"
---
# <a name="unit-type"></a>單位類型

類型是一種類型, 表示沒有特定的值。此`unit`類型只有單一值, 當沒有其他值存在或需要時, 會做為預留位置。 `unit`

## <a name="syntax"></a>語法

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>備註

每F#個運算式都必須評估為值。 若為不會產生相關值的運算式, 則會使用類型`unit`的值。 類型類似于C#和`void` C++等語言中的類型。 `unit`

此`unit`類型具有單一值, 且該值是由標記`()`表示。

`unit`類型的值通常用於程式F#設計, 以保存語言語法需要值的位置, 但不需要或不需要任何值時。 範例可能是`printf`函數的傳回值。 因為作業的重要動作`printf`會在函式中發生, 所以函式不需要傳回實際的值。 因此, 傳回值的類型`unit`為。

某些結構預期會`unit`有值。 例如, 位於模組`do`最上層的系結或任何程式碼, 都應該評估`unit`為值。 當模組最上層的系結`do`或程式碼產生的結果`unit`不是未使用的值時, 編譯器會報告警告, 如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

此警告是功能性程式設計的特性;它不會出現在其他 .NET 程式設計語言中。 在純粹功能的程式中, 函式沒有任何副作用, 最後傳回的值是函式呼叫的唯一結果。 因此, 忽略結果時, 可能是程式設計錯誤。 雖然F#不是純粹的功能性程式設計語言, 但最好是盡可能遵循功能性程式設計風格。

## <a name="see-also"></a>另請參閱

- [橢圓](primitive-types.md)
- [F# 語言參考](index.md)
