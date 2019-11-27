---
title: Resume 陳述式
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
ms.openlocfilehash: 95137a9f6a4a4a18655b51b95300bfaf93cca193
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333021"
---
# <a name="resume-statement"></a>Resume 陳述式
在錯誤處理常式完成後繼續執行。  
  
 我們建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外處理和 `On Error` 和 `Resume` 語句。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="syntax"></a>語法  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>組件  
 `Resume`  
 必要。 如果錯誤發生在與錯誤處理常式相同的程式中，則會繼續執行與造成錯誤的語句。 如果錯誤發生在被呼叫的程式中，則會在最後一次從包含錯誤處理常式的程式中呼叫的語句繼續執行。  
  
 `Next`  
 選擇性。 如果錯誤發生在與錯誤處理常式相同的程式中，則會以緊接在造成錯誤的語句之後的語句繼續執行。 如果錯誤發生在被呼叫的程式中，則會繼續執行，並緊接在最後一次從包含錯誤處理常式（或 `On Error Resume Next` 語句）的程式所呼叫的語句之後。  
  
 `line`  
 選擇性。 執行會在所需的 `line` 引數中指定的那一行繼續進行。 `line` 引數是行標籤或行號，而且必須與錯誤處理常式位於相同的程式中。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 我們建議您盡可能在程式碼中使用結構化例外狀況處理，而不要使用非結構化例外處理和 `On Error` 和 `Resume` 語句。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 如果您在錯誤處理常式以外的任何地方使用 `Resume` 語句，就會發生錯誤。  
  
 `Resume` 語句不能用在包含 `Try...Catch...Finally` 語句的任何程式中。  
  
## <a name="example"></a>範例  
 這個範例會使用 `Resume` 語句來結束程式中的錯誤處理，然後使用導致錯誤的語句繼續執行。 產生錯誤號碼55，以說明如何使用 `Resume` 語句。  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）  
  
## <a name="see-also"></a>請參閱

- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error 陳述式](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
