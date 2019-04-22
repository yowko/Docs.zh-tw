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
ms.openlocfilehash: 635c791f81107a1800e2ef381f6bea78cbc18e18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820767"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic 的算術運算子
算術運算子用來執行許多熟悉的算術作業牽涉到數字常值、 變數、 其他運算式、 函式和屬性呼叫和常數所代表的值計算。 搭配算術運算子也分類為位元移位運算子，運算元的個別位元層級處理，並向左或向右移位其位元模式。  
  
## <a name="arithmetic-operations"></a>算術運算  
 您可以新增兩個值中搭配使用的運算式[+ 運算子](../../../../visual-basic/language-reference/operators/addition-operator.md)，或從另一個具有減去[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，如下列範例示範。  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 也會使用否定[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，但只有一個運算元，如下列範例示範。  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 使用乘法和除法[* 運算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)並[/ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)分別，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 使用乘冪[^ 運算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 整數除法運算會執行使用[\ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)。 整數除法傳回商數，也就是代表次數的整數除數分成數個而不考慮任何餘數被除數。 被除數和除數必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，以及`ULong`) 這個運算子。 所有其他型別必須先轉換成整數類資料類型。 下列範例示範了整數除法。  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 使用執行算術模數[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)。 這個運算子會傳回其餘部分對被除數除以除數之後的次數的整數。 如果除數與被除數是整數類資料類型，傳回的值是整數。 如果除數與被除數是浮點類型，傳回的值也是浮點數。 下列範例示範此行為。  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>嘗試的除以零  
 除數為零會有不同的結果，根據相關的資料類型。 中不可或缺的部門 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`)，則[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]會擲回<xref:System.DivideByZeroException>例外狀況。 在除法運算`Decimal`或`Single`資料類型[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]也會擲回<xref:System.DivideByZeroException>例外狀況。  
  
 涉及浮點劃分`Double`資料類型，會擲回任何例外狀況，以及結果是代表該類別的成員<xref:System.Double.NaN>， <xref:System.Double.PositiveInfinity>，或<xref:System.Double.NegativeInfinity>，端視被除數。 下表摘要說明各種不同的嘗試將結果`Double`零的值。  
  
|被除數資料類型|除數資料類型|被除數的值|結果|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> （不是以數學方式定義數字）|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 當您攔截<xref:System.DivideByZeroException>例外狀況，您可以使用其成員可協助您處理它。 比方說，<xref:System.Exception.Message%2A>屬性會保留例外狀況的訊息文字。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="bit-shift-operations"></a>位元移位作業  
 位元移位作業執行位元模式的算術移位。 模式包含在左邊的運算元中，而右邊的運算元指定的模式移位的位置數目。 您可以將模式移位至右側[>> 運算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)或至與左[<< 運算子](../../../../visual-basic/language-reference/operators/left-shift-operator.md)。  
  
 模式運算元的資料類型必須是`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`。 移位量運算元的資料類型必須是`Integer`或必須擴展為`Integer`。  
  
 算術的排班不是循環，這表示移出結果的某一端的位元不會重新引入另一端。 移位空出的位元位置設定，如下所示：  
  
-   算術左移位的 0  
  
-   0 為正數的算術右移位的  
  
-   0 代表不帶正負號的資料類型的算術右移位 (`Byte`， `UShort`， `UInteger`， `ULong`)  
  
-   1 是負數值的算術右移位 (`SByte`， `Short`， `Integer`，或`Long`)  
  
 下列範例會轉移`Integer`左和右值。  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 算術移位絕不會產生溢位例外狀況。  
  
## <a name="bitwise-operations"></a>位元運算  
 邏輯運算子，除了`Not`， `Or`， `And`，和`Xor`也會執行位元的算術運算時數字的值上使用。 如需詳細資訊，請參閱 「 位元 」 的作業[邏輯和位元 Visual Basic 中的運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)。  
  
## <a name="type-safety"></a>型別安全  
 運算元通常應該是相同的型別。 比方說，如果您正在使用加法`Integer`變數，您應該將它新增至另一個`Integer`變數，而且您應該將結果指派給變數的型別`Integer`以及。  
  
 其中一種方式確保良好的型別安全程式碼撰寫做法是使用[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)。 如果您設定`Option Strict On`，會自動執行 Visual Basic*型別安全*轉換。 比方說，如果您嘗試新增`Integer`變數設為`Double`變數並將值指派給`Double`變數，作業會繼續正常，因為`Integer`值可以轉換成`Double`而不會遺失資料。 類型安全的轉換，相反地，會造成編譯器錯誤`Option Strict On`。 例如，如果您嘗試新增`Integer`變數設為`Double`變數並將值指派給`Integer`變數，則編譯器會產生錯誤，因為`Double`變數不能以隱含方式轉換為類型`Integer`。  
  
 如果您將設定`Option Strict Off`，不過，Visual Basic 允許隱含的縮小轉換，以進行應用程式，雖然它們可能會導致非預期的資料或精確度遺失。 基於這個理由，我們建議您改用`Option Strict On`撰寫實際執行程式碼時。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## <a name="see-also"></a>另請參閱

- [算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [位元移位運算子](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [在 Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
