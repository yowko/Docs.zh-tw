---
title: "Arithmetic Operators in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "type safety"
  - "operators [Visual Basic], bitwise"
  - "operators [Visual Basic], bit-shift"
  - "bitwise operators"
  - "bit-shift operators"
  - "zero, division by zero"
  - "operators [Visual Basic], arithmetic"
  - "division, by zero"
  - "Visual Basic code, operators"
  - "arithmetic operators, about arithmetic operators"
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Arithmetic Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

算術運算子通常是用來執行許多熟悉的算術運算，這些算術運算涉及常值、變數、其他運算式、函式和屬性 \(Property\) 呼叫以及常數所代表的數值計算。  同樣歸為算術運算子的還有位元移位運算子，此運算子是在運算元的個別位元層次運作，可將運算元的位元模式往左移動或往右移動。  
  
## 算術運算  
 您可以在運算式中用 [\+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) 將兩個數值相加，或是用 [\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md) 將某數值減另一數值，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 負運算也會使用 [\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，但只使用一個運算元，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 乘法及除法分別會使用 [\* Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md) 及 [\/ Operator](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 乘冪運算會使用 [^ Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 整數除法會使用 [\\ Operator](../../../../visual-basic/language-reference/operators/integer-division-operator.md)執行。  整數除法會傳回商數，也就是可以用除數對被除數進行分割的整數次數，而不考慮任何餘數。  對此運算子而言，除數和被除數都必須是整數類資料型別 \(Integral Type\) \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 和 `ULong`\)。  所有其他的型別都必須先轉換成整數型別。  下列為整數除法的範例。  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 模數算術是使用 [Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md) 來執行。  這個運算子會在用除數對被除數進行整數次數分割後傳回餘數。  如果除數及被除數都是整數型別，則傳回值是整數。  如果除數及被除數都是浮點型別，則傳回值也會是浮點。  以下為這項行為的範例。  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### 嘗試以零為除數  
 除數為零會因所涉及的資料型別而有不同的結果。  在整數除法 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`\) 中，[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 會擲回 <xref:System.DivideByZeroException> 例外狀況。  在 `Decimal` 或 `Single` 資料型別上進行除法運算時，[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 也會擲回 <xref:System.DivideByZeroException> 例外狀況。  
  
 在涉及 `Double` 資料型別的浮點除法中，並不會擲回任何例外狀況，而是視除數而定，產生代表 <xref:System.Double.NaN>、<xref:System.Double.PositiveInfinity> 或 <xref:System.Double.NegativeInfinity> 的類別成員。  下表為嘗試將 `Double` 值除以零之各種結果的摘要。  
  
|||||  
|-|-|-|-|  
|被除數資料型別|除數資料型別|被除數值|結果|  
|`Double`|`Double`|0|<xref:System.Double.NaN> \(非數學上所定義的值\)|  
|`Double`|`Double`|\> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 遇到 <xref:System.DivideByZeroException> 例外狀況時，可以使用它的成員協助您進行處理。  例如，<xref:System.Exception.Message%2A> 屬性可保有例外狀況的訊息文字。  如需詳細資訊，請參閱 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## 位元移位作業  
 位元移位作業會在位元模式上執行算術移位 \(Arithmetic Shift\)。  模式是在左方的運算元內，右方的運算元則指定要將模式移位的位置數目。  您可以使用 [\>\> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md) 將模式移位到右方，或使用 [\<\< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md) 將模式移位到左方。  
  
 模式運算元的資料型別必須是 `SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`。  位移量運算元的資料型別必須是 `Integer`，或者必須擴展為 `Integer`。  
  
 算術移位不是循環型，這表示位元從結果某端移出後，就不會再從另一端進入。  移位空下的位元位置設定如下：  
  
-   算術左移位所空下的位置為 0  
  
-   正數的算術右移位所空下的位置為 0  
  
-   不帶正負號資料型別 \(`Byte`、`UShort`、`UInteger`、`ULong`\) 的算術右移位所空下的位置為 0  
  
-   負數 \(`SByte`、`Short`、`Integer` 或 `Long`\) 的算術右移位所空下的位置為 1  
  
 下列範例會將 `Integer` 值往左移動和往右移動。  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 算術移位不會產生溢位例外狀況。  
  
## 位元運算  
 除了做為邏輯運算子之外，當 `Not`、`Or`、`And` 及 `Xor` 用在數值運算時，也會執行位元算術。  如需詳細資訊，請參閱[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)中「位元運算」的部分。  
  
## 型別安全  
 運算元通常應屬於相同型別。  例如，如果您正在進行加上 `Integer` 變數的運算，則應將它與另一個 `Integer` 變數相加，並將結果指派給同樣屬於 `Integer` 型別的變數。  
  
 使用 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是確保良好型別安全之程式碼撰寫做法的其中一種方式。  如果您設定 `Option Strict On`，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 就會自動執行「*型別安全*」\(Type\-Safe\) 轉換。  例如，如果您嘗試將 `Integer` 變數與 `Double` 變數相加，並將值指派給 `Double` 變數，則因為 `Integer` 變數可以轉換成 `Double`，使得資料不會遺失，所以可正常執行運算。  相反地，型別不安全的轉換會在 `Option Strict On` 時，造成編譯器錯誤。  例如，如果您嘗試將 `Integer` 變數與 `Double` 變數相加，並將值指派給 `Integer` 變數，則因為 `Double` 變數無法隱含轉換成 `Integer` 型別，所以會產生編譯器錯誤。  
  
 不過，如果設定 `Option Strict Off`，則 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 可允許隱含由大變小的轉換發生，但這可能會造成未預期的資料或精確度遺失。  因此，建議您在撰寫實際執行的程式碼時，使用 `Option Strict On`。  如需詳細資訊，請參閱[Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## 請參閱  
 [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Bit Shift Operators](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)