---
title: "+ Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.+"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arithmetic operators, addition"
  - "+ operator"
  - "concatenation operators, syntax"
  - "strings [Visual Basic], concatenating"
  - "sum operator"
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# + Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

加入兩個數字，或傳回數值運算式的正值。  也可用於串連兩個字串運算式。  
  
## 語法  
  
```  
  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`expression1`|必要項。  任意數值或字串運算式。|  
|`expression2`|除非 `+` 運算子計算的是負值，否則為必要項。  任意數值或字串運算式。|  
  
## 結果  
 如果 `expression1` 和 `expression2` 都是數值，則結果會是其算術總和。  
  
 如果缺少 `expression2`，則 `+` 運算子會是運算式之未變更值的「*一元*」識別運算子。  就這個意義來說，運算保留有 `expression1` 的正負號，因此如果 `expression1` 是負值，則結果就是負值。  
  
 如果 `expression1` 和 `expression2` 都是字串，則結果會是其值的串連。  
  
 如果 `expression1` 和 `expression2` 是混合型別，採取的動作則視其型別、其內容和 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) 的設定而定。  如需詳細資訊，請參閱＜備註＞中的表格。  
  
## 支援類型  
 所有數字型別，包括不帶正負號和浮點型別，以及 `Decimal` 和 `String`。  
  
## 備註  
 一般而言，`+` 會在可能時執行算術加法，且只有在兩個運算式都是字串時才進行串連。  
  
 如果兩個運算式都不是 `Object`，則 Visual Basic 會採取下列動作。  
  
|||  
|-|-|  
|運算式的資料型別|編譯器的動作|  
|這兩個運算式都是數字資料型別 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single` 或 `Double`\)|相加。  結果資料型別會是數字型別，適用於 `expression1` 和 `expression2` 的資料型別。  請參閱[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」表。|  
|這兩個運算式的型別都是 `String`|串連。|  
|一個運算式為數值資料型別，另一個是字串|如果 `Option Strict` 為 `On`，即產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off`，則將 `String` 隱含轉換成 `Double` 並且相加。<br /><br /> 如果無法將 `String` 轉換成 `Double`，則擲回 <xref:System.InvalidCastException> 例外狀況。|  
|一個運算式為數值資料型別，另一個是 [Nothing](../../../visual-basic/language-reference/nothing.md)|相加 \(將 `Nothing` 的值當成零\)。|  
|一個運算式為字串，另一個是 `Nothing`|串連 \(將 `Nothing` 的值當成 ""\)。|  
  
 如果其中一個運算式是 `Object` 運算式，則 Visual Basic 會採取下列動作。  
  
|||  
|-|-|  
|運算式的資料型別|編譯器的動作|  
|`Object` 運算式會保留數值，而另一個則是數字資料型別|如果 `Option Strict` 為 `On`，即產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off`，則相加。|  
|`Object`運算式會保留數值，而另一個的型別則為 `String`|如果 `Option Strict` 為 `On`，即產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off`，則將 `String` 隱含轉換成 `Double` 並且相加。<br /><br /> 如果無法將 `String` 轉換成 `Double`，則擲回 <xref:System.InvalidCastException> 例外狀況。|  
|`Object` 運算式會保留字串，而另一個則是數字資料型別|如果 `Option Strict` 為 `On`，即產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off`，則將字串 `Object` 隱含轉換成 `Double` 並且相加。<br /><br /> 如果無法將字串 `Object` 轉換成 `Double`，則擲回 <xref:System.InvalidCastException> 例外狀況。|  
|`Object` 運算式會保留字串，而另一個的型別則為 `String`|如果 `Option Strict` 為 `On`，即產生編譯器錯誤。<br /><br /> 如果 `Option Strict` 為 `Off`，則會將 `Object` 隱含轉換成 `String` 並且串連。|  
  
 如果這兩個運算式都是 `Object` 運算式，則 Visual Basic 會採取下列動作 \(僅限 `Option Strict Off`\)。  
  
|||  
|-|-|  
|運算式的資料型別|編譯器的動作|  
|這兩個 `Object` 運算式都保留數值|相加。|  
|這兩個 `Object` 運算式都是型別 `String`|串連。|  
|其中一個 `Object` 運算式會保留數值，而另一個則保留字串|將字串 `Object` 隱含轉換成 `Double` 並且相加。<br /><br /> 如果無法將字串 `Object` 轉換成數值，則擲回 <xref:System.InvalidCastException> 例外狀況。|  
  
 如果其中一個 `Object` 運算式評估為 [Nothing](../../../visual-basic/language-reference/nothing.md) 或 <xref:System.DBNull>，則 `+` 運算子會將它視為值為 "" 的 `String`。  
  
> [!NOTE]
>  當使用 `+` 運算子時，可能無法判斷是否會發生加法或字串串連。  使用 `&` 運算子執行串連，以排除模稜兩可的情況並提供自我文件化的程式碼。  
  
## 多載化  
 `+` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列範例使用 `+` 運算子將數字相加。  如果運算元都是數值，則 Visual Basic 會計算算術結果。  算術結果代表兩個運算元的總和。  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 您也可使用 `+` 運算子來串連字串。  如果運算元都是字串，則 Visual Basic 會串連它們。  串連結果代表由兩個運算元 \(一個接著另一個\) 的內容組合而成的單一字串。  
  
 如果運算元是混合型別，結果則視 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) 的設定而定。  下列範例說明 `Option Strict` 為 `On` 時的結果。  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 下列範例說明 `Option Strict` 為 `Off` 時的結果。  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 若要排除模稜兩可的情形，則應使用 `&` 運算子，而非 `+` 執行串連。  
  
## 請參閱  
 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)