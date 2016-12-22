---
title: "ConnectionTimeout 必須大於 0 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrNetwork_BadConnectionTimeout"
ms.assetid: 15ac09a7-47f0-44f3-9e84-5bd10bd07450
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ConnectionTimeout 必須大於 0
使用 [My.Computer.Network Object](../../visual-basic/language-reference/objects/my-computer-network-object.md) 上傳和下載檔案時，您必須指定大於 `0` 的 `connectionTimeout`。  
  
### 更正這個錯誤  
  
-   請提供大於 `0` 的 `connectionTimeout`。  
  
## 請參閱  
 [My.Computer.Network.UploadFile 方法](http://msdn.microsoft.com/zh-tw/5505ea3e-3dbd-460b-9f8f-62c84c0a4de6)   
 [My.Computer.Network.DownloadFile 方法](http://msdn.microsoft.com/zh-tw/aeb7ed8f-1ac9-4242-ae57-9f35914eb329)   
 [How to: Upload a File](../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)   
 [How to: Download a File](../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)   
 [.NET Framework 中使用 Visual Basic 的網路作業](http://msdn.microsoft.com/zh-tw/c5379021-44ef-4d6a-acf5-e951fdcab6b2)