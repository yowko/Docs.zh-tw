---
title: "Or 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Or
dev_langs:
- VB
helpviewer_keywords:
- Or operator
- operators [Visual Basic], bitwise
- inclusive Or operator
- bitwise operators, OR operator
- Or keyword
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison
- logical disjunction
- disjunction operator
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: 12
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
ms.openlocfilehash: f3f6c013df6cd5c3b99e465bdc8bb0b4ead6bdf4
ms.lasthandoff: 03/13/2017

---
# <a name="or-operator-visual-basic"></a>Or 運算子 (Visual Basic)
對兩個執行邏輯分離`Boolean`運算式或兩個數值運算式的位元分離。  
  
## <a name="syntax"></a>語法  
  
```  
  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`Boolean`或數值運算式。 如`Boolean`相較之下，`result`是兩個 （含） 的邏輯分離`Boolean`值。 位元運算，如`result`是數值，代表兩個數值位元模式 （含） 的位元分離。  
  
 `expression1`  
 必要項。 任何`Boolean`或數值運算式。  
  
 `expression2`  
 必要項。 任何`Boolean`或數值運算式。  
  
## <a name="remarks"></a>備註  
 如`Boolean`相較之下，`result`是`False`如果且只有兩個`expression1`和`expression2`評估為`False`。 下表將說明如何`result`決定。  
  
|If `expression1` is|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  在`Boolean`相較之下，`Or`運算子一律會評估這兩個運算式，其中包括程序呼叫。 [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)執行*最少運算*，這表示如果`expression1`是`True`，然後`expression2`不會評估。  
  
 位元運算，如`Or`運算子執行兩個數值運算式中的相同位置的位元的位元比較，並設定對應位元中`result`根據下表。  
  
|如果位元`expression1`是|在位元和`expression2`是|中的位元`result`是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  由於邏輯和位元運算子的優先順序低於其他算術和關係運算子，任何位元運算應該加上括號，以確保執行結果的正確性。  
  
## <a name="data-types"></a>資料類型  
 如果運算元組成一個`Boolean`Visual Basic 運算式和一個數值運算式，將轉換`Boolean`數值的運算式 (為 – 1 `True` 0 `False`) 和執行位元運算。  
  
 如`Boolean`相較之下，結果的資料型別是`Boolean`。 位元的比較結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。 請參閱 < 關聯式和位元比較 」 的表格[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
## <a name="overloading"></a>多載化  
 `Or`運算子可以*多載*，也就是說，類別或結構可以重新定義它的行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用此運算子在這種類別或結構，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Or`運算子，對兩個運算式執行內含的邏輯分離。 結果是`Boolean`值，表示其中兩個運算式是否`True`。  
  
 [!code-vb[VbVbalrOperators #&35;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 上述範例產生的結果`True`， `True`，和`False`分別。  
  
## <a name="example"></a>範例  
 下列範例會使用`Or`運算子的兩個數值運算式的個別位元執行內含邏輯分離。 如果任一運算元的對應位元會設為 1，會設定結果模式中的位元。  
  
 [!code-vb[VbVbalrOperators #&36;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 上述範例中會分別產生 10、 14 和 14 的結果。  
  
## <a name="see-also"></a>另請參閱  
 [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [在 Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)   
 [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
