---
title: "String Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.String"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], character"
  - "strings [Visual Basic], fixed-length"
  - "string keyword [Visual Basic]"
  - "fixed-length strings, string data type"
  - "literals, string"
  - "text [Visual Basic], String data type"
  - "$ identifier type character"
  - "String data type"
  - "fixed-length strings"
  - "string literals"
  - "data types [Visual Basic], assigning"
  - "" String literals"
  - "identifier type characters, $"
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# String Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

保存不帶正負號的 16 位元 \(2 個位元組\) 字碼指標的序列，其範圍是在從 0 到 65535 的值。  每個「*字碼指標*」或字元碼，都表示單一的 Unicode 字元。  一個字串能包含 0 個到約二十億 \(2 ^ 31\) 個 Unicode 字元。  
  
## 備註  
 使用 `String` 資料型別保存多個字元，而不需 `Char()` \(`Char` 項目的陣列\) 的陣列管理負荷。  
  
 `String` 的預設值為 `Nothing` \(null 參考\)。  請注意，這不同於空字串 \(值 `""`\)。  
  
## Unicode 字元  
 Unicode 的前 128 個字碼指標 \(0–127\) 對應於標準美式鍵盤上的字母和符號。  鍵盤。  這些前 128 個字碼指標和 ASCII 字元集中所定義的字碼指標相同。  後 128 個字碼指標 \(128–255\) 代表的是特殊字元，例如拉丁文字母、腔調字、貨幣符號與分數。  Unicode 可將其餘字碼指標 \(256\-65535\) 用於各種符號，  包括各國文字字元、變音符號 \(Diacritic\) 以及數學和技術符號。  
  
 您可以針對 `String` 變數中的個別字元使用如 <xref:System.Char.IsDigit%2A> 和 <xref:System.Char.IsPunctuation%2A> 等方法，來判斷其 Unicode 分類。  
  
## 格式需求  
 您必須將 `String` 常值括在雙引號 \(`" "`\) 內。  如果您必須併入引號做為字串的其中一個字元，請使用兩個雙引號 \(`""`\)。  下列範例將說明這點。  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 請注意，代表字串中引號的雙引號，與開始和結束 `String` 常值的引號無關。  
  
## 字串操作  
 一旦將字串指派給 `String` 變數，該字串就會是「*不變的*」，表示您無法變更其長度或內容。  當您以任何方法變更字串時，Visual Basic 會建立新的字串並放棄先前的字串。  然後，`String` 變數會指向新的字串。  
  
 您可以使用各種字串函式操作 `String` 變數的內容。  下列範例說明 <xref:Microsoft.VisualBasic.Strings.Left%2A> 函式。  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 其他元件所建立的字串可能會填補前端或後端空白字元。  如果收到此類字串，您可以使用 <xref:Microsoft.VisualBasic.Strings.Trim%2A>、<xref:Microsoft.VisualBasic.Strings.LTrim%2A> 和 <xref:Microsoft.VisualBasic.Strings.RTrim%2A> 函式來移除這些空白字元。  
  
 如需字串操作的詳細資訊，請參閱 [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md)。  
  
## 程式設計提示  
  
-   **負數：** 請記住，`String` 所保留的字元不帶正負號，因此無法表示負值。  無論如何，您都不應該使用 `String` 來存放數值。  
  
-   **Interop 考量：** 如果您正在使用的元件不是針對 .NET Framework 所撰寫 \(例如 Automation 或 COM 物件\)，請記住，字串字元在其他環境中會有不同的資料寬度 \(8 位元\)。  如果您正在傳遞 8 位元字元的字串引數給此種元件，請將它宣告為 `Byte()` \(`Byte` 項目的陣列\)，而不是新 Visual Basic 程式碼中的 `String`。  
  
-   **型別字元。** 將識別碼型別字元 `$` 附加到任何識別項，會強制其成為 `String` 資料型別。  `String` 沒有常值型別字元。  但是，編譯器會將括在引號 \(`" "`\) 中的常值視為 `String` 處理。  
  
-   **架構型別。** .NET Framework 中的對應型別為 <xref:System.String?displayProperty=fullName> 類別。  
  
## 請參閱  
 <xref:System.String?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)