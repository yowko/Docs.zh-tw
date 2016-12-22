---
title: "Using Regular Expressions with the MaskedTextBox Control in Visual Basic | Microsoft Docs"
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
  - "strings [Visual Basic], regular expressions"
  - "strings [Visual Basic], masked edit"
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Using Regular Expressions with the MaskedTextBox Control in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

這個範例會轉換簡單的規則運算式，搭配 <xref:System.Windows.Forms.MaskedTextBox> 控制項一起使用。  
  
## 遮罩語言說明  
 標準的 <xref:System.Windows.Forms.MaskedTextBox> 遮罩語言是以 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 之 `Masked Edit` 控制項中所使用的同一遮罩語言為基礎，對於從該平台移轉過來的使用者而言應該不陌生。  
  
 <xref:System.Windows.Forms.MaskedTextBox> 控制項的 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> 屬性 \(Property\) 會指定要使用哪個輸入遮罩。  該遮罩必須是由下表中一或多個遮罩項目所組成的字串。  
  
|遮罩項目|描述|規則運算式項目|  
|----------|--------|-------------|  
|0|任何介於 0 和 9 之間的單一數字。  必要項目。|\\d|  
|9|數字或空格。  選擇項目。|\[ \\d\]?|  
|\#|數字或空格。  選擇項目。  如果將遮罩中的這個位置保留空白，則它會呈現為空格。  允許使用加號 \(\+\) 和減號 \(\-\)。|\[ \\d\+\-\]?|  
|L|ASCII 字母。  必要項目。|\[a\-zA\-Z\]|  
|?|ASCII 字母。  選擇項目。|\[a\-zA\-Z\]?|  
|&|字元 \(Character\)。  必要項目。|\[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lm}\\p{Lo}\]|  
|C|字元 \(Character\)。  選擇項目。|\[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lm}\\p{Lo}\]?|  
|A|英數字元。  選擇項目。|\\W|  
|.|適當文化特性的小數位數符號。|無法使用。|  
|,|適當文化特性專用的千位數符號。|無法使用。|  
|:|適當文化特性專用的時間分隔符號。|無法使用。|  
|\/|適當文化特性專用的日期分隔符號。|無法使用。|  
|$|適當文化特性專用的貨幣符號。|無法使用。|  
|\<|將之後的所有字元轉換成小寫。|無法使用。|  
|\>|將後面的所有字元轉換成大寫。|無法使用。|  
|&#124;|復原先前的上移或下移動作。|無法使用。|  
|\\|逸出遮罩字元，將它轉換成常值。 「  \\\\" 是反斜線的逸出序列。|\\|  
|所有其他字元。|常值。  所有非遮罩項目在 <xref:System.Windows.Forms.MaskedTextBox> 內都將以原貌呈現。|所有其他字元。|  
  
 顯示小數點 \(.\)、千位數 \(,\)、時間 \(:\)、日期 \(\/\) 和貨幣 \($\) 符號時，預設為顯示應用程式之文化特性所定義的符號。  您可以使用 <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> 屬性，強制顯示其他文化特性的符號。  
  
## 規則運算式和遮罩  
 雖然規則運算式和遮罩都可以用於驗證使用者輸入，但這兩者並非全然相同。  規則運算式可以表達比遮罩更複雜的模式，而遮罩可以用更簡潔的方式和文化特性所特有的格式，表達相同的資訊。  
  
 下表會比較四個規則運算式，以及每個規則運算式的對等遮罩。  
  
|規則運算式|遮罩|備註|  
|-----------|--------|--------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|遮罩中的 `/` 字元是邏輯日期分隔符號，對使用者而言，它將會顯示為應用程式目前之文化特性所特有的日期分隔符號。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|美國的日期格式 \(天、月份縮寫和年份\)，其中三個字母的月份縮寫格式顯示為第一個字母大寫，後面為兩個小寫字母。|  
|`(\(\d{3}\)-)?  \d{3}-d{4}`|`(999)-000-0000`|美國的電話號碼，區碼為選擇項。  如果使用者不希望輸入選擇項的字元，則可以輸入空格，或直接將滑鼠指標置於遮罩中由第一個 0 所表示的位置上。|  
|`$\d{6}.00`|`$999,999.00`|範圍在 0\-999999 內的貨幣值。  貨幣、千位和十進位字元將會在執行階段由文化特性特有的對等項目所取代。|  
  
## 請參閱  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>   
 <xref:System.Windows.Forms.MaskedTextBox>   
 [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)   
 [MaskedTextBox 控制項](../Topic/MaskedTextBox%20Control%20\(Windows%20Forms\).md)