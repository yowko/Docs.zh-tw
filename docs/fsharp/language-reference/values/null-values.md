---
title: Null 值
description: 了解如何將 null 值會在F#程式設計語言。
ms.date: 05/16/2016
ms.openlocfilehash: 58c54065a98a84c4d4e912cbc42d59cfea8c6de1
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610992"
---
# <a name="null-values"></a>Null 值

本主題描述如何將 null 值會在F#。

## <a name="null-value"></a>Null 值

Null 值通常不使用在F#的值或變數。 不過，null 會出現在某些情況下異常值。 如果類型定義在F#，除非，做為一般的值不允許 null [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)屬性會套用至型別。 Null 的型別定義於其他.NET 語言中，如果是可能的值，您會使用這種類型時，交互操作時，您F#程式碼可能會遇到 null 值。

中定義的類型為F#和使用嚴格地從F#，唯一的方法來建立 null 值，使用F#程式庫是直接使用[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)或[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)。 不過，對於F#類型，可從其他.NET 語言，或如果您使用該類型的 api，不以F#，例如.NET Framework 中，可能會發生 null 值。

您可以使用`option`中輸入F#當您可能使用參考變數，最可能的 null 值，另一種.NET 語言。 而不是 null，使用F#`option`類型，您使用的選項值`None`如果沒有任何物件。 您使用的選項值`Some(obj)`的物件`obj`物件時。 如需詳細資訊，請參閱 <<c0> [ 選項](../options.md)。

`null`關鍵字是有效的關鍵字，在F#語言，而您必須使用.NET Framework Api 或以另一種.NET 語言所撰寫的其他 Api 時，請使用它。 當您呼叫.NET API，並做為引數，傳遞 null 值，並當您解譯傳回的值或.NET 方法呼叫的輸出參數時，就會是兩個，您可能需要 null 值的情況。

若要將 null 值傳遞至.NET 方法，只要使用`null`呼叫程式碼中的關鍵字。 下列程式碼範例會說明這點。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

若要解譯取自於.NET 方法的 null 值，使用模式比對，如果可以的話。 下列程式碼範例示範如何使用將從傳回的 null 值的模式比對`ReadLine`當它嘗試讀取超過結尾的輸入資料流。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Null 值的F#類型也可能以其他方式，例如當您使用會產生`Array.zeroCreate`，其會呼叫`Unchecked.defaultof`。 您必須小心這類的程式碼，以保留封裝的 null 值。 僅適用於文件庫中F#，您就不必在檢查每個函式中的 null 值。 如果您正在撰寫的程式庫與其他.NET 語言的交互操作，您可能必須新增 null 檢查輸入參數，則擲回`ArgumentNullException`，就像您在 C# 或 Visual Basic 程式碼中。

您可以使用下列程式碼來檢查是否為任意值為 null。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>另請參閱

- [值](index.md)
- [比對運算式](../match-expressions.md)