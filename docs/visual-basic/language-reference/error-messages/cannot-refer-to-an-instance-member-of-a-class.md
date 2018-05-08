---
title: 沒有類別的明確執行個體，因此無法從共用方法或共用成員初始設定式中參考至類別的執行個體成員
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: 368539ed24d9819c8d1ddbbb9e3e0dff21d27c32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>沒有類別的明確執行個體，因此無法從共用方法或共用成員初始設定式中參考至類別的執行個體成員
您嘗試參考非共用的成員共用的程序內的類別。 下列範例會示範這種情況。  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 在上述範例中，指派陳述式`x = 10`會產生此錯誤訊息。 這是因為共用的程序正嘗試存取的執行個體變數。  
  
 變數`x`是執行個體成員，因為它未宣告為[共用](../../../visual-basic/language-reference/modifiers/shared.md)。 每個類別執行個體`sample`包含它自己的個別變數`x`。 當某個執行個體設定或變更的值`x`，不會影響值`x`中任何其他執行個體。  
  
 不過，此程序`setX`是`Shared`類別的所有執行個體之間`sample`。 這表示它不是類別的任何一個執行個體相關聯，但而是會與個別的執行個體無關。 因為它有特定的執行個體，與連線`setX`無法存取的執行個體變數。 它必須只在運作`Shared`變數。 當`setX`設定或變更共用的變數，新的值可供類別的所有執行個體的值。  
  
 **錯誤 ID:** BC30369  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  決定您是否想要的類別，所有執行個體之間共用或保留每個執行個體的個別成員。  
  
2.  如果您想要在所有執行個體之間共用之成員的單一複本時，新增`Shared`成員宣告的關鍵字。 保留`Shared`程序宣告中的關鍵字。  
  
3.  如果您想要有自己的個別複本成員的每個執行個體時，請勿指定`Shared`成員宣告。 移除`Shared`程序宣告中的關鍵字。  
  
## <a name="see-also"></a>另請參閱  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
