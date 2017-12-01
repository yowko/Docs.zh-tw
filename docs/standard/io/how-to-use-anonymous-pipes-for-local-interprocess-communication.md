---
title: "如何：使用匿名管道進行本機處理序間通訊"
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
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f457cc91e6fbfc118e5363d1b0a8e8c2ad800748
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>如何：使用匿名管道進行本機處理序間通訊
匿名管道提供在本機電腦上的處理序間通訊。 它們提供的功能比具名管道少，但其負荷也比較小。 您可以在本機電腦上輕鬆處理序間通訊使用匿名管道。 您無法透過網路來使用匿名管道進行通訊。  
  
 若要實作匿名管道，請使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 類別。  
  
## <a name="example"></a>範例  
 下列範例會示範如何從父處理序的字串傳送至子處理序使用匿名管道。 這個範例會建立<xref:System.IO.Pipes.AnonymousPipeServerStream>父處理序中的物件<xref:System.IO.Pipes.PipeDirection>值<xref:System.IO.Pipes.PipeDirection.Out>。 父處理序然後建立子處理序使用的用戶端控制代碼來建立<xref:System.IO.Pipes.AnonymousPipeClientStream>物件。 子處理序具有<xref:System.IO.Pipes.PipeDirection>值<xref:System.IO.Pipes.PipeDirection.In>。  
  
 父處理序便會傳送給子處理序的使用者提供的字串。 此字串會顯示子處理序中的主控台。  
  
 下列範例會顯示伺服器處理序。  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a>範例  
 下列範例會示範用戶端處理序。 伺服器處理序會啟動用戶端處理序，並提供該程序的用戶端控制代碼。 用戶端程式碼產生可執行檔應該命名為`pipeClient.exe`而會複製到伺服器之前執行的伺服器處理序可執行檔相同的目錄。  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>另請參閱  
 [管道](../../../docs/standard/io/pipe-operations.md)  
 [操作說明：使用具名管道進行網路處理序間通訊](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
