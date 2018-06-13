---
title: Visual Basic 的算術運算子
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: cd66d08eba973a796472fcbd40a6a84edbbb62ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655580"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic 的算術運算子
算術運算子可用來執行許多熟悉的算術運算涉及數值常值、 變數、 其他運算式、 函式和屬性呼叫和常數所代表的計算。 搭配算術運算子也分類為位元移位運算子會在一個運算元的個別位元層級執行動作，並向左或向右移位的位元模式。  
  
## <a name="arithmetic-operations"></a>算術運算  
 您可以搭配運算式中加入兩個值[+ 運算子](../../../../visual-basic/language-reference/operators/addition-operator.md)，或從另一個具有減去[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，如下列範例會示範。  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 也會使用否定[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，但只有一個運算元，如下列範例示範。  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 使用乘法和除法[* 運算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)和[/ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)分別，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 會使用指數[^ 運算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 整數除法場所使用[\ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)。 整數除法傳回商數，也就是代表次數的整數除數分成數個而不考慮任何餘數被除數。 被除數和除數必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，和`ULong`) 為此運算子。 所有其他類型必須先轉換成整數類資料類型。 下列範例會示範整數除法。  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 使用執行算術模數[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)。 這個運算子傳回餘數對被除數除以除數之後的整數類資料的次數。 如果除數與被除數都是整數類資料類型，傳回的值是整數。 如果除數與被除數浮點型別，傳回的值也是浮點數。 下列範例將示範這個行為。  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>嘗試的除以零  
 除數為零會有不同的結果，根據相關的資料類型而定。 整數類資料劃分 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`)、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]會擲回<xref:System.DivideByZeroException>例外狀況。 在除法運算`Decimal`或`Single`資料型別，[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]也會擲回<xref:System.DivideByZeroException>例外狀況。  
  
 涉及浮點劃分`Double`資料型別，擲回任何例外狀況，且結果為該類別的成員代表<xref:System.Double.NaN>， <xref:System.Double.PositiveInfinity>，或<xref:System.Double.NegativeInfinity>，端視被除數。 下表摘要說明不同的結果的嘗試將`Double`除以零的值。  
  
|被除數資料類型|除數資料型別|被除數的值|結果|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> （不是以數學方式定義數字）|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 當您攔截<xref:System.DivideByZeroException>例外狀況，您可以使用其成員可協助您處理它。 例如，<xref:System.Exception.Message%2A>屬性會保留例外狀況的訊息文字。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="bit-shift-operations"></a>位元移位作業  
 位元移位作業位元模式上執行算術的位移。 模式包含在左邊的運算元中，而右運算元指定的位置模式移位的數目。 您可以將模式移位至右側[>> 運算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)或左側[<< 運算子](../../../../visual-basic/language-reference/operators/left-shift-operator.md)。  
  
 模式運算元的資料類型必須是`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`。 移位量運算元的資料類型必須是`Integer`或必須擴展為`Integer`。  
  
 算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。 移位空出的位元位置設定，如下所示：  
  
-   0 代表算術左移位  
  
-   0 為正數的算術右移位的  
  
-   0 代表不帶正負號的資料類型的算術右移位 (`Byte`， `UShort`， `UInteger`， `ULong`)  
  
-   1 是負數值的算術右移位 (`SByte`， `Short`， `Integer`，或`Long`)  
  
 下列範例會轉移`Integer`值 left 和 right。  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 算術移位不會產生溢位例外狀況。  
  
## <a name="bitwise-operations"></a>位元運算  
 邏輯運算子，除了`Not`， `Or`， `And`，和`Xor`也執行位元的算術運算，使用數字值時。 如需詳細資訊，請參閱 < 位元作業 >[邏輯和位元 Visual Basic 中的運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)。  
  
## <a name="type-safety"></a>型別安全  
 運算元通常應該是相同的型別。 例如，如果您要加入`Integer`變數時，您應該將它加入另一個`Integer`變數，而且您應該將結果指派給類型的變數`Integer`以及。  
  
 一種方式以確保好的型別安全程式碼撰寫的作法是使用[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)。 如果您設定`Option Strict On`，Visual Basic 會自動執行*型別安全*轉換。 例如，如果您嘗試新增`Integer`變數設為`Double`變數和指派值`Double`變數時，作業正常執行，因為`Integer`值可以轉換成`Double`而不會遺失資料。 類型安全的轉換，相反地，會造成編譯器錯誤與`Option Strict On`。 比方說，如果您嘗試新增`Integer`變數設為`Double`變數和指派值`Integer`變數，則編譯器會產生錯誤，因為`Double`變數無法以隱含方式轉換為類型`Integer`。  
  
 如果您設定`Option Strict Off`，不過，Visual Basic 允許隱含的縮小轉換，才能進行應用程式，雖然它們可能會導致非預期的資料或精確度遺失。 基於這個理由，我們建議您改用`Option Strict On`寫入實際執行程式碼時。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [位元移位運算子](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [在 Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
