---
title: 延遲運算 (F#)
description: '了解 F # 延遲運算如何改善您的應用程式和程式庫的效能。'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744611"
---
# <a name="lazy-computations"></a>延遲運算

*延遲運算*是指不會立即進行評估，但會改為評估，當需要結果時。 這可協助改善您的程式碼的效能。

## <a name="syntax"></a>語法

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>備註

在先前語法中，*運算式*是結果為必要項時，才會評估的程式碼並*識別碼*是將結果儲存的值。 值為類型[ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)，其中的實際型別用於`'T`會從運算式的結果來決定。

延遲運算可讓您藉由限制執行的計算結果為所需的情況來改善效能。

若要強制執行計算，您可以呼叫方法`Force`。 `Force` 會導致執行一次只能執行。 後續呼叫`Force`傳回相同結果，但不是執行任何程式碼。

下列程式碼示範使用的延遲計算，以及使用`Force`。 在此程式碼的型別`result`已`Lazy<int>`，而`Force`方法會傳回`int`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

延遲評估，而非`Lazy`類型，也可用於序列。 如需詳細資訊，請參閱 <<c0> [ 序列](sequences.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [LazyExtensions 模組](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
