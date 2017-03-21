---
title: "字串資料類型 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.String
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings, string data type
- literals, string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals
- data types [Visual Basic], assigning
- String literals
- identifier type characters, $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
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
ms.openlocfilehash: 9221a89a1fb46609b4b8550968e3a2bbe874772c
ms.lasthandoff: 03/13/2017

---
# <a name="string-data-type-visual-basic"></a>String 資料類型 (Visual Basic)
保存不帶正負號的 16 位元 （2 個位元組） 字碼指標順序該範圍從 0 到 65535 的值。 每個*程式碼點*，或字元的代碼，表示單一 Unicode 字元。 字串可以包含從 0 到約二十億 (2 ^31) 的 Unicode 字元。  
  
## <a name="remarks"></a>備註  
 使用`String`資料型別來存放多個字元的陣列管理負擔不`Char()`，陣列`Char`項目。  
  
 預設值的`String`是`Nothing`（null 參考）。 請注意，這是不相同則為空字串 (值`""`)。  
  
## <a name="unicode-characters"></a>Unicode 字元  
 Unicode 的前 128 個字碼指標 (0-127) 對應至的字母和標準美式鍵盤上的符號。 這些第 128 個字碼指標是所定義的 ASCII 字元集的相同。 第二個 128 個字碼指標 (128-255) 代表特殊字元，例如拉丁文字母、 腔調字、 貨幣符號和句號。 Unicode 使用其餘的字碼指標 (256-65535) 的各種不同的符號。 這包括各國文字字元、 變音符號以及數學和技術的符號。  
  
 您可以使用的方法，例如<xref:System.Char.IsDigit%2A>和<xref:System.Char.IsPunctuation%2A>上中的個別字元`String`變數，以判斷其 Unicode 分類。</xref:System.Char.IsPunctuation%2A> </xref:System.Char.IsDigit%2A>  
  
## <a name="format-requirements"></a>格式需求  
 您必須將`String`常值雙引號 (`" "`)。 如果您必須為一個字元字串中包含引號，則會使用兩個雙引號 (`""`)。 下列範例將說明這點。  
  
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
 一旦指派字串給`String`變數時，該字串是*變*，這表示您無法變更其長度或內容。 當您改變任何方式的字串時，Visual Basic 來建立新的字串和放棄前一個。 `String`變數接著會指向新的字串。  
  
 您可以管理的內容`String`變數使用各種不同的字串函式。 下列範例說明<xref:Microsoft.VisualBasic.Strings.Left%2A>函式</xref:Microsoft.VisualBasic.Strings.Left%2A>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 另一個元件所建立的字串可能會填補前置或尾端空格。 如果您收到此類字串，您可以使用<xref:Microsoft.VisualBasic.Strings.Trim%2A>， <xref:Microsoft.VisualBasic.Strings.LTrim%2A>，和<xref:Microsoft.VisualBasic.Strings.RTrim%2A>函式來移除這些空格。</xref:Microsoft.VisualBasic.Strings.RTrim%2A> </xref:Microsoft.VisualBasic.Strings.LTrim%2A> </xref:Microsoft.VisualBasic.Strings.Trim%2A>  
  
 如需字串操作的詳細資訊，請參閱[字串](../../../visual-basic/programming-guide/language-features/strings/index.md)。  
  
## <a name="programming-tips"></a>程式設計提示  
  
-   **負的數字。** 請記住所持有的字元`String`是不帶正負號和不能代表負數值。 在任何情況下，您不應該使用`String`來保存數值。  
  
-   **Interop 考量。** 如果您要使用的元件不是撰寫.NET framework 中，例如 Automation 或 COM 物件，請記得字串字元具有不同的資料寬度 （8 位元） 在其他環境中。 如果您要將 8 位元的字元字串引數傳遞至這類元件，將它宣告為`Byte()`，陣列`Byte`項目，而不是`String`新的 Visual Basic 程式碼。  
  
-   **類型字元。** 將識別項類型字元附加`$`到任何識別項會強制其成為`String`資料型別。 `String`有任何常值類型的字元。 不過，編譯器會以引號括住的常值 (`" "`) 做為`String`。  
  
-   **架構類型。** .NET Framework 中對應的類型是<xref:System.String?displayProperty=fullName>類別。</xref:System.String?displayProperty=fullName>  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String?displayProperty=fullName></xref:System.String?displayProperty=fullName>   
 [資料型別](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Char 資料類型](../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換的摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [如何︰ 呼叫 Windows 函式會採用不帶正負號的類型](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

