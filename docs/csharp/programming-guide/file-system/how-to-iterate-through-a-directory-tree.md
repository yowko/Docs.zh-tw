---
title: "如何：逐一查看目錄樹狀結構 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "檔案逐一查看 [C#]"
  - "逐一查看資料夾 [C#]"
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# 如何：逐一查看目錄樹狀結構 (C# 程式設計手冊)
「逐一查看目錄樹狀結構」一詞，代表存取指定根資料夾下每個巢狀子目錄中任意深度的每個檔案。  您不需要開啟每個檔案。  只需要以 `string` 方式擷取檔案或子目錄的名稱，或者以 <xref:System.IO.FileInfo?displayProperty=fullName> 或 <xref:System.IO.DirectoryInfo?displayProperty=fullName> 物件的型式擷取其他的資訊。  
  
> [!NOTE]
>  在 Windows 中可以交替使用「目錄」和「資料夾」這兩個詞彙。  大部分的文件和使用者介面文字是使用「資料夾」，但 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別庫是使用「目錄」一詞。  
  
 在最簡單的情況下，當您確定具有指定根資料夾下所有目錄的存取權限時，則可以使用 `System.IO.SearchOption.AllDirectories` 旗標。  這個旗標會傳回符合指定模式的所有巢狀子目錄。  下列範例顯示如何使用這個旗標。  
  
```c#  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 這個方式有個缺點，就是指定根資料夾下如果有任何一個子目錄造成 <xref:System.IO.DirectoryNotFoundException> 或 <xref:System.UnauthorizedAccessException>，整個方法就會失敗並且不會傳回任何目錄。  同樣的情形也適用於使用 <xref:System.IO.DirectoryInfo.GetFiles%2A> 方法時。  如果必須對特定子資料夾處理這些例外狀況 \(Exception\)，您必須手動走遍目錄樹狀結構，如下列範例所示。  
  
 手動走遍目錄樹狀結構時，您可以先處理子目錄 \(「*前序走訪*」\(Pre\-order Traversal\)\)，或是先處理檔案 \(「*後序走訪*」\(Post\-order Traversal\)\)。  如果執行的是前序走訪，您要先走遍目前資料夾下的整個樹狀結構，才逐一查看直接位於資料夾本身中的檔案。  本文件稍後的範例會執行後序走訪，但您只要簡單修改一下即可執行前序走訪。  
  
 另一個選擇為是否要使用遞迴或堆疊式走訪。  本文件稍後的範例會顯示這兩種方式。  
  
 如果必須對檔案和資料夾執行各式各樣的作業，您可以藉由將作業重構到個別函式中以模組化這些範例，這樣就可以使用單一委派 \(Delegate\) 來叫用這些函式。  
  
> [!NOTE]
>  NTFS 檔案系統可以包含的「*重新分析點*」\(Reparse Point\) 型式有「*連接點交叉點*」\(Junction Point\)、「*符號連結*」\(Symbolic Link\) 和「*永久連結*」\(Hard Link\)。  而 <xref:System.IO.DirectoryInfo.GetFiles%2A> 和 <xref:System.IO.DirectoryInfo.GetDirectories%2A> 這類的 .NET Framework 方法，不會傳回重新分析點下的任何子目錄。  這個行為可以在兩個重新分析點彼此參考時，預防進入無限迴圈的風險。  一般而言，處理重新分析點要特別謹慎，避免不小心修改或刪除檔案。  如果需要精確控制重新分析點，請使用平台叫用或機器碼，直接呼叫適當的 Win32 檔案系統方法。  
  
## 範例  
 下列範例會示範如何使用遞迴走遍目錄樹狀結構。  遞迴是很簡潔的方式，但在目錄樹狀結構很大且巢狀結構很深時，很可能造成堆疊溢位 \(Stack Overflow\) 例外狀況。  
  
 這裡所處理的特定例外狀況，以及對每個檔案和資料夾所執行的特定動作，都僅是提供做為範例用途。  您應該針對您的特定需求修改這個程式碼。  如需詳細資訊，請參閱程式碼中的註解。  
  
 [!code-cs[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## 範例  
 下列範例會示範如何在不使用遞迴的情況下，逐一查看目錄樹狀結構中的檔案和資料夾。  這項技術使用泛型 <xref:System.Collections.Generic.Stack%601> 集合型別，這是屬於後進先出 \(LIFO\) 堆疊。  
  
 這裡所處理的特定例外狀況，以及對每個檔案和資料夾所執行的特定動作，都僅是提供做為範例用途。  您應該針對您的特定需求修改這個程式碼。  如需詳細資訊，請參閱程式碼中的註解。  
  
 [!code-cs[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 藉由測試每個資料夾，判斷應用程式是否有權限開啟資料夾的作業，通常都非常耗時。  因此，程式碼範例只有在 `try/catch` 區塊中封入該部分的作業。  您可以修改 `catch` 區塊，好讓您在存取資料夾遭到拒絕時，可以嘗試升級權限，然後再次存取資料夾。  通常，您只需要攔截那些您可以處理的例外狀況，不要讓應用程式處於未知狀態。  
  
 如果必須儲存目錄樹狀結構的內容，不管是存於記憶體或磁碟中，最佳的選項就是只要儲存每個檔案的 <xref:System.IO.FileSystemInfo.FullName%2A> 屬性 \(型別為 `string`\)。  然後，您可以視需要使用這個字串建立新 <xref:System.IO.FileInfo> 或 <xref:System.IO.DirectoryInfo> 物件，或者是開啟任何需要其他處理的檔案。  
  
## 穩固程式設計  
 建立穩固的檔案逐一查看程式碼，必須考慮許多檔案系統的複雜度。  如需詳細資訊，請參閱 [NTFS 技術參考](http://go.microsoft.com/fwlink/?LinkId=79488) \(英文\)。  
  
## 請參閱  
 <xref:System.IO>   
 [LINQ and File Directories](../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)   
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)