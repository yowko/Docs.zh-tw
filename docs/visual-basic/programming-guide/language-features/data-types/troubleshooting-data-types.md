---
title: "疑難排解資料類型 (Visual Basic) |Microsoft 文件"
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
- Char data type, converting
- Decimal data type, conversions
- data types [Visual Basic], troubleshooting
- literals, default types
- type characters, literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types
- floating-point numbers, precision
- Boolean data type, converting
- literal types
- literal type characters
- floating-point numbers, imprecision
- String data type, converting
- floating-point numbers, comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
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
ms.openlocfilehash: cfb8fc77d3e0d85ef795a94fc95ab61a8f68ff39
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-data-types-visual-basic"></a>疑難排解資料類型 (Visual Basic)
此頁面會列出您的內建函式的資料類型上執行作業時所發生的一些常見問題。  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>浮點運算式不會比較為相等  
 當您使用浮點數 ([單一資料型別](../../../../visual-basic/language-reference/data-types/single-data-type.md)和[Double 資料型別](../../../../visual-basic/language-reference/data-types/double-data-type.md))，請記住它們會儲存為二進位分數。 這表示它們不能保存任何不是二進位分數的數量的精確表示 (在表單 k / (2 ^ n) k 和 n 都是整數)。 例如，0.5 （= 1/2） 和 0.3125 （= 5/16） 可以保留為精確的值，而 0.2 （= 1/5） 和 0.3 （= 3/10） 可以僅為近似值。  
  
 正因為如此的不精確，當您操作的浮點值不能依賴確切的結果。 特別是，理論上相等的兩個值可能稍有不同的表示法。  
  
| 若要比較浮點數量 | 
|---| 
|1.使用計算差異的絕對值<xref:System.Math.Abs%2A>方法<xref:System.Math>類別<xref:System>命名空間。</xref:System> </xref:System.Math> </xref:System.Math.Abs%2A><br />2.判斷可接受的最大差異，，，您可以考慮將兩個數量視為相等實際上如果差異不大。<br />3.比較數值到可接受的差異差異的絕對值。|  
  
 下列範例會示範兩個不正確且正確比較`Double`值。  
  
 [!code-vb[VbVbalrDataTypes #&10;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 上述範例使用<xref:System.Double.ToString%2A>方法<xref:System.Double>結構，因此它可以指定更好的精確度超過`CStr`關鍵字使用。</xref:System.Double> </xref:System.Double.ToString%2A> 預設值是 15 位數，但是"G17"格式將它擴充到 17 位數。  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod 運算子不會傳回精確的結果  
 由於不精確的浮點的儲存體， [Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)至少其中一個運算元是浮點數時，會傳回非預期的結果。  
  
 [Decimal 資料型別](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)不會使用浮點表示。 在不精確的許多數字`Single`和`Double`會完全在`Decimal`（例如 0.2 和 0.3）。 雖然算術中更慢`Decimal`比在浮點數，它可能是值得以達到更好的精確度降低效能。  
  
|若要尋找浮點數量的整數餘數|  
|---|  
|1.宣告變數為`Decimal`。<br />2.使用常值類型字元`D`強制常值加入至`Decimal`，萬一它們的值太大`Long`資料型別。|  
  
 下列範例將示範可能會不精確的浮點運算元。  
  
 [!code-vb[VbVbalrDataTypes #&11;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 上述範例使用<xref:System.Double.ToString%2A>方法<xref:System.Double>結構，因此它可以指定更好的精確度超過`CStr`關鍵字使用。</xref:System.Double> </xref:System.Double.ToString%2A> 預設值是 15 位數，但是"G17"格式將它擴充到 17 位數。  
  
 因為`zeroPointTwo`是`Double`，其值 0.2 是預存值為 0.20000000000000001 無限重複二進位小數。 此數量除以 2.0 會得到 9.9999999999999995 0.19999999999999991 的其餘部分。  
  
 在運算式中的`decimalRemainder`，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確的表示。 因此`Mod`運算子會產生預期的餘數 0.0。  
  
 請注意，不足夠宣告`decimalRemainder`為`Decimal`。 您也必須強制常值加入至`Decimal`，或者使用`Double`預設和`decimalRemainder`收到不正確的相同值，做為`doubleRemainder`。  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>布林型別不會準確地轉換為數字類型  
 [布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)值不會儲存成數字，並儲存的值不是數字相等。 為了與舊版中，相容[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供轉換關鍵字 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)， `CBool`，`CInt`等) 之間進行轉換`Boolean`和數字類型。 不過，其他語言有時會執行這些轉換以不同的方式，也是如此[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]方法。  
  
 您不需撰寫程式碼所使用的對等數值`True`和`False`。 可能的話，您應該限制的使用方式`Boolean`它們專為邏輯值的變數。 如果您要混合`Boolean`和數字的值，請確定您已了解您所選取的轉換方法。  
  
### <a name="conversion-in-visual-basic"></a>在 Visual Basic 中的轉換  
 當您使用`CType`或`CBool`來轉換數值資料類型以轉換關鍵字`Boolean`，0 會變成`False`和所有其他值會變成`True`。 當您轉換`Boolean`使用轉換的關鍵字，數字類型的值`False`變成 0 和`True`變成-1。  
  
### <a name="conversion-in-the-framework"></a>Framework 中的轉換  
 <xref:System.Convert.ToInt32%2A>方法<xref:System.Convert>類別<xref:System>命名空間將轉換`True`到 +&1;。</xref:System> </xref:System.Convert> </xref:System.Convert.ToInt32%2A>  
  
 如果您必須先轉換`Boolean`值設為數值資料類型，請謹慎使用哪一種轉換方法的詳細。  
  
## <a name="character-literal-generates-compiler-error"></a>字元常值會產生編譯器錯誤  
 如果沒有任何型別字元，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]假設預設的常值的資料型別。 字元常值的預設類型 — 以引號括住 (`" "`) — 是`String`。  
  
 `String`資料型別並不會擴展為[Char 資料型別](../../../../visual-basic/language-reference/data-types/char-data-type.md)。 這表示，如果您想要指派將常值`Char`變數時，您必須進行縮小轉換，或將常值來強制`Char`型別。  

|若要建立字元常值指派給變數或常數|
|---|  
|1.宣告變數或常數當作`Char`。<br />2.以引號括住的字元值 (`" "`)。<br />3.請遵循右雙引號常值型別字元`C`強制常值，以便`Char`。 這是必要的型別檢查切換 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`，這時就在任何情況下。|  
  
 下列範例示範將常值的失敗和成功指派`Char`變數。  
  
 [!code-vb[VbVbalrDataTypes #&12;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 總是有風險使用縮小轉換，因為它們可以在執行階段失敗。 例如，從轉換`String`至`Char`就會失敗`String`值包含多個字元。 因此，它進一步撰寫使用`C`輸入字元。  
  
## <a name="string-conversion-fails-at-run-time"></a>字串轉換在執行階段失敗  
 [字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)參與很少的擴展轉換。 `String`擴展至本身只和`Object`，而且只有`Char`和`Char()`(`Char`陣列) 擴展為`String`。 這是因為`String`變數和常數可以包含其他資料型別不能包含的值。  
  
 當型別檢查切換 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`，編譯器不允許所有隱含的縮小轉換。 這包括涉及`String`。 您的程式碼仍然可以使用轉換關鍵字例如`CStr`和[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)，哪些直接[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]嘗試轉換。  
  
> [!NOTE]
>  轉換中的項目會隱藏縮小轉換錯誤`For Each…Next`迴圈控制變數的集合。 如需詳細資訊和範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
### <a name="narrowing-conversion-protection"></a>縮小轉換保護  
 縮小轉換的缺點是它們可以在執行階段失敗。 例如，如果`String`變數包含任何項目不是"True"或"False，"無法轉換成`Boolean`。 如果它包含標點符號字元，則任何數值類型的轉換會失敗。 除非您知道您`String`變數一律會保留在目的型別可接受的值，您不應該嘗試轉換。  
  
 如果您必須將`String`最安全的程序是來括住中的嘗試的轉換成其他資料類型，[試...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。 這可讓您處理執行階段失敗。  
  
### <a name="character-arrays"></a>字元陣列  
 單一`Char`和陣列`Char`項目同時擴展為`String`。 不過，`String`並不會擴展為`Char()`。 要轉換`String`值`Char`陣列，您可以使用<xref:System.String.ToCharArray%2A>方法的<xref:System.String?displayProperty=fullName>類別。</xref:System.String?displayProperty=fullName> </xref:System.String.ToCharArray%2A>  
  
### <a name="meaningless-values"></a>無意義的值  
 一般而言，`String`值不在其他資料類型的意義，而且轉換會相當麻煩且危險。 可能的話，您應該限制的使用方式`String`變數，它們設計的字元序列。 您不需撰寫程式碼所使用的其他型別的值相等。  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [有效率地使用資料類型](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
