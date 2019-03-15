---
title: 延遲的運算式
description: 了解如何F#延遲運算式可以改善您的應用程式和程式庫的效能。
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57853320"
---
# <a name="lazy-expressions"></a>延遲的運算式

*延遲運算式*是不會立即進行評估，但改為會在需要結果時所評估的運算式。 這可協助改善您的程式碼的效能。

## <a name="syntax"></a>語法

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>備註

在先前語法中，*運算式*是結果為必要項時，才會評估的程式碼並*識別碼*是將結果儲存的值。 值為類型[ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)，其中的實際型別用於`'T`會從運算式的結果來決定。

延遲的運算式可讓您藉由限制執行的運算式結果所需的情況來改善效能。

若要強制執行的運算式，您可以呼叫方法`Force`。 `Force` 會導致執行一次只能執行。 後續呼叫`Force`傳回相同結果，但不是執行任何程式碼。

下列程式碼說明如何使用消極式運算式以及使用`Force`。 在此程式碼的型別`result`已`Lazy<int>`，而`Force`方法會傳回`int`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

延遲評估，而非`Lazy`類型，也可用於序列。 如需詳細資訊，請參閱 <<c0> [ 序列](sequences.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [LazyExtensions 模組](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
