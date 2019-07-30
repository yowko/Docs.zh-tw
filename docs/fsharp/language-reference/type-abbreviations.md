---
title: 類型縮寫
description: 瞭解F#類型縮寫, 為類型提供更有意義的名稱, 以便讓程式碼更容易閱讀。
ms.date: 05/16/2016
ms.openlocfilehash: 339b22a675e3f1ad8a3da207053e611942b55a22
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630209"
---
# <a name="type-abbreviations"></a>類型縮寫

*類型縮寫*是類型的別名或替代名稱。

## <a name="syntax"></a>語法

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>備註

您可以使用類型縮寫來為類型提供更有意義的名稱, 以便讓程式碼更容易閱讀。 您也可以使用它們來建立容易使用的名稱, 以用於不需要寫出的其他類型。此外, 您可以使用類型縮寫, 讓變更基礎類型變得更容易, 而不需要變更使用該類型的所有程式碼。 以下是簡單的類型縮寫。

縮寫類型的存取範圍預設`public`為。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

類型縮寫可以包含泛型參數, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

在先前的程式碼`Transform`中, 是類型縮寫, 代表接受任何類型的單一引數, 並傳回該相同類型之單一值的函式。

類型縮寫不會保留在 .NET Framework 的 MSIL 程式碼中。 因此, 當您使用另F#一個 .NET Framework 語言的元件時, 您必須使用基礎類型名稱做為類型縮寫。

類型縮寫也可以用在測量單位上。 如需詳細資訊, 請參閱[測量單位](units-of-measure.md)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
