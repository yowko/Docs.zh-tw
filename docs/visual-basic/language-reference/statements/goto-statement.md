---
title: GoTo 陳述式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a>GoTo 陳述式
無條件分支的程序中指定的行。  
  
## <a name="syntax"></a>語法  
  
```  
GoTo line  
```  
  
## <a name="part"></a>組件  
 `line`  
 必要項。 任何行標籤。  
  
## <a name="remarks"></a>備註  
 `GoTo`陳述式只能將程式分支中的程序中的行。 行必須擁有行加上標籤的`GoTo`可以參考。 如需詳細資訊，請參閱[How to： 標籤陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
> [!NOTE]
>  `GoTo`陳述式會讓程式碼難以讀取和維護。 您應該盡可能改用控制結構。 如需詳細資訊，請參閱[控制流程](../../../visual-basic/programming-guide/language-features/control-flow/index.md)。  
  
 您無法使用`GoTo`陳述式來從外部的分支`For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`，或`Using`...`End Using`建構內的標籤。  
  
## <a name="branching-and-try-constructions"></a>分支，然後再次嘗試語法結構  
 內`Try`...`Catch`...`Finally`建構，下列規則適用於與分支`GoTo`陳述式。  
  
|區塊或地區|分支中從外部|從內部往外分支|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`區塊|只能從`Catch`相同建構區塊<sup>1</sup>|只在整個建構之外|  
|`Catch`區塊|不允許|僅外部整個建構，或為`Try`相同建構區塊<sup>1</sup>|  
|`Finally`區塊|不允許|不允許|  
  
 <sup>1</sup>如果一個`Try`...`Catch`...`Finally`建構，巢狀`Catch`區塊可以分支到`Try`區塊在它自己的巢狀層級，而不用到任何其他`Try`區塊。 巢狀`Try`...`Catch`...`Finally`建構必須完全在包含`Try`或`Catch`建構巢狀所在的區塊。  
  
 下圖顯示一個`Try`建構巢狀方式置於另一個。 兩個建構區塊之間的不同分支就會表示成有效或無效。  
  
 ![Try 語法結構的分支示意圖](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Try 語法結構的有效和無效的分支  
  
## <a name="example"></a>範例  
 下列範例會使用`GoTo`分支到程序中的線條標籤的陳述式。  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Select...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
