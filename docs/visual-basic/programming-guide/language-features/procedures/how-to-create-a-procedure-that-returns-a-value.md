---
title: HOW TO：建立程序傳回值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 88e30caed97938501302c05830df6546a6822a48
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831250"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>HOW TO：建立程序傳回值 (Visual Basic)
您使用`Function`程序來將值傳回給呼叫程式碼。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>若要建立傳回值的程序  
  
1.  任何其他程序外, 使用`Function`陳述式，後面接著`End Function`陳述式。  
  
2.  在 `Function`陳述式中，遵循`Function`關鍵字的程序，然後按一下 參數清單括號括住名稱。  
  
3.  括號後面`As`子句來指定傳回值的資料類型。  
  
4.  放置程序的程式碼陳述式之間`Function`和`End Function`陳述式。  
  
5.  使用`Return`陳述式來將值傳回給呼叫程式碼。  
  
     下列`Function`程序會計算已知值的其他兩個邊直角三角形斜邊的最長的側邊。  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     下列範例示範的典型呼叫`hypotenuse`。  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)
- [如何：從程序傳回值](./how-to-return-a-value-from-a-procedure.md)
- [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
