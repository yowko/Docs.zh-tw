---
title: 運算子程序 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8fba5180da6498d280fa4192937c39d3e33168e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="operator-procedures-visual-basic"></a>運算子程序 (Visual Basic)
運算子程序是一系列的 Visual Basic 陳述式，定義標準的運算子的行為 (例如`*`， `<>`，或`And`) 上的類別或您已定義的結構。 這也稱為*運算子多載*。  
  
## <a name="when-to-define-operator-procedures"></a>當定義運算子程序  
 當您已經定義類別或結構時，您可以宣告為該類別或結構類型的變數。 有時候這類變數都必須參與作業為運算式的一部分。 若要這樣做，它必須是運算子的運算元。  
  
 Visual Basic 定義於其基本資料類型的運算子。 您可以定義一個運算子的行為，或這兩個運算元屬於類別或結構的類型。  
  
 如需詳細資訊，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## <a name="types-of-operator-procedure"></a>類型的運算子程序  
 運算子程序可以是下列類型之一：  
  
-   一元運算子的引數會是類別或結構的類型定義。  
  
-   二元運算子，其中至少一個引數為類別或結構的類型定義。  
  
-   轉換運算子的引數會是類別或結構的類型定義。  
  
-   傳回的類別或結構類型轉換運算子定義。  
  
 轉換運算子一律是一元 （unary），且一律使用`CType`做為您正在定義的運算子。  
  
## <a name="declaration-syntax"></a>宣告語法  
 宣告運算子程序的語法如下所示：  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *運算子符號*`(` *operand1*`[,`*operand2* `]) As`*資料類型*   
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 您使用`Widening`或`Narrowing`關鍵字只在類型轉換運算子。 運算子符號一律是[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)類型轉換運算子。  
  
 宣告兩個運算元來定義二元運算子，並宣告一個定義一元運算子，包括類型轉換運算子的運算元。 所有的運算元必須宣告`ByVal`。  
  
 宣告參數的相同方式宣告每個運算元[Sub 程序](./sub-procedures.md)。  
  
### <a name="data-type"></a>資料類型  
 因為您正在定義的運算子上類別或您已定義的結構，其中至少一個運算元必須是該類別或結構的資料類型。 類型轉換運算子，運算元或傳回型別必須是類別或結構的資料類型。  
  
 如需詳細資訊，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## <a name="calling-syntax"></a>呼叫語法  
 在運算式中使用運算子符號隱含地呼叫運算子程序。 您提供運算元的預先定義的運算子，相同的方式。  
  
 運算子程序的隱含呼叫的語法如下所示：  
  
 `Dim testStruct As`  *結構名稱*  
  
 `Dim testNewStruct As`  *結構名稱*`= testStruct`*運算子符號*   `10`  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列結構的構成的高序位和低序位組件以儲存 128 位元帶正負號的整數值。 它會定義`+`運算子，將兩個`veryLong`值，並產生產生`veryLong`值。  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 下列範例會示範一般呼叫`+`上定義的運算子`veryLong`。  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 如需詳細資訊和範例，請參閱 [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703) (Visual Basic 2005 中的運算子多載)。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [函式程序](./function-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [如何：定義運算子](./how-to-define-an-operator.md)  
 [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)  
 [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)  
 [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
