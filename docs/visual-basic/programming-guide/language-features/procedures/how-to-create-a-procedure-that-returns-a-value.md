---
title: 如何：建立傳回值的程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 472f55173a4897a23a82812a2b24bf1646c1a6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648433"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>如何：建立傳回值的程序 (Visual Basic)
您使用`Function`程序來將值傳回給呼叫程式碼。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>若要建立程序傳回值  
  
1.  任何其他程序，之外使用`Function`陳述式，後面接著`End Function`陳述式。  
  
2.  在`Function`陳述式，請遵循`Function`關鍵字與程序，然後按一下 參數清單括號括住的名稱。  
  
3.  括號後面`As`子句來指定傳回值的資料類型。  
  
4.  放置程序的程式碼陳述式之間`Function`和`End Function`陳述式。  
  
5.  使用`Return`陳述式來將值傳回給呼叫程式碼。  
  
     下列`Function`已知值的其他兩個邊直角三角形斜邊的最長邊，程序會計算。  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     下列範例會示範一般呼叫`hypotenuse`。  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [如何：傳回程序的值](./how-to-return-a-value-from-a-procedure.md)  
 [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
