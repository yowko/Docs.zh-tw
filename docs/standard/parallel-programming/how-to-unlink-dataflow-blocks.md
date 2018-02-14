---
title: "如何：取消連結資料流程區塊"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db3c0d3a6d94e2e9eb65046267f14feff0c056cb
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="a1fbc-102">如何：取消連結資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="a1fbc-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="a1fbc-103">本文件將說明如何解除目標資料流程區塊與其來源之間的連結。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-103">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="a1fbc-104">範例</span><span class="sxs-lookup"><span data-stu-id="a1fbc-104">Example</span></span>  
 <span data-ttu-id="a1fbc-105">下列範例會建立三個 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件，每一個 `TrySolution` 方法都會計算一個值。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-105">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="a1fbc-106">這個範例只要求來自第一次呼叫 `TrySolution` 的結果必須完成。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-106">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="a1fbc-107">為了要從第一個完成的 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 接收值，這個範例會定義 `ReceiveFromAny(T)` 方法。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-107">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="a1fbc-108">`ReceiveFromAny(T)` 方法可接受 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 物件陣列，並且將這些物件連結至 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-108">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="a1fbc-109">當您使用 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法將來源資料流程區塊連結至目標區塊時，來源會在有可用資料時將訊息傳播至目標。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-109">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="a1fbc-110">由於 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 類別只接受提供給它的第一個訊息，因此 `ReceiveFromAny(T)` 方法會藉由呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> 方法產生其結果。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-110">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="a1fbc-111">這樣就會產生提供給 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件的第一個訊息。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-111">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="a1fbc-112"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法有一個會採用 <xref:System.Boolean> 參數 `unlinkAfterOne` 的多載版本，當它設為 `True` 時，就會指示來源區塊在目標收到來自來源的第一個訊息之後，中斷與目標的連結。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-112">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="a1fbc-113"><xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件一定要與其來源中斷連結，因為在 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件接收訊息之後，就不再需要來源陣列與 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-113">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="a1fbc-114">若要在其中一個對 `TrySolution` 的呼叫計算出值之後讓其餘呼叫結束，`TrySolution` 方法會採用 <xref:System.Threading.CancellationToken> 物件，該物件會在 `ReceiveFromAny(T)` 的呼叫傳回之後取消。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-114">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="a1fbc-115"><xref:System.Threading.SpinWait.SpinUntil%2A> 方法會在這個 <xref:System.Threading.CancellationToken> 物件取消時傳回。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-115">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a1fbc-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a1fbc-116">Compiling the Code</span></span>  
 <span data-ttu-id="a1fbc-117">請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `DataflowReceiveAny.cs` 的檔案中 (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中為 `DataflowReceiveAny.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="a1fbc-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="a1fbc-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="a1fbc-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="a1fbc-119">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="a1fbc-119">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="a1fbc-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1fbc-120">See Also</span></span>  
 [<span data-ttu-id="a1fbc-121">資料流程</span><span class="sxs-lookup"><span data-stu-id="a1fbc-121">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
