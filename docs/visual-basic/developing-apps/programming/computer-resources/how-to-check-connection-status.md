---
title: "How to: Check Connection Status in Visual Basic | Microsoft Docs"
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
  - "Web connections"
  - "IsAvailable property, about IsAvailable"
  - "connections, checking status"
  - "connection status"
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# How to: Check Connection Status in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> 屬性可以用來判斷電腦是否具有工作網路或網際網路連線。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要檢查電腦是否有作用中的連接  
  
-   判斷 `IsAvailable` 屬性為 `True` 或 `False`。  下列程式碼會檢查屬性的狀態並報告：  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-check-connection-_1.vb)]  
  
     這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，這個程式碼片段位於 \[**連線和網路**\] 中。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A>