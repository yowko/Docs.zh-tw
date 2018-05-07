---
title: do 繫結 (F#)
description: "了解如何 F # 'do' 繫結用來執行程式碼，但未定義函式或值。"
ms.date: 05/16/2016
ms.openlocfilehash: 6fd084090a204beab0da1c2deb5b5ae2a86281c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="do-bindings"></a>do 繫結

A`do`繫結會用來執行程式碼，但未定義函式或值。 此外，請勿繫結可以是在類別中使用，請參閱[`do`類別中的繫結](../members/do-bindings-in-classes.md)。


## <a name="syntax"></a>語法

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>備註
使用`do`繫結，當您想要執行的函式或值的定義獨立的程式碼。 中的運算式`do`繫結必須傳回`unit`。 程式碼中的最上層`do`模組初始化時，會執行繫結。 關鍵字`do`是選擇性的。

屬性可以套用至最上層`do`繫結。 例如，如果您的程式使用 COM interop，您可能要套用`STAThread`屬性加入您的程式。 您可以使用屬性上`do`繫結，如下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a>另請參閱
[F# 語言參考](../index.md)

[函式](index.md)

