---
title: 單位類型 (F#)
description: "了解 F # 'unit' 型別通常如何使用保留值需要的語言語法所需或預期任何值時的位置。"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1a8c8f74e31c5426a9fb6a7143e9d2ac9a7104c0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="unit-type"></a>單位類型

`unit`類型是類型，指出特定的值; 不存在`unit`類型具有只有單一值，當沒有其他值存在，或是否需要做為預留位置。


## <a name="syntax"></a>語法

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>備註
每個 F # 運算式必須評估為值。 不會產生值感興趣，類型的值，這個值的運算式`unit`用。 `unit`類型類似於`void`C# 和 c + + 等語言中的類型。

`unit`類型具有單一值，而且該值會指出語彙基元所`()`。

值`unit`類型通常用在 F # 的程式設計語言語法，所需有一個值，但所需或預期任何值時，保留位置。 可能的傳回值的範例。`printf`函式。 因為重要的動作`printf`作業發生在函數中，函式沒有傳回實際的值。 因此，傳回的值屬於型別`unit`。

有些建構預期`unit`值。 例如，`do`繫結或最上層模組的任何程式碼必須評估為`unit`值。 編譯器會回報警告時`do`繫結或在模組的最上層的程式碼會產生結果以外`unit`未使用，如下列範例所示的值。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

這項警告是功能性程式設計; 的特性它不會出現在其他.NET 程式設計語言。 在純粹功能的程式中，在其中函式沒有任何副作用，最終的傳回值會是函式呼叫的唯一結果。 因此，當結果會被忽略，就可能發生程式設計錯誤。 雖然 F # 不是純功能性程式設計語言，它是最好的作法是遵循盡可能的功能性程式設計方式。

## <a name="see-also"></a>另請參閱
[基本](primitive-types.md)

[F# 語言參考](index.md)
