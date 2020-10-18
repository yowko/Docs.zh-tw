---
title: "'#ElseIf' 之前必須搭配相對應的 '#If' 或 '#ElseIf'"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 142c142afe0d9be0ecd4d8a0340f0f1957b20470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162774"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>BC30014： ' #ElseIf ' 之前必須搭配相對應的 ' #If ' 或 ' #ElseIf '

`#ElseIf` 是條件式編譯指示詞。 `#ElseIf`子句之前必須搭配相對應的 `#If` 或 `#ElseIf` 子句。

 **錯誤識別碼：** BC30014

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 請檢查中間的 `#If` `#ElseIf` `#ElseIf` 條件式編譯區塊或未正確放置之前的或尚未與此分隔 `#End If` 。

2. 如果 `#ElseIf` 之前是指示詞 `#Else` ，請移除 `#Else` 或將它變更為 `#ElseIf` 。

3. 如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。

## <a name="see-also"></a>另請參閱

- [#If .。。Then ... #Else 指示詞](../directives/if-then-else-directives.md)
