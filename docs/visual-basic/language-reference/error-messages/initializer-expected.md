---
title: 必須是初始設定式
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 13fa8917f228661fc44f5e0920d91c596e250c38
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402833"
---
# <a name="initializer-expected"></a>必須是初始設定式
您嘗試使用物件初始化運算式來宣告類別的實例，其中的初始設定清單是空的，如下列範例所示。  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 至少必須在初始化運算式清單中初始化一個欄位或屬性，如下列範例所示。  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **錯誤識別碼：** BC30996  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 在初始化運算式中至少初始化一個欄位或屬性，或不要使用物件初始化運算式。  
  
## <a name="see-also"></a>另請參閱

- [物件初始設定式：具名和匿名型別](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [如何：使用物件初始設定式宣告物件](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
