---
title: 延遲運算 (F#)
description: '了解 F # 延遲運算如何改善您的應用程式和程式庫的效能。'
ms.date: 05/16/2016
ms.openlocfilehash: 1c4eb6ab247c44a04a9d145185e2de7ec01b8e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563928"
---
# <a name="lazy-computations"></a>延遲運算

*延遲運算*是指不會立即進行評估，但會改為評估需要結果時。 這可協助改善您的程式碼的效能。

## <a name="syntax"></a>語法

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>備註

在先前的語法，*運算式*是程式碼，只有當結果為必要項，會評估和*識別碼*是將結果儲存的值。 值為類型[ `Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)其中的實際型別、 用於`'T`取決於運算式的結果。

延遲運算可讓您藉由限制的計算結果都需要這些情況下執行改善效能。

若要強制執行計算，您可以呼叫方法`Force`。 `Force` 會執行一次只能執行。 後續呼叫`Force`傳回相同結果，但不是執行任何程式碼。

下列程式碼說明如何使用延遲的計算，以及使用`Force`。 在此程式碼的型別`result`是`Lazy<int>`，而`Force`方法會傳回`int`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

延遲評估，但不是`Lazy`類型，也會使用序列 (sequence)。 如需詳細資訊，請參閱[序列](sequences.md)。

## <a name="see-also"></a>另請參閱

[F# 語言參考](index.md)

[LazyExtensions 模組](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
