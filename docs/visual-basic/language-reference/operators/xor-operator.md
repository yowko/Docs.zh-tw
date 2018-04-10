---
title: Xor 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b14f11f2df2df9c29e88e9188390cfe245d2cb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xor-operator-visual-basic"></a>Xor 運算子 (Visual Basic)
執行邏輯排除在兩個`Boolean`運算式或兩個數值運算式的位元互斥。  
  
## <a name="syntax"></a>語法  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 任何`Boolean`或數值的變數。 布林比較，`result`是兩個邏輯排除 （獨佔邏輯分離）`Boolean`值。 位元運算，如`result`是數值，表示兩個數值的位元模式的位元互斥 （位元排除分離）。  
  
 `expression1`  
 必要項。 任何`Boolean`或數值運算式。  
  
 `expression2`  
 必要項。 任何`Boolean`或數值運算式。  
  
## <a name="remarks"></a>備註  
 布林比較，`result`是`True`如果且只有其中一個`expression1`和`expression2`評估為`True`。 也就是說，如果且只有`expression1`和`expression2`評估為相反`Boolean`值。 下表將說明如何`result`決定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  布林值相較之下，`Xor`運算子一律會評估這兩個運算式，可能會使程序呼叫。 沒有任何最少運算的對應項目來`Xor`，因為結果一定會相依於這兩個運算元。 如*最少運算*邏輯運算子，請參閱[AndAlso 運算子](../../../visual-basic/language-reference/operators/andalso-operator.md)和[OrElse 運算子](../../../visual-basic/language-reference/operators/orelse-operator.md)。  
  
 位元運算，如`Xor`運算子中兩個數值運算式執行位元的比較相同位置的位元並對應中位元設`result`根據下表。  
  
|如果位元`expression1`是|在位元和`expression2`是|中的位元`result`是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  因為邏輯和位元運算子會有較低的優先順序高於其他算術和關係運算子，所以任何位元運算應該括在括號可確保能夠正確執行。  
  
 例如，5 `Xor` 3 為 6。 若要查看為什麼會這樣，轉換成 5 和 3 101 和 011 其二進位表示。 然後使用上表，判斷 101 Xor 011 為 110 時，也就是十進位數字 6 的二進位表示法。  
  
## <a name="data-types"></a>資料類型  
 如果運算元組成一個`Boolean`Visual Basic 運算式和一個數值運算式，將轉換`Boolean`為數值運算式 (如 – 1`True`以 0 代表`False`) 和執行位元運算。  
  
 如`Boolean`比較結果的資料類型是`Boolean`。 位元的比較，將結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。 請參閱 「 關聯式和位元比較 」 的表格[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
## <a name="overloading"></a>多載化  
 `Xor`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Xor`上兩個運算式執行邏輯排除 （獨佔邏輯分離） 運算子。 結果是`Boolean`值，表示只有其中一個運算式是否`True`。  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 前一個範例產生的結果`False`， `True`，和`False`分別。  
  
## <a name="example"></a>範例  
 下列範例會使用`Xor`運算子的兩個數值運算式的個別位元執行邏輯排除 （獨佔邏輯分離）。 如果只有其中一個運算元的對應位元設為 1，會設定結果模式中的位元。  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 前一個範例會分別產生 2，12 和 14 的結果。  
  
## <a name="see-also"></a>另請參閱  
 [邏輯/位元運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [在 Visual Basic 中的邏輯和位元運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
