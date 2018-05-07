---
title: Char 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: e672402535215ca30d19cc480e39b42b0364f137
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="char-data-type-visual-basic"></a>Char 資料類型 (Visual Basic)
保存不帶正負號的 16 位元 （2 個位元組） 字碼指標值範圍從 0 到 65535 之間。 每個*程式碼點*，或字元碼，表示單一 Unicode 字元。  
  
## <a name="remarks"></a>備註  
 使用`Char`資料類型，當您需要保存只有一個字元，而且不需要的額外負荷`String`。 在某些情況下，您可以使用`Char()`，陣列`Char`項目，來保留多個字元。  
  
 預設值`Char`是與字碼指標為 0 的字元。  
  
## <a name="unicode-characters"></a>Unicode 字元  
 Unicode 的第一個 128 個字碼指標 (0-127) 對應至的字母和標準美國鍵盤上的符號。 這些第一個 128 個字碼指標是相同 ASCII 字元集所定義。 第二個 128 個字碼指標 (128-255) 代表特殊字元，例如拉丁文字母字元、 重音符號、 貨幣符號和分數。 Unicode 會使用各種不同的符號，包括全球文字字元、 變音符號和數學和技術符號剩餘的字碼指標 (256-65535)。  
  
 您可以使用類似的方法<xref:System.Char.IsDigit%2A>和<xref:System.Char.IsPunctuation%2A>上`Char`變數，以判斷其 Unicode 分類。  
  
## <a name="type-conversions"></a>類型轉換  
 Visual Basic 不會直接之間轉換`Char`和數字類型。 您可以使用<xref:Microsoft.VisualBasic.Strings.Asc%2A>或<xref:Microsoft.VisualBasic.Strings.AscW%2A>函式將轉換`Char`值設定為`Integer`表示其字碼指標。 您可以使用<xref:Microsoft.VisualBasic.Strings.Chr%2A>或<xref:Microsoft.VisualBasic.Strings.ChrW%2A>函式將轉換`Integer`值設定為`Char`具有該字碼指標。  
  
 如果類型檢查參數 ([Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)) 已開啟，您必須將常值類型字元附加至單一字元字串常值，以便將它做為識別`Char`資料型別。 下列範例將說明這點。  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>程式設計提示  
  
-   **負的數字。** `Char` 是不帶正負號的類型，因此無法表示負數值。 在任何情況下，您不應該使用`Char`來保存數值。  
  
-   **Interop 考量。** 如果您正在使用不是針對.NET Framework 中，撰寫的元件例如 Automation 或 COM 物件，請記得字元類型具有不同資料寬度 （8 位元） 在其他環境中。 如果您將 8 位元引數傳遞至這類元件時，將它宣告為`Byte`而不是`Char`新的 Visual Basic 程式碼。  
  
-   **擴展。** `Char`資料類型可擴展成`String`。 這表示您可以將轉換`Char`至`String`並不會遇到<xref:System.OverflowException?displayProperty=nameWithType>錯誤。  
  
-   **類型字元。** 將常值類型字元附加`C`為單一字元字串常值會強制其成為`Char`資料型別。 `Char` 有任何識別項類型字元。  
  
-   **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Char?displayProperty=nameWithType> 結構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [String 資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
