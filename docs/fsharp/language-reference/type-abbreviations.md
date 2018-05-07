---
title: 類型縮寫 (F#)
description: '深入了解 F # 類型縮寫來提供型別更有意義的名稱以使程式碼更容易讀取。'
ms.date: 05/16/2016
ms.openlocfilehash: cd0b2365aecc5d5b73df95a4b94ae4dd8327446d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="type-abbreviations"></a>類型縮寫

A*類型縮寫*是別名或替代名稱的類型。

## <a name="syntax"></a>語法

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a>備註
您可以使用類型縮寫來提供型別更有意義的名稱，以使程式碼更容易讀取。 您也可以使用它們建立易於使用，否則會寫出麻煩型別的名稱。此外，您可以讓您更輕鬆地變更的基礎類型，而不需要變更使用類型的所有程式碼使用類型縮寫。 以下是簡單類型縮寫。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

類型縮寫可以包含泛型參數，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

先前的程式碼，`Transform`是代表任何類型的單一引數的函式類型縮寫，並傳回該相同類型的單一值。

類型縮寫不會保留在.NET Framework MSIL 程式碼。 因此，當您使用 F # 組件從另一種.NET Framework 語言，您必須使用的基礎類型縮寫的類型名稱。

類型縮寫也可用在測量單位。 如需詳細資訊，請參閱[測量單位](units-of-measure.md)。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

