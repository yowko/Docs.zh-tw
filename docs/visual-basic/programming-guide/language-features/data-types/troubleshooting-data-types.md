---
title: 疑難排解資料類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: c5ff9d097c0660956a9751a23511d8273766227c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655781"
---
# <a name="troubleshooting-data-types-visual-basic"></a>疑難排解資料類型 (Visual Basic)
此頁面會列出您內建資料類型上執行作業時所發生的一些常見問題。  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>浮點運算式不會比較為相等  
 當您使用浮點數 ([單一的資料型別](../../../../visual-basic/language-reference/data-types/single-data-type.md)和[Double 資料類型](../../../../visual-basic/language-reference/data-types/double-data-type.md))，請記住，它們會儲存為二進位分數。 這表示它們無法保留不是二進位分數任何數量的精確表示 (格式 k 的 / (2 ^ n) k 和 n 都是整數)。 例如，0.5 （= 1/2） 和 0.3125 （= 5/16） 可以保留為精確的值，而 0.2 （= 1/5） 和 0.3 （= 3/10） 可以是僅是近似值。  
  
 基於此原因的不精確而受到，當您操作的浮點值不能依賴確切的結果。 特別是，理論上是相等的兩個值可能會有稍微不同的表示方式。  
  
| 要比較浮點數量 | 
|---| 
|1.使用計算差異的絕對值<xref:System.Math.Abs%2A>方法<xref:System.Math>類別<xref:System>命名空間。<br />2.判斷可接受的最大差異，，，您可以考慮將兩個數量視為等於實際上如果差異不大。<br />3.比較的差異可接受的差異的絕對值。|  
  
 下列範例會示範兩個不正確且正確比較`Double`值。  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 先前的範例使用<xref:System.Double.ToString%2A>方法<xref:System.Double>結構，讓它可以指定更好的精確度卻高於`CStr`關鍵字使用。 預設值為 15 位數，但是"G17"格式將它擴充為 17 個位數。  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod 運算子不會傳回精確的結果  
 不精確而受到浮點數的存放裝置，因為[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)至少其中一個運算元是浮點數時，會傳回非預期的結果。  
  
 [Decimal 資料類型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)不會使用浮點表示法。 會在不精確的許多數字`Single`和`Double`並在精確`Decimal`（例如 0.2 和 0.3）。 雖然算術中更慢`Decimal`比在浮點數，其可能值得以達到更好的精確度降低效能。  
  
|若要尋找浮點數量的整數餘數|  
|---|  
|1.宣告變數為`Decimal`。<br />2.使用常值類型字元`D`強制常值加入至`Decimal`，以免它們的值太大，`Long`資料型別。|  
  
 下列範例示範可能會不精確而受到浮點數運算元。  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 先前的範例使用<xref:System.Double.ToString%2A>方法<xref:System.Double>結構，讓它可以指定更好的精確度卻高於`CStr`關鍵字使用。 預設值為 15 位數，但是"G17"格式將它擴充為 17 個位數。  
  
 因為`zeroPointTwo`是`Double`，0.2 其值是無限重複的二進位小數 0.20000000000000001 預存值。 2.0 除以此數量會得到 9.9999999999999995 0.19999999999999991 的其餘部分。  
  
 中的運算式`decimalRemainder`，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確地表示法。 因此`Mod`運算子會產生預期的其餘部分是 0.0。  
  
 請注意，並非足夠宣告`decimalRemainder`為`Decimal`。 您也必須強制常值加入至`Decimal`，或者使用`Double`預設和`decimalRemainder`接收相同的不正確值`doubleRemainder`。  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>布林型別不會精確地轉換成數值類型  
 [布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)值不會儲存為數字，並儲存的值不是數字相等。 為了與舊版相容，Visual Basic 提供轉換關鍵字 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)， `CBool`， `CInt`，依此類推) 之間進行轉換`Boolean`和數字類型。 不過，其他語言有時會執行這些轉換不同，一樣[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]方法。  
  
 您不需撰寫程式碼所使用的對等數值`True`和`False`。 可能的話，您應該限制使用`Boolean`為其所設計的邏輯值的變數。 如果您必須混合`Boolean`和數字的值，請確定您了解您所選取的轉換方法。  
  
### <a name="conversion-in-visual-basic"></a>在 Visual Basic 中的轉換  
 當您使用`CType`或`CBool`轉換關鍵字，來轉換數值資料類型，以`Boolean`，會變成 0`False`和所有其他值會變成`True`。 當您轉換`Boolean`值以數字類型，使用轉換關鍵字，`False`變成 0 和`True`變成-1。  
  
### <a name="conversion-in-the-framework"></a>Framework 中的轉換  
 <xref:System.Convert.ToInt32%2A>方法<xref:System.Convert>類別<xref:System>命名空間轉換`True`為 + 1。  
  
 如果您必須將轉換`Boolean`值設定為數值資料類型，請謹慎使用哪一種轉換方法的相關。  
  
## <a name="character-literal-generates-compiler-error"></a>字元常值會產生編譯器錯誤  
 如果沒有任何型別字元，在 Visual Basic 會假設預設常值的資料型別。 字元常值的預設類型 — 以引號括住 (`" "`) — 是`String`。  
  
 `String`資料型別並不會擴展為[Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)。 這表示，如果您想要指派常值，以便`Char`變數時，您必須讓縮小轉換，或是將常值來強制`Char`型別。  

|若要建立字元常值指派給變數或常數|
|---|  
|1.宣告變數或常數當作`Char`。<br />2.以引號括住的字元值 (`" "`)。<br />3.請依照下列兩個引號以常值類型字元`C`強制常值，以便`Char`。 這是必要，如果型別檢查切換 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`，而且想要在任何情況下。|  
  
 下列範例會示範將常值的失敗和成功指派`Char`變數。  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 一定會有風險使用縮小轉換，因為它們可以在執行階段失敗。 例如，從轉換`String`至`Char`就會失敗`String`該值包含一個以上的字元。 因此，它更加程式設計使用`C`輸入字元。  
  
## <a name="string-conversion-fails-at-run-time"></a>字串轉換會在執行階段失敗  
 [字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)參與極少數的擴展轉換。 `String` 可擴展為本身只和`Object`，僅限和`Char`和`Char()`(`Char`陣列) 擴展為`String`。 這是因為`String`變數和常數可以包含其他資料類型不能包含的值。  
  
 當型別檢查切換 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`，編譯器不允許所有隱含的縮小轉換。 這包括涉及`String`。 您的程式碼仍然可以使用轉換關鍵字例如`CStr`和[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)，哪些 direct[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]嘗試轉換。  
  
> [!NOTE]
>  縮小轉換錯誤的轉換中的項目隱藏`For Each…Next`迴圈控制變數的集合。 如需詳細資訊與範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
### <a name="narrowing-conversion-protection"></a>縮小轉換保護  
 縮小轉換的缺點是它們可以在執行階段失敗。 例如，如果`String`變數包含任何項目不是"True"或"False，"無法轉換成`Boolean`。 如果它包含標點符號字元，則任何數字類型的轉換會失敗。 除非您已了解您`String`變數會永遠保留目的型別可以接受的值，您不應該嘗試轉換。  
  
 如果您必須轉換`String`另一個資料類型，最安全的程序會括住中的嘗試的轉換[再試一次...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。 這可讓您處理執行階段失敗。  
  
### <a name="character-arrays"></a>字元陣列  
 單一`Char`和陣列`Char`元素同時擴展為`String`。 不過，`String`並不會擴展為`Char()`。 要轉換`String`值設定為`Char`陣列，您可以使用<xref:System.String.ToCharArray%2A>方法<xref:System.String?displayProperty=nameWithType>類別。  
  
### <a name="meaningless-values"></a>無意義的值  
 一般情況下，`String`值不是有意義的其他資料類型，而轉換是相當麻煩且危險。 可能的話，您應該限制使用`String`變數為其所設計的字元序列。 您不需撰寫程式碼所使用的其他型別的值相等。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [有效率地使用資料類型](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
