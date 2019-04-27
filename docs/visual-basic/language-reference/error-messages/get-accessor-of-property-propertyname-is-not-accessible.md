---
title: 無法存取屬性 '<propertyname>' 的 'Get' 存取子
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 8fb78f3c14708c79f1910e202287c25a3b2213b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803047"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a>'Get' 存取子的屬性 '\<屬性名稱 >' 不能存取
陳述式來擷取屬性的值，當它並沒有屬性的存取嘗試`Get`程序。  
  
 如果[Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)標示為更嚴格的存取權層級比其[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)，嘗試讀取屬性值無法在下列情況：  
  
-   `Get`陳述式會標示[私人](../../../visual-basic/language-reference/modifiers/private.md)，而且呼叫程式碼是類別或結構定義的屬性之外。  
  
-   `Get`陳述式會標示[Protected](../../../visual-basic/language-reference/modifiers/protected.md)和呼叫的程式碼是不在類別或結構中定義的屬性，也不是在衍生類別中。  
  
-   `Get`陳述式會標示[Friend](../../../visual-basic/language-reference/modifiers/friend.md)而且呼叫程式碼不是處於相同的組件中定義屬性。  
  
 **錯誤 ID:** BC31103  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您可以定義該屬性的原始程式碼控制，請考慮宣告`Get`屬性本身以相同的存取層級的程序。  
  
-   如果您沒有定義屬性的原始程式碼控制，或者您必須限制`Get`程序在多個屬性本身，嘗試移動讀取屬性值的程式碼區域具有更好的存取權的陳述式存取層級屬性。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [如何：宣告混合的存取層級的屬性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
