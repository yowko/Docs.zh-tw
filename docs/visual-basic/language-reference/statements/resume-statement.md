---
title: Resume 陳述式 (Visual Basic)
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
ms.openlocfilehash: 853f3fe060b70c8a43957d3c843fb95539981679
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39296152"
---
# <a name="resume-statement"></a>Resume 陳述式
錯誤處理常式完成之後，請繼續執行。  
  
 我們建議您使用結構化例外狀況處理，可能的話，程式碼中的，而不是使用非結構化例外狀況處理和`On Error`和`Resume`陳述式。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="syntax"></a>語法  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>組件  
 `Resume`  
 必要。 如果在相同的程序中的錯誤處理常式發生錯誤，造成錯誤的陳述式將會繼續執行。 如果呼叫的程序中發生錯誤，則會在一次從程序包含錯誤處理常式呼叫的陳述式繼續執行。  
  
 `Next`  
 選擇性。 如果錯誤發生的錯誤處理常式的相同程序中，緊接著造成錯誤的陳述式的陳述式將會繼續執行。 如果呼叫的程序中發生錯誤，立即包含錯誤處理常式的程序從上次呼叫的陳述式之後繼續執行 (或`On Error Resume Next`陳述式)。  
  
 `line`  
 選擇性。 指定在所需的那一行就會繼續執行`line`引數。 `line`引數是行標籤或行號，且必須位於相同的程序，為錯誤處理常式。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  我們建議您改用可能的話，您的程式碼中的結構化例外狀況處理，而不是使用非結構化例外狀況處理和`On Error`和`Resume`陳述式。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
 如果您使用`Resume`陳述式中任何位置以外的錯誤處理常式中，會發生錯誤。  
  
 `Resume`陳述式不能包含任何程序在`Try...Catch...Finally`陳述式。  
  
## <a name="example"></a>範例  
 這個範例會使用`Resume`陳述式來結束處理程序中的錯誤，然後以造成錯誤的陳述式繼續執行。 會產生錯誤數字 55，來說明使用`Resume`陳述式。  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組件：** Visual Basic 執行階段程式庫 （位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Error 陳述式](../../../visual-basic/language-reference/statements/error-statement.md)  
 [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
