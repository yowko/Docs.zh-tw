---
title: 內嵌函式
description: 瞭解如何使用F#直接整合到呼叫程式碼中的內嵌函式。
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630673"
---
# <a name="inline-functions"></a>內嵌函式

*內嵌*函式是直接整合到呼叫程式碼中的函式。

## <a name="using-inline-functions"></a>使用內嵌函數

當您使用靜態類型參數時, 以類型參數參數化的任何函式都必須是內嵌的。 這可保證編譯器可以解析這些型別參數。 當您使用一般泛型型別參數時, 沒有這類限制。

除了啟用成員條件約束以外, 內嵌函數也有助於優化程式碼。 不過, 過度利用內嵌函式可能會導致您的程式碼較不能抵抗編譯器優化和程式庫函式的變更。 基於這個理由, 您應該避免使用內嵌函式進行優化, 除非您已經嘗試過所有其他的優化技術。 讓函式或方法內嵌的作業有時可以改善效能, 但不一定都是如此。 因此, 您也應該使用效能測量來確認讓任何指定的函式內嵌確實具有正面的效果。

`inline`修飾詞可以套用至最上層的函式、模組層級, 或類別中的方法層級。

下列程式碼範例說明最上層的內嵌函式、內嵌實例方法, 以及內嵌的靜態方法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>內嵌函式和型別推斷

的存在`inline`會影響型別推斷。 這是因為內嵌函式可以有靜態解析的類型參數, 而非內嵌函數則不能。 下列`inline`程式碼範例顯示的案例很有用`float` , 因為您使用的函式具有靜態解析的類型參數, 也就是轉換運算子。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

如果沒有`int`修飾詞, 型別推斷會強制函式採用特定的型別, 在此案例中為。 `inline` 但是使用`inline`修飾詞時, 函式也會推斷為具有靜態解析的類型參數。 `inline`使用修飾詞時, 會推斷型別, 如下所示:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

這表示函式會接受任何支援轉換成**float**的類型。

## <a name="see-also"></a>另請參閱

- [函式](index.md)
- [條件約束](../generics/constraints.md)
- [以統計方式解析的類型參數](../generics/statically-resolved-type-parameters.md)
