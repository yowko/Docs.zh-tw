---
title: "運算子程序 (Visual Basic) |Microsoft 文件"
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
- procedures, operator
- Visual Basic code, operators
- syntax, Operator procedures
- operators [Visual Basic], overloading
- overloaded operators
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
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
ms.openlocfilehash: a9e86c9c466ba236cc33153f2f341af35c622de6
ms.lasthandoff: 03/13/2017

---
# <a name="operator-procedures-visual-basic"></a>運算子程序 (Visual Basic)
運算子程序是一系列的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]陳述式，定義標準的運算子的行為 (例如`*`， `<>`，或`And`) 上的類別或您已定義的結構。 這也稱為*運算子多載*。  
  
## <a name="when-to-define-operator-procedures"></a>當定義運算子程序  
 當您已經定義的類別或結構時，您可以宣告為該類別或結構的型別變數。 有時這類變數需要參與作業為運算式的一部分。 若要這樣做，它必須是運算子的運算元。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]只在它的基本資料型別定義運算子。 您可以定義一種運算子的行為，或兩個運算元屬於類別或結構的型別。  
  
 如需詳細資訊，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## <a name="types-of-operator-procedure"></a>運算子程序的類型  
 運算子程序可以是下列類型的其中一個︰  
  
-   一元運算子，其中引數是類別或結構的型別定義。  
  
-   二元運算子，其中至少一個引數是類別或結構的型別定義。  
  
-   轉換運算子，其中引數是類別或結構的型別定義。  
  
-   轉換運算子會傳回類別或結構的型別定義。  
  
 轉換運算子一律是一元，且一律使用`CType`做為您定義的運算子。  
  
## <a name="declaration-syntax"></a>宣告語法  
 宣告運算子程序的語法如下所示︰  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 您使用`Widening`或`Narrowing`關鍵字只有在類型轉換運算子。 運算子符號總是[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)類型轉換運算子。  
  
 宣告兩個運算元，以定義一個二元運算子，並宣告一個定義的一元運算子，包括型別轉換運算子的運算元。 必須宣告所有運算元`ByVal`。  
  
 同樣的方法宣告的參數宣告每一個運算元[Sub 程序](./sub-procedures.md)。  
  
### <a name="data-type"></a>資料類型  
 由於您在類別或結構定義上定義運算子，其中至少一個運算元必須是該類別或結構的資料型別。 類型轉換運算子，運算元或傳回型別必須是類別或結構的資料型別。  
  
 如需詳細資訊，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## <a name="calling-syntax"></a>呼叫語法  
 在運算式中使用運算子符號以隱含方式呼叫運算子程序。 您提供運算元的方式相同的預先定義的運算子。  
  
 運算子程序的隱含呼叫的語法如下所示︰  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol    *  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列結構儲存 128 位元帶正負號的整數值為構成的高序位和低序位組件。 它會定義`+`運算子，以將兩個`veryLong`值，並產生結果`veryLong`值。  
  
 [!code-vb[VbVbcnProcedures #&23;](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 下列範例會示範一般呼叫`+`上定義的運算子`veryLong`。  
  
 [!code-vb[VbVbcnProcedures #&24;](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 如需詳細資訊和範例，請參閱[Visual Basic 2005 中的運算子多載](http://go.microsoft.com/fwlink/?LinkId=101703)。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [Sub 程序](./sub-procedures.md)   
 [Function 程序](./function-procedures.md)   
 [Property 程序](./property-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [如何︰ 定義運算子](./how-to-define-an-operator.md)   
 [如何︰ 定義轉換運算子](./how-to-define-a-conversion-operator.md)   
 [如何︰ 呼叫運算子程序](./how-to-call-an-operator-procedure.md)   
 [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
