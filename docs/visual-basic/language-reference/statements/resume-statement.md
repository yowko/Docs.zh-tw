---
title: Resume 語句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 884bdaa0c19508b5a6bf6377568a53acc6880518
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957683"
---
# <a name="resume-statement"></a>Resume 陳述式
在錯誤處理常式完成後繼續執行。  
  
 我們建議您盡可能在程式碼中使用結構化例外狀況處理, 而不是使用非結構化`On Error`例外`Resume`狀況處理和和語句。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="syntax"></a>語法  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>組件  
 `Resume`  
 必要項。 如果錯誤發生在與錯誤處理常式相同的程式中, 則會繼續執行與造成錯誤的語句。 如果錯誤發生在被呼叫的程式中, 則會在最後一次從包含錯誤處理常式的程式中呼叫的語句繼續執行。  
  
 `Next`  
 選擇性。 如果錯誤發生在與錯誤處理常式相同的程式中, 則會以緊接在造成錯誤的語句之後的語句繼續執行。 如果錯誤發生在被呼叫的程式中, 則會繼續執行, 語句緊接在最後一次從包含錯誤處理常式 (或`On Error Resume Next`語句) 的程式所呼叫的語句之後。  
  
 `line`  
 選擇性。 執行會在必要`line`引數中指定的那一行繼續進行。 `line`引數是行標籤或行號, 而且必須與錯誤處理常式位於相同的程式中。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 我們建議您盡可能在程式碼中使用結構化例外狀況處理, 而不是使用非結構化`On Error`例外`Resume`狀況處理和和語句。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 如果您在錯誤`Resume`處理常式以外的任何地方使用語句, 就會發生錯誤。  
  
 語句不能用在`Try...Catch...Finally`包含語句的任何程式中。 `Resume`  
  
## <a name="example"></a>範例  
 這個範例會使用`Resume`語句來結束程式中的錯誤處理, 然後使用導致錯誤的語句繼續執行。 產生錯誤號碼55以說明`Resume`語句的使用。  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly**Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error 陳述式](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
