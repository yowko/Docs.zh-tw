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
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="90b0c-102">如何：使用匿名管道進行本機處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="90b0c-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="90b0c-103">匿名管道提供在本機電腦上的處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="90b0c-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="90b0c-104">它們提供的功能比具名管道少，但其負荷也比較小。</span><span class="sxs-lookup"><span data-stu-id="90b0c-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="90b0c-105">您可以在本機電腦上輕鬆處理序間通訊使用匿名管道。</span><span class="sxs-lookup"><span data-stu-id="90b0c-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="90b0c-106">您無法透過網路來使用匿名管道進行通訊。</span><span class="sxs-lookup"><span data-stu-id="90b0c-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="90b0c-107">若要實作匿名管道，請使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 類別。</span><span class="sxs-lookup"><span data-stu-id="90b0c-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90b0c-108">範例</span><span class="sxs-lookup"><span data-stu-id="90b0c-108">Example</span></span>  
 <span data-ttu-id="90b0c-109">下列範例會示範如何從父處理序的字串傳送至子處理序使用匿名管道。</span><span class="sxs-lookup"><span data-stu-id="90b0c-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="90b0c-110">這個範例會建立<xref:System.IO.Pipes.AnonymousPipeServerStream>父處理序中的物件<xref:System.IO.Pipes.PipeDirection>值<xref:System.IO.Pipes.PipeDirection.Out>。</span><span class="sxs-lookup"><span data-stu-id="90b0c-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="90b0c-111">父處理序然後建立子處理序使用的用戶端控制代碼來建立<xref:System.IO.Pipes.AnonymousPipeClientStream>物件。</span><span class="sxs-lookup"><span data-stu-id="90b0c-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="90b0c-112">子處理序具有<xref:System.IO.Pipes.PipeDirection>值<xref:System.IO.Pipes.PipeDirection.In>。</span><span class="sxs-lookup"><span data-stu-id="90b0c-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="90b0c-113">父處理序便會傳送給子處理序的使用者提供的字串。</span><span class="sxs-lookup"><span data-stu-id="90b0c-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="90b0c-114">此字串會顯示子處理序中的主控台。</span><span class="sxs-lookup"><span data-stu-id="90b0c-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="90b0c-115">下列範例會顯示伺服器處理序。</span><span class="sxs-lookup"><span data-stu-id="90b0c-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="90b0c-116">範例</span><span class="sxs-lookup"><span data-stu-id="90b0c-116">Example</span></span>  
 <span data-ttu-id="90b0c-117">下列範例會示範用戶端處理序。</span><span class="sxs-lookup"><span data-stu-id="90b0c-117">The following example shows the client process.</span></span> <span data-ttu-id="90b0c-118">伺服器處理序會啟動用戶端處理序，並提供該程序的用戶端控制代碼。</span><span class="sxs-lookup"><span data-stu-id="90b0c-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="90b0c-119">用戶端程式碼產生可執行檔應該命名為`pipeClient.exe`而會複製到伺服器之前執行的伺服器處理序可執行檔相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="90b0c-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="90b0c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90b0c-120">See Also</span></span>  
 [<span data-ttu-id="90b0c-121">管道</span><span class="sxs-lookup"><span data-stu-id="90b0c-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="90b0c-122">操作說明：使用具名管道進行網路處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="90b0c-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
