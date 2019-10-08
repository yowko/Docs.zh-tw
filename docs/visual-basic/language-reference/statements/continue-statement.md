---
title: Continue 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005112"
---
# <a name="continue-statement-visual-basic"></a>Continue 陳述式 (Visual Basic)
立即將控制權轉移到迴圈的下一個反復專案。  
  
## <a name="syntax"></a>語法  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>備註  
 您可以從 `Do`、`For` 或 @no__t 2 迴圈內部傳輸到該迴圈的下一個反復專案。 控制權會立即傳遞至迴圈條件測試，這相當於傳送至 `For` 或 `While` 語句，或包含 `Until` 或 `While` 子句的 `Do` 或 `Loop` 語句。  
  
 您可以在允許傳輸的迴圈中的任何位置使用 `Continue`。 允許傳送控制項的規則與[GoTo 語句](../../../visual-basic/language-reference/statements/goto-statement.md)相同。  
  
 例如，如果迴圈完全包含在 `Try` 區塊、@no__t 1 區塊或 @no__t 2 區塊中，您可以使用 `Continue` 來傳出迴圈。 另一方面，如果 `Try` ... `End Try` 結構包含在迴圈內，您就不能使用 `Continue` 將控制權轉移出 @no__t 3 區塊，而且只有在您完全轉移完 @no__t 時，才能使用它來傳出 `Try` 或 @no_-5 區塊。_t-6 ... `End Try` 結構。  
  
 如果您有相同類型的嵌套迴圈（例如，在另一個 `Do` 迴圈內的 `Do` 迴圈），@no__t 2 語句會跳到包含它的最內層 `Do` 迴圈的下一個反復專案。 您無法使用 `Continue` 來跳至相同類型之包含迴圈的下一個反復專案。  
  
 如果您有不同類型的嵌套迴圈（例如，在 @no__t 1 迴圈內的 `Do` 迴圈），您可以使用 `Continue Do` 或 `Continue For`，跳到任一迴圈的下一個反復專案。  
  
## <a name="example"></a>範例  
 如果除數為零，下列程式碼範例會使用 `Continue While` 語句來跳到陣列的下一個資料行。 @No__t-0 位於 @no__t 1 迴圈內。 它會傳送至 `While col < lastcol` 語句，這是包含 @no__t 2 迴圈的最內層 `While` 迴圈的下一個反復專案。  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>另請參閱

- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
