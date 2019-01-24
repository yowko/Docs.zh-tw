---
title: '&#39;取得&#39;屬性存取子&#39; &lt;propertyname&gt; &#39;不能存取'
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 10b7168ac40ca7c7d696cd63cd823454f404bb94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582210"
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;取得&#39;屬性存取子&#39; &lt;propertyname&gt; &#39;不能存取
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
