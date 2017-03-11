---
title: "無法將檔案儲存至 TEMP | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID735"
ms.assetid: 1055fc15-9641-43b2-a40c-a0a9fbbb34b2
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# 無法將檔案儲存至 TEMP
元件找不到名為 TEMP 的目錄，或包含 TEMP 目錄的磁碟機或磁碟分割的空間不足，無法儲存資訊。  
  
### 更正這個錯誤  
  
1.  建立名為 "TEMP" 的目錄，並設定等於其路徑的 TEMP 環境變數。  
  
2.  清除不必要的檔案來清出磁碟機上的空間，或在另一個磁碟分割上建立 TEMP 目錄，並設定等於其路徑的 TEMP 環境變數。  
  
## 請參閱  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)