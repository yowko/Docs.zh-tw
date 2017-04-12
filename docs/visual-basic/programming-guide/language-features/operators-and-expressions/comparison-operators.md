---
title: "在 Visual Basic 中的比較運算子 |Microsoft 文件"
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
- comparison operators, comparing strings
- comparison operators, comparing objects
- strings [Visual Basic], comparing
- comparison operators
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers, comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values, comparing
- comparison operators, comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 6185d1676f2cd160c9c3e855cce4a6d2bbe2ffb4
ms.lasthandoff: 03/13/2017

---
# <a name="comparison-operators-in-visual-basic"></a>Comparison Operators in Visual Basic
比較運算子比較兩個運算式，並傳回`Boolean`值，表示其值的關聯性。 有運算子來比較數值、 運算子來比較字串和比較物件的運算子。 本文將討論這三種運算子。  
  
## <a name="comparing-numeric-values"></a>比較數值  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]比較數值資料，請使用六個數值的比較運算子。 每個運算子會使用兩個運算式評估為數值，做為運算元。 下表列出的運算子，並顯示每個範例。  
  
|運算子|測試的條件|範例|  
|--------------|----------------------|--------------|  
|`=`（相等）|第二個值是第一個運算式相等的值？|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>`（不等）|是第一個運算式的值等於第二個值？|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<`（小於）|是第一個運算式的值大於或等於第二個值？|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>`（大於）|是第一個運算式的值大於第二個值？|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=`（小於或等於）|小於或等於第二個值是第一個運算式的值？|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=`（大於或等於）|大於或等於第二個值是第一個運算式的值？|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>比較字串  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]比較字串使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)以及數值比較運算子。 `Like`運算子可讓您指定的模式。 字串比較是模式，以及如果相符，則結果是`True`。 否則，結果就是`False`。 數值運算子可讓您比較`String`值根據其排序次序，如下列範例所示。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 在上述範例中的結果是`True`因為第一個字串的第一個字元順序是排在第二個字串的第一個字元。 如果第一個字元相同，比較會繼續進行下一個字元，在這兩個字串，依此類推。 您也可以測試使用等號比較運算子，如下列範例所示的字串相等。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 如果某字串是另一個前置詞，例如"aa"和"aaa"，較長的字串視為大於較短的字串。 下列範例將說明這點。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 排序順序根據二進位比較或設定而定的文字比較`Option Compare`。 如需詳細資訊，請參閱[選項比較陳述式](../../../../visual-basic/language-reference/statements/option-compare-statement.md)。  
  
## <a name="comparing-objects"></a>比較物件  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]比較兩個物件參考變數[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)和[IsNot 運算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)。 您可以使用這些運算子來判斷兩個參考變數參考相同的物件執行個體。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators #&65;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 在上述範例中，`x Is y`評估為`True`，因為這兩個變數參考相同的執行個體。 對照此結果與以下的範例。  
  
 [!code-vb[VbVbalrOperators #&66;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 在上述範例中，`x Is y`評估為`False`，因為它們雖然變數參考相同類型的物件，參考該類型的不同執行個體。  
  
 當您想要測試兩個物件未指向相同的執行個體，`IsNot`運算子可讓您避免文法笨拙的組合`Not`和`Is`。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators #&67;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 在上述範例中，`If a IsNot b`相當於`If Not a Is b`。  
  
### <a name="comparing-object-type"></a>比較物件型別  
 您可以測試物件是否屬於特定型別與`TypeOf`...`Is`運算式。 語法如下：  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 當`typename`指定介面型別，則`TypeOf`...`Is`運算式傳回`True`如果物件實作的介面型別。 當`typename`是類別型別，則運算式會傳回`True`的物件是否屬於指定的類別或衍生自指定類別的類別執行個體。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators #&68;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 在上述範例中，`TypeOf x Is Control`運算式評估為`True`因為的型別`x`是`Button`，繼承自`Control`。  
  
 如需詳細資訊，請參閱[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。  
  
## <a name="see-also"></a>另請參閱  
 [值的比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [比較運算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [運算子](../../../../visual-basic/language-reference/operators/index.md)   
 [在 Visual Basic 中的算術運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [在 Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
