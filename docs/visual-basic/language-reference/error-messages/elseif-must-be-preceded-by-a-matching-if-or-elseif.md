---
title: "'#ElseIf' 之前必須搭配相對應的 '#If' 或 '#ElseIf'"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: d6fa76b2aba45e3455cef6ceafc0f737ef56225d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271547"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>'#ElseIf' 之前必須搭配相對應的 '#If' 或 '#ElseIf'
`#ElseIf` 是條件式編譯指示詞。 `#ElseIf`子句之前必須搭配相對應`#If`或`#ElseIf`子句。  
  
 **錯誤 ID:** BC30014  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查前面`#If`或`#ElseIf`不已從這個分隔`#ElseIf`藉由使用介入條件式編譯區塊或不正確地放置`#End If`。  
  
2.  如果`#ElseIf`前面加上`#Else`指示詞，則移除`#Else`或將它變更為`#ElseIf`。  
  
3.  如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。  
  
## <a name="see-also"></a>另請參閱
- [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
