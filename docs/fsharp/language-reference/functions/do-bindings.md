---
title: do 繫結
description: 瞭解如何使用F# 「do」系結來執行程式碼, 而不需要定義函數或值。
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630534"
---
# <a name="do-bindings"></a>do 繫結

`do`系結是用來執行程式碼, 而不需要定義函式或值。 此外, 您可以在類別中使用系結, 請參閱[ `do`類別中的](../members/do-bindings-in-classes.md)系結。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>備註

`do`當您想要獨立執行函式或值定義以外的程式碼時, 請使用系結。 系結中`do`的運算式`unit`必須傳回。 當模組初始化時, 會`do`執行最上層系結中的程式碼。 關鍵字`do`是選擇性的。

屬性可以套用至最上層`do`系結。 例如, 如果您的程式使用 COM Interop, 您可能會想要將`STAThread`屬性套用至您的程式。 您可以使用系結上`do`的屬性來執行此動作, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](../index.md)
- [函式](index.md)
