---
title: '&#39; #ElseIf &#39;之前必須搭配相對應的 &#39; #If &#39;或 &#39; #ElseIf &#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b3a4e809e1108fcd6e116538a1947057e9548ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39; #ElseIf &#39;之前必須搭配相對應的 &#39; #If &#39;或 &#39; #ElseIf &#39;
`#ElseIf`是條件式編譯指示詞。 `#ElseIf`子句之前必須搭配相對應的`#If`或`#ElseIf`子句。  
  
 **錯誤 ID:** BC30014  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查前面`#If`或`#ElseIf`不已從這個分開`#ElseIf`使用介入條件式編譯區塊或不正確地放置`#End If`。  
  
2.  如果`#ElseIf`前面加上`#Else`指示詞，則移除`#Else`或將它變更為`#ElseIf`。  
  
3.  如果一切狀況良好，請將 `#If` 指示詞加入條件式編譯區塊的開頭。  
  
## <a name="see-also"></a>另請參閱  
 [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
