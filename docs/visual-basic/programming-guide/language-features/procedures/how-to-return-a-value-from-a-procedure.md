---
title: 如何：傳回程序的值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 62e8a52e488247d4dfcde2a560920447abe1c182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651830"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>如何：傳回程序的值 (Visual Basic)
A`Function`值傳回給呼叫程式碼藉由執行`Return`陳述式或遇到`Exit Function`或`End Function`陳述式。  
  
### <a name="to-return-a-value-using-the-return-statement"></a>傳回值，使用 Return 的陳述式  
  
1.  Put`Return`程序的工作完成的位置處的陳述式。  
  
2.  請遵循`Return`您想要傳回呼叫程式碼會產生值的運算式的關鍵字。  
  
3.  同一個程序中可以有多個 `Return` 陳述式。  
  
     下列`Function`程序會計算直角三角形斜邊的最長邊，並傳回到呼叫的程式碼。  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     下列範例會示範一般呼叫`hypotenuse`，它會儲存傳回的值。  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>傳回值使用結束函式或結束函式  
  
1.  在中至少一個就地`Function`程序中，指派值到程序的名稱。  
  
2.  當您執行`Exit Function`或`End Function`陳述式，Visual Basic 會傳回最近指派給程序的名稱的值。  
  
3.  同一個程序中可以有多個 `Exit Function` 陳述式，也可以混合 `Return` 和 `Exit Function` 陳述式。  
  
4.  您只能有一個`End Function`陳述式中的`Function`程序。  
  
     如需詳細資訊和範例，請參閱 「 傳回的值 」 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [如何：建立傳回值的程序](./how-to-create-a-procedure-that-returns-a-value.md)  
 [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
