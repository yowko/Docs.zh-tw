---
title: "- 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Negate
- vb.-
dev_langs:
- VB
helpviewer_keywords:
- '- operator [Visual Basic]'
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator
- operators [Visual Basic], arithmetic
- subtraction operator, syntax
- arithmetic operators, subtraction
- difference operator
- math operators
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7f45094da7bc61687d9c767d25858aa214bf1978
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="--operator-visual-basic"></a>- 運算子 (Visual Basic)
傳回兩個數值運算式或數值運算式的負值之間的差異。  
  
## <a name="syntax"></a>語法  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>組件  
 `expression1`  
 必要項。 任何數值運算式。  
  
 `expression2`  
 除非`–`運算子計算的負值。 任何數值運算式。  
  
## <a name="result"></a>結果  
 結果是之間的差異`expression1`和`expression2`，相反的值或`expression1`。  
  
 結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。 請參閱中的 「 整數算術 」 資料表[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
## <a name="supported-types"></a>支援的型別  
 所有數字型別。 這包括不帶正負號和浮點類型和`Decimal`。  
  
## <a name="remarks"></a>備註  
 在先前所示的語法中顯示的第一個使用`–`運算子是*二進位*算術減法運算子的兩個數值運算式之間的差異。  
  
 在先前所示的語法中顯示的第二個使用方式`–`運算子是*一元*負運算子的運算式的負值。 在這種情況下，否定包含反轉的正負號`expression1`使結果為正數如果`expression1`是負數。  
  
 如果任一個運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)、`–`運算子會將其視為零。  
  
> [!NOTE]
>  `–`運算子可以*多載*，也就是說，類別或結構可以重新定義它的行為時運算元具有該類別或結構的型別。 如果您的程式碼會使用此運算子在這種類別或結構，請確定您已了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`–`運算子來計算並傳回兩個數字，之間的差異，然後要變換正負號的數字。  
  
 [!code-vb[VbVbalrOperators #&10;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 在執行這些陳述式，`binaryResult`包含 124.45 和`unaryResult`包含 –334.90。  
  
## <a name="see-also"></a>另請參閱  
 [-= 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [在 Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

