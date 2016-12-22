---
title: "如何：轉換 RTF 為純文字 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "字串 [C#]，從 RTF 轉換"
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：轉換 RTF 為純文字 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Rich Text Format \(RTF\) 是 Microsoft 在 1980 年代後期開發出來的文件格式，讓文件可跨作業系統進行交換。  Microsoft Word 和 WordPad 都可以讀取及寫入 RTF 文件。  在 .NET Framework 中，使用 <xref:System.Windows.Forms.RichTextBox> 控制項建立的文書處理器，可以支援 RTF 並讓使用者以 WYSIWIG 的方式將格式套用至文字。  
  
 <xref:System.Windows.Forms.RichTextBox> 控制項還可以讓您以程式設計方式，移除文件中的 RTF 格式程式碼，並將文件轉換成純文字。  您不需要在 Windows Form 中嵌入該控制項，就能執行這類作業。  
  
### 若要在專案中使用 RichTextBox 控制項  
  
1.  加入 System.Windows.Forms.dll 的參考。  
  
2.  加入 `System.Windows.Forms` 命名空間 \(Namespace\) 的 using 指示詞 \(選擇性\)。  
  
## 範例  
 下列範例會將範例 RTF 檔為純文字。  檔案包含 RTF 格式 \(例如字型資訊\)，四個 Unicode 字元和四個延伸 ASCII 字元。  當 RTF，擷取內容為文字，顯示在 <xref:System.Windows.Forms.MessageBox>上的文字，並輸出至文字以 UTF\-8 格式，的檔案範例程式碼會開啟檔案，將的內容儲存至 <xref:System.Windows.Forms.RichTextBox> 。  
  
 `MessageBox` 和輸出檔案包含下列文字:  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
  
```  
  
 [!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]  
  
 RTF 字元以八個位元來編碼，  不過，刪除指定的字碼頁，的延伸 ASCII 字元以外的使用者可以指定 Unicode 字元。  因為 <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> 屬性的型別是 [string](../../../csharp/language-reference/keywords/string.md)，因此會以 Unicode UTF\-16 來編碼字元。  原始碼 RTF 文件的任何延伸 ASCII 字元和 Unicode 字元在文字輸出中都可以正確編碼。  
  
 如果使用 <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> 方法將文字寫入磁碟，則會以 UTF\-8 \(不含位元組順序標記\) 來編碼文字。  
  
## 請參閱  
 <xref:System.Windows.Forms.RichTextBox?displayProperty=fullName>   
 [字串](../../../csharp/programming-guide/strings/index.md)