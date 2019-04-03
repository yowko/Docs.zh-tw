---
title: Continue 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 5523be69f2901851c86f6c0263548e3577507ff9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835373"
---
# <a name="continue-statement-visual-basic"></a>Continue 陳述式 (Visual Basic)
將控制權立即迴圈的下一個反覆項目。  
  
## <a name="syntax"></a>語法  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>備註  
 您可以從傳輸內`Do`， `For`，或`While`迴圈，迴圈的下一個反覆項目。 控制傳遞到迴圈的條件測試，這相當於將傳送到立即`For`或是`While`陳述式，或`Do`或`Loop`包含的陳述式`Until`或`While`子句。  
  
 您可以使用`Continue`循環，允許傳輸的任何位置。 允許將控制轉移的規則都具有相同[GoTo 陳述式](../../../visual-basic/language-reference/statements/goto-statement.md)。  
  
 比方說，如果迴圈是完全包含在`Try`區塊中，`Catch`區塊中，或有`Finally`區塊中，您可以使用`Continue`傳送出迴圈。 另一方面，如果`Try`...`End Try`結構是否包含在迴圈內，您不能使用`Continue`出的控制權轉移`Finally`區塊，以及您可以使用它來傳輸共`Try`或`Catch`共完全傳輸時，才會受阻`Try`...`End Try`結構。  
  
 如果您擁有巢狀的迴圈相同的類型，例如`Do`在另一個迴圈`Do`迴圈`Continue Do`陳述式就會跳到最內層的下一個反覆項目`Do`迴圈包含它。 您無法使用`Continue`跳到包含相同類型的迴圈的下一個反覆項目。  
  
 如果您擁有巢狀的迴圈的不同類型，例如`Do`迴圈內`For`迴圈中，您可以使用其中一種跳至任一個迴圈的下一個反覆項目`Continue Do`或`Continue For`。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Continue While`陳述式跳至下一步 的資料行的陣列，如果除數為零。 `Continue While`位於`For`迴圈。 它所傳輸到`While col < lastcol`陳述式，這是最內層的下一個反覆運算`While`迴圈，其中包含`For`迴圈。  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>另請參閱

- [Do...Loop 陳述式](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While 陳述式](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
