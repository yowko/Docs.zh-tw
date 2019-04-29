---
title: 例外狀況類型
description: 了解如何定義和使用F#例外狀況類型。
ms.date: 05/16/2016
ms.openlocfilehash: ed721dd0dc46a486fafeac2fa4c096800995ccb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772719"
---
# <a name="exception-types"></a>例外狀況類型

有兩種類別中的例外狀況的F#:.NET 例外狀況類型和F#例外狀況類型。 本主題描述如何定義和使用F#例外狀況類型。

## <a name="syntax"></a>語法

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>備註

在先前語法中，*例外狀況型別*的新名稱F#例外狀況類型，和*引數型別*表示當您提高此類型的例外狀況時可以提供引數的類型。 您可以指定多個引數使用的是 tuple 型別*引數型別*。

一般定義F#例外狀況如下所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

您可以使用來產生此類型的例外狀況`raise`函式，，如下所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

您可以使用F#直接在中的篩選器中的例外狀況型別`try...with`運算式，如下列範例所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

您定義的例外狀況類型`exception`關鍵字，在F#是新的型別繼承自`System.Exception`。

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況：`raise` 函式](the-raise-function.md)
- [例外狀況階層架構](https://msdn.microsoft.com/library/z4c5tckx.aspx)