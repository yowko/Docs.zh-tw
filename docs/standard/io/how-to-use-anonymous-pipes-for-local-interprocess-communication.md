---
title: "如何：使用匿名管道進行本機處理序間通訊 | Microsoft Docs"
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
  - "匿名管道 [.NET Framework]"
  - "本機電腦通訊 [.NET Framework], 管道"
  - "單向通訊 [.NET Framework]"
  - "父子通訊 [.NET Framework]"
  - "管道 [.NET Framework]"
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用匿名管道進行本機處理序間通訊
匿名管道提供本機電腦上處理序之間通訊的方法。  它們提供的功能比具名管道少，但其負荷也少。  您可以使用匿名管道，讓本機電腦上的處理序之間更容易通訊。  匿名管道不能用於網路上的通訊。  
  
 若要實作匿名管道，請使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 類別。  
  
## 範例  
 下列範例示範如何使用匿名管道，將字串從父處理序 \(Parent Process\) 傳送到子處理序 \(Child Process\)。  這個範例會在父處理序中建立一個 <xref:System.IO.Pipes.AnonymousPipeServerStream> 物件，並將其 <xref:System.IO.Pipes.PipeDirection> 值設為 <xref:System.IO.Pipes.PipeDirection>。  父處理序接著再建立一個子處理序，方式是使用用戶端控制碼建立 <xref:System.IO.Pipes.AnonymousPipeClientStream> 物件。  這個子處理序的 <xref:System.IO.Pipes.PipeDirection> 值為 <xref:System.IO.Pipes.PipeDirection>。  
  
 父處理序接著將使用者提供的字串傳送到子處理序。  主控台會顯示子處理序中的這個字串。  
  
 下列範例顯示伺服器處理序。  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## 範例  
 下列範例顯示用戶端處理序。  伺服器處理序會啟動用戶端處理序，給予該處理序用戶端控制碼。  從用戶端程式碼產生的可執行檔應名為 `pipeClient.exe` 並在執行伺服器處理序前，複製到與伺服器可執行檔相同的目錄中。  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## 請參閱  
 [管道](../../../docs/standard/io/pipe-operations.md)   
 [如何：使用具名管道進行網路處理序間通訊](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)