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
ms.openlocfilehash: 9bbc7f51de9899354184d051d8f1a584651dd030
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745485"
---
# <a name="troubleshooting-data-types-visual-basic"></a>疑難排解資料類型 (Visual Basic)
此頁面會列出您的內建資料型別上執行作業時所發生的一些常見問題。  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>浮點運算式不會比較為相等  
 當您使用浮點數 ([單一的資料型別](../../../../visual-basic/language-reference/data-types/single-data-type.md)並[Double 資料型別](../../../../visual-basic/language-reference/data-types/double-data-type.md))，請記住，它們會儲存為二進位分數。 這表示它們不能保存不是二進位分數任何數量的精確表示 (格式為 k 的 / (2 ^ n) 其中 k 和 n 是整數)。 比方說，0.5 （= 1/2） 和 0.3125 （= 5/16） 可以保留為精確的值，而 （= 1/5） 的 0.2 和 0.3 （= 3/10） 可以是僅為近似值。  
  
 基於此原因的不精確，當您處理浮點數的值不能依賴確切的結果。 特別是，理論上相等的兩個值可能稍有不同的表示法。  
  
| 要比較浮點數的數量 | 
|---| 
|1.使用計算其差異的絕對值<xref:System.Math.Abs%2A>方法<xref:System.Math>類別中<xref:System>命名空間。<br />2.您可以考慮將兩個數量相當實際上其差異不大，才會決定可接受的最大差異。<br />3.比較值的差異可接受的差異的絕對值。|  
  
 下列範例示範兩個不正確的和正確比較`Double`值。  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 先前的範例使用<xref:System.Double.ToString%2A>方法<xref:System.Double>結構，讓它可以指定更好的精確度卻高於`CStr`關鍵字使用。 預設值是 15 位數，但是"G17"格式將它擴充到 17 個位數。  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod 運算子不會傳回精確的結果  
 因為浮點數的存放裝置，並不精確[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)其中至少一個運算元為浮點數時，可以傳回非預期的結果。  
  
 [十進位資料類型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)不會使用浮點數表示法。 會在不精確的許多數字`Single`及`Double`會在確切`Decimal`（例如 0.2 和 0.3）。 雖然算術中更慢`Decimal`比在浮點數，可能值得以達到更佳的精確度降低效能。  
  
|若要尋找的浮點數的數量的整數餘數|  
|---|  
|1.宣告變數為`Decimal`。<br />2.使用常值類型字元`D`強制常值，以`Decimal`，如果其值太大，`Long`資料型別。|  
  
 下列範例示範可能會不精確的浮點運算元。  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 先前的範例使用<xref:System.Double.ToString%2A>方法<xref:System.Double>結構，讓它可以指定更好的精確度卻高於`CStr`關鍵字使用。 預設值是 15 位數，但是"G17"格式將它擴充到 17 個位數。  
  
 因為`zeroPointTwo`是`Double`，0.2 其值是無限期地重複的二進位分數與 0.20000000000000001 預存值。 2.0 除以這個數量，就會產生 9.9999999999999995 0.19999999999999991 的其餘部分。  
  
 中的運算式`decimalRemainder`，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確的表示法。 因此`Mod`運算子會產生預期的其餘部分為 0.0。  
  
 請注意，不宣告足夠`decimalRemainder`做為`Decimal`。 您也必須強制常值，以`Decimal`，或者使用`Double`根據預設並`decimalRemainder`收到不正確的相同值，做為`doubleRemainder`。  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>布林值類型不會精確地轉換成數值類型  
 [布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)值不會儲存為 數字，儲存的值不可為等同於數字。 為了與舊版相容，Visual Basic 提供轉換關鍵字 ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)， `CBool`，`CInt`等) 之間進行轉換`Boolean`和數字類型。 不過，其他語言有時會執行這些轉換以不同的方式一樣[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]方法。  
  
 您不需撰寫程式碼，以針對對等數值`True`和`False`。 可能的話，您應該限制的使用方式`Boolean`它們設計的邏輯值的變數。 如果您必須混合使用`Boolean`和數字的值，請確定您了解您所選取的轉換方法。  
  
### <a name="conversion-in-visual-basic"></a>在 Visual Basic 中的轉換  
 當您使用`CType`或是`CBool`轉換關鍵字，來轉換數值資料類型，以`Boolean`，會變成 0`False`和所有其他值會變成`True`。 當您將轉換`Boolean`藉由使用轉換的關鍵字，數字類型的值`False`會變成 0 和`True`變成-1。  
  
### <a name="conversion-in-the-framework"></a>Framework 中的轉換  
 <xref:System.Convert.ToInt32%2A>方法<xref:System.Convert>類別中<xref:System>命名空間轉換`True`為 + 1。  
  
 如果您必須將轉換`Boolean`值設為數值資料類型，請小心在您使用哪一種轉換方法有關。  
  
## <a name="character-literal-generates-compiler-error"></a>字元常值會產生編譯器錯誤  
 如果沒有任何型別字元，在 Visual Basic 會假設預設常值的資料類型。 字元常值的預設類型 — 以引號括住 (`" "`)，是`String`。  
  
 `String`資料類型不會不會擴展為[Char 資料型別](../../../../visual-basic/language-reference/data-types/char-data-type.md)。 這表示，如果您想要指派常值，以便`Char`變數，您必須進行縮小轉換，或是將常值，以強制`Char`型別。  

|若要建立字元常值指派給變數或常數|
|---|  
|1.宣告變數或常數當作`Char`。<br />2.以引號括住的字元值 (`" "`)。<br />3.請遵循右雙引號與常值類型字元`C`強制常值，以便`Char`。 這是需要類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`，因而適合在任何情況下。|  
  
 下列範例示範不成功，並成功指派到常值`Char`變數。  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 中一律會有風險使用縮小轉換，因為它們可以在執行階段失敗。 例如，從轉換`String`要`Char`就會失敗`String`值包含多個字元。 因此，它更好的程式設計使用`C`輸入字元。  
  
## <a name="string-conversion-fails-at-run-time"></a>在執行階段的字串轉換失敗  
 [字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)參與極少數的擴展轉換。 `String` 可擴展為本身只和`Object`，並只`Char`並`Char()`(`Char`陣列) 擴展為`String`。 這是因為`String`變數和常數可以包含其他資料類型不能包含的值。  
  
 當類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`，編譯器不允許隱含的縮小轉換。 這包括涉及`String`。 您的程式碼仍然可以使用轉換關鍵字這類`CStr`並[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)，哪一個 direct[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]嘗試轉換。  
  
> [!NOTE]
>  轉換中的項目隱藏的縮小轉換錯誤`For Each…Next`迴圈控制變數的集合。 如需詳細資訊和範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。  
  
### <a name="narrowing-conversion-protection"></a>縮小轉換保護  
 縮小轉換的缺點是它們可以在執行階段失敗。 例如，如果`String`變數會包含任何項目不是"True"或"False，"無法轉換成`Boolean`。 如果它包含標點符號字元，則任何數值類型的轉換會失敗。 除非您知道您`String`變數一律會保留目的型別可接受的值，您不應該嘗試轉換。  
  
 如果您必須轉換`String`成另一個資料類型，最安全的程序是括住中的嘗試的轉換[試...Catch...Try...catch...finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。 這可讓您處理執行階段失敗。  
  
### <a name="character-arrays"></a>字元陣列  
 單一`Char`和陣列`Char`項目同時擴展為`String`。 不過，`String`不會不會擴展為`Char()`。 要轉換`String`值加入`Char`陣列中，您可以使用<xref:System.String.ToCharArray%2A>方法<xref:System.String?displayProperty=nameWithType>類別。  
  
### <a name="meaningless-values"></a>無意義的值  
 一般情況下，`String`值不在其他資料類型的有意義且轉換是相當麻煩且危險。 可能的話，您應該限制的使用方式`String`它們設計的字元序列的變數。 您不需撰寫程式碼相依於其他型別中的對等值。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/index.md)  
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [有效率地使用資料類型](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
