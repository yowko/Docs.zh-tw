---
title: "'#ElseIf' 之前必須搭配相對應的 '#If' 或 '#ElseIf'"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 808cf35fb05da092cdef560721b2f667778aa78f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409656"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>'#ElseIf' 之前必須搭配相對應的 '#If' 或 '#ElseIf'
`#ElseIf` 是條件式編譯指示詞。 `#ElseIf`子句之前必須搭配相對應的 `#If` 或 `#ElseIf` 子句。  
  
 **錯誤識別碼：** BC30014  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請檢查前面的 `#If` 或尚未 `#ElseIf` `#ElseIf` 由中間條件式編譯區塊與此分隔，或不正確地放置 `#End If` 。  
  
2. 如果 `#ElseIf` 前面加上指示詞 `#Else` ，請移除， `#Else` 或將它變更為 `#ElseIf` 。  
  
3. 如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。  
  
## <a name="see-also"></a>另請參閱

- [#If .。。Then ... #Else 指示詞](../directives/if-then-else-directives.md)
