---
title: 無法存取屬性 '<propertyname>' 的 'Set' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3bc50d6762998ca5d8f445d84c8b698c9f46436f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834461"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a>'Set' 存取子的屬性 '\<屬性名稱 >' 不能存取
陳述式嘗試儲存屬性的值，當它並沒有屬性的存取`Set`程序。  
  
 如果[Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)標示為更嚴格的存取權層級比其[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)，嘗試設定屬性值無法在下列情況：  
  
-   `Set`陳述式會標示[私人](../../../visual-basic/language-reference/modifiers/private.md)，而且呼叫程式碼是類別或結構定義的屬性之外。  
  
-   `Set`陳述式會標示[Protected](../../../visual-basic/language-reference/modifiers/protected.md)和呼叫的程式碼是不在類別或結構中定義的屬性，也不是在衍生類別中。  
  
-   `Set`陳述式會標示[Friend](../../../visual-basic/language-reference/modifiers/friend.md)而且呼叫程式碼不是處於相同的組件中定義屬性。  
  
 **錯誤 ID:** BC31102  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您可以定義該屬性的原始程式碼控制，請考慮宣告`Set`屬性本身以相同的存取層級的程序。  
  
-   如果您沒有定義屬性的原始程式碼控制，或者您必須限制`Set`程序在多個屬性本身，試著將移至具有更好的存取權的程式碼區域中設定屬性值的陳述式存取層級屬性。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [如何：宣告混合的存取層級的屬性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
