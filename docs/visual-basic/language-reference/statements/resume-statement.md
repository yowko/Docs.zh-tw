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
ms.openlocfilehash: db9d47798d087d60f4318b06fe3291fb895e6618
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871871"
---
# <a name="resume-statement"></a>Resume 陳述式

在錯誤處理常式完成之後繼續執行。  
  
 建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外 `On Error` 狀況處理和和 `Resume` 語句。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>組件  

 `Resume`  
 必要。 如果錯誤發生在與錯誤處理常式相同的程式中，則會繼續執行並產生錯誤的語句。 如果在呼叫的程式中發生錯誤，則會在最後從包含錯誤處理常式的程式中呼叫的語句繼續執行。  
  
 `Next`  
 選擇性。 如果錯誤發生在與錯誤處理常式相同的程式中，則會以緊接在引發錯誤的語句後面的語句繼續執行。 如果在被呼叫的程式中發生錯誤，則會繼續執行最後一次從包含錯誤處理常式的程式所呼叫的語句，而不是) 的 (或 `On Error Resume Next` 語句。  
  
 `line`  
 選擇性。 執行會在所需的引數中指定的行繼續 `line` 。 `line`引數是行標籤或行號，而且必須與錯誤處理常式在相同的程式中。  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 建議您盡可能在程式碼中使用結構化例外狀況處理，而不是使用非結構化例外 `On Error` 狀況處理和和 `Resume` 語句。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)。  
  
 如果您 `Resume` 在錯誤處理常式以外的任何地方使用語句，則會發生錯誤。  
  
 `Resume`語句不能用在包含語句的任何程式中 `Try...Catch...Finally` 。  
  
## <a name="example"></a>範例  

 這則範例會使用 `Resume` 語句來結束程式中的錯誤處理，然後再繼續執行造成錯誤的語句。 產生錯誤號碼55，以說明如何使用 `Resume` 語句。  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>規格需求  

 **命名空間：** [Microsoft.](../runtime-library-members.md)  
  
 **元件：** Microsoft.VisualBasic.dll) 中的 Visual Basic 執行時間程式庫 (  
  
## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](try-catch-finally-statement.md)
- [Error 陳述式](error-statement.md)
- [On Error 陳述式](on-error-statement.md)
