---
title: 如何：使用匿名管道進行本機處理序間通訊
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: ea4aee60d090a56eb0cf3f2a81c1b05c04806d4b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627990"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="e92c6-102">如何：使用匿名管道進行本機處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="e92c6-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="e92c6-103">匿名管道會在本機電腦上提供處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="e92c6-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="e92c6-104">它們提供的功能比具名管道少，但其負荷也比較小。</span><span class="sxs-lookup"><span data-stu-id="e92c6-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="e92c6-105">您可以使用匿名管道，讓本機電腦上的處理序間通訊更容易。</span><span class="sxs-lookup"><span data-stu-id="e92c6-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="e92c6-106">您無法透過網路，使用匿名管道進行通訊。</span><span class="sxs-lookup"><span data-stu-id="e92c6-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="e92c6-107">若要實作匿名管道，請使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 和 <xref:System.IO.Pipes.AnonymousPipeClientStream> 類別。</span><span class="sxs-lookup"><span data-stu-id="e92c6-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e92c6-108">範例</span><span class="sxs-lookup"><span data-stu-id="e92c6-108">Example</span></span>  
 <span data-ttu-id="e92c6-109">下列範例會示範如何使用匿名管道，將字串從父處理序傳送至子處理序。</span><span class="sxs-lookup"><span data-stu-id="e92c6-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="e92c6-110">此範例會在父處理序中，使用 <xref:System.IO.Pipes.AnonymousPipeServerStream> 的 <xref:System.IO.Pipes.PipeDirection> 值建立 <xref:System.IO.Pipes.PipeDirection.Out> 物件。</span><span class="sxs-lookup"><span data-stu-id="e92c6-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="e92c6-111">接著，父處理序會使用建立 <xref:System.IO.Pipes.AnonymousPipeClientStream> 物件的用戶端控制代碼來建立子處理序。</span><span class="sxs-lookup"><span data-stu-id="e92c6-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="e92c6-112">子處理序具有 <xref:System.IO.Pipes.PipeDirection> 的 <xref:System.IO.Pipes.PipeDirection.In> 值。</span><span class="sxs-lookup"><span data-stu-id="e92c6-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="e92c6-113">接著，父處理序會將使用者提供的字串傳送給子處理序。</span><span class="sxs-lookup"><span data-stu-id="e92c6-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="e92c6-114">此字串會顯示到子處理序中的主控台。</span><span class="sxs-lookup"><span data-stu-id="e92c6-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="e92c6-115">下列範例示範伺服器處理序。</span><span class="sxs-lookup"><span data-stu-id="e92c6-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="e92c6-116">範例</span><span class="sxs-lookup"><span data-stu-id="e92c6-116">Example</span></span>  
 <span data-ttu-id="e92c6-117">下列範例示範用戶端處理序。</span><span class="sxs-lookup"><span data-stu-id="e92c6-117">The following example shows the client process.</span></span> <span data-ttu-id="e92c6-118">伺服器處理序會啟動用戶端處理序，並為該處理序提供一個用戶端控制代碼。</span><span class="sxs-lookup"><span data-stu-id="e92c6-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="e92c6-119">從用戶端程式碼產生的可執行檔應該命名為 `pipeClient.exe`，並在執行伺服器處理序之前，複製到與伺服器可執行檔相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="e92c6-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="e92c6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e92c6-120">See also</span></span>

- [<span data-ttu-id="e92c6-121">管道</span><span class="sxs-lookup"><span data-stu-id="e92c6-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="e92c6-122">操作說明：使用具名管道進行網路處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="e92c6-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
