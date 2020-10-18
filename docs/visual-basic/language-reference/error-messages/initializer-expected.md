---
title: 必須是初始設定式
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: cbe77bab3e4f8bf2094c70c1c16d95ee897c729e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163008"
---
# <a name="bc30996-initializer-expected"></a>BC30996：需要初始化運算式

您已嘗試使用物件初始化運算式宣告類別的實例，其中的初始化清單是空的，如下列範例所示。

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 必須在初始化運算式清單中初始化至少一個欄位或屬性，如下列範例所示。

 `Dim aStudent As New Student With {.year = "Senior"}`

 **錯誤識別碼：** BC30996

## <a name="to-correct-this-error"></a>更正這個錯誤

- 在初始化運算式中至少初始化一個欄位或屬性，或不要使用物件初始化運算式。

## <a name="see-also"></a>另請參閱

- [物件初始設定式：具名和匿名型別](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [如何：使用物件初始設定式宣告物件](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
