---
title: "Input past end of file | Microsoft Docs"
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
  - "vbrID62"
dev_langs: 
  - "VB"
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Input past end of file
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

可能是由於 `Input` 陳述式正在讀取的檔案是空的，或者讀取檔案中有一筆資料正在使用，也可能是因為您對以二進位存取方式開啟的檔案使用了 `EOF` 函式。  
  
### 若要更正這個錯誤  
  
1.  請在 `Input` 陳述式之前立即使用 `EOF` 函式，以便偵測檔案結尾。  
  
2.  如果檔案是以二進位存取方式開啟的，請使用 `Seek` 和 `Loc`。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>