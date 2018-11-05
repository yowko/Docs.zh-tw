---
title: Null 值 (F#)
description: '了解 F # 程式設計語言中使用 null 值的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: 8751ac402c43ddb07fb62e08b6c6d5403cbe9acc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43787893"
---
# <a name="null-values"></a>Null 值

本主題說明 F # 中使用 null 值的方式。

## <a name="null-value"></a>Null 值

Null 值不通常是 F # 中的值或變數。 不過，null 會出現在某些情況下異常值。 如果類型定義在 F # 中，允許 null 的不是標準值除非[AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)屬性會套用至型別。 如果類型定義某些其他.NET 語言中，null 是可能值，而 F # 程式碼時您會在這種型別與交互操作，可能會遇到 null 值。

在 F # 中定義，用於從 F # 是型別，建立 null 值，直接使用 F # 程式庫的唯一方式是使用[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)或是[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)。 不過，F # 型別，會使用從其他.NET 語言，或如果您使用該類型不以 F # 中，例如.NET Framework 撰寫的 api 可能會發生 null 值。

您可以使用`option`F # 中會使用最可能的 null 值，另一種.NET 語言的參考變數的類型。 而不是 null，使用 F #`option`類型，您使用的選項值`None`是否有任何物件。 您使用的選項值`Some(obj)`的物件`obj`物件時。 如需詳細資訊，請參閱 <<c0> [ 選項](../options.md)。

`null`關鍵字是有效的關鍵字，在 F # 語言中，而且您必須使用.NET Framework Api 或以另一種.NET 語言所撰寫的其他 Api 時，請使用它。 當您呼叫.NET API，並做為引數，傳遞 null 值，並當您解譯傳回的值或.NET 方法呼叫的輸出參數時，就會是兩個，您可能需要 null 值的情況。

若要將 null 值傳遞至.NET 方法，只要使用`null`呼叫程式碼中的關鍵字。 下列程式碼範例會說明這點。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

若要解譯取自於.NET 方法的 null 值，使用模式比對，如果可以的話。 下列程式碼範例示範如何使用將從傳回的 null 值的模式比對`ReadLine`當它嘗試讀取超過結尾的輸入資料流。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

F # 類型的 null 值也可能以其他方式，例如當您使用會產生`Array.zeroCreate`，其會呼叫`Unchecked.defaultof`。 您必須小心這類的程式碼，以保留封裝的 null 值。 在僅供 F # 程式庫，您不必檢查每個函式中的 null 值。 如果您正在撰寫的程式庫與其他.NET 語言的交互操作，您可能必須新增 null 檢查輸入參數，則擲回`ArgumentNullException`，就像您在 C# 或 Visual Basic 程式碼中。

您可以使用下列程式碼來檢查是否為任意值為 null。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>另請參閱

- [值](index.md)
- [比對運算式](../match-expressions.md)
