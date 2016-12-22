---
title: "File is too large to read into a byte array | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# File is too large to read into a byte array
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您嘗試讀取到位元組陣列的檔案大小超過 4 GB。  `My.Computer.FileSystem.ReadAllBytes` 方法無法讀取超過此大小的檔案。  
  
### 若要更正這個錯誤  
  
-   使用 <xref:System.IO.StreamReader> 讀取檔案。  如需詳細資訊，請參閱 [.NET Framework 檔案 I\/O 和檔案系統基本概念 \(Visual Basic\)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>   
 <xref:System.IO.StreamReader>   
 [File Access with Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)   
 [How to: Read Text from Files with a StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)