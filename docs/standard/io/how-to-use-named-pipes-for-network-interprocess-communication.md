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
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="85d16-102">如何：使用具名管道進行網路處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="85d16-102">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="85d16-103">具名的管道提供一個或多個管道用戶端之間的處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="85d16-103">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="85d16-104">它們比在本機電腦上處理流程間通訊的匿名管道提供更多的功能。</span><span class="sxs-lookup"><span data-stu-id="85d16-104">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="85d16-105">具名管道支援在網路及多個伺服器執行個體上進行全雙工通訊、訊息架構通訊及用戶端模擬。用戶端模擬可讓連接處理序在遠端伺服器上使用本身的權限集合。</span><span class="sxs-lookup"><span data-stu-id="85d16-105">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="85d16-106">若要實作具名管道，請使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 類別。</span><span class="sxs-lookup"><span data-stu-id="85d16-106">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85d16-107">範例</span><span class="sxs-lookup"><span data-stu-id="85d16-107">Example</span></span>  
 <span data-ttu-id="85d16-108">下列範例示範如何建立使用具名的管道<xref:System.IO.Pipes.NamedPipeServerStream>類別。</span><span class="sxs-lookup"><span data-stu-id="85d16-108">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="85d16-109">在此範例中，伺服器處理序會建立四個執行緒。</span><span class="sxs-lookup"><span data-stu-id="85d16-109">In this example, the server process creates four threads.</span></span> <span data-ttu-id="85d16-110">每個執行緒可接受用戶端連線。</span><span class="sxs-lookup"><span data-stu-id="85d16-110">Each thread can accept a client connection.</span></span> <span data-ttu-id="85d16-111">連線的用戶端處理序，然後提供具有檔案名稱的伺服器。</span><span class="sxs-lookup"><span data-stu-id="85d16-111">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="85d16-112">如果用戶端有足夠的權限，伺服器處理序開啟的檔案，並將其內容傳送回用戶端。</span><span class="sxs-lookup"><span data-stu-id="85d16-112">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="85d16-113">範例</span><span class="sxs-lookup"><span data-stu-id="85d16-113">Example</span></span>  
 <span data-ttu-id="85d16-114">下列範例示範用戶端處理序，會使用<xref:System.IO.Pipes.NamedPipeClientStream>類別。</span><span class="sxs-lookup"><span data-stu-id="85d16-114">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="85d16-115">用戶端連接至伺服器處理序，並且傳送至伺服器的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="85d16-115">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="85d16-116">此範例會使用模擬，以便執行用戶端應用程式的身分識別必須擁有存取該檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="85d16-116">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="85d16-117">伺服器接著會傳送回用戶端檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="85d16-117">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="85d16-118">檔案內容隨即顯示到主控台。</span><span class="sxs-lookup"><span data-stu-id="85d16-118">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="85d16-119">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="85d16-119">Robust Programming</span></span>  
 <span data-ttu-id="85d16-120">在此範例中的用戶端和伺服器處理程序要在相同的電腦上執行，因此伺服器名稱提供給<xref:System.IO.Pipes.NamedPipeClientStream>物件是`"."`。</span><span class="sxs-lookup"><span data-stu-id="85d16-120">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="85d16-121">如果不同的電腦上所執行的用戶端和伺服器處理`"."`會變成執行的伺服器處理序的電腦的網路名稱。</span><span class="sxs-lookup"><span data-stu-id="85d16-121">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d16-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85d16-122">See Also</span></span>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
 [<span data-ttu-id="85d16-123">管道</span><span class="sxs-lookup"><span data-stu-id="85d16-123">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="85d16-124">操作說明：使用匿名管道進行本機處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="85d16-124">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
