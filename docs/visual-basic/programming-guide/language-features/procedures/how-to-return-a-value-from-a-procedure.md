---
title: HOW TO：傳回值，從程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 8b53df1634d2b9971bc44c968a17db81cac3924f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665750"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>HOW TO：傳回值，從程序 (Visual Basic)
A`Function`程序傳回值給呼叫程式碼藉由執行`Return`陳述式或遇到`Exit Function`或`End Function`陳述式。  
  
### <a name="to-return-a-value-using-the-return-statement"></a>傳回值，使用 Return 的陳述式  
  
1. Put`Return`程序的工作完成的其中一點的陳述式。  
  
2. 請依照下列`Return`您想要傳回給呼叫程式碼會產生值的運算式的關鍵字。  
  
3. 同一個程序中可以有多個 `Return` 陳述式。  
  
     下列`Function`程序會計算直角三角形斜邊的最長的側邊，並將它傳回呼叫程式碼。  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     下列範例示範的典型呼叫`hypotenuse`，它會儲存傳回的值。  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>傳回值，使用 Exit 函式或結束函式  
  
1. 在中的至少一個就地`Function`程序中，指派值至該程序的名稱。  
  
2. 當您執行`Exit Function`或`End Function`陳述式，Visual Basic 會傳回最近指派給此程序名稱的值。  
  
3. 同一個程序中可以有多個 `Exit Function` 陳述式，也可以混合 `Return` 和 `Exit Function` 陳述式。  
  
4. 您只能有一個`End Function`中的陳述式`Function`程序。  
  
     如需詳細資訊和範例，請參閱 「 傳回的值 」 中[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md)
- [如何：建立程序傳回值](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
