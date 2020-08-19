---
title: 延遲運算式
description: '瞭解 F # 延遲運算式如何改善應用程式和程式庫的效能。'
ms.date: 08/15/2020
ms.openlocfilehash: 71c466ca3b74c9e92b81a3c268e07438ec944905
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558084"
---
# <a name="lazy-expressions"></a>延遲運算式

*延遲運算式* 是不會立即評估的運算式，而是在需要結果時進行評估。 這有助於提升程式碼的效能。

## <a name="syntax"></a>語法

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>備註

在先前的語法中， *expression* 是只有在需要結果時才會評估的程式碼，而 *identifier* 是儲存結果的值。 值的型別為 [`Lazy<'T>`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazy-1-0.html) ，其中使用的實際型別取決於 `'T` 運算式的結果。

延遲運算式可讓您藉由將運算式的執行限制在需要結果的情況下，來改善效能。

若要強制執行運算式，您可以呼叫方法 `Force` 。 `Force` 只會執行一次執行。 後續呼叫 `Force` 會傳回相同的結果，但不會執行任何程式碼。

下列程式碼說明如何使用 lazy 運算式和使用 `Force` 。 在此程式碼中，的型別 `result` 為 `Lazy<int>` ，而且方法會傳回 `Force` `int` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

延遲評估（但不 `Lazy` 是類型）也用於序列。 如需詳細資訊，請參閱 [序列](sequences.md)。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [LazyExtensions 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
