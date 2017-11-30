---
title: "比較運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa450f7978f46196663c7534b31597b04d80482a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-operators-visual-basic"></a>比較運算子 (Visual Basic)
以下是定義在 Visual Basic 中的比較運算子。  
  
 `<`運算子  
  
 `<=`運算子  
  
 `>`運算子  
  
 `>=`運算子  
  
 `=`運算子  
  
 `<>`運算子  
  
 [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like 運算子](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 這些運算子比較兩個運算式來判斷相等，以及如果不是，有何差異。 `Is``IsNot`，和`Like`都會在個別的 [說明] 頁中詳細討論。 關係比較運算子會詳細討論此頁面上。  
  
## <a name="syntax"></a>語法  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>組件  
 `result`  
 必要項。 A`Boolean`值，代表比較的結果。  
  
 `expression`  
 必要項。 任何運算式。  
  
 `comparisonoperator`  
 必要項。 任何關聯的比較運算子。  
  
 `object1`, `object2`  
 必要項。 任何參考的物件名稱。  
  
 `string`  
 必要項。 任何 `String` 運算式。  
  
 `pattern`  
 必要項。 任何`String`運算式或字元範圍。  
  
## <a name="remarks"></a>備註  
 下表包含一份關係比較運算子的條件來決定是否`result`是`True`或`False`。  
  
|運算子|`True`如果|`False`如果|  
|--------------|---------------|----------------|  
|`<`（小於）|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=`（小於或等於）|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>`（大於）|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=`（大於或等於）|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=`（等於）|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>`（不等於）|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)也會使用指派運算子。  
  
 `Is`運算子，`IsNot`運算子，而`Like`運算子有特定的比較功能，來與上表中的運算子的不同。  
  
## <a name="comparing-numbers"></a>比較的數字  
 當您比較型別的運算式`Single`類型的其中一個`Double`、`Single`運算式轉換成`Double`。 此行為是以 Visual Basic 6 中的行為。  
  
 同樣地，當您比較型別的運算式`Decimal`型別的運算式`Single`或`Double`、`Decimal`運算式轉換成`Single`或`Double`。 如`Decimal`運算式中，任何小數的值小於 1E 28 可能會遺失。 這類小數的值遺失可能會導致不時，比較結果為相等的兩個值。 基於這個理由，您應該謹慎使用等號時 (`=`) 比較兩個浮點變數。 它會測試是否兩個數字之間的差異的絕對值是可接受的容忍小於比較安全。  
  
### <a name="floating-point-imprecision"></a>浮點不精確而受到  
 當您使用浮點數值，請記住它們在記憶體中不一定有精確的表示。 這可能會導致非預期的結果從某些作業，例如值比較而[Mod 運算子](../../../visual-basic/language-reference/operators/mod-operator.md)。 如需詳細資訊，請參閱[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## <a name="comparing-strings"></a>比較字串  
 當您比較字串時，會評估字串運算式根據字母排序次序，取決於`Option Compare`設定。  
  
 `Option Compare Binary`基底的字串比較衍生自內部的二進位表示法的字元的排序次序。 排序順序取決於字碼頁。 下列範例示範典型的二進位排序順序。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text`基底的字串比較不區分大小寫、 文字排序順序取決於您的應用程式地區設定。 當您將`Option Compare Text`和排序在上述範例中的字元，請套用下列的文字排序順序：  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>地區設定相依性  
 當您將`Option Compare Text`，字串比較的結果可能會相依於應用程式執行所在的地區設定。 兩個字元可能會比較為相等，但不是在另一個地區設定內。 如果您使用字串比較做出重要的項目，例如是否要接受嘗試登入，您應該區分地區設定的警示。 請考慮設定`Option Compare Binary`或呼叫<xref:Microsoft.VisualBasic.Strings.StrComp%2A>，其地區設定列入考量。  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>使用關聯式的比較運算子的無類型程式設計  
 與關聯式的比較運算子的用法`Object`下，不允許運算式`Option Strict On`。 當`Option Strict`是`Off`，任一個`expression1`或`expression2`是`Object`運算式中，執行階段類型可讓您決定在進行比較。 下表來比較運算式和比較，根據執行階段類型的運算元的結果。  
  
|如果運算元都是|比較|  
|---------------------|-------------------|  
|兩者`String`|排序依據排序特性的字串比較。|  
|這兩個數值|物件轉換成`Double`，數值比較。|  
|一個數值和一個`String`|`String`轉換成`Double`而且會執行數值的比較。 如果`String`無法轉換成`Double`、<xref:System.InvalidCastException>就會擲回。|  
|或兩者皆是以外的參考型別`String`|擲回 <xref:System.InvalidCastException>。|  
  
 將數字比較`Nothing`為 0。 字串比較視為`Nothing`為`""`（空字串）。  
  
## <a name="overloading"></a>多載化  
 關係比較運算子 (`<`。 `<=``>`， `>=`， `=`， `<>`) 可以是*多載*，這表示，類別或結構可以重新定義其行為時的運算元有該類別或結構的類型。 如果您的程式碼會使用這些運算子的任何這類類別或結構上，請確定您了解重新定義的行為。 如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
 請注意， [= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)僅做為關聯式的比較運算子、 指派運算子可以多載。  
  
## <a name="example"></a>範例  
 下列範例顯示各種關係比較運算子，用來比較運算式用法。 關聯式的比較運算子會傳回`Boolean`結果，表示是否在指定的運算式評估為`True`。 當您將套用`>`和`<`字串運算子，則會進行比較使用標準字母排序次序的字串。 此順序可能相依於地區設定。 排序是否會區分大小寫取決於[Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)設定。  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 在上述範例中，傳回第一個比較`False`和其他的比較會傳回`True`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.InvalidCastException>  
 [= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [運算子 (依功能排列)](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [資料類型的疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [在 Visual Basic 中的比較運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
