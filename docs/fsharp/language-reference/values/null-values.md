---
title: Null 值
description: 瞭解如何在程式F#設計語言中使用 null 值。
ms.date: 03/22/2019
ms.openlocfilehash: 2038c0a461fec9884c51edd50c3c9f336104e30e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630811"
---
# <a name="null-values"></a>Null 值

本主題描述如何在中F#使用 null 值。

## <a name="null-value"></a>Null 值

Null 值通常不會用於F#值或變數。 不過, 在某些情況下, null 會顯示為異常值。 如果類型定義于中F#, 除非將[AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)屬性套用至類型, 否則不允許使用 null 做為一般值。 如果類型是以其他 .NET 語言定義, null 是可能的值, 而當您與這類類型互通時, 您的F#程式碼可能會遇到 null 值。

針對F#中定義且完全使用的類型F#, 使用連結F#庫直接建立 null 值的唯一方法是使用[unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)或[array.zerocreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)。 不過, 針對從F#其他 .net 語言使用的類型, 或如果您使用該類型搭配未寫入F#的 API (例如 .NET Framework, 則可能會出現 null 值)。

當您可能在`option`另一個F# .net 語言中使用具有可能 null 值的參考變數時, 可以使用中的類型。 若不是 null, F# `option`則使用類型, 如果沒有物件, `None`您可以使用選項值。 當有物件時, `Some(obj)`您可以使用`obj`選項值搭配物件。 如需詳細資訊，請參閱[選項](../options.md)。 請注意`null` , 如果 (for `Some x`) `x`剛好是`null`, 您仍然可以將值封裝成一個選項。 因此, 當值為`None` `null`時, 請務必使用。

關鍵字是F#語言中的有效關鍵字, 而且當您使用以其他 .net 語言撰寫的 .NET Framework api 或其他 api 時, 您必須使用它。 `null` 當您呼叫 .NET API 並傳遞 null 值做為引數, 以及從 .NET 方法呼叫解讀傳回值或輸出參數時, 這兩種情況下, 您可能會需要 null 值。

若要將 null 值傳遞給 .net 方法, 只要在呼叫`null`程式碼中使用關鍵字即可。 下列程式碼範例會說明這點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

若要解讀從 .NET 方法取得的 null 值, 請使用模式比對 (如果可以的話)。 下列程式碼範例示範如何使用模式比對, 來解讀`ReadLine`當它嘗試讀取超過輸入資料流程的結尾時, 所傳回的 null 值。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

類型的F# Null 值也可以用其他方式產生, 例如當您使用`Array.zeroCreate`時, 會呼叫。 `Unchecked.defaultof` 您必須謹慎處理這類程式碼, 才能將 null 值封裝起來。 在僅供使用的F#程式庫中, 您不需要在每個函式中檢查是否有 null 值。 如果您要撰寫與其他 .net 語言互通的程式庫, 您可能必須新增 null 輸入參數的檢查, 並擲`ArgumentNullException`回, 就如同您在或 Visual Basic 程式碼中C#所做的一樣。

您可以使用下列程式碼來檢查任意值是否為 null。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>另請參閱

- [值](index.md)
- [比對運算式](../match-expressions.md)
