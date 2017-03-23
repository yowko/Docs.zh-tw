---
title: "在 Visual Basic 中的算術運算子 |Microsoft 文件"
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
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators
- bit-shift operators
- zero, division by zero
- operators [Visual Basic], arithmetic
- division, by zero
- Visual Basic code, operators
- arithmetic operators, about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c724bf8b6794e71d49b32c7d3ce9e010f541f68f
ms.lasthandoff: 03/13/2017

---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic 的算術運算子
算術運算子用來執行許多熟悉的算術作業涉及的常值、 變數、 其他運算式、 函式和屬性呼叫和常數所代表的數值計算。 搭配算術運算子也分類為位元移位運算子會在運算元的個別位元的層級執行動作，並向左或向右移位的位元模式。  
  
## <a name="arithmetic-operations"></a>算術運算  
 一起使用的運算式中，您可以加入兩個值[+ 運算子](../../../../visual-basic/language-reference/operators/addition-operator.md)，或從另一個具有減去[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators #&57;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 也會使用負[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，但只有一個運算元，如下列範例示範。  
  
 [!code-vb[VbVbalrOperators #&58;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 乘法和除法使用[* 運算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)和[/ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)分別，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators #&59;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 乘冪使用[^ 運算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators #&60;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 整數除法場所使用[\ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)。 整數除法傳回商數，也就是代表次數的整數除數分成數個而不考慮任何餘數被除數。 除數與被除數必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，和`ULong`) 這個運算子。 所有其他型別必須先轉換成整數型別。 下列範例將示範整數除法。  
  
 [!code-vb[VbVbalrOperators #&61;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 使用執行模數算術[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)。 這個運算子會傳回其餘部分對被除數除以除數後的次數的整數。 如果除數與被除數是整數類資料類型，傳回的值是整數類資料。 如果除數與被除數浮點型別，傳回的值也是浮點數。 下列範例將示範這個行為。  
  
 [!code-vb[VbVbalrOperators #&62;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators #&63;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>嘗試的除以零  
 除數為零會有不同的結果，視所涉及的資料類型而定。 In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] throws a <xref:System.DivideByZeroException> exception.</xref:System.DivideByZeroException> 在除法運算`Decimal`或`Single`資料型別，[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]也會擲回<xref:System.DivideByZeroException>例外狀況。</xref:System.DivideByZeroException>  
  
 涉及浮點劃分`Double`資料型別，擲回任何例外狀況，且結果為類別成員代表<xref:System.Double.NaN>， <xref:System.Double.PositiveInfinity>，或<xref:System.Double.NegativeInfinity>，根據被除數。</xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity> </xref:System.Double.NaN> 下表摘要說明不同的結果的嘗試將`Double`除以零的值。  
  
|被除數資料型別|除數資料型別|被除數的值|結果|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>（不是以數學方式定義數字）</xref:System.Double.NaN>|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity></xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity></xref:System.Double.NegativeInfinity>|  
  
 當您攔截<xref:System.DivideByZeroException>例外狀況，您可以使用其成員，以協助您處理它。</xref:System.DivideByZeroException> 例如，<xref:System.Exception.Message%2A>屬性會保留例外狀況的訊息文字。</xref:System.Exception.Message%2A> 如需詳細資訊，請參閱[試...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="bit-shift-operations"></a>位元移位作業  
 位元移位作業執行算術移位的位元模式上。 模式中左邊的運算元，而右運算元所指定的位置模式移位的數目。 您可以將模式移位至右側[>> 運算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)或向左與[ <> </> ](../../../../visual-basic/language-reference/operators/left-shift-operator.md)。  
  
 模式運算元的資料型別必須是`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`。 Shift 量運算元的資料型別必須是`Integer`或必須擴展為`Integer`。  
  
 算術移位不是循環，這表示移出某一端之結果的位元會重新引入另一端。 移位空出的位元位置會設定，如下所示︰  
  
-   0 表示算術左移位  
  
-   0 為正數的算術右移位的  
  
-   0 代表不帶正負號的資料類型的算術右移位 (`Byte`， `UShort`， `UInteger`， `ULong`)  
  
-   1 是負數值的算術右移位 (`SByte`， `Short`， `Integer`，或`Long`)  
  
 下列範例會轉移`Integer`左和右值。  
  
 [!code-vb[VbVbalrOperators #&64;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 算術移位不會產生溢位例外狀況。  
  
## <a name="bitwise-operations"></a>位元運算  
 除了做為邏輯運算子， `Not`， `Or`， `And`，和`Xor`也會執行位元算術時使用數字值。 如需詳細資訊，請參閱 < 位元作業 」[邏輯和位元 Visual Basic 中的運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)。  
  
## <a name="type-safety"></a>型別安全  
 運算元通常應屬於相同的型別。 例如，如果您要加入`Integer`變數時，您應該將它加入至另一個`Integer`變數，而且您應該將結果指派給類型的變數`Integer`以及。  
  
 其中一種確保良好的型別安全程式碼撰寫練習是使用[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)。 如果您設定`Option Strict On`，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會自動執行*型別安全*轉換。 例如，如果您嘗試新增`Integer`變數`Double`變數並指派的值`Double`變數時，作業正常執行，因為`Integer`值可以轉換成`Double`而不會遺失資料。 型別不安全的轉換，相反地，會造成編譯器錯誤與`Option Strict On`。 例如，如果您嘗試新增`Integer`變數`Double`變數並指派的值`Integer`變數時，會產生編譯器錯誤，因為`Double`變數無法以隱含方式轉換成`Integer`。  
  
 如果您設定`Option Strict Off`，不過[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]允許生效，隱含的縮小轉換，但它們可能會導致非預期的資料或精確度遺失。 基於這個理由，我們建議您改用`Option Strict On`撰寫實際執行程式碼時。 如需詳細資訊，請參閱[擴大和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [位元移位運算子](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [在 Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
