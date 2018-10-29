---
title: 如何：使用具名管道進行網路處理序間通訊
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cc481c7370a21c56daf9ce2949247e65fa33bda
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836097"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>如何：使用具名管道進行網路處理序間通訊
具名管道可在管道伺服器及一個或多個管道用戶端之間提供處理序間通訊。 它們比在本機電腦上處理流程間通訊的匿名管道提供更多的功能。 具名管道支援在網路及多個伺服器執行個體上進行全雙工通訊、訊息架構通訊及用戶端模擬。用戶端模擬可讓連接處理序在遠端伺服器上使用本身的權限集合。  
  
 若要實作具名管道，請使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.IO.Pipes.NamedPipeServerStream> 類別建立具名管道。 在此範例中，伺服器處理序會建立四個執行緒。 每個執行緒都可以接受用戶端連線。 接著，連線的用戶端處理序會提供具有檔案名稱的伺服器。 如果用戶端有足夠的權限，伺服器處理序就會開啟檔案，並將其內容傳回用戶端。  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>範例  
 下列範例示範使用 <xref:System.IO.Pipes.NamedPipeClientStream> 類別的用戶端處理序。 用戶端會連線至伺服器處理序，並將檔案名稱傳送至伺服器。 此範例會使用模擬，因此，執行用戶端應用程式的身分識別必須擁有存取該檔案的權限。 接著，伺服器會將檔案的內容傳回用戶端。 檔案內容隨即顯示到主控台。  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 此範例中的用戶端和伺服器處理序要在相同的電腦上執行，因此，提供給 <xref:System.IO.Pipes.NamedPipeClientStream> 物件的伺服器名稱為 `"."`。 如果用戶端和伺服器處理序在不同的電腦上，`"."` 將會取代成執行伺服器處理序之電腦的網路名稱。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Principal.TokenImpersonationLevel>  
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
- [管道](../../../docs/standard/io/pipe-operations.md)  
- [操作說明：使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
