---
title: 內嵌函式 (F#)
description: '了解如何使用 F # 內嵌函式會直接整合至呼叫端程式碼。'
ms.date: 05/16/2016
ms.openlocfilehash: 47fca0fe34630792aeb0908b0cee02a927e2567d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685669"
---
# <a name="inline-functions"></a>內嵌函式

*內嵌函式*是會直接整合至呼叫端程式碼的函式。

## <a name="using-inline-functions"></a>使用內嵌函式

當您使用靜態型別參數時，則為型別參數所參數化的任何函式必須是內嵌。 這可確保編譯器可以解決這些型別參數。 當您使用一般的泛型型別參數時，但也沒有任何這類限制。

不會啟用之成員的條件約束，內嵌函式能幫助您最佳化程式碼。 不過，過度使用的內嵌函式可能會導致您的程式碼，是較能抵抗編譯器最佳化和程式庫函式的實作中的變更。 基於這個理由，您應該避免使用內嵌函式的最佳化，除非您已試過所有其他的最佳化技術。 進行內嵌的函式或方法有時可以改善效能，但這不一定如此。 因此，您也應該使用的效能度量來驗證，讓任何指定的函式內嵌事實上有正面的影響。

`inline`修飾詞可以套用至函式的最上層，在模組層級或類別中的方法層級。

下列程式碼範例說明在最高層級、 內嵌執行個體方法和內嵌的靜態方法的內嵌函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>內嵌函式和型別推斷

是否存在`inline`影響型別推斷。 這是因為內嵌函式可以以統計方式解析型別參數，而非內嵌函式不能。 下列程式碼範例所示的範例位置`inline`很有用，因為您使用具有以統計方式解析的類型參數的函式`float`轉換運算子。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

不含`inline`修飾詞，型別推斷會強制函式，在此情況下採用特定的型別， `int`。 但`inline`修飾詞，此函式也推斷為具有以統計方式解析的型別參數。 使用`inline`修飾詞，型別推斷為下列：

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

這表示函式會接受任何支援的轉換的型別**浮點數**。

## <a name="see-also"></a>另請參閱

- [函式](index.md)
- [條件約束](../generics/constraints.md)
- [以統計方式解析的類型參數](../generics/statically-resolved-type-parameters.md)
