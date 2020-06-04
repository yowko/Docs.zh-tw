---
title: 迴圈結構
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403510"
---
# <a name="loop-structures-visual-basic"></a>迴圈結構 (Visual Basic)
Visual Basic 迴圈結構可讓您重複執行一或多行程式碼。 您可以重複迴圈結構中的語句，直到條件為、 `True` `False` 指定的次數，或集合中的每個元素一次為止。  
  
 下圖顯示執行一組語句直到條件變成 true 為止的迴圈結構：  
  
 ![顯示 [...] 的流程圖Until 迴圈。](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a>While 迴圈  
 [ `While` ... `End While` ] 結構會執行一組語句，前提是語句中指定的條件 `While` 是 `True` 。 如需詳細資訊，請參閱[While .。。End While 語句](../../../language-reference/statements/while-end-while-statement.md)。  
  
## <a name="do-loops"></a>Do 迴圈  
 `Do`... `Loop` 結構可讓您測試迴圈結構開頭或結尾的條件。 您也可以指定是否要在條件保留時重複迴圈， `True` 或直到它變成為止 `True` 。 如需詳細資訊，請參閱[Do .。。Loop 語句](../../../language-reference/statements/do-loop-statement.md)。  
  
## <a name="for-loops"></a>For 迴圈  
 `For`... `Next` 結構會以設定的次數執行迴圈。 它會使用迴圈控制變數（也稱為*計數器*）來追蹤重複項。 您可指定此計數器的開始和結束值，也可以選擇性地指定從一個重複到下一個的增加量。 如需詳細資訊，請參閱[For .。。下一個語句](../../../language-reference/statements/for-next-statement.md)。  
  
## <a name="for-each-loops"></a>針對每個迴圈  
 `For Each`... `Next` 結構會針對集合中的每個元素執行一組語句。 您可以指定迴圈控制變數，但是您不需要決定它的開始或結束值。 如需詳細資訊，請參閱[For Each .。。下一個語句](../../../language-reference/statements/for-each-next-statement.md)。  
  
## <a name="see-also"></a>另請參閱

- [控制流程](index.md)
- [決策結構](decision-structures.md)
- [其他控制結構](other-control-structures.md)
- [巢狀控制結構](nested-control-structures.md)
