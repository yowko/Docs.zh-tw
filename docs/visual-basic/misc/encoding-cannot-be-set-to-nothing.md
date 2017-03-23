---
title: "編碼不能設定為 Nothing。 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# 編碼不能設定為 Nothing。
讀取或寫入檔案的嘗試失敗，因為參數 `encoding` 已設定為 `Nothing`，但需要有效的值。  
  
 <xref:System.Text.Encoding> 用來判斷在寫入檔案時要使用的編碼方式。 預設值為 UTF\-8。  
  
### 更正這個錯誤  
  
-   請為 `encoding` 參數提供有效的值。  
  
## 請參閱  
 [File Encodings](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)   
 [Reading from Files](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Writing to Files](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)   
 [My.Computer.FileSystem.ReadAllText 方法](http://msdn.microsoft.com/zh-tw/3a7ac8be-fb1d-4087-bc65-167d6754d57f)   
 [My.Computer.FileSystem.WriteAllText 方法](http://msdn.microsoft.com/zh-tw/f507460c-87d9-4504-b74f-3ff825c7d5c4)