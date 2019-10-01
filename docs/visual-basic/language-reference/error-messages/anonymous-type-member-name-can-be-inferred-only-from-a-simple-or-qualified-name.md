---
title: 只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: 38f669fe183ac79ebed6e5a122bc70aedc9bb753
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701219"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>只能從不含引數的簡單或限定名稱來推斷匿名類型成員名稱
您無法從複雜運算式推斷匿名型別成員名稱。  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 如需匿名型別可以和無法推斷成員名稱和類型之來源的詳細資訊，請參閱 @no__t 0How 至：在匿名型別宣告中推斷屬性名稱和類型 @ no__t-0。  
  
 **錯誤識別碼：** BC36556  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將運算式指派給成員名稱，如下列程式碼所示：  
  
    ```vb  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>另請參閱

- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [如何：在匿名型別宣告中推斷屬性名稱和類型 @ no__t-0
