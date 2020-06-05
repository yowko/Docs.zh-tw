---
title: Continue 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382090"
---
# <a name="continue-statement-visual-basic"></a>Continue 陳述式 (Visual Basic)
立即將控制權轉移到迴圈的下一個反復專案。  
  
## <a name="syntax"></a>語法  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>備註  
 您可以從 `Do` 、 `For` 或迴圈內部傳輸 `While` 到該迴圈的下一個反復專案。 控制權會立即傳遞至迴圈條件測試，這相當於傳送至 `For` 或 `While` 語句，或是 `Do` `Loop` 包含或子句的或語句 `Until` `While` 。  
  
 您可以在 `Continue` 迴圈中允許傳輸的任何位置使用。 允許傳送控制項的規則與[GoTo 語句](goto-statement.md)相同。  
  
 例如，如果迴圈完全包含在 `Try` 區塊、 `Catch` 區塊或 `Finally` 區塊內，您可以使用 `Continue` 從迴圈傳出。 另一方面，如果 `Try` ... `End Try` 結構包含在迴圈內，您就無法使用 `Continue` 將控制權轉移到 `Finally` 區塊之外，而且 `Try` `Catch` 只有在您完全傳輸到 `Try` ... `End Try` 結構時，才可以使用它來傳送或封鎖。  
  
 如果您有相同類型的嵌套迴圈，例如 `Do` 另一個迴圈內的迴圈 `Do` ，則語句會 `Continue Do` 跳到包含它的最內層迴圈的下一個反復專案 `Do` 。 您不能使用 `Continue` 跳到相同類型之包含迴圈的下一個反復專案。  
  
 如果您有不同類型的嵌套迴圈（例如 `Do` 迴圈內的迴圈 `For` ），您可以使用或跳到任一迴圈的下一個反覆運算 `Continue Do` `Continue For` 。  
  
## <a name="example"></a>範例  
 如果除數為零，下列程式碼範例會使用 `Continue While` 語句來跳到陣列的下一個資料行。 `Continue While`位於 `For` 迴圈內部。 它會傳送至 `While col < lastcol` 語句，這是包含迴圈的最內層迴圈的下一個反復專案 `While` `For` 。  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>另請參閱

- [Do...Loop 陳述式](do-loop-statement.md)
- [For...Next 陳述式](for-next-statement.md)
- [While...End While 陳述式](while-end-while-statement.md)
- [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)
