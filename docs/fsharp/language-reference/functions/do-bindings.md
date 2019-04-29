---
title: do 繫結
description: 了解如何F#'do' 繫結用來執行程式碼，而不需定義的函式或值。
ms.date: 05/16/2016
ms.openlocfilehash: d29f8557fda06097d2e85748ab6286f0415730b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683375"
---
# <a name="do-bindings"></a>do 繫結

A`do`繫結會用來執行程式碼，而不需定義的函式或值。 此外，執行繫結可以是在類別中使用，請參閱[`do`類別中的繫結](../members/do-bindings-in-classes.md)。

## <a name="syntax"></a>語法

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>備註

使用`do`繫結，當您想要執行的函式或值的定義獨立的程式碼。 中的運算式`do`繫結必須傳回`unit`。 在最上層的程式碼`do`模組初始化時，會執行繫結。 關鍵字`do`是選擇性的。

屬性可以套用至最上層`do`繫結。 比方說，如果您的程式使用 COM interop，您可能想要套用`STAThread`屬性設定為您的程式。 您可以使用屬性上`do`繫結，如下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>另請參閱

- [F# 語言參考](../index.md)
- [函式](index.md)