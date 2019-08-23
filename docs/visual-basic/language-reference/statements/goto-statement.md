---
title: GoTo 語句 (Visual Basic)
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
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912454"
---
# <a name="goto-statement"></a>GoTo 陳述式
無條件地分支到程式中的指定行。  
  
## <a name="syntax"></a>語法  
  
```  
GoTo line  
```  
  
## <a name="part"></a>組件  
 `line`  
 必要項。 任何行標籤。  
  
## <a name="remarks"></a>備註  
 `GoTo`語句只能分支至其出現所在程式中的行。 這`GoTo`一行必須有可以參考的行標籤。 如需詳細資訊，請參閱[如何：標籤](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)語句。  
  
> [!NOTE]
> `GoTo`語句可能會使程式碼更容易讀取和維護。 請盡可能改用控制結構。 如需詳細資訊, 請參閱[控制流程](../../../visual-basic/programming-guide/language-features/control-flow/index.md)。  
  
 您不能使用`GoTo`語句從`For`外部進行分支 .。。`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`、或`Using`.。。`End Using`結構到內的標籤。  
  
## <a name="branching-and-try-constructions"></a>分支和 Try 結構  
 `Try`在 .。。`Catch`...結構中, 下列規則適用于`GoTo`使用語句的分支。 `Finally`  
  
|封鎖或區域|從外部分支|從內部分支|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`總匯|僅來自`Catch`相同結構<sup>1</sup>的區塊|僅限於整個結構外|  
|`Catch`總匯|不允許|僅限於整個結構外, 或`Try`相同結構<sup>1</sup>的區塊|  
|`Finally`總匯|不允許|不允許|  
  
 <sup>1</sup> (如果`Try`有的話)`Catch`...結構會在另一個內嵌套`Catch` , `Try`區塊可以在自己的嵌套層級分支到區塊中, 但不能`Try`放入任何其他區塊中。 `Finally` Nested `Try`.。。`Catch`...結構必須完全包含`Try`在其所用`Catch`的結構的或區塊中。 `Finally`  
  
 下圖顯示在另`Try`一個中嵌套的一個結構。 兩個結構的區塊之間的各種分支會指出為有效或無效。  
  
 ![Try 語法結構中的分支示意圖](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>範例  
 下列範例會使用`GoTo`語句, 在程式中分支至行標籤。  
  
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
