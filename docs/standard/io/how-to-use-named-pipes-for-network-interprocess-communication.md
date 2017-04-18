---
title: "如何：使用具名管道進行網路處理序間通訊 | Microsoft Docs"
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
  - "全雙工通訊 [.NET Framework], 具名管道"
  - "模擬 [.NET Framework], 具名管道"
  - "訊息架構通訊 [.NET Framework], 具名管道"
  - "透過具名管道的多個連接"
  - "具名管道 [.NET Framework]"
  - "網路通訊 [.NET Framework], 具名管道"
  - "管道 [.NET Framework]"
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用具名管道進行網路處理序間通訊
具名管道可在管道伺服器與一個或多個管道用戶端之間提供處理序間通訊。  它們比在本機電腦上處理流程間通訊的匿名管道提供更多的功能。  具名管道支援在網路及多個伺服器執行個體上的全雙工通訊、訊息架構通訊、用戶端模擬。用戶端模擬可讓連接處理序在遠端伺服器上使用本身的使用權限集合。  
  
 若要實作具名管道，請使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 類別。  
  
## 範例  
 下列範例示範如何使用 <xref:System.IO.Pipes.NamedPipeServerStream> 類別建立具名管道。  在這個範例中，伺服器處理序會建立四個執行緒。  每個執行緒都接受一個用戶端連接。  連接的用戶端處理序接著將檔案名稱提供給伺服器。  如果用戶端有足夠的使用權限，伺服器處理序會開啟檔案，並將檔案內容傳送回用戶端。  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## 範例  
 下列範例顯示使用 <xref:System.IO.Pipes.NamedPipeClientStream> 類別的用戶端處理序。  用戶端會連接到伺服器處理序，並將檔案名稱傳送給伺服器。  這個範例使用模擬，因此執行用戶端應用程式的識別必須具有存取檔案的權限。  伺服器接著會將檔案內容傳送回用戶端。  檔案內容隨後會顯示在主控台上。  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## 穩固程式設計  
 這個範例中的用戶端和伺服器處理序是要在同一台電腦上執行，因此，提供給 <xref:System.IO.Pipes.NamedPipeClientStream> 物件的伺服器名稱為 `"."`。  如果用戶端和伺服器處理序在不同的電腦上，則 `"."` 會以執行伺服器處理序之電腦的網路名稱取代。  
  
## 請參閱  
 <xref:System.Security.Principal.TokenImpersonationLevel>   
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>   
 [管道](../../../docs/standard/io/pipe-operations.md)   
 [如何：使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)