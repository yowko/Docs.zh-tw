---
title: GoTo 陳述式
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
ms.openlocfilehash: 000f6754575bcce6b2d79d85541e755219aca956
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866623"
---
# <a name="goto-statement"></a>GoTo 陳述式

無條件地分支至程式中的指定行。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>組件  

 `line`  
 必要。 任何行標籤。  
  
## <a name="remarks"></a>備註  

 `GoTo`語句只能分支至其出現程式中的行。 這一行必須有可以參考的行標籤 `GoTo` 。 如需詳細資訊，請參閱 [如何：標記語句](../../programming-guide/program-structure/how-to-label-statements.md)。  
  
> [!NOTE]
> `GoTo` 語句可能使程式碼難以讀取和維護。 可能的話，請改用控制項結構。 如需詳細資訊，請參閱 [控制流程](../../programming-guide/language-features/control-flow/index.md)。  
  
 您無法使用 `GoTo` 語句從外部 `For` `Next` `For Each` `Next` `SyncLock` `End SyncLock` `Try` 進行分支 ...、...、...、...。 `Catch`...、... `Finally` `With` `End With` 或 `Using` ... `End Using` 結構的內部標籤。  
  
## <a name="branching-and-try-constructions"></a>分支和 Try 結構  

 在 `Try` ... `Catch`...`Finally` 結構，下列規則適用于與語句的分支 `GoTo` 。  
  
|封鎖或區域|從外部分支|從內部分支|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` 區塊|僅從 `Catch` 相同結構<sup>1</sup>的區塊|僅在整個結構之外|  
|`Catch` 區塊|永不允許|只有在整個結構之外，或 `Try` 相同結構<sup>1</sup>的區塊|  
|`Finally` 區塊|永不允許|永不允許|  
  
 <sup>1</sup> （如果 `Try` 有的話 `Catch` ） .。。...`Finally` 結構會內嵌在另一個區塊中， `Catch` 區塊可以 `Try` 在它自己的嵌套層級分支至區塊，但不能分成任何其他 `Try` 區塊。 嵌套的 `Try` ... `Catch`...`Finally` 結構必須完整地包含在 `Try` `Catch` 它所用之結構的或區塊中。  
  
 下圖顯示 `Try` 在另一個結構中嵌套的結構。 兩個結構的區塊之間的各種分支都會表示為有效或無效。  
  
 ![Try 語法結構中的分支示意圖](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>範例  

 下列範例會使用 `GoTo` 語句來分支至程式中的行標籤。  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>另請參閱

- [Do...Loop 陳述式](do-loop-statement.md)
- [For...Next 陳述式](for-next-statement.md)
- [For Each...Next 陳述式](for-each-next-statement.md)
- [If...Then...Else 陳述式](if-then-else-statement.md)
- [Select...Case 陳述式](select-case-statement.md)
- [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)
- [While...End While 陳述式](while-end-while-statement.md)
- [With...End With 陳述式](with-end-with-statement.md)
