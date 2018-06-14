---
title: 物件運算式 (F#)
description: '了解如何使用 F # 物件運算式，當您想要避免額外的程式碼並建立新的所需的額外負荷具名型別。'
ms.date: 05/16/2016
ms.openlocfilehash: fed78e2be52838eedf55759b195696f1210a8a20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564387"
---
# <a name="object-expressions"></a>物件運算式

*物件運算式*是建立動態建立的匿名物件類型的新執行個體的運算式為基礎的現有基底類型、 介面或介面的集合。


## <a name="syntax"></a>語法

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>備註
在先前的語法， *typename*代表現有的類別類型或介面類型。 *型別參數*描述選擇性的泛型型別參數。 *引數*只能用於類別類型，需要建構函式的參數。 *成員定義*基底類別方法的覆寫或實作抽象基底類別或介面的方法。

下列範例會說明許多不同類型的物件運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>使用物件運算式
當您想要避免額外的程式碼，才能建立新的具名類型的額外負荷時，您可以使用物件運算式。 如果您使用物件運算式在程式中建立型別的數目降至最低，您可以減少程式碼行的數目，並避免不必要的型別激增。 而不是建立許多類型，只是為了處理特定的情況下，您可以使用物件運算式，可自訂現有的類型，或提供特定的大小寫的適當實作的介面。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)
