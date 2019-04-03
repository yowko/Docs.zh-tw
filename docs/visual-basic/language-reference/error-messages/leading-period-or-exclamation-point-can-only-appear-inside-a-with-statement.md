---
title: 前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 4821dbab90eec3c99c0996e8bff10d51b5a8f99d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824945"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現
句號 （.） 或驚嘆號 （！） 不深入探討`With`區塊就會發生，而不需要在左邊的運算式。 成員存取 (`.`) 和字典成員存取 (`!`) 需要一個運算式來指定包含該成員的項目。 這必須立刻出現左側的存取子，或做為目標的`With`記錄檔區塊內含成員存取。  
  
 **錯誤 ID:** BC30157  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確認`With`區塊的格式正確。  
  
2.  如果沒有任何`With`區塊中，將運算式加入至定義的項目，包含成員的存取子，會評估的左邊。  
  
## <a name="see-also"></a>另請參閱

- [程式碼中的特殊字元](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
