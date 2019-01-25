---
title: 前置&#39;。&#39;或&#39;！&#39;只可以出現&#39;與&#39;陳述式
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: e64318d4ececbd887f55a1a202cc2d58c90c8fc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625948"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>前置&#39;。&#39;或&#39;！&#39;只可以出現&#39;與&#39;陳述式
句號 （.） 或驚嘆號 （！） 不深入探討`With`區塊就會發生，而不需要在左邊的運算式。 成員存取 (`.`) 和字典成員存取 (`!`) 需要一個運算式來指定包含該成員的項目。 這必須立刻出現左側的存取子，或做為目標的`With`記錄檔區塊內含成員存取。  
  
 **錯誤 ID:** BC30157  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確認`With`區塊的格式正確。  
  
2.  如果沒有任何`With`區塊中，將運算式加入至定義的項目，包含成員的存取子，會評估的左邊。  
  
## <a name="see-also"></a>另請參閱
- [程式碼中的特殊字元](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
