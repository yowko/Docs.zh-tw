---
title: String 資料類型 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90f126a5cca36969617446e81a8d13434e39df75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="string-data-type-visual-basic"></a>String 資料類型 (Visual Basic)
保存該範圍的不帶正負號的 16 位元 （2 個位元組） 字碼指標的序列，從 0 到 65535 的值。 每個*程式碼點*，或字元碼，表示單一 Unicode 字元。 字串可包含 0 到大約二十億 (2 ^31) 的 Unicode 字元。  
  
## <a name="remarks"></a>備註  
 使用`String`資料型別包含多個字元的陣列管理額外負荷不`Char()`，陣列`Char`項目。  
  
 預設值`String`是`Nothing`（null 參考）。 請注意，這不是空的字串相同 (值`""`)。  
  
## <a name="unicode-characters"></a>Unicode 字元  
 Unicode 的第一個 128 個字碼指標 (0-127) 對應至的字母和標準美國鍵盤上的符號。 這些第一個 128 個字碼指標是相同 ASCII 字元集所定義。 第二個 128 個字碼指標 (128-255) 代表特殊字元，例如拉丁文字母字元、 重音符號、 貨幣符號和分數。 Unicode 會使用其餘的字碼指標 (256-65535) 的各種不同的符號。 這包括各國文字字元，變音符號，以及數學和技術的符號。  
  
 您可以使用方法，例如<xref:System.Char.IsDigit%2A>和<xref:System.Char.IsPunctuation%2A>上中的個別字元`String`變數，以判斷其 Unicode 分類。  
  
## <a name="format-requirements"></a>格式需求  
 您必須將`String`常值引號內 (`" "`)。 如果您必須包含引號，做為其中一個字串中的字元，您會使用兩個雙引號 (`""`)。 下列範例將說明這點。  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 請注意連續引號表示字串中的引號無關的開頭和結尾引號`String`常值。  
  
## <a name="string-manipulations"></a>字串操作  
 一旦指派字串給`String`變數時，該字串是*不可變*，這表示您無法變更其長度或內容。 當您改變任何方式的字串時，Visual Basic 來建立新的字串和放棄前一個。 `String`變數接著會指向新的字串。  
  
 您可以操作的內容`String`變數使用各種不同的字串函式。 下列範例說明<xref:Microsoft.VisualBasic.Strings.Left%2A>函式  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 另一個元件所建立的字串可能會填補開頭或尾端空格。 如果您收到此類字串時，您可以使用<xref:Microsoft.VisualBasic.Strings.Trim%2A>， <xref:Microsoft.VisualBasic.Strings.LTrim%2A>，和<xref:Microsoft.VisualBasic.Strings.RTrim%2A>函式來移除這些空格。  
  
 如需字串操作的詳細資訊，請參閱[字串](../../../visual-basic/programming-guide/language-features/strings/index.md)。  
  
## <a name="programming-tips"></a>程式設計提示  
  
-   **負的數字。** 請記住所持有字元`String`為不帶正負號，且不能代表負數值。 在任何情況下，您不應該使用`String`來保存數值。  
  
-   **Interop 考量。** 如果您要使用的元件不是針對.NET Framework 中，撰寫例如 Automation 或 COM 物件，請記得字串字元具有不同資料寬度 （8 位元） 在其他環境中。 如果您要將 8 位元的字元字串引數至這類元件，將它宣告為`Byte()`，陣列`Byte`項目，而不是`String`新的 Visual Basic 程式碼。  
  
-   **類型字元。** 附加識別項類型字元`$`到任何識別項會強制其成為`String`資料型別。 `String`有沒有常值類型字元。 不過，編譯器會將常值以引號括住 (`" "`) 做為`String`。  
  
-   **架構類型。** .NET Framework 中對應的類型是<xref:System.String?displayProperty=nameWithType>類別。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [操作說明：呼叫使用不帶正負號類型的 Windows 函式](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
