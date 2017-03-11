---
title: "如何：提供檔案作業的進度對話方塊 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "進度對話方塊 [C#]"
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 如何：提供檔案作業的進度對話方塊 (C# 程式設計手冊)
如果您使用 <xref:Microsoft.VisualBasic?displayProperty=fullName> 命名空間中的 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> 方法，則可以提供標準對話方塊來顯示 Windows 中檔案作業的進度。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要在 Visual Studio 中加入參考  
  
1.  在功能表列上，選擇 \[**專案**\]、\[**加入參考**\]。  
  
     \[**參考管理員**\] 對話方塊隨即出現。  
  
2.  在 \[**組件**\] 區域中，如果尚未選取，請選擇 \[**架構**\] 。  
  
3.  在名稱清單中，選取 \[**Microsoft.VisualBasic**\] 核取方塊，然後選擇 \[**確定**\] 按鈕以關閉對話方塊。  
  
## 範例  
 下列程式碼會將 `sourcePath` 指定的目錄複製到 `destinationPath` 指定的目錄。  這個程式碼也提供標準對話方塊，顯示作業完成前的預估剩餘時間量。  
  
 [!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#11)]  
  
## 請參閱  
 [檔案系統和登錄](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)