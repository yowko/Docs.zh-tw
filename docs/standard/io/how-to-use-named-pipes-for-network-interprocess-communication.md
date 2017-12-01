---
title: "如何：使用具名管道進行網路處理序間通訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communcation [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 952600e71311184c4a4f906734addbf335d0358a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>如何：使用具名管道進行網路處理序間通訊
具名的管道提供一個或多個管道用戶端之間的處理序間通訊。 它們比在本機電腦上處理流程間通訊的匿名管道提供更多的功能。 具名管道支援在網路及多個伺服器執行個體上進行全雙工通訊、訊息架構通訊及用戶端模擬。用戶端模擬可讓連接處理序在遠端伺服器上使用本身的權限集合。  
  
 若要實作具名管道，請使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立使用具名的管道<xref:System.IO.Pipes.NamedPipeServerStream>類別。 在此範例中，伺服器處理序會建立四個執行緒。 每個執行緒可接受用戶端連線。 連線的用戶端處理序，然後提供具有檔案名稱的伺服器。 如果用戶端有足夠的權限，伺服器處理序開啟的檔案，並將其內容傳送回用戶端。  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>範例  
 下列範例示範用戶端處理序，會使用<xref:System.IO.Pipes.NamedPipeClientStream>類別。 用戶端連接至伺服器處理序，並且傳送至伺服器的檔案名稱。 此範例會使用模擬，以便執行用戶端應用程式的身分識別必須擁有存取該檔案的權限。 伺服器接著會傳送回用戶端檔案的內容。 檔案內容隨即顯示到主控台。  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 在此範例中的用戶端和伺服器處理程序要在相同的電腦上執行，因此伺服器名稱提供給<xref:System.IO.Pipes.NamedPipeClientStream>物件是`"."`。 如果不同的電腦上所執行的用戶端和伺服器處理`"."`會變成執行的伺服器處理序的電腦的網路名稱。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
 [管道](../../../docs/standard/io/pipe-operations.md)  
 [操作說明：使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
