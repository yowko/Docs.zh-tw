---
title: 內嵌函式 (F#)
description: '了解如何使用 F # 內嵌函式，會直接整合至呼叫的程式碼。'
ms.date: 05/16/2016
ms.openlocfilehash: d265f9b4e828946c510bd8e84b14d5236ab511fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563502"
---
# <a name="inline-functions"></a>內嵌函式

*內嵌函式*會直接整合呼叫程式碼的函式。


## <a name="using-inline-functions"></a>使用內嵌函式
當您使用靜態型別參數時，會參數化的型別參數的任何函式必須是內嵌。 這可確保編譯器可以解決這些型別參數。 當您使用一般的泛型型別參數時，沒有任何這類限制。

不能使用成員條件約束，內嵌函式可以在最佳化程式碼很有幫助。 不過，內嵌函式的過度使用，可能會造成較不能抵抗編譯器最佳化和程式庫函式的實作中變更您的程式碼。 基於這個理由，您應該避免使用內嵌函式的最佳化，除非您已嘗試所有其他的最佳化技術。 進行函式或方法的內嵌有時可以改善效能，但是並非永遠案例。 因此，您也應該使用的效能度量來驗證，讓任何指定的函式內嵌事實上有正面的影響。

`inline`修飾詞可以套用至函式的最上層，在模組層級，或類別中方法層級。

下列程式碼範例說明在最上層、 內嵌執行個體方法和內嵌的靜態方法的內嵌函式。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a>內嵌函式和類型推斷
與否`inline`影響型別推斷。 這是因為內嵌函式可以以統計方式解析型別參數，而非內嵌函式不能。 下列程式碼範例示範案例其中`inline`很有用，因為您使用的函式具有以統計方式解析的型別參數，`float`轉換運算子。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

不含`inline`修飾詞，型別推斷會強制函式，以在此情況下接受特定型別， `int`。 但`inline`修飾詞，此函式也被推斷為具有以統計方式解析的型別參數。 與`inline`修飾詞，類型就會推斷是如下所示：

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

這表示函式接受任何類型的支援轉換成**float**。


## <a name="see-also"></a>另請參閱
[函式](index.md)

[條件約束](../generics/constraints.md)

[以統計方式解析的類型參數](../generics/statically-resolved-type-parameters.md)
