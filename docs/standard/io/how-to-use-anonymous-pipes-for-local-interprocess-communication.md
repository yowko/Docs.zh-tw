---
title: 作法：使用匿名管道進行本機處理序間通訊
description: 瞭解如何在 .NET 中的本機電腦上，使用匿名管道進行本機進程間的通訊。 匿名管道需要的額外負荷比具名管道少。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET]
- parent-child communication [.NET]
- pipes [.NET]
- one-way communication [.NET]
- local computer communication [.NET], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: c9d223d975dc7ab251717a66de0bc845845dc9d7
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189351"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="ed02b-104">作法：使用匿名管道進行本機處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="ed02b-104">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>

<span data-ttu-id="ed02b-105">匿名管道會在本機電腦上提供處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="ed02b-105">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="ed02b-106">它們提供的功能比具名管道少，但其負荷也比較小。</span><span class="sxs-lookup"><span data-stu-id="ed02b-106">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="ed02b-107">您可以使用匿名管道，讓本機電腦上的處理序間通訊更容易。</span><span class="sxs-lookup"><span data-stu-id="ed02b-107">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="ed02b-108">您無法透過網路，使用匿名管道進行通訊。</span><span class="sxs-lookup"><span data-stu-id="ed02b-108">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="ed02b-109">若要實作匿名管道，請使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 類別。</span><span class="sxs-lookup"><span data-stu-id="ed02b-109">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed02b-110">範例</span><span class="sxs-lookup"><span data-stu-id="ed02b-110">Example</span></span>  
 <span data-ttu-id="ed02b-111">下列範例會示範如何使用匿名管道，將字串從父處理序傳送至子處理序。</span><span class="sxs-lookup"><span data-stu-id="ed02b-111">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="ed02b-112">此範例會在父處理序中，使用 <xref:System.IO.Pipes.PipeDirection.Out> 的 <xref:System.IO.Pipes.PipeDirection> 值建立 <xref:System.IO.Pipes.AnonymousPipeServerStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="ed02b-112">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="ed02b-113">接著，父處理序會使用建立 <xref:System.IO.Pipes.AnonymousPipeClientStream> 物件的用戶端控制代碼來建立子處理序。</span><span class="sxs-lookup"><span data-stu-id="ed02b-113">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="ed02b-114">子處理序具有 <xref:System.IO.Pipes.PipeDirection.In> 的 <xref:System.IO.Pipes.PipeDirection> 值。</span><span class="sxs-lookup"><span data-stu-id="ed02b-114">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="ed02b-115">接著，父處理序會將使用者提供的字串傳送給子處理序。</span><span class="sxs-lookup"><span data-stu-id="ed02b-115">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="ed02b-116">此字串會顯示到子處理序中的主控台。</span><span class="sxs-lookup"><span data-stu-id="ed02b-116">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="ed02b-117">下列範例示範伺服器處理序。</span><span class="sxs-lookup"><span data-stu-id="ed02b-117">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="ed02b-118">範例</span><span class="sxs-lookup"><span data-stu-id="ed02b-118">Example</span></span>  
 <span data-ttu-id="ed02b-119">下列範例示範用戶端處理序。</span><span class="sxs-lookup"><span data-stu-id="ed02b-119">The following example shows the client process.</span></span> <span data-ttu-id="ed02b-120">伺服器處理序會啟動用戶端處理序，並為該處理序提供一個用戶端控制代碼。</span><span class="sxs-lookup"><span data-stu-id="ed02b-120">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="ed02b-121">從用戶端程式碼產生的可執行檔應該命名為 `pipeClient.exe`，並在執行伺服器處理序之前，複製到與伺服器可執行檔相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="ed02b-121">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="ed02b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed02b-122">See also</span></span>

- [<span data-ttu-id="ed02b-123">管道</span><span class="sxs-lookup"><span data-stu-id="ed02b-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="ed02b-124">作法：使用具名管道進行網路處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="ed02b-124">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
