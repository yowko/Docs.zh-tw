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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68c1ad34952ee4d20dbf56aa8ca437a3f99db751
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="63bfb-102">.NET Framework 中的管道作業</span><span class="sxs-lookup"><span data-stu-id="63bfb-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="63bfb-103">管道會提供一種處理序間通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="63bfb-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="63bfb-104">管道有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="63bfb-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="63bfb-105">匿名管道。</span><span class="sxs-lookup"><span data-stu-id="63bfb-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="63bfb-106">匿名管道會在本機電腦上提供處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="63bfb-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="63bfb-107">相較於具名管道，匿名管道需要的額外負荷更少，但提供的服務有限。</span><span class="sxs-lookup"><span data-stu-id="63bfb-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="63bfb-108">匿名管道是單向的，而且無法透過網路使用。</span><span class="sxs-lookup"><span data-stu-id="63bfb-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="63bfb-109">它們僅支援單一伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="63bfb-109">They support only a single server instance.</span></span> <span data-ttu-id="63bfb-110">匿名管道可用於執行緒之間的通訊，或父處理序和子處理序之間的通訊，其中管道控制代碼可以在建立通訊時，輕鬆地傳遞給子處理序。</span><span class="sxs-lookup"><span data-stu-id="63bfb-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="63bfb-111">在 .NET Framework 中，您可以使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 類別實作匿名管道。</span><span class="sxs-lookup"><span data-stu-id="63bfb-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="63bfb-112">請參閱[操作說明：使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="63bfb-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="63bfb-113">具名管道。</span><span class="sxs-lookup"><span data-stu-id="63bfb-113">Named pipes.</span></span>  
  
     <span data-ttu-id="63bfb-114">具名管道可在管道伺服器及一個或多個管道用戶端之間提供處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="63bfb-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="63bfb-115">具名管道可以是單向或雙向的。</span><span class="sxs-lookup"><span data-stu-id="63bfb-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="63bfb-116">它們支援訊息式通訊，且允許多個用戶端使用相同的管道名稱，同時連線到伺服器處理序。</span><span class="sxs-lookup"><span data-stu-id="63bfb-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="63bfb-117">具名管道也支援模擬，讓連線處理序在遠端伺服器上使用自己的權限。</span><span class="sxs-lookup"><span data-stu-id="63bfb-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="63bfb-118">在 .NET Framework 中，您可以使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 類別實作具名管道。</span><span class="sxs-lookup"><span data-stu-id="63bfb-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="63bfb-119">請參閱[操作說明：使用具名管道進行網路處理序間通訊](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="63bfb-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bfb-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="63bfb-120">See Also</span></span>  
 [<span data-ttu-id="63bfb-121">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="63bfb-121">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="63bfb-122">操作說明：使用匿名管道進行本機處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="63bfb-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="63bfb-123">操作說明：使用具名管道進行網路處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="63bfb-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
