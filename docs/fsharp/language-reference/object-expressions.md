---
title: 物件運算式 (F#)
description: '了解如何使用 F # 物件運算式，當您想要避免額外的程式碼和建立新的所需的額外負荷具名型別。'
ms.date: 05/16/2016
ms.openlocfilehash: 1a971044d680d3bf5a6fff38affdaf001d5403b4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865458"
---
# <a name="object-expressions"></a>物件運算式

*物件運算式*是建立以動態方式建立、 匿名物件類型的新執行個體的運算式為基礎的現有基底型別、 介面或介面的集合。

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

在先前的語法*typename*代表現有的類別類型或介面型別。 *類型-params*描述的選擇性的泛型類型參數。 *引數*僅用於需要建構函式參數的類別類型。 *成員定義*覆寫基底類別方法，或從基底類別或介面的抽象方法的實作。

下列範例會說明許多不同類型的物件運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>使用物件運算式

當您想要避免額外的程式碼，才能建立新的具名類型的額外負荷時，您可以使用物件運算式。 如果您使用物件運算式在程式中建立的類型數目降到最低時，您可以減少程式碼行的數目，並避免不必要的激增的型別。 不需要建立許多類型只可處理特定的情況下，您可以使用自訂現有的型別或手邊的特定案例提供適當的介面實作的物件運算式。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
