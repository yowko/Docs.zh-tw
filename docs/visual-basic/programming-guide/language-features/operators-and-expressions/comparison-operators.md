---
title: 比較運算子
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
ms.openlocfilehash: fbe81532bb435e54e694f9b5fe9dd497392f31e1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071764"
---
# <a name="comparison-operators-in-visual-basic"></a>Comparison Operators in Visual Basic

比較運算子會比較兩個運算式，並傳回 `Boolean` 值，表示其值的關聯性。 有一些運算子可比較數值、比較字串的運算子，以及比較物件的運算子。 本文將討論這三種運算子類型。  
  
## <a name="comparing-numeric-values"></a>比較數值  

 Visual Basic 使用六個數值比較運算子來比較數值。 每個運算子都採用兩個評估為數值的運算式做為運算元。 下表列出這些運算子，並顯示每個運算子的範例。  
  
|運算子|測試的條件|範例|  
|--------------|----------------------|--------------|  
|`=` (相等) |第一個運算式的值是否等於第二個運算式的值？|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (不相等) |第一個運算式的值是否不等於第二個運算式的值？|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (小於) |第一個運算式的值是否小於第二個運算式的值？|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (大於) |第一個運算式的值是否大於第二個運算式的值？|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (小於或等於) |第一個運算式的值是否小於或等於第二個運算式的值？|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (大於或等於) |第一個運算式的值是否大於或等於第二個運算式的值？|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>比較字串  

 Visual Basic 使用 [Like 運算子](../../../language-reference/operators/like-operator.md) 以及數值比較運算子來比較字串。 `Like`運算子可讓您指定模式。 然後，此字串會與模式進行比較，如果相符，則結果為 `True` 。 否則，結果為 `False`。 數值運算子可讓您 `String` 根據值的排序次序來比較值，如下列範例所示。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 上述範例中的結果是 `True` 因為第一個字串中的第一個字元會在第二個字串的第一個字元之前排序。 如果第一個字元相等，則比較會繼續進行兩個字串中的下一個字元，依此類推。 您也可以使用等號比較運算子來測試字串是否相等，如下列範例所示。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 如果有一個字串是另一個字串的前置詞，例如 "aa" 和 "aaa"，則較長的字串會被視為大於較短的字串。 下列範例將說明這點。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 排序次序是根據的設定，以二進位比較或文字比較為基礎 `Option Compare` 。 如需詳細資訊，請參閱 [Option Compare 語句](../../../language-reference/statements/option-compare-statement.md)。  
  
## <a name="comparing-objects"></a>比較物件  

 Visual Basic 會比較兩個物件參考變數與「 [是」運算子](../../../language-reference/operators/is-operator.md) 和 [IsNot 運算子](../../../language-reference/operators/isnot-operator.md)。 您可以使用其中一個運算子來判斷兩個參考變數是否參考相同的物件實例。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 在上述範例中，會 `x Is y` 評估為 `True` ，因為這兩個變數都參考相同的實例。 將此結果與下列範例做比較。  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 在上述範例中， `x Is y` 會評估為 `False` ，因為雖然變數參考相同類型的物件，但它們參考該類型的不同實例。  
  
 當您想要測試兩個未指向相同實例的物件時， `IsNot` 運算子可讓您避免和的文法笨拙組合 `Not` `Is` 。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 在上述範例中， `If a IsNot b` 相當於 `If Not a Is b` 。  
  
### <a name="comparing-object-type"></a>比較物件類型  

 您可以使用 `TypeOf` ... 運算式測試物件是否為特定類型。 `Is` 語法如下：  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 當 `typename` 指定介面類別型時，如果物件會執行介面型別，則會傳回 `TypeOf` ... `Is` 運算式。 `True` 當 `typename` 是類別型別時， `True` 如果物件是指定類別的實例或衍生自指定類別的類別，則運算式會傳回。 下列範例將說明這點。  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 在上述範例中， `TypeOf x Is Control` 運算式會評估為 `True` ，因為的型別 `x` 是 `Button` ，它會繼承自 `Control` 。  
  
 如需詳細資訊，請參閱 [TypeOf 運算子](../../../language-reference/operators/typeof-operator.md)。  
  
## <a name="see-also"></a>另請參閱

- [數值比較](value-comparisons.md)
- [比較運算子](../../../language-reference/operators/comparison-operators.md)
- [運算子](../../../language-reference/operators/index.md)
- [Visual Basic 的算術運算子](arithmetic-operators.md)
- [Visual Basic 中的串連運算子](concatenation-operators.md)
- [Visual Basic 中的邏輯運算子和位元運算子](logical-and-bitwise-operators.md)
