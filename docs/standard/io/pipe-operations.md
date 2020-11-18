---
title: .NET 中的管道作業
description: 瞭解如何在 .NET 中進行管線作業。 管道會提供一種處理序間通訊的方法。 管道有兩種：匿名管道和具名管道。
ms.date: 03/30/2017
helpviewer_keywords:
- pipes [.NET]
- pipe operations [.NET]
- interprocess communication [.NET], pipes
- I/O [.NET], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 3ec4ee61bfd3a0a82eb0a0884b89c19a9300b078
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819093"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="cece1-105">.NET 中的管道作業</span><span class="sxs-lookup"><span data-stu-id="cece1-105">Pipe Operations in .NET</span></span>
<span data-ttu-id="cece1-106">管道會提供一種處理序間通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="cece1-106">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="cece1-107">管道有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="cece1-107">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="cece1-108">匿名管道。</span><span class="sxs-lookup"><span data-stu-id="cece1-108">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="cece1-109">匿名管道會在本機電腦上提供處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="cece1-109">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="cece1-110">相較於具名管道，匿名管道需要的額外負荷更少，但提供的服務有限。</span><span class="sxs-lookup"><span data-stu-id="cece1-110">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="cece1-111">匿名管道是單向的，而且無法透過網路使用。</span><span class="sxs-lookup"><span data-stu-id="cece1-111">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="cece1-112">它們僅支援單一伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="cece1-112">They support only a single server instance.</span></span> <span data-ttu-id="cece1-113">匿名管道可用於執行緒之間的通訊，或父處理序和子處理序之間的通訊，其中管道控制代碼可以在建立通訊時，輕鬆地傳遞給子處理序。</span><span class="sxs-lookup"><span data-stu-id="cece1-113">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="cece1-114">在 .NET 中，您可以使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 類別實作匿名管道。</span><span class="sxs-lookup"><span data-stu-id="cece1-114">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="cece1-115">請參閱[操作說明：使用匿名管道進行本機處理序間通訊](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="cece1-115">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="cece1-116">具名管道。</span><span class="sxs-lookup"><span data-stu-id="cece1-116">Named pipes.</span></span>  
  
     <span data-ttu-id="cece1-117">具名管道可在管道伺服器及一個或多個管道用戶端之間提供處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="cece1-117">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="cece1-118">具名管道可以是單向或雙向的。</span><span class="sxs-lookup"><span data-stu-id="cece1-118">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="cece1-119">它們支援訊息式通訊，且允許多個用戶端使用相同的管道名稱，同時連線到伺服器處理序。</span><span class="sxs-lookup"><span data-stu-id="cece1-119">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="cece1-120">具名管道也支援模擬，讓連線處理序在遠端伺服器上使用自己的權限。</span><span class="sxs-lookup"><span data-stu-id="cece1-120">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="cece1-121">在 .NET 中，您可以使用 <xref:System.IO.Pipes.NamedPipeServerStream> 和 <xref:System.IO.Pipes.NamedPipeClientStream> 類別實作匿名管道。</span><span class="sxs-lookup"><span data-stu-id="cece1-121">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="cece1-122">請參閱[操作說明：使用具名管道進行網路處理序間通訊](how-to-use-named-pipes-for-network-interprocess-communication.md)。</span><span class="sxs-lookup"><span data-stu-id="cece1-122">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cece1-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="cece1-123">See also</span></span>

- [<span data-ttu-id="cece1-124">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="cece1-124">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="cece1-125">作法：使用匿名管道進行本機處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="cece1-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="cece1-126">作法：使用具名管道進行網路處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="cece1-126">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
