---
title: 類型縮寫 (F#)
description: '深入了解 F # 類型縮寫可以提供更有意義的名稱以使程式碼更容易讀取。'
ms.date: 05/16/2016
ms.openlocfilehash: 259cd6c84e22fc7c98e08255d3e0ded5b87af352
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678382"
---
# <a name="type-abbreviations"></a>類型縮寫

A*類型縮寫*是別名或替代名稱的型別。

## <a name="syntax"></a>語法

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>備註

您可以使用類型縮寫可以提供更有意義的名稱，以使程式碼更容易讀取。 您也可以使用它們來建立簡單易用的類型，否則就會很麻煩，寫出名稱。此外，您可以使用類型縮寫，讓您更輕鬆地變更的基礎類型，而不需要變更使用類型的所有程式碼。 以下是簡單類型縮寫。

類型縮寫的存取範圍預設為`public`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

類型縮寫可以包含一般的參數，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

在先前的程式碼`Transform`是類型縮寫表示接受任何類型的單一引數的函式並傳回該相同型別的單一值。

在.NET Framework MSIL 程式碼中，不會保留類型縮寫。 因此，當您使用 F # 組件從另一種.NET Framework 語言，您必須使用類型縮寫的基礎類型名稱。

類型縮寫也可用的量值單位上。 如需詳細資訊，請參閱 <<c0> [ 量值單位](units-of-measure.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
