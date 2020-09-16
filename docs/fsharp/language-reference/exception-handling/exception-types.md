---
title: 例外狀況類型
description: '瞭解如何定義和使用 F # 例外狀況類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 8b4ceec31a2d68abbcd025812ffeeefc0c090efb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557225"
---
# <a name="exception-types"></a>例外狀況類型

F # 中有兩種例外狀況類別： .NET 例外狀況類型和 F # 例外狀況類型。 本主題說明如何定義和使用 F # 例外狀況類型。

## <a name="syntax"></a>語法

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>備註

在先前的語法中， *例外狀況類型* 是新 F # 例外狀況類型的名稱，而 *引數類型* 代表當您引發此類型的例外狀況時，可以提供的引數類型。 您可以使用 *引數*類型的元組類型來指定多個引數。

F # 例外狀況的一般定義如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

您可以使用函數來產生此類型的例外狀況 `raise` ，如下所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

您可以直接在運算式中的篩選準則中使用 F # 例外狀況類型 `try...with` ，如下列範例所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

您使用 F # 中的關鍵字定義的例外狀況類型 `exception` 是繼承自的新類型 `System.Exception` 。

## <a name="see-also"></a>另請參閱

- [例外狀況處理](index.md)
- [例外狀況：`raise` 函式](the-raise-function.md)
- [例外狀況階層](../../../standard/exceptions/index.md)
