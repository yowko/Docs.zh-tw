---
title: 只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: b798f296b62b51de34a7ec5ce5a8b608273f5748
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751523"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
您無法推斷匿名類型成員名稱，從複雜的運算式。  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 如需匿名型別可以和無法推斷成員名稱和類型的來源的詳細資訊，請參閱[How to:推斷屬性名稱和匿名類型宣告中的型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
 **錯誤 ID:** BC36556  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 為成員的名稱，指派運算式，如下列程式碼所示：  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>另請參閱

- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [如何：推斷屬性名稱和匿名類型宣告中的類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
