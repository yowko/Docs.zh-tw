---
title: Null 值
description: '瞭解如何在 F # 程式設計語言中使用 null 值。'
ms.date: 08/15/2020
ms.openlocfilehash: 3b2c7ebe7b8eff08f7c3e76b9715ccab1bbd5d36
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558344"
---
# <a name="null-values"></a>Null 值

本主題說明如何在 F # 中使用 null 值。

## <a name="null-value"></a>Null 值

Null 值通常不會用於 F # 中的值或變數。 不過，在某些情況下，null 會顯示為異常值。 如果類型是在 F # 中定義，除非將 [AllowNullLiteral](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-allownullliteralattribute.html#Value) 屬性套用至類型，否則不允許使用 null 作為一般值。 如果類型是以其他 .NET 語言定義，null 是可能的值，而且當您與這類型別互通時，F # 程式碼可能會遇到 null 值。

針對 F # 中定義且嚴格地使用 f # 的型別，直接使用 F # 程式庫建立 null 值的唯一方法是使用 [Unchecked unchecked.defaultof](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators-unchecked.html#defaultof) 或 [array2d.zerocreate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate)。 不過，針對從其他 .NET 語言使用的 F # 類型，或如果您使用的是不是以 F # 撰寫的 API （例如 .NET Framework），則可能會發生 null 值。

您可以使用 `option` F # 中的型別，因為您可能會在另一個 .net 語言中使用具有可能 null 值的參考變數。 `option`如果沒有任何物件，則您可以使用選項值（如果沒有物件），而不是 null `None` 。 `Some(obj)`當有物件時，您可以使用選項值與物件 `obj` 。 如需詳細資訊，請參閱[選項](../options.md)。 請注意，如果是，則您仍然可以 `null` 將值封裝至選項中 `Some x` `x` `null` 。 因此，當值為時，請務必使用此 `None` 值 `null` 。

`null`關鍵字是 F # 語言中的有效關鍵字，當您使用以其他 .net 語言撰寫的 .NET Framework api 或其他 api 時，您必須使用此關鍵字。 在兩種情況下，您可能需要 null 值，就是當您呼叫 .NET API 並將 null 值當作引數傳遞時，以及當您從 .NET 方法呼叫中解讀傳回值或輸出參數時。

若要將 null 值傳遞至 .NET 方法，只需在 `null` 呼叫程式碼中使用關鍵字。 下列程式碼範例會說明這點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

若要解讀從 .NET 方法取得的 null 值，請使用模式比對（如果可以的話）。 下列程式碼範例示範如何使用模式比對來解讀 `ReadLine` 當它嘗試讀取超過輸入資料流程結尾時所傳回的 null 值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

F # 類型的 Null 值也可以使用其他方式產生，例如，當您使用時，會 `Array.zeroCreate` 呼叫 `Unchecked.defaultof` 。 您必須小心使用這類程式碼，以將 null 值保持封裝。 在僅供 F # 使用的程式庫中，您不需要在每個函式中檢查是否有 null 值。 如果您要撰寫與其他 .NET 語言交互操作的程式庫，您可能必須加入 null 輸入參數的檢查並擲回 `ArgumentNullException` ，就像在 c # 或 Visual Basic 程式碼中所做的一樣。

您可以使用下列程式碼來檢查任意值是否為 null。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>另請參閱

- [值](index.md)
- [比對運算式](../match-expressions.md)
