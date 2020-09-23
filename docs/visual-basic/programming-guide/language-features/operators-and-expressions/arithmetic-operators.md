---
title: 算術運算子
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
ms.openlocfilehash: 023e479736285aa2d04509e05f49fe930cb4721d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090075"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic 的算術運算子

算術運算子用來執行許多常見的算數運算，這些運算牽涉到以常值、變數、其他運算式、函數和屬性呼叫和常數所表示的數值計算。 此外，以算術運算子分類的是位移位運算子，可在運算元的個別位層級上運作，並將其位模式向左或向右移動。  
  
## <a name="arithmetic-operations"></a>算術運算  

 您可以在運算式中加入兩個值，並加上 [+ 運算子](../../../language-reference/operators/addition-operator.md)，或從另一個值減去另一個值 [ (Visual Basic) ](../../../language-reference/operators/subtraction-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 否定也會使用 [-運算子 (Visual Basic) ](../../../language-reference/operators/subtraction-operator.md)，但只有一個運算元，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 乘法和除法分別使用 [* 運算子](../../../language-reference/operators/multiplication-operator.md) 和 [/運算子 (Visual Basic) ](../../../language-reference/operators/floating-point-division-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 乘冪會使用 [^ 運算子](../../../language-reference/operators/exponentiation-operator.md)，如下列範例所示。  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 使用 [\ 運算子 (Visual Basic) ](../../../language-reference/operators/integer-division-operator.md)來執行整數除法。 整數除法會傳回商，也就是代表除數可以分成被除數的整數數目，而不考慮任何餘數。 除數和被除數都必須是整數類資料類型 (`SByte` 、、、、、、 `Byte` `Short` `UShort` `Integer` `UInteger` `Long` 和 `ULong`) 此運算子。 所有其他類型都必須先轉換成整數類資料類型。 下列範例示範整數除法。  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 模數算術是使用 [Mod 運算子](../../../language-reference/operators/mod-operator.md)來執行。 這個運算子會傳回除數除以整數次之後的餘數。 如果除數和被除數都是整數類資料類型，則傳回的值為整數。 如果除數和被除數為浮點數型別，則傳回的值也是浮點類型。 下列範例示範此行為。  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>嘗試除以零  

 根據相關的資料類型而定，零除有不同的結果。 在整數片段 (`SByte` 、 `Byte` 、 `Short` 、、、、 `UShort` `Integer`) 中 `UInteger` `Long` `ULong` ，.NET Framework <xref:System.DivideByZeroException> 會擲回例外狀況。 在或資料類型的除法運算中 `Decimal` `Single` ，.NET Framework 也會擲回 <xref:System.DivideByZeroException> 例外狀況。  
  
 在涉及資料類型的浮點除法中 `Double` ，不會擲回例外狀況，而且結果會是代表、或的類別成員，視被除數而定 <xref:System.Double.NaN> <xref:System.Double.PositiveInfinity> <xref:System.Double.NegativeInfinity> 。 下表摘要說明嘗試將值除以零的各種結果 `Double` 。  
  
|被除數的資料類型|除數資料類型|被除數值|結果|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (不是以數學方式定義的數位) |  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 當您攔截例外狀況時 <xref:System.DivideByZeroException> ，您可以使用它的成員來協助您處理它。 例如，屬性會 <xref:System.Exception.Message%2A> 保存例外狀況的郵件內文。 如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="bit-shift-operations"></a>位移位作業  

 位移位運算會在位模式上執行算術移位。 此模式包含在左邊的運算元中，而右邊的運算元則指定要移位模式的位置數目。 您可以使用 [>> 運算子](../../../language-reference/operators/right-shift-operator.md) 或左邊加上 [<< 運算子](../../../language-reference/operators/left-shift-operator.md)，將模式向右移動。  
  
 模式運算元的資料類型必須是 `SByte` 、 `Byte` 、 `Short` 、、、 `UShort` `Integer` `UInteger` 、 `Long` 或 `ULong` 。 移位量運算元的資料類型必須是 `Integer` 或必須擴展至 `Integer` 。  
  
 算術移位不是迴圈的，這表示不會在另一端重新出現從結果的一端移出的位。 由 shift 空出的位位置會設定如下：  
  
- 0用於算術左移位  
  
- 0代表正數位的算術右移位  
  
- 0代表不帶正負號資料類型的算術右移（不帶正負號的資料類型 `Byte` ） (、 `UShort` 、 `UInteger` 、 `ULong`)   
  
- 1代表數位 (`SByte` 、、 `Short` `Integer` 或 `Long`) 的算術右移位  
  
 下列範例會將 `Integer` 值向左和向右移。  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 算術移位絕不會產生溢位例外狀況。  
  
## <a name="bitwise-operations"></a>位運算  

 除了為邏輯運算子之外，、 `Not` 、 `Or` `And` 和也會在 `Xor` 使用於數值時執行位運算。 如需詳細資訊，請參閱 [Visual Basic 中邏輯和位運算子](logical-and-bitwise-operators.md)中的「位運算」。  
  
## <a name="type-safety"></a>型別安全  

 運算元通常應該是相同的類型。 例如，如果您要加入 `Integer` 變數，您應該將它新增至另一個 `Integer` 變數，也應該將結果指派給類型的變數 `Integer` 。  
  
 有一種方法可確保良好的型別安全程式碼撰寫作法是使用 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)。 如果設定 `Option Strict On` ，Visual Basic 會自動執行 *型別安全* 轉換。 例如，如果您嘗試將 `Integer` 變數新增至 `Double` 變數，並將值指派給 `Double` 變數，則作業會正常執行，因為 `Integer` 值可以轉換成 `Double` 不會遺失資料。 另一方面，型別 unsafe 轉換會造成編譯器錯誤 `Option Strict On` 。 例如，如果您嘗試將變數加入變數 `Integer` `Double` ，並將值指派給 `Integer` 變數，就會產生編譯器錯誤，因為 `Double` 變數無法隱含轉換成類型 `Integer` 。  
  
 但是，如果您設定 `Option Strict Off` Visual Basic 允許隱含的縮小轉換，雖然它們可能會導致非預期的資料或精確度遺失。 基於這個理由，我們建議您在 `Option Strict On` 撰寫生產程式碼時使用。 如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)。  
  
## <a name="see-also"></a>另請參閱

- [算術運算子](../../../language-reference/operators/arithmetic-operators.md)
- [位元移位運算子](../../../language-reference/operators/bit-shift-operators.md)
- [Comparison Operators in Visual Basic](comparison-operators.md)
- [Visual Basic 中的串連運算子](concatenation-operators.md)
- [Visual Basic 中的邏輯運算子和位元運算子](logical-and-bitwise-operators.md)
- [有效的運算子組合](efficient-combination-of-operators.md)
