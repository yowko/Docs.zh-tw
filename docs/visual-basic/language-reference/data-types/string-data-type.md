---
title: String 資料類型
ms.date: 07/20/2015
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
ms.openlocfilehash: cd4b64c101ae56928e84a04649e49c17b6f4023c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415501"
---
# <a name="string-data-type-visual-basic"></a>String 資料類型 (Visual Basic)

保留不帶正負號16位（2位元組）程式碼點的序列，其範圍介於0到65535之間。 每個程式*代碼點*或字元碼都代表一個 Unicode 字元。 字串可包含0到大約2000000000（2 ^ 31）個 Unicode 字元。  
  
## <a name="remarks"></a>備註  

 使用 `String` 資料類型來保存多個字元，而不需要的陣列管理額外負荷，也就 `Char()` 是元素的陣列 `Char` 。  
  
 的預設值 `String` 為 `Nothing` （null 參考）。 請注意，這與空字串（值 `""` ）不同。  
  
## <a name="unicode-characters"></a>Unicode 字元  

 Unicode 的第一個128程式碼點（0–127）對應到標準美式鍵盤上的字母和符號。 這些前128個程式碼點與 ASCII 字元集所定義的相同。 第二個128程式碼片段（128–255）代表特殊字元，例如以拉丁為基礎的字母、重音、貨幣符號和分數。 Unicode 會針對各種不同的符號使用其餘的程式碼點（256-65535）。 這包括全球文字字元、變音符號和數學和技術符號。  
  
 您可以在 <xref:System.Char.IsDigit%2A> <xref:System.Char.IsPunctuation%2A> 變數中的個別字元上使用和之類的方法， `String` 以判斷其 Unicode 分類。  
  
## <a name="format-requirements"></a>格式需求  

 您必須將常值括 `String` 在引號內（ `" "` ）。 如果您必須在字串中包含引號做為其中一個字元，您可以使用兩個連續的引號（ `""` ）。 下列範例將說明這點。  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 請注意，在字串中代表引號的連續引號，與開始和結束常值的引號無關 `String` 。  
  
## <a name="string-manipulations"></a>字串操作  

 一旦您將字串指派給 `String` 變數，該字串就是*不可變*的，這表示您無法變更其長度或內容。 當您以任何方式改變字串時，Visual Basic 會建立新的字串，並放棄上一個字串。 `String`然後，變數會指向新的字串。  
  
 您可以 `String` 使用各種字串函數來操作變數的內容。 下列範例說明函式 <xref:Microsoft.VisualBasic.Strings.Left%2A>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 另一個元件所建立的字串可能會以前置或尾端空格填補。 如果您收到這類字串，您可以使用 <xref:Microsoft.VisualBasic.Strings.Trim%2A> 、 <xref:Microsoft.VisualBasic.Strings.LTrim%2A> 和 <xref:Microsoft.VisualBasic.Strings.RTrim%2A> 函數來移除這些空格。  
  
 如需有關字串操作的詳細資訊，請參閱[字串](../../programming-guide/language-features/strings/index.md)。  
  
## <a name="programming-tips"></a>程式設計提示  
  
- **負數。** 請記住，保留的字元 `String` 是不帶正負號的，而且不能代表負數值。 在任何情況下，您都不應該使用 `String` 來保存數值。  
  
- **Interop 考量：** 如果您要使用的元件不是針對 .NET Framework 所撰寫（例如 Automation 或 COM 物件），請記住，在其他環境中，字串字元具有不同的資料寬度（8位）。 如果您要將8位字元的字串引數傳遞給這類元件，請將它宣告為 `Byte()` 、 `Byte` 元素陣列，而不是 `String` 新的 Visual Basic 程式碼。  
  
- **輸入字元。** 將識別項型別字元附加 `$` 至任何識別碼，會強制其成為 `String` 資料類型。 `String`沒有常數值型別字元。 不過，編譯器會將以引號（）括住的常值視為 `" "` `String` 。  
  
- **架構類型：** .NET Framework 中的對應類型是 <xref:System.String?displayProperty=nameWithType> 類別。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.String?displayProperty=nameWithType>
- [資料類型](index.md)
- [Char 資料類型](char-data-type.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [轉換摘要](../keywords/conversion-summary.md)
- [作法：呼叫不帶正負號的類型的 Windows 函式](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效率地使用資料類型](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
