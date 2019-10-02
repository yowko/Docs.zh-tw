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
ms.openlocfilehash: a2a5ab99ff68e6dce783a2fd986ee6e8c15ae858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701167"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>沒有類別的明確執行個體，因此無法從共用方法或共用成員初始設定式中參考至類別的執行個體成員
您已嘗試從共用的程式中參考類別的非共用成員。 下列範例示範這種情況。  
  
```vb  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 在上述範例中，指派語句 `x = 10` 會產生這個錯誤訊息。 這是因為共用程式嘗試存取執行個體變數。  
  
 變數 `x` 是實例成員，因為它並未宣告為[Shared](../../../visual-basic/language-reference/modifiers/shared.md)。 類別的每個實例 `sample` 都包含自己的個別變數 `x`。 當某個實例設定或變更 `x` 的值時，不會影響任何其他實例中 `x` 的值。  
  
 不過，在類別 `sample` 的所有實例中，`setX` 的程式 `Shared`。 這表示它不會與類別的任何一個實例相關聯，而是獨立于個別實例運作。 因為它沒有與特定實例的連接，所以 `setX` 無法存取執行個體變數。 它必須只在 `Shared` 變數上運作。 當 `setX` 設定或變更共用變數的值時，該新值可供類別的所有實例使用。  
  
 **錯誤識別碼：** BC30369  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 決定您是否要在類別的所有實例之間共用成員，或為每個實例保留個人。  
  
2. 如果您想要在所有實例之間共用成員的單一複本，請將 `Shared` 關鍵字加入至成員宣告。 在程式宣告中保留 `Shared` 關鍵字。  
  
3. 如果您想要讓每個實例擁有其本身的個別複本，請勿針對成員宣告指定 `Shared`。 請從程式宣告中移除 `Shared` 關鍵字。  
  
## <a name="see-also"></a>另請參閱

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
