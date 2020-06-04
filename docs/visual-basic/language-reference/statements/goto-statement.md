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
ms.openlocfilehash: eb6f48d04b7d14591003e340464451da7df45cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404611"
---
# <a name="goto-statement"></a>GoTo 陳述式
無條件地分支到程式中的指定行。  
  
## <a name="syntax"></a>語法  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>部分  
 `line`  
 必要。 任何行標籤。  
  
## <a name="remarks"></a>備註  
 `GoTo`語句只能分支至其出現所在程式中的行。 這一行必須有可以參考的行標籤 `GoTo` 。 如需詳細資訊，請參閱 how [to： Label 語句](../../programming-guide/program-structure/how-to-label-statements.md)。  
  
> [!NOTE]
> `GoTo`語句可能會使程式碼更容易讀取和維護。 請盡可能改用控制結構。 如需詳細資訊，請參閱 [控制流程](../../programming-guide/language-features/control-flow/index.md)。  
  
 您不能使用 `GoTo` 語句從 [ `For` ... `Next` `For Each` `Next` `SyncLock` `End SyncLock` `Try` `Catch` ]、[...]、[...] 和 [...]... `Finally` 、 `With` ... `End With` 或 `Using` ... `End Using` 結構，到內的標籤。  
  
## <a name="branching-and-try-constructions"></a>分支和 Try 結構  
 在 `Try` ... `Catch`...`Finally`結構中，下列規則適用于使用語句的分支 `GoTo` 。  
  
|封鎖或區域|從外部分支|從內部分支|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`總匯|僅來自 `Catch` 相同結構<sup>1</sup>的區塊|僅限於整個結構外|  
|`Catch`總匯|不允許|僅限於整個結構外，或 `Try` 相同結構<sup>1</sup>的區塊|  
|`Finally`總匯|不允許|不允許|  
  
 <sup>1</sup> （如果 `Try` 有的話 `Catch` ）...`Finally`結構會在另一個內嵌套， `Catch` 區塊可以 `Try` 在自己的嵌套層級分支到區塊中，但不能放入任何其他 `Try` 區塊中。 Nested `Try` ... `Catch`...`Finally`結構必須完全包含在 `Try` 其所用的結構的或 `Catch` 區塊中。  
  
 下圖顯示 `Try` 在另一個中嵌套的一個結構。 兩個結構的區塊之間的各種分支會指出為有效或無效。  
  
 ![Try 語法結構中的分支示意圖](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>範例  
 下列範例會使用 `GoTo` 語句，在程式中分支至行標籤。  
  
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
