---
title: "&#39;設定 &#39;存取子屬性 &#39;&lt;propertyname&gt;&#39; 不能存取"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords: BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9256a09b719ad3890e1d7c2cc23ffb0d40eec62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a>&#39;設定 &#39;存取子屬性 &#39;&lt;propertyname&gt;&#39; 不能存取
陳述式嘗試儲存屬性的值，它並沒有存取權的屬性時`Set`程序。  
  
 如果[Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)標示為更具限制性的存取層級比其[Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)，嘗試設定屬性值，可能會失敗，在下列情況：  
  
-   `Set`陳述式會標示[私人](../../../visual-basic/language-reference/modifiers/private.md)，而且呼叫程式碼是類別或結構定義的屬性之外。  
  
-   `Set`陳述式會標示[保護](../../../visual-basic/language-reference/modifiers/protected.md)和呼叫的程式碼是不在類別或結構中定義的屬性，也不是在衍生類別中。  
  
-   `Set`陳述式會標示[Friend](../../../visual-basic/language-reference/modifiers/friend.md)和呼叫的程式碼不是相同的組件中定義屬性。  
  
 **錯誤 ID:** BC31102  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   如果您有定義該屬性的原始程式碼控制，請考慮宣告`Set`屬性本身相同的存取層級的程序。  
  
-   如果您沒有定義屬性的原始程式碼控制，或您必須限制`Set`程序在多個屬性本身，嘗試將移至具有更好的存取權的程式碼的區域設定的屬性值的陳述式存取層級屬性。  
  
## <a name="see-also"></a>另請參閱  
 [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [如何：宣告混合存取層級的屬性](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
