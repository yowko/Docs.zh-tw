---
title: 運算子程序 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 611195143fd216caab0b5f89badefb93d7dea017
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589106"
---
# <a name="operator-procedures-visual-basic"></a>運算子程序 (Visual Basic)
運算子程序是一系列的 Visual Basic 陳述式可定義標準運算式的行為 (例如`*`， `<>`，或`And`) 上類別或您已定義的結構。 這也稱為*多載的運算子*。  
  
## <a name="when-to-define-operator-procedures"></a>定義運算子程序的時機  
 當您已定義類別或結構時，您可以宣告為該類別或結構類型的變數。 有時候這類變數必須參與作業為運算式的一部分。 若要這樣做，它必須是運算子的運算元。  
  
 Visual Basic 只能在其基本資料類型上定義運算子。 您可以定義一種運算子的行為，或兩個運算元屬於您的類別或結構的類型。  
  
 如需詳細資訊，請參閱 < [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## <a name="types-of-operator-procedure"></a>類型的運算子程序  
 運算子程序可以是下列類型之一：  
  
-   一元運算子的引數會是您的類別或結構的類型定義。  
  
-   二元運算子，其中至少一個引數是您自己的類別或結構之型別的定義。  
  
-   轉換運算子，其中的引數是類別或結構的類型定義。  
  
-   轉換運算子會傳回您類別或結構的型別定義。  
  
 轉換運算子一律是一元 （unary），且一律使用`CType`做為您正在定義的運算子。  
  
## <a name="declaration-syntax"></a>宣告語法  
 宣告運算子程序的語法如下所示：  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 您使用`Widening`或`Narrowing`關鍵字只在型別轉換運算子。 運算子符號總是[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)的型別轉換運算子。  
  
 您宣告兩個運算元來定義二元運算子，並宣告一個定義的一元運算子，包括型別轉換運算子的運算元。 所有的運算元必須宣告`ByVal`。  
  
 同樣的方法宣告參數宣告每一個運算元[Sub 程序](./sub-procedures.md)。  
  
### <a name="data-type"></a>資料類型  
 因為您正在定義的運算子上類別或您已定義的結構，其中至少一個運算元必須是該類別或結構的資料類型。 型別轉換運算子，運算元或傳回類型必須是類別或結構的資料類型。  
  
 如需詳細資訊，請參閱 < [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。  
  
## <a name="calling-syntax"></a>呼叫語法  
 您叫用運算子程序隱含地在運算式中使用運算子的符號。 您提供運算元相同方式和預先定義的運算子。  
  
 隱含呼叫運算子程序的語法如下所示：  
  
 `Dim testStruct As`  *structurename*  
  
 `Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列結構儲存為構成的高序位和低序位部分的 128 位元帶正負號的整數值。 它會定義`+`運算子，將兩個`veryLong`值，並產生所產生`veryLong`值。  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 下列範例示範典型的呼叫來`+`上定義的運算子`veryLong`。  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 如需詳細資訊和範例，請參閱 [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx) (Visual Basic 2005 中的運算子多載)。  
  
## <a name="see-also"></a>另請參閱
- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [如何：定義運算子](./how-to-define-an-operator.md)
- [如何：定義轉換運算子](./how-to-define-a-conversion-operator.md)
- [如何：呼叫運算子程序](./how-to-call-an-operator-procedure.md)
- [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)
