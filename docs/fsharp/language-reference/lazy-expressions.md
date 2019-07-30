---
title: 延遲運算式
description: 瞭解延遲F#運算式如何改善應用程式和程式庫的效能。
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630746"
---
# <a name="lazy-expressions"></a>延遲運算式

*延遲運算式*是不會立即評估的運算式, 而是在需要結果時進行評估。 這有助於改善程式碼的效能。

## <a name="syntax"></a>語法

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>備註

在先前的語法中, *expression*是只在需要結果時才會評估的程式碼, 而*identifier*則是儲存結果的值。 值的型[`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)別為, 其中`'T`用於的實際型別是從運算式的結果決定。

延遲運算式可讓您藉由將運算式的執行限制為只需要結果的情況, 來改善效能。

若要強制執行運算式, 請呼叫方法`Force`。 `Force`導致執行只執行一次。 後續呼叫`Force`會傳回相同的結果, 但不會執行任何程式碼。

下列程式碼說明如何使用延遲運算式和使用`Force`。 在此`result`程式碼中, 的型`Lazy<int>`別是, `Force` `int`而方法會傳回。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

延遲評估 (但不`Lazy`是類型) 也會用於序列。 如需詳細資訊, 請參閱[序列](sequences.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [LazyExtensions 模組](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
