---
title: "如何：取得有關檔案、資料夾和磁碟機的資訊 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "檔案 [C#], 取得相關資訊"
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# 如何：取得有關檔案、資料夾和磁碟機的資訊 (C# 程式設計手冊)
在 .NET Framework 中，您可以使用下列類別 \(Class\) 存取檔案系統資訊：  
  
-   <xref:System.IO.FileInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DriveInfo?displayProperty=fullName>  
  
-   <xref:System.IO.Directory?displayProperty=fullName>  
  
-   <xref:System.IO.File?displayProperty=fullName>  
  
 <xref:System.IO.FileInfo> 和 <xref:System.IO.DirectoryInfo> 類別表示檔案或目錄，而包含的屬性 \(Property\) 可公開 NTFS 檔案系統支援的許多檔案屬性 \(Attribute\)。  這兩個類別也包含可用來開啟、關閉、移動和刪除檔案及資料夾的方法。  只要將表示檔案、資料夾或磁碟機的名稱傳遞給建構函式 \(Constructor\)，就可以建立這些類別的執行個體 \(Instance\)。  
  
```c#  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 您還可以呼叫 <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=fullName>、<xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=fullName> 和 <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=fullName>，取得檔案、資料夾或磁碟機的名稱。  
  
 <xref:System.IO.Directory?displayProperty=fullName> 和 <xref:System.IO.File?displayProperty=fullName> 類別提供的靜態 \(Static\) 方法可用來擷取目錄及檔案的相關資訊。  
  
## 範例  
 在下列範例中，會示範各種方法來存取檔案和資料夾的相關資訊。  
  
 [!code-cs[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#6)]  
  
## 穩固程式設計  
 處理使用者指定的路徑字串時，也必須處理下列情形的例外狀況 \(Exception\)：  
  
-   檔案名稱格式不正確，  例如包含無效字元或只有泛空白字元 \(White Space\)。  
  
-   檔案名稱為 null。  
  
-   檔案名稱長度超過系統定義的最大長度。  
  
-   檔案名稱包含冒號 \(:\)。  
  
 如果應用程式沒有足夠的權限可以讀取指定的檔案，則無論路徑是否存在，`Exists` 方法都會傳回 `false`，此方法並不會擲回例外狀況。  
  
## 請參閱  
 <xref:System.IO?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)