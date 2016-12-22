---
title: "Troubleshooting Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Char data type, converting"
  - "Decimal data type, conversions"
  - "data types [Visual Basic], troubleshooting"
  - "literals, default types"
  - "type characters, literal"
  - "Mod operator [Visual Basic], in floating-point operations"
  - "troubleshooting Visual Basic, data types"
  - "troubleshooting data types"
  - "floating-point numbers, precision"
  - "Boolean data type, converting"
  - "literal types"
  - "literal type characters"
  - "floating-point numbers, imprecision"
  - "String data type, converting"
  - "floating-point numbers, comparison"
  - "floating-point numbers"
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

這個頁面會列出在對內建 \(Intrinsic\) 資料型別執行作業時會發生的一些常見問題。  
  
## 浮點運算式不會比較為相等  
 當您處理浮點數值 \(Floating\-Point Number\) \([Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) 和 [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md)\) 時，請記得它們會當做二進位分數儲存。  這表示它們無法保留任何非二進位分數 \(形式為 k \/ \(2 ^ n\)，其中 k 和 n 為整數\) 之數量的確切表示。  例如，0.5 \(\= 1\/2\) 和 0.3125 \(\= 5\/16\) 可以當做精確值保留，而 0.2 \(\= 1\/5\) 和 0.3 \(\= 3\/10\) 則只可為近似值。  
  
 因為這樣的不精確狀況，因此您在處理浮點數值時無法依賴確切結果。  特別是理論上相等的兩個值可能會有稍微不同的表示方式。  
  
||  
|-|  
|若要比較浮點數量|  
|1.  在 <xref:System> 命名空間中使用 <xref:System.Math> 類別的 <xref:System.Math.Abs%2A> 方法，計算差異的絕對值。<br />2.  判斷可接受的最大差異，如果差異沒有大於此值，您可以實際上將兩個數量視為相等。<br />3.  比較差異的絕對值與可接受的差異。|  
  
 下列範例是兩個 `Double` 值的不正確與正確比較。  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 上述範例會使用 <xref:System.Double> 結構的 <xref:System.Double.ToString%2A> 方法，以便指定比 `CStr` 關鍵字所使用之精確度更好的精確度。  預設值為 15 位數，但 "G17" 格式會將它擴充為 17 位數。  
  
## Mod 運算子不會傳回準確結果  
 由於浮點儲存區的不精確狀況，所以在至少其中一個運算元為浮點數時，[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md) 會傳回未預期的結果。  
  
 [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) 不會使用浮點表示。  以 `Single` 和 `Double` 表示會不精確的許多數字，以 `Decimal` 表示則會精確 \(例如 0.2 和 0.3\)。  雖然以 `Decimal` 表示的計算速度比以浮點數表示還慢，但卻值得降低效能以達到更好的精確度。  
  
||  
|-|  
|若要尋找浮點數量的整數餘數|  
|1.  將變數宣告為 `Decimal`。<br />2.  使用常值型別字元 `D` 將常值強制為 `Decimal`，以免它們的值對於 `Long` 資料型別而言太大。|  
  
 下列範例示範浮點數運算元的潛在不精確情況。  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 上述範例會使用 <xref:System.Double> 結構的 <xref:System.Double.ToString%2A> 方法，以便指定比 `CStr` 關鍵字所使用之精確度更好的精確度。  預設值為 15 位數，但 "G17" 格式會將它擴充為 17 位數。  
  
 因為 `zeroPointTwo` 為 `Double`，所以它對於 0.2 的值為無限重複的二進位分數，具有儲存值為 0.20000000000000001。  此數量除以 2.0 會得到 9.9999999999999995，餘數為 0.19999999999999991。  
  
 在 `decimalRemainder` 的運算式中，常值型別字元 `D` 會將兩個運算元強制為 `Decimal`，而 0.2 具有精確表示。  因此，`Mod` 運算子會產生預期的餘數 0.0。  
  
 請注意，這樣並不足以將 `decimalRemainder` 宣告為 `Decimal`。  您還必須將常值強制設為 `Decimal`，否則常值預設會使用 `Double`，而且 `decimalRemainder` 會得到和 `doubleRemainder` 一樣不準確的值。  
  
## 布林型別不會準確地轉換成數字型別  
 [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) 值不會儲存為數字，且儲存值也不會等於數字。  為了與舊版相容，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會提供轉換關鍵字 \([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)、`CBool`、`CInt` 等等\)，以便在 `Boolean` 和數字型別 \(Numeric Type\) 之間進行轉換。  不過，有時其他語言執行這些轉換的方式會不同，例如 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 方法。  
  
 您不需撰寫程式碼，藉以取得 `True` 和 `False` 的相等數值。  盡可能地將 `Boolean` 變數的使用方式限制為所設計的邏輯值。  如果必須將 `Boolean` 和數值混合使用，請確定了解您選取的轉換方法。  
  
### 在 Visual Basic 中進行轉換  
 當您使用 `CType` 或 `CBool` 轉換關鍵字，將數字資料型別轉換成 `Boolean` 時，0 會變成 `False` 而其他所有值會變成 `True`。  當您使用轉換關鍵字將 `Boolean` 值轉換成數字型別時，`False` 會變成 0 而 `True` 會變成 \-1。  
  
### 在 Framework 中進行轉換  
 在 <xref:System> 命名空間中 <xref:System.Convert> 類別的 <xref:System.Convert.ToInt32%2A> 方法，會將 `True` 轉換成 \+1。  
  
 如果您必須將 `Boolean` 值轉換成數字資料型別，請注意您所使用的轉換方法。  
  
## 字元常值會產生編譯器錯誤  
 在有任何型別字元缺少的情況下，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會假設常值的預設資料型別。  字元常值的預設型別為 `String`，此預設型別會放在引號 \(`" "`\) 之中。  
  
 `String` 資料型別不會擴展至 [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)。  這表示如果您想將常值指派給 `Char` 變數，就必須進行縮小轉換或將常值強制為 `Char` 型別。  
  
||  
|-|  
|若要建立 Char 常值以指派至變數或常數|  
|1.  將變數或常數宣告為 `Char`。<br />2.  將字元值放在引號 \(`" "`\) 之中。<br />3.  在右雙引號後面接著常值型別字元 `C`，將常值強制為 `Char`。  如果型別檢查參數 \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) 為 `On` 則不管在任何情況下，都必須這麼做。|  
  
 下列範例同時說明了將常值成功指派至 `Char` 變數或是指派失敗的情形。  
  
 [!CODE [VbVbalrStatements#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrStatements#49)]  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_4.vb)]  
  
 因為縮小轉換可能會在執行階段失敗，所有使用縮小轉換一定會有風險。  舉例而言，如果 `String` 值包含一個以上的字元，則從 `String` 轉換成 `Char` 會失敗。  因此，將程式設計為使用 `C` 型別字元比較好。  
  
## 字串轉換會在執行階段失敗  
 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) 會參與極少的擴展轉換。  `String` 只會擴展至本身和 `Object`，且只有 `Char` 和 `Char()` \(`Char` 陣列\) 會擴展至 `String`。  這是因為 `String` 變數和常數可以包含其他資料型別無法包含的值。  
  
 當型別檢查參數 \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) 為 `On` 時，編譯器不允許所有隱含的縮小轉換，  包括涉及 `String` 的轉換。  您的程式碼仍然可以使用轉換關鍵字 \(例如 `CStr` 和 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)\)，此關鍵字會指引 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 嘗試轉換。  
  
> [!NOTE]
>  從 `For Each…Next` 集合中的項目轉換至迴圈控制變數時，會隱藏縮小轉換錯誤。  如需詳細資訊和範例，請參閱 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) 中的＜縮小轉換＞一節。  
  
### 縮小轉換保護  
 縮小轉換的缺點就是它們可能會在執行階段失敗。  例如，如果 `String` 變數包含除了 "True" 或 "False" 以外的項目，就無法轉換為 `Boolean`。  如果它包含標點符號字元，轉換成任何數字型別都會失敗。  除非您知道 `String` 變數永遠保有目的型別可以接受的值，否則您不該嘗試轉換。  
  
 如果您必須從 `String` 轉換為另一個資料型別，最安全的程序就是將所嘗試的轉換封入 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) 中。  這可以讓您處理執行階段失敗。  
  
### 字元陣列  
 單一 `Char` 和 `Char` 元素的陣列，都會擴展至 `String`。  不過，`String` 不會擴展至 `Char()`。  若要將 `String` 值轉換成 `Char` 陣列，您可以使用 <xref:System.String?displayProperty=fullName> 類別的 <xref:System.String.ToCharArray%2A> 方法。  
  
### 無意義的值  
 一般而言，`String` 值在其他資料型別中是毫無意義的，而且進行轉換會相當麻煩且危險。  盡可能地將 `String` 變數的使用方式限制為所設計的字元順序。  您不需撰寫依賴其他型別中之對等值的程式碼。  
  
## 請參閱  
 [資料類型](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)