---
title: Continue 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354115"
---
# <a name="continue-statement-visual-basic"></a>Continue 陳述式 (Visual Basic)
立即將控制權轉移到迴圈的下一個反復專案。  
  
## <a name="syntax"></a>語法  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>備註  
 您可以從 `Do`、`For`或 `While` 迴圈內部轉移到該迴圈的下一個反復專案。 控制權會立即傳遞至迴圈條件測試，這相當於傳送至 `For` 或 `While` 語句，或包含 `Until` 或 `While` 子句的 `Do` 或 `Loop` 語句。  
  
 您可以使用迴圈中允許傳輸的任何位置上的 `Continue`。 允許傳送控制項的規則與[GoTo 語句](../../../visual-basic/language-reference/statements/goto-statement.md)相同。  
  
 例如，如果迴圈完全包含在 `Try` 區塊、`Catch` 區塊或 `Finally` 區塊中，您可以使用 `Continue` 來傳出迴圈。 另一方面，如果 `Try`...`End Try` 結構包含在迴圈內，您就無法使用 `Continue` 從 `Finally` 區塊中轉移控制權，而且只有在您完全從 `Try` 結構傳輸出來時，才可以使用它來傳出 `Catch` 或 `Try`區塊。`End Try`  
  
 如果您有相同類型的嵌套迴圈（例如，另一個 `Do` 迴圈內的 `Do` 迴圈），`Continue Do` 語句會跳到包含它的最內層 `Do` 迴圈的下一個反復專案。 您無法使用 `Continue` 跳到相同類型之包含迴圈的下一個反復專案。  
  
 如果您有不同類型的嵌套迴圈（例如 `For` 迴圈內的 `Do` 迴圈），您可以使用 `Continue Do` 或 `Continue For`跳到任一迴圈的下一個反復專案。  
  
## <a name="example"></a>範例  
 如果除數為零，下列程式碼範例會使用 `Continue While` 語句來跳到陣列的下一個資料行。 `Continue While` 是在 `For` 迴圈內。 它會傳送至 `While col < lastcol` 語句，這是包含 `For` 迴圈的最內層 `While` 迴圈的下一個反復專案。  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>請參閱

- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
