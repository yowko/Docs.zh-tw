---
title: GoTo 陳述式 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 5e7aa036f632b4c310c4978d0d684c1222d2b096
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125560"
---
# <a name="goto-statement"></a>GoTo 陳述式
無條件分支到程序中指定的行。  
  
## <a name="syntax"></a>語法  
  
```  
GoTo line  
```  
  
## <a name="part"></a>組件  
 `line`  
 必要項。 任何行標籤。  
  
## <a name="remarks"></a>備註  
 `GoTo`陳述式只可以分支在程序中出現的行。 列必須有標籤的列`GoTo`可以參考。 如需詳細資訊，請參閱[如何：標記陳述式](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
> [!NOTE]
>  `GoTo` 陳述式可以讓程式碼難以閱讀和維護。 可能的話，請改為使用控制結構。 如需詳細資訊，請參閱 <<c0> [ 控制流程](../../../visual-basic/programming-guide/language-features/control-flow/index.md)。  
  
 您無法使用`GoTo`陳述式，以從外部的分支`For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`，或`Using`...`End Using`建構內的標籤。  
  
## <a name="branching-and-try-constructions"></a>分支，然後再試語法結構  
 內`Try`...`Catch`...`Finally`建構，下列規則適用於使用分支`GoTo`陳述式。  
  
|區塊或地區|分支中從外部|從內往外分支|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` 區塊|只能從`Catch`相同的建構區塊<sup>1</sup>|只為整個建構之外|  
|`Catch` 區塊|永遠不允許|只之外的整個建構，或是`Try`相同的建構區塊<sup>1</sup>|  
|`Finally` 區塊|永遠不允許|永遠不允許|  
  
 <sup>1</sup>如果`Try`...`Catch`...`Finally`建構巢狀在另一個`Catch`區塊可以分支到`Try`區塊，在它自己的巢狀層級，但不是到任何其他`Try`區塊。 巢狀`Try`...`Catch`...`Finally`建構必須完全在包含`Try`或`Catch`建構巢狀所在的區塊。  
  
 下圖顯示一個`Try`建構巢狀在另一個。 在兩個建構的區塊之間的各種分支會表示成有效或無效。  
  
 ![Try 語法結構中的分支示意圖](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>範例  
 下列範例會使用`GoTo`分支到程序中的線條標籤的陳述式。  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>另請參閱
- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
