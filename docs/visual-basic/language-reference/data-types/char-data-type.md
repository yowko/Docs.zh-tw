---
title: "Char Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Char"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literal type characters, C"
  - "Char data type"
  - "C literal type character"
  - "data types [Visual Basic], assigning"
  - "Char data type, character literals"
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Char Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

保存不帶正負號的 16 位元 \(2 個位元組\) 字碼指標，值的範圍從 0 到 65535。  每個「*字碼指標*」或字元碼，都表示單一的 Unicode 字元。  
  
## 備註  
 只需要保留單一字元而不需使用 `String` 的額外負荷時，請使用 `Char` 資料型別。  在某些情況下，可使用 `Char()` \(`Char` 元素的陣列\) 來保留多個字元。  
  
 `Char` 的預設值是擁有字碼指標 0 的字元。  
  
## Unicode 字元  
 Unicode 的前 128 個字碼指標 \(0–127\) 對應於標準美式鍵盤上的字母和符號。  鍵盤。  這些前 128 個字碼指標和 ASCII 字元集中所定義的字碼指標相同。  後 128 個字碼指標 \(128–255\) 代表的是特殊字元，例如拉丁文字母、腔調字、貨幣符號與分數。  Unicode 將其餘字碼指標 \(256\-65535\) 使用在各種符號，包括各國文字字元、變音符號以及數學和技術符號。  
  
 您可以在 `Char` 變數上，使用像是 <xref:System.Char.IsDigit%2A> 和 <xref:System.Char.IsPunctuation%2A> 等方法，決定其 Unicode 分類。  
  
## 型別轉換  
 Visual Basic 不會在 `Char` 和數字型別之間進行直接轉換。  您可以使用 <xref:Microsoft.VisualBasic.Strings.Asc%2A> 或 <xref:Microsoft.VisualBasic.Strings.AscW%2A> 函式，將 `Char` 值轉換成 `Integer`，表示其字碼指標。  您可以使用 <xref:Microsoft.VisualBasic.Strings.Chr%2A> 或 <xref:Microsoft.VisualBasic.Strings.ChrW%2A> 函式，將 `Integer` 值轉換成具備該字碼指標的 `Char`。  
  
 如果型別檢查參數 \([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)\) 是 on，則必須將常值型別字元附加至單一字元字串常值，將其識別為 `Char` 資料型別。  下列範例將說明這點。  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## 程式設計提示  
  
-   **負數**：`Char` 是不帶正負號的型別且無法代表負值。  無論如何，您都不應該使用 `Char` 來存放數值。  
  
-   **Interop 考量：** 如果您正在使用的元件不是針對 .NET Framework 所撰寫 \(例如 Automation 或 COM 物件\)，請記住，字元型別在其他環境中會有不同的資料寬度 \(8 位元\)。  如果傳遞 8 位元引數到這類元件，則需將其宣告為 `Byte` 而不是新 Visual Basic 程式碼中的 `Char`。  
  
-   **擴展：** `Char` 資料型別會擴大至 `String`。  這表示您可以將 `Char` 轉換成 `String` 而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
-   **型別字元。** 將常值型別字元 `C` 附加至單一字元字串常值，便會強制它成為 `Char` 資料型別。  `Char` 沒有識別項型別字元。  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.Char?displayProperty=fullName> 結構。  
  
## 請參閱  
 <xref:System.Char?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)