---
title: "如何：寫入文字檔 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "TextWriter.WriteLine"
  - "StreamWriter.Close"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "檔案 [C#], 文字檔"
  - "文字, 寫入檔案 [C#]"
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# 如何：寫入文字檔 (C# 程式設計手冊)
在下列這些範例中，會示範幾個將文字寫入檔案的方法。  前兩個範例會在 <xref:System.IO.File?displayProperty=fullName> 類別上使用靜態便利方法，將任何 IEnumerable\<string\> 的每個項目和字串寫入文字檔。  範例 3 中會示範寫入檔案時，如何在需要分別處理每一行時，將文字加入至檔案。  範例 1\-3 會覆寫檔案中所有現有的內容，但是範例 4 將示範如何將文字附加至現有的檔案。  
  
 這些範例全都會將字串常值寫入至檔案，不過您可能比較想要使用 <xref:System.String.Format%2A> 方法，該方法提供許多控制項讓您撰寫不同類型的值，在欄位中靠右或靠左對齊、使用或不使用邊框間距等等。  您也可以使用 C\# [字串插值](../../../csharp/language-reference/keywords/interpolated-strings.md)功能。  
  
## 範例  
 [!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 這些範例全都會將字串常值寫入至檔案，不過您可能比較想要使用 <xref:System.String.Format%2A> 方法，該方法提供許多控制項讓您撰寫不同類型的值，在欄位中靠右或靠左對齊、使用或不使用邊框間距等等。  您也可以使用 C\# [字串插值](../../../csharp/language-reference/keywords/interpolated-strings.md)功能。  
  
## 穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   該檔案存在而且是唯讀的。  
  
-   路徑名稱可能太長。  
  
-   磁碟可能已滿。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [如何將自訂物件集合儲存至本機存放區](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)