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
ms.openlocfilehash: aad068b5857eb956ded63fa2a57cb163d3cf5c58
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322689"
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
  
 在上述範例中，指派陳述式`x = 10`會產生此錯誤訊息。 這是因為共用的程序嘗試存取執行個體變數。  
  
 變數`x`是執行個體成員，因為它未宣告為[共用](../../../visual-basic/language-reference/modifiers/shared.md)。 每個類別執行個體`sample`包含它自己的個別變數`x`。 當某個執行個體設定或變更的值`x`，它不會影響值`x`中任何其他執行個體。  
  
 不過，此程序`setX`已`Shared`類別的所有執行個體之間`sample`。 這表示它不是類別的任何一個執行個體相關聯，但而不是個別的執行個體獨立運作。 因為它有沒有特定的執行個體，連接`setX`無法存取執行個體變數。 它必須只在運作`Shared`變數。 當`setX`設定或變更共用的變數，新的值可供類別的所有執行個體的值。  
  
 **錯誤 ID:** BC30369  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 決定是否要在類別中的所有執行個體之間共用或保留每個執行個體的個別成員。  
  
2. 如果您想要在所有執行個體之間共用之成員的單一複本，新增`Shared`成員宣告的關鍵字。 保留`Shared`程序宣告中的關鍵字。  
  
3. 如果您想要有自己的個別複本成員的每個執行個體時，請勿指定`Shared`成員宣告。 移除`Shared`從程序宣告的關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
