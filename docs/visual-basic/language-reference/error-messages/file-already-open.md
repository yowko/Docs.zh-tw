---
title: "File already open | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID55"
dev_langs: 
  - "VB"
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# File already open
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

有時候檔案必須先關閉，才能進行另一個 `FileOpen` 或其他作業。  可能導致本錯誤的各種原因包括：  
  
-   為已開啟的檔案，執行循序輸出模式 `FileOpen` 作業  
  
-   陳述式參考至已開啟的檔案。  
  
### 若要更正這個錯誤  
  
1.  請在執行陳述式之前先關閉該檔案。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>