---
title: "如何：使用 JoinBlock 從多個來源讀取資料"
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
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41445e4874b94809840ecf9ebda6f27ccc955c9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a><span data-ttu-id="d0f95-102">如何：使用 JoinBlock 從多個來源讀取資料</span><span class="sxs-lookup"><span data-stu-id="d0f95-102">How to: Use JoinBlock to Read Data From Multiple Sources</span></span>
<span data-ttu-id="d0f95-103">本文件將說明，如何在有多個來源的資料可用時，使用 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 類別執行作業。</span><span class="sxs-lookup"><span data-stu-id="d0f95-103">This document explains how to use the <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> class to perform an operation when data is available from multiple sources.</span></span> <span data-ttu-id="d0f95-104">另外也會示範如何使用非窮盡模式，讓多個聯結區塊更有效率地共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="d0f95-104">It also demonstrates how to use non-greedy mode to enable multiple join blocks to share a data source more efficiently.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="d0f95-105">TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0f95-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="d0f95-106">若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。</span><span class="sxs-lookup"><span data-stu-id="d0f95-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0f95-107">範例</span><span class="sxs-lookup"><span data-stu-id="d0f95-107">Example</span></span>  
 <span data-ttu-id="d0f95-108">下列範例會定義三個資源類型 `NetworkResource`、`FileResource` 和 `MemoryResource`，並且在有可用資源時執行作業。</span><span class="sxs-lookup"><span data-stu-id="d0f95-108">The following example defines three resource types, `NetworkResource`, `FileResource`, and `MemoryResource`, and performs operations when resources become available.</span></span> <span data-ttu-id="d0f95-109">這個範例需要 `NetworkResource` 和 `MemoryResource` 配對，以便執行第一個作業，而且需要 `FileResource` 和 `MemoryResource` 配對，以便執行第二個作業。</span><span class="sxs-lookup"><span data-stu-id="d0f95-109">This example requires a `NetworkResource` and `MemoryResource` pair in order to perform the first operation and a `FileResource` and `MemoryResource` pair in order to perform the second operation.</span></span> <span data-ttu-id="d0f95-110">為了要讓這些作業在所有必要的資源可供使用時發生，這個範例會使用 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 類別。</span><span class="sxs-lookup"><span data-stu-id="d0f95-110">To enable these operations to occur when all required resources are available, this example uses the <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> class.</span></span> <span data-ttu-id="d0f95-111">當 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件接收來自所有來源的資料時，它會將該資料傳播至其目標，也就是這個範例中的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="d0f95-111">When a <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> object receives data from all sources, it propagates that data to its target, which in this example is an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="d0f95-112">這兩個 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件都會從 `MemoryResource` 物件的共用集區讀取。</span><span class="sxs-lookup"><span data-stu-id="d0f95-112">Both <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objects read from a shared pool of `MemoryResource` objects.</span></span>  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 <span data-ttu-id="d0f95-113">為了要讓 `MemoryResource` 物件共用集區的使用更有效率，這個範例會指定 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> 物件並將其 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> 屬性設定為 `False`，建立以非窮盡模式執行的 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件。</span><span class="sxs-lookup"><span data-stu-id="d0f95-113">To enable efficient use of the shared pool of `MemoryResource` objects, this example specifies a <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> property set to `False` to create <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objects that act in non-greedy mode.</span></span> <span data-ttu-id="d0f95-114">非窮盡聯結區塊會延後所有傳入訊息，直到每個來源都有一個為止。</span><span class="sxs-lookup"><span data-stu-id="d0f95-114">A non-greedy join block postpones all incoming messages until one is available from each source.</span></span> <span data-ttu-id="d0f95-115">如果有任一個延後的訊息被另一個區塊所接受，聯結區塊就會重新啟動處理序。</span><span class="sxs-lookup"><span data-stu-id="d0f95-115">If any of the postponed messages were accepted by another block, the join block restarts the process.</span></span> <span data-ttu-id="d0f95-116">非窮盡模式會在其他區塊等待資料的同時，讓共用一個或多個來源區塊的聯結區塊往前進行。</span><span class="sxs-lookup"><span data-stu-id="d0f95-116">Non-greedy mode enables join blocks that share one or more source blocks to make forward progress as the other blocks wait for data.</span></span> <span data-ttu-id="d0f95-117">在這個範例中，如果 `MemoryResource` 物件已加入至 `memoryResources` 集區，則要接收其第二個資料來源的第一個聯結區塊就能繼續往前進行。</span><span class="sxs-lookup"><span data-stu-id="d0f95-117">In this example, if a `MemoryResource` object is added to the `memoryResources` pool, the first join block to receive its second data source can make forward progress.</span></span> <span data-ttu-id="d0f95-118">如果這個範例是使用窮盡模式，也就是預設值，則聯結區塊可能會採用 `MemoryResource` 物件並等待可供使用的第二個資源。</span><span class="sxs-lookup"><span data-stu-id="d0f95-118">If this example were to use greedy mode, which is the default, one join block might take the `MemoryResource` object and wait for the second resource to become available.</span></span> <span data-ttu-id="d0f95-119">不過，如果其他聯結區塊都有自己的第二個資料來源可用，就無法繼續往前進行，因為 `MemoryResource` 物件已由另一個聯結區塊佔用。</span><span class="sxs-lookup"><span data-stu-id="d0f95-119">However, if the other join block has its second data source available, it cannot make forward progress because the `MemoryResource` object has been taken by the other join block.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0f95-120">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d0f95-120">Compiling the Code</span></span>  
 <span data-ttu-id="d0f95-121">請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `DataflowNonGreedyJoin.cs` 的檔案中 (在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]中為 `DataflowNonGreedyJoin.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="d0f95-121">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowNonGreedyJoin.cs` (`DataflowNonGreedyJoin.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="d0f95-122">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**</span><span class="sxs-lookup"><span data-stu-id="d0f95-122">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="d0f95-123">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**</span><span class="sxs-lookup"><span data-stu-id="d0f95-123">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d0f95-124">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d0f95-124">Robust Programming</span></span>  
 <span data-ttu-id="d0f95-125">使用非窮盡聯結還可以協助您防止應用程式中發生死結。</span><span class="sxs-lookup"><span data-stu-id="d0f95-125">The use of non-greedy joins can also help you prevent deadlock in your application.</span></span> <span data-ttu-id="d0f95-126">在軟體應用程式中，*死結*兩個或多個處理序每個保留的資源，且會互相等候另一個處理序釋放其他一些資源時發生。</span><span class="sxs-lookup"><span data-stu-id="d0f95-126">In a software application, *deadlock* occurs when two or more processes each hold a resource and mutually wait for another process to release some other resource.</span></span> <span data-ttu-id="d0f95-127">假設有一個應用程式定義了兩個 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件。</span><span class="sxs-lookup"><span data-stu-id="d0f95-127">Consider an application that defines two <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objects.</span></span> <span data-ttu-id="d0f95-128">這兩個物件都會從兩個共用來源區塊讀取資料。</span><span class="sxs-lookup"><span data-stu-id="d0f95-128">Both objects each read data from two shared source blocks.</span></span> <span data-ttu-id="d0f95-129">在窮盡模式下，如果其中一個聯結區塊是從第一個來源讀取，而第二個聯結區塊是從第二個來源讀取，則應用程式可能會發生死結，因為這兩個聯結區塊會互相等候彼此釋放其資源。</span><span class="sxs-lookup"><span data-stu-id="d0f95-129">In greedy mode, if one join block reads from the first source and the second join block reads from the second source, the application might deadlock because both join blocks mutually wait for the other to release its resource.</span></span> <span data-ttu-id="d0f95-130">在非窮盡模式下，每個聯結區塊只會在所有資料都可用時才從其來源讀取，因此可排除死結的情況發生。</span><span class="sxs-lookup"><span data-stu-id="d0f95-130">In non-greedy mode, each join block reads from its sources only when all data is available, and therefore, the risk of deadlock is eliminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f95-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0f95-131">See Also</span></span>  
 [<span data-ttu-id="d0f95-132">資料流程</span><span class="sxs-lookup"><span data-stu-id="d0f95-132">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
