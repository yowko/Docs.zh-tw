---
title: "do 繫結 (F#)"
description: "了解如何 F # 'do' 繫結用來執行程式碼，但未定義函式或值。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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

