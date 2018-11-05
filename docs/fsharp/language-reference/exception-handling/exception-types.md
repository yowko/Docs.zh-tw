---
title: 例外狀況類型 (F#)
description: 了解如何定義及使用 F# 例外狀況類型。
ms.date: 05/16/2016
ms.openlocfilehash: b8d648a3649153a3604856deb61ce41db8c40bf2
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858817"
---
# <a name="exception-types"></a>例外狀況類型

有兩種類別的 F# 中的例外狀況：.NET 例外狀況型別和 F# 例外狀況類型。 本主題描述如何定義及使用 F# 例外狀況類型。

## <a name="syntax"></a>語法

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>備註

在先前的語法*例外狀況型別*是新的 F# 例外狀況類型、 名稱和*引數型別*表示當您提高此類型的例外狀況時可以提供引數的類型。 您可以指定多個引數使用的是 tuple 型別*引數型別*。

F# 例外狀況的一般定義，如下所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

您可以使用來產生此類型的例外狀況`raise`函式，，如下所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

您可以直接在中的篩選條件中使用 F# 例外狀況型別`try...with`運算式，如下列範例所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

您定義的例外狀況類型`exception`F# 中的關鍵字是新的類型繼承自`System.Exception`。

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況：`raise` 函式](the-raise-function.md)
- [例外狀況階層架構](https://msdn.microsoft.com/library/z4c5tckx.aspx)
