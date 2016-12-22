---
title: "如何：複製、刪除和移動檔案和資料夾 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "I/O [C#]"
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：複製、刪除和移動檔案和資料夾 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在下列範例中，會示範如何使用 <xref:System.IO?displayProperty=fullName> 命名空間 \(Namespace\) 的 <xref:System.IO.File?displayProperty=fullName>、<xref:System.IO.Directory?displayProperty=fullName>、<xref:System.IO.FileInfo?displayProperty=fullName> 和 <xref:System.IO.DirectoryInfo?displayProperty=fullName> 類別，同步複製、刪除和移動檔案及資料夾。  這些範例不提供進度列或任何其他使用者介面。  如果您要提供標準進度對話方塊，請參閱 [如何：提供檔案作業的進度對話方塊](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)。  
  
 <xref:System.IO.FileSystemWatcher?displayProperty=fullName> 可用來提供事件，讓您在處理多個檔案時計算進度。  另一種方法是使用平台叫用，呼叫 Windows Shell 中與檔案有關的相關方法。  如需如何非同步執行這些檔案作業的詳細資訊，請參閱[非同步檔案 I\/O](../Topic/Asynchronous%20File%20I-O.md)。  
  
## 範例  
 在下列範例中，會示範如何複製檔案和目錄。  
  
 [!CODE [csFilesandFolders#7](../CodeSnippet/VS_Snippets_VBCSharp/csFilesAndFolders#7)]  
  
## 範例  
 在下列範例中，會示範如何移動檔案和目錄。  
  
 [!CODE [csFilesandFolders#8](../CodeSnippet/VS_Snippets_VBCSharp/csFilesAndFolders#8)]  
  
## 範例  
 在下列範例中，會示範如何刪除檔案和目錄。  
  
 [!CODE [csFilesandFolders#9](../CodeSnippet/VS_Snippets_VBCSharp/csFilesAndFolders#9)]  
  
## 請參閱  
 <xref:System.IO?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [如何：提供檔案作業的進度對話方塊](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)   
 [檔案和資料流 I\/O](../Topic/File%20and%20Stream%20I-O.md)   
 [一般 I\/O 工作](../Topic/Common%20I-O%20Tasks.md)