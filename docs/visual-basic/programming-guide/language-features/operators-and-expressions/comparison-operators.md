---
title: Comparison Operators in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: 873ee31bf9c2ab195d66337d52e4a1bb7075ac76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655132"
---
# <a name="comparison-operators-in-visual-basic"></a>Comparison Operators in Visual Basic
比較運算子比較兩個運算式，並傳回`Boolean`值，表示其值的關聯性。 比較數值、 運算子、 用於比較字串和運算子比較物件有運算子。 本文件討論所有的三種類型的運算子。  
  
## <a name="comparing-numeric-values"></a>比較數值  
 Visual Basic 會比較數值資料，請使用六個數值的比較運算子。 每個運算子會做為運算元評估為數值的兩個運算式。 下表列出的運算子，並顯示每個範例。  
  
|運算子|測試的條件|範例|  
|--------------|----------------------|--------------|  
|`=` （相等）|第二個值是第一個運算式相等的值嗎？|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` （不等比較）|是第一個運算式的值等於第二個值？|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` （小於）|第一個運算式的值大於或等於第二個值是？|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` （大於）|是第一個運算式的值大於第二個值？|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` （小於或等於）|小於或等於第二個值是第一個運算式的值？|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` （大於或等於）|第一個運算式的值是大於或等於第二個值？|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>比較字串  
 Visual Basic 中比較字串時，使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)以及數值比較運算子。 `Like`運算子可讓您指定的模式。 字串接著會比較模式中，以及如果相符，則結果是`True`。 否則，結果就是`False`。 數值運算子可讓您比較`String`值根據其排序次序，如下列範例所示。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 上述範例中的結果會`True`因為中的第一個字串的第一個字元順序是排在第二個字串的第一個字元。 如果第一個字元相同，會繼續下一個字元，在這兩個字串比較，並以此類推。 您也可以測試相等的字串時，使用等號比較運算子，如下列範例所示。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 如果一個字串是另一個的前置詞，例如"aa"和"aaa"，較長的字串視為大於較短的字串。 下列範例將說明這點。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 排序順序根據二進位比較或根據設定的文字比較`Option Compare`。 如需詳細資訊，請參閱[選項比較陳述式](../../../../visual-basic/language-reference/statements/option-compare-statement.md)。  
  
## <a name="comparing-objects"></a>比較物件  
 Visual Basic 會比較兩個物件參考變數與[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)和[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)。 您可以使用這些運算子來判斷兩個參考變數參考相同的物件執行個體。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 在上述範例中，`x Is y`評估為`True`，因為這兩個變數參考相同的執行個體。 對照此結果與以下的範例。  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 在上述範例中，`x Is y`評估為`False`，因為它們雖然變數都參考相同類型的物件，參考該類型的不同執行個體。  
  
 當您想要測試兩個物件未指向相同的執行個體，`IsNot`運算子可讓您避免的文法笨組合`Not`和`Is`。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 在上述範例中，`If a IsNot b`相當於`If Not a Is b`。  
  
### <a name="comparing-object-type"></a>比較物件型別  
 您可以測試具有特定類型的物件是否`TypeOf`...`Is`運算式。 語法如下：  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 當`typename`指定介面型別，則`TypeOf`...`Is`運算式傳回`True`如果物件實作的介面型別。 當`typename`是類別類型，則運算式會傳回`True`的物件是否為指定的類別或衍生自指定類別的類別執行個體。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 在上述範例中，`TypeOf x Is Control`運算式評估為`True`因為的型別`x`是`Button`，後者繼承自`Control`。  
  
 如需詳細資訊，請參閱[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。  
  
## <a name="see-also"></a>另請參閱  
 [數值比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [比較運算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [運算子](../../../../visual-basic/language-reference/operators/index.md)  
 [在 Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [在 Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
