---
title: ".NET Framework 中的管道作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "管道 [.NET Framework]"
  - "管道作業 [.NET Framework]"
  - "處理序間通訊 [.NET Framework]，管道"
  - "I/O [.NET Framework]，管道"
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# .NET Framework 中的管道作業
管道提供處理序間通訊的方法。  管道有兩種：  
  
-   匿名管道。  
  
     匿名管道提供本機電腦上處理序之間通訊的方法。  匿名管道的負荷比具名管道少，但提供的服務有限。  匿名管道是單向的，無法用於網路上。  這種管道只支援單一伺服器執行個體。  匿名管道適合用於執行緒之間的通訊，或是父處理序 \(Parent Process\) 與子處理序 \(Child Process\) 之間的通訊，因為當子處理序建立時，可以很容易將管道控制碼傳遞給它。  
  
     在 .NET Framework 中，實作匿名管道的方式是使用<xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 類別。  
  
     請參閱 [如何：使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)。  
  
-   具名管道。  
  
     具名管道可在管道伺服器與一個或多個管道用戶端之間提供處理序間通訊。  具名管道可以是單向或雙向的。  這種管道支援訊息架構通訊，可讓多個用戶端使用相同的管道名稱同時連接至伺服器處理序。  具名管道也支援模擬，這可讓連接的處理序在遠端伺服器上使用其本身的使用權限。  
  
     在 .NET Framework 中，實作具名管道的方式是使用<xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 類別。  
  
     請參閱 [如何：使用具名管道進行網路處理序間通訊](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)。  
  
## 請參閱  
 [檔案和資料流 I\/O](../../../docs/standard/io/index.md)   
 [如何：使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)   
 [如何：使用具名管道進行網路處理序間通訊](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)