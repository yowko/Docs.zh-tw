---
title: "Comparison Operators (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.<>"
  - "vb.>="
  - "vb.<="
  - "vb.>"
  - "vb.<"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "greater than or equal to operator [Visual Basic]"
  - ">= operator [Visual Basic]"
  - "= operator [Visual Basic]"
  - "< operator [Visual Basic]"
  - "less than operator [Visual Basic]"
  - "relational operators, syntax"
  - "Like operator [Visual Basic]"
  - "<> operator [Visual Basic]"
  - "> operator [Visual Basic]"
  - "equal operator [Visual Basic]"
  - "less than or equal to operator [Visual Basic]"
  - "symbols, operators"
  - "greater than operator [Visual Basic]"
  - "comparing values [Visual Basic]"
  - "operators [Visual Basic], relational"
  - "string comparison [Visual Basic]"
  - "not equal to comparison operator [Visual Basic]"
  - "<= operator [Visual Basic]"
  - "operators [Visual Basic], comparison"
  - "Is operator [Visual Basic]"
  - "comparison operators, Visual Basicl"
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Comparison Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

下列是在 Visual Basic 中定義的比較運算子。  
  
 `<` 運算子  
  
 `<=` 運算子  
  
 `>` 運算子  
  
 `>=` 運算子  
  
 `=` 運算子  
  
 `<>` 運算子  
  
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 這些運算子會比較兩個運算式來判斷是否相等，若不相等，其間的差異有多少。  `Is`、`IsNot` 和 `Like` 在個別的說明頁會有更詳細的討論。  這個頁面更詳細討論了關係比較運算子。  
  
## 語法  
  
```  
  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## 組件  
 `result`  
 必要項。  `Boolean` 值，代表比較的結果。  
  
 `expression`  
 必要項。  任何運算式。  
  
 `comparisonoperator`  
 必要項。  任何關聯式比較運算子。  
  
 `object1`, `object2`  
 必要項。  任何參考物件名稱。  
  
 `string`  
 必要項。  任何 `String` 運算式。  
  
 `pattern`  
 必要項。  任何 `String` 運算式或字元範圍。  
  
## 備註  
 下表包含關係比較運算子以及用來判斷 `result` 是 `True` 還是 `False` 條件的清單。  
  
|運算子|`True` 如果|`False` 如果|  
|---------|---------------|----------------|  
|`<` \(小於\)|`expression1` \< `expression2`|`expression1` \>\= `expression2`|  
|`<=` \(小於或等於\)|`expression1` \<\= `expression2`|`expression1` \> `expression2`|  
|`>` \(大於\)|`expression1` \> `expression2`|`expression1` \<\= `expression2`|  
|`>=` \(大於或等於\)|`expression1` \>\= `expression2`|`expression1` \< `expression2`|  
|`=` \(等於\)|`expression1` \= `expression2`|`expression1` \<\> `expression2`|  
|`<>` \(不等於\)|`expression1` \<\> `expression2`|`expression1` \= `expression2`|  
  
> [!NOTE]
>  [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) 也可以當做指派運算子使用。  
  
 `Is` 運算子、`IsNot` 運算子和 `Like` 運算子有特定的比較功能，不同於上表的運算子功能。  
  
## 比較數字  
 當比較 `Single` 型別運算式與其中一種 `Double` 型別時，會將 `Single` 運算式轉換成 `Double`。  此行為與 Visual Basic 6 中的行為相反。  
  
 同樣地，當您將型別 `Decimal` 的運算式與型別 `Single` 或 `Double` 的運算式做比較時，會將 `Decimal` 運算式轉換成 `Single` 或 `Double`。  若為 `Decimal` 運算式，則會遺失小於 1E\-28 的所有小數值。  遺失此範圍內的小數值可能會導致將兩個數值的比較結果當做相等，然而這兩個數值並不相等。  因此，使用等式 \(`=`\) 比較兩個浮點變數時應謹慎處理。  比較安全的作法是，測試兩數間之差值的絕對值是否小於可接受的容忍值。  
  
### 浮點數非精確度 \(Floating\-point Imprecision\)  
 當您使用浮點數值時，請記住它們在記憶體中並非永遠有精確的表示。  這樣可能會因為某些作業，例如值比較和 [Mod 運算子](../../../visual-basic/language-reference/operators/mod-operator.md)，而導致未預期的結果。  如需詳細資訊，請參閱 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## 比較字串  
 比較字串時，會依字串運算式 \(String Expression\) 的字母排序順序 \(根據 `Option Compare` 設定\) 來評估該字串運算式。  
  
 `Option Compare Binary` 的字串比較是依據字元內部二進位表示所衍生的排序次序而定。  排序次序是由字碼頁 \(Code Page\) 所決定。  下列範例顯示一般二進位排序次序。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` 的字串比較是依據應用程式地區設定 \(Locale\) 所決定的不區分大小寫文字排序次序而定。  當您在前述範例中設定 `Option Compare Text` 並排序字元時，下列文字排序次序會套用：  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### 地區設定依存性  
 設定 `Option Compare Text` 時，字串比較的結果將取決於執行應用程式的地區設定。  在某個地區設定中，兩個字元的比較結果可能相等，另一個地區設定則可能不相等。  如果使用字串比較來做重要決策，例如是否接受登入嘗試，則應該看到地區設定敏感度的警示。  請考慮設定 `Option Compare Binary` 或呼叫 <xref:Microsoft.VisualBasic.Strings.StrComp%2A> 來考量地區設定。  
  
## 使用關係比較運算子進行無型別程式設計 \(Typeless Programming\)  
 在 `Option Strict On` 下，不能以 `Object` 運算式使用關聯式比較運算子。  當 `Option Strict` 是 `Off`，且 `expression1` 或 `expression2` 是 `Object` 運算式，則執行階段型別可決定其比較方式。  下表說明如何依據運算元的執行階段型別來比較運算式和比較的結果。  
  
|如果運算元是|比較是|  
|------------|---------|  
|兩者都是 `String`|依據字串排序特性排序比較。|  
|兩者都是數字|物件轉換成 `Double`，數字比較。|  
|一個是數值，另一個是 `String`|將 `String` 轉換成 `Double`，並且執行數值比較。  如果無法將 `String` 轉換為 `Double`，會擲回 <xref:System.InvalidCastException>。|  
|任一或兩邊是 `String` 以外的參考型別|擲回 <xref:System.InvalidCastException>。|  
  
 數值比較會將 `Nothing` 視為 0。  字串比較會將 `Nothing` 視為 `""` \(空字串\)。  
  
## 多載化  
 關係比較運算子 `<` 。  `<=`、`>`、`>=`、`=`、`<>`\) 可以「*多載*」，這表示當運算元具有某類別或建構的型別時，類別或建構即可重新定義它們的行為。  如果您的程式碼在這種類別或結構上使用任何運算子，就一定要先了解重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
 請注意，[\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) 只能多載為關聯式比較運算子，而非指派運算子。  
  
## 範例  
 下列範例呈現用來比較運算式的各種關聯式比較運算子用法。  關聯式比較運算子傳回用來代表指定之運算式是否評估為 `True` 的 `Boolean` 結果。  當您將 `>` 和 `<` 運算子套用至字串時，可使用字串的一般字母排序次序進行比較。  此順序取決於您的地區設定。  排序是否區分大小寫是依據[Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)的設定而定。  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 在前述範例中，第一個比較傳回 `False`，其餘比較則傳回 `True`。  
  
## 請參閱  
 <xref:System.InvalidCastException>   
 [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)