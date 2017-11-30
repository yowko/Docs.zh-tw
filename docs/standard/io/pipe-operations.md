---
title: ".NET Framework 中的管道作業"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 879e5a73417f9347224bc22b397814b83972751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="9f624-102">.NET Framework 中的管道作業</span><span class="sxs-lookup"><span data-stu-id="9f624-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="9f624-103">管道提供處理序間通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="9f624-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="9f624-104">有兩種類型的管道：</span><span class="sxs-lookup"><span data-stu-id="9f624-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="9f624-105">匿名管道。</span><span class="sxs-lookup"><span data-stu-id="9f624-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="9f624-106">匿名管道提供在本機電腦上的處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="9f624-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="9f624-107">匿名管道需要較少的額外負荷比具名管道，但提供有限的服務。</span><span class="sxs-lookup"><span data-stu-id="9f624-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="9f624-108">匿名管道是單向的不能在網路上。</span><span class="sxs-lookup"><span data-stu-id="9f624-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="9f624-109">它們僅支援單一伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f624-109">They support only a single server instance.</span></span> <span data-ttu-id="9f624-110">匿名管道可用於其中管道控制代碼可以輕鬆地傳遞給子處理序所建立的父和子處理序或執行緒之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="9f624-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="9f624-111">.NET Framework 中，在您實作使用匿名管道<xref:System.IO.Pipes.AnonymousPipeServerStream>和<xref:System.IO.Pipes.AnonymousPipeClientStream>類別。</span><span class="sxs-lookup"><span data-stu-id="9f624-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="9f624-112">請參閱[How to： 使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="9f624-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="9f624-113">具名的管道。</span><span class="sxs-lookup"><span data-stu-id="9f624-113">Named pipes.</span></span>  
  
     <span data-ttu-id="9f624-114">具名的管道提供一個或多個管道用戶端之間的處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="9f624-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="9f624-115">具名的管道可以是單向或雙工。</span><span class="sxs-lookup"><span data-stu-id="9f624-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="9f624-116">它們支援訊息為基礎的通訊，且允許多個用戶端可同時連接到使用相同的管道名稱的伺服器處理序。</span><span class="sxs-lookup"><span data-stu-id="9f624-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="9f624-117">具名的管道也支援模擬，讓連接處理序在遠端伺服器上使用他們自己的權限。</span><span class="sxs-lookup"><span data-stu-id="9f624-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="9f624-118">在.NET Framework 中，您必須實作具名的管道使用<xref:System.IO.Pipes.NamedPipeServerStream>和<xref:System.IO.Pipes.NamedPipeClientStream>類別。</span><span class="sxs-lookup"><span data-stu-id="9f624-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="9f624-119">請參閱[How to： 使用具名管道進行網路處理序間通訊](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="9f624-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f624-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f624-120">See Also</span></span>  
 [<span data-ttu-id="9f624-121">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="9f624-121">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="9f624-122">操作說明：使用匿名管道進行本機處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="9f624-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="9f624-123">操作說明：使用具名管道進行網路處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="9f624-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
