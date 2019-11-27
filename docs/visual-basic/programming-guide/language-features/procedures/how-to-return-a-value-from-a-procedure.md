---
title: 如何：傳回程序的值
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346032"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>如何：傳回程序的值 (Visual Basic)
`Function` 程式會藉由執行 `Return` 語句或遇到 `Exit Function` 或 `End Function` 語句，將值傳回給呼叫程式碼。  
  
### <a name="to-return-a-value-using-the-return-statement"></a>使用 Return 語句傳回值  
  
1. 將 `Return` 語句放在程式的工作完成的位置。  
  
2. 請在 `Return` 關鍵字後面加上運算式，其會產生您想要傳回給呼叫程式碼的值。  
  
3. 同一個程序中可以有多個 `Return` 陳述式。  
  
     下列 `Function` 程式會計算直角三角形的最長端（或斜邊），並將它傳回給呼叫程式碼。  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     下列範例示範 `hypotenuse`的一般呼叫，它會儲存傳回的值。  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>使用 Exit 函數或 End 函式傳回值  
  
1. 在 `Function` 程式的至少一個位置中，將值指派給程式的名稱。  
  
2. 當您執行 `Exit Function` 或 `End Function` 語句時，Visual Basic 會傳回最近指派給程式名稱的值。  
  
3. 同一個程序中可以有多個 `Exit Function` 陳述式，也可以混合 `Return` 和 `Exit Function` 陳述式。  
  
4. `Function` 程式中只能有一個 `End Function` 語句。  
  
     如需詳細資訊和範例，請參閱[Function 語句](../../../../visual-basic/language-reference/statements/function-statement.md)中的「傳回值」。  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md)
- [如何：建立傳回值的程序](./how-to-create-a-procedure-that-returns-a-value.md)
- [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
