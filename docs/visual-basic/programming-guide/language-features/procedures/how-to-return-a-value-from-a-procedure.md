---
title: "如何︰ 從 (Visual Basic) 的程序傳回值 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- procedures, returning from
- procedures, returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 98f0fb0740a021a16e87454bfaebbfad7858477c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>如何：傳回程序的值 (Visual Basic)
A`Function`值傳回給呼叫程式碼藉由執行`Return`陳述式或遇到`Exit Function`或`End Function`陳述式。  
  
### <a name="to-return-a-value-using-the-return-statement"></a>傳回值，使用 Return 陳述式  
  
1.  將`Return`陳述式，在完成該程序的工作之處。  
  
2.  請依照下列`Return`您想要傳回給呼叫程式碼將會產生值的運算式的關鍵字。  
  
3.  您可以有一個以上`Return`陳述式中相同的程序。  
  
     下列`Function`程序會計算直角三角形斜邊的最長邊，並將其傳回呼叫程式碼。  
  
     [!code-vb[VbVbcnProcedures #&1;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     下列範例會示範一般呼叫`hypotenuse`，它會儲存傳回的值。  
  
     [!code-vb[VbVbcnProcedures #&6;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>傳回值使用結束函式或結束函式  
  
1.  在中至少一個就地`Function`程序中，指派值給程序的名稱。  
  
2.  當您執行`Exit Function`或`End Function`陳述式，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]傳回最近指派給程序的名稱的值。  
  
3.  您可以有一個以上`Exit Function`陳述式中相同的程序，而且您可以混合`Return`和`Exit Function`陳述式中相同的程序。  
  
4.  您只能有一個`End Function`陳述式中的`Function`程序。  
  
     如需詳細資訊和範例，請參閱 「 傳回的值 」 中[Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [Sub 程序](./sub-procedures.md)   
 [Property 程序](./property-procedures.md)   
 [運算子程序](./operator-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Function 陳述式](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Return 陳述式](../../../../visual-basic/language-reference/statements/return-statement.md)   
 [如何︰ 建立程序傳回值](./how-to-create-a-procedure-that-returns-a-value.md)   
 [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)
