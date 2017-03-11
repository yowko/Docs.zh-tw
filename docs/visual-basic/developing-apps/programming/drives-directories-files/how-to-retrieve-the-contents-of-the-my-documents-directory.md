---
title: "How to: Retrieve the Contents of the My Documents Directory in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My Documents directory"
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Retrieve the Contents of the My Documents Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> 物件可用於讀取 \[**All Users**\] 目錄中的數個目錄，例如 \[**我的文件**\] 或 \[**桌面**\]。  
  
### 若要讀取我的文件資料夾  
  
-   使用 `ReadAllText` 方法，讀取特定目錄中每一個檔案的文字。  下列程式碼會指定目錄與檔案，然後使用 `ReadAllText` 將它們讀入名為 `patients` 的字串。  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-retrieve-the-cont_1.vb)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>