---
title: "字串函式 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "字串函式"
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# 字串函式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

下表列出 Visual Basic 提供用來搜尋與處理字串的函式。  
  
|.NET Framework 方法|描述|  
|-----------------------|--------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|傳回 `Integer` 值，表示對應至字元的字元碼。|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|傳回與指定的字元碼關聯的字元。|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|傳回以零起始的陣列，其中包含以指定篩選準則為依據的 `String` 陣列子集。|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|傳回字串，其格式化方式是根據格式 `String` 運算式內包含的指令。|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|使用 \[系統\] 控制台中定義的貨幣符號，傳回格式化成貨幣值的運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|傳回表示日期\/時間值的字串運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|傳回格式化成數字的運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|傳回格式化成百分比的運算式 \(也就是乘以 100\)，並加上結尾的 % 字元。|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|傳回整數，指定一個字串在另一個字串內第一次出現的起始位置。|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|傳回某個字串在另一個字串中第一次出現的位置，從字串的右邊開始。|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|傳回結合包含在陣列中幾個子字串所建立的字串。|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|傳回已轉換成小寫的字串或字元。|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|傳回字串，其中包含從字串的左邊開始的指定數目的字元。|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|傳回包含字串中字元數的整數。|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|傳回靠左對齊的字串，其中包含調整為指定之長度的指定字串。|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|傳回包含指定字串複本的字串，但其中不包含前置空格。|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|傳回包含來自於某一字串之指定字元數量的字串。|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|傳回字串，其中的指定之子字串已經被另一個子字串取代了指定的次數。|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|傳回字串，其中包含從字串的右邊開始的指定數目的字元。|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|傳回靠右對齊的字串，其中包含調整為指定之長度的指定字串。|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|傳回包含指定字串複本的字串，但其中不包含尾端空格。|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|傳回字串，此字串是由指定之空格數所組成。|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|傳回以零起始的一維陣列，其中包含指定之子字串數目。|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|根據字串比較的結果傳回 \-1、0 或 1。|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|傳回依照指定方式轉換的字串。|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|傳回由重複指定次數的指定字元所組成的字串或物件。|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|傳回字串，其中的指定之字串的字元順序會顛倒。|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|傳回包含指定字串複本的字串，但其中不包含前置空格或尾端空格。|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|傳回包含已轉換成大寫之指定字串的字串或字元。|  
  
 您可以使用 [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) 陳述式，設定要使用由系統地區設定 \(`Text`\) 還是字元之內部二進位表示 \(`Binary`\) 所決定的區分大小寫文字排序順序來比較字串。  預設的文字比較方法是 `Binary`。  
  
## 範例  
 此範例使用 `UCase` 函式，傳回大寫字母版本的字串。  
  
 [!code-vb[VbVbalrStrings#31](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_1.vb)]  
  
## 範例  
 此範例使用 `LTrim` 函式刪除字串變數中的前置空格，並使用 `RTrim` 函式刪除字串變數中的尾端空格。  它會使用 `Trim` 函式刪除這兩種類型的空格。  
  
 [!code-vb[VbVbalrStrings#25](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_2.vb)]  
  
## 範例  
 此範例使用 `Mid` 函式，從字串中傳回指定數目的字元。  
  
 [!code-vb[VbVbalrStrings#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_3.vb)]  
  
## 範例  
 這個範例使用 `Len` 傳回字串中的字元數。  
  
 [!code-vb[VbVbalrStrings#33](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_4.vb)]  
  
## 範例  
 此範例使用 `InStr` 函式傳回某個字串在另一個字串中第一次出現的位置。  
  
 [!code-vb[VbVbalrStrings#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_5.vb)]  
  
## 範例  
 此範例將示範 `Format` 函式的各種使用方式，以透過 `String` 格式及使用者定義的格式，將值格式化。  對於日期分隔符號 \(`/`\)、時間分隔符號 \(`:`\) 和 AM\/PM 指示器 \(`t` 和 `tt`\) 而言，系統顯示的實際格式化輸出需視程式碼使用的地區設定而定。  當時間和日期顯示在開發環境內時，會使用程式碼地區設定的簡短時間格式和簡短日期格式。  
  
> [!NOTE]
>  若為使用 24 小時制的地區設定，AM\/PM 指示器 \(`t` 和 `tt`\) 不會顯示任何內容。  
  
 [!code-vb[VbVbalrStrings#27](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_6.vb)]  
  
## 請參閱  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)   
 [Visual Basic Runtime Library Members](../../../visual-basic/language-reference/runtime-library-members.md)   
 [String Manipulation Summary](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)