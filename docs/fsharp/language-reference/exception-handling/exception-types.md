---
title: 例外狀況類型
description: 瞭解如何定義和使用F#例外狀況類型。
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630321"
---
# <a name="exception-types"></a>例外狀況類型

有兩種類別的例外狀況F#: .net 例外狀況類型F#和例外狀況類型。 本主題描述如何定義和使用F#例外狀況類型。

## <a name="syntax"></a>語法

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>備註

在先前的語法中,*例外狀況類型*是新F#例外狀況類型的名稱, 而*引數類型*代表當您引發這個類型的例外狀況時, 可以提供的引數類型。 您可以使用*引數類型*的元組類型來指定多個引數。

F#例外狀況的一般定義如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

您可以使用`raise`函數來產生此類型的例外狀況, 如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

您可以直接在F# `try...with`運算式的篩選中使用例外狀況類型, 如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

您在中`exception` F#使用關鍵字定義的例外狀況類型, 是繼承自`System.Exception`的新類型。

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況：`raise` 函式](the-raise-function.md)
- [例外狀況階層架構](https://msdn.microsoft.com/library/z4c5tckx.aspx)
