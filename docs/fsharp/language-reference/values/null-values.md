---
title: Null 值 (F#)
description: '了解如何使用 F # 程式語言中的 null 值。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 8d302cc78c5de582f58c6f9b9dea7b23ee7ddfea
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="null-values"></a>Null 值

本主題描述如何使用 F # 中的 null 值。


## <a name="null-value"></a>Null 值
Null 值已不正常 F # 中使用的值或變數。 不過，null 會顯示為在某些情況下的異常值。 如果類型定義在 F # 中，允許 null 的不是標準值除非[AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)屬性套用至類型。 如果類型定義在其他.NET 語言中，null 是可能值，且當您進行交互操作，使用這類的類型，F # 程式碼可能會遇到 null 值。

在 F # 中定義和使用嚴格地從 F # 類型建立 null 值，並直接使用 F # 程式庫的唯一方式是使用[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)或[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)。 不過，F # 型別，會使用其他.NET 語言，或如果您正在使用在 F # 中，例如.NET Framework 中，不會寫入應用程式開發介面中的該類型可能會發生 null 值。

您可以使用`option`F # 中會使用參考變數與另一種.NET 語言中可能的 null 值的類型。 而不是 null，F #`option`類型，您使用的選項值`None`如果沒有任何物件。 您使用的選項值`Some(obj)`物件`obj`物件時。 如需詳細資訊，請參閱[選項](../options.md)。

`null`關鍵字是有效的關鍵字，在 F # 語言中，而且您必須使用.NET Framework 應用程式開發介面或其他以另一種.NET 語言撰寫的應用程式開發介面時，請使用它。 您可能需要 null 值的兩個情況是當您呼叫.NET API，並做為引數，傳遞 null 值，而且當您解譯傳回的值或輸出參數從.NET 方法呼叫時。

若要傳遞 null 值的.NET 方法，只要使用`null`呼叫的程式碼中的關鍵字。 下列程式碼範例會說明這點。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

若要解譯 null 值取自.NET 方法，使用模式比對，如果可以的話。 下列程式碼範例示範如何使用模式比對，解譯傳回的 null 值`ReadLine`當它嘗試讀取的輸入資料流結尾。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

F # 類型的 null 值，也可以產生以其他方式，例如當您使用`Array.zeroCreate`，而它會呼叫`Unchecked.defaultof`。 您必須非常小心這類程式碼，以保留封裝 null 值。 在僅供 F # 程式庫，您不必檢查每個函式中的 null 值。 如果您正在撰寫的程式庫的其他.NET 語言進行交互操作，您可能必須新增檢查 null 輸入參數，則擲回`ArgumentNullException`，就像您在 C# 或 Visual Basic 程式碼中執行。

您可以使用下列程式碼來檢查是否為 null 的任意值。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>另請參閱
[值](index.md)

[比對運算式](../match-expressions.md)
