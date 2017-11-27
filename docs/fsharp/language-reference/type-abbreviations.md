---
title: "類型縮寫 (F#)"
description: "深入了解 F # 類型縮寫來提供型別更有意義的名稱以使程式碼更容易讀取。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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

