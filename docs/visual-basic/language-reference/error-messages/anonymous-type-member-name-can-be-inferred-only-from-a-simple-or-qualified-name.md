---
title: 只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: f4f62a9ac97c6dbd8d2426f8bfd17afa66c4001a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
您無法推斷匿名類型成員名稱，從複雜的運算式。  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 如需來源匿名型別可以和無法推斷成員的名稱和類型的詳細資訊，請參閱[How to： 推斷屬性名稱和匿名類型宣告中的型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
 **錯誤 ID:** BC36556  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將運算式指派給成員名稱，如下列程式碼所示：  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
