---
title: "逐步解說：建立自訂資料流程區塊類型"
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
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 809b21fa6e1470890011604792d849998dd03ede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a><span data-ttu-id="76d98-102">逐步解說：建立自訂資料流程區塊類型</span><span class="sxs-lookup"><span data-stu-id="76d98-102">Walkthrough: Creating a Custom Dataflow Block Type</span></span>
<span data-ttu-id="76d98-103">雖然 TPL 資料流程式庫提供數個資料流程區塊類型，可讓各種不同的功能，但是您也可以建立自訂的區塊類型。</span><span class="sxs-lookup"><span data-stu-id="76d98-103">Although the TPL Dataflow Library provides several dataflow block types that enable a variety of functionality, you can also create custom block types.</span></span> <span data-ttu-id="76d98-104">本文件說明如何建立會實作自訂行為的資料流程區塊類型。</span><span class="sxs-lookup"><span data-stu-id="76d98-104">This document describes how to create a dataflow block type that implements custom behavior.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="76d98-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="76d98-105">Prerequisites</span></span>  
 <span data-ttu-id="76d98-106">讀取[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)閱讀這份文件之前。</span><span class="sxs-lookup"><span data-stu-id="76d98-106">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you read this document.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="76d98-107">TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="76d98-107">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="76d98-108">若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。</span><span class="sxs-lookup"><span data-stu-id="76d98-108">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="defining-the-sliding-window-dataflow-block"></a><span data-ttu-id="76d98-109">定義滑動視窗資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="76d98-109">Defining the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="76d98-110">請考慮要求輸入的值必須緩衝處理，並接著在滑動視窗的方式輸出的資料流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="76d98-110">Consider a dataflow application that requires that input values be buffered and then output in a sliding window manner.</span></span> <span data-ttu-id="76d98-111">例如，{0、 1、 2、 3、 4，5} 的輸入的值和視窗大小為三個，滑動視窗資料流程區塊會產生輸出陣列 {0，1，2}，{1，2，3}，{2，3，4} 和 {3，4，5}。</span><span class="sxs-lookup"><span data-stu-id="76d98-111">For example, for the input values {0, 1, 2, 3, 4, 5} and a window size of three, a sliding window dataflow block produces the output arrays {0, 1, 2}, {1, 2, 3}, {2, 3, 4}, and {3, 4, 5}.</span></span> <span data-ttu-id="76d98-112">下列各節說明兩種方式可建立會實作這個自訂行為的資料流程區塊類型。</span><span class="sxs-lookup"><span data-stu-id="76d98-112">The following sections describe two ways to create a dataflow block type that implements this custom behavior.</span></span> <span data-ttu-id="76d98-113">第一種技術會使用<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>方法來結合的功能<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>物件和<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>成一個傳播程式區塊的物件。</span><span class="sxs-lookup"><span data-stu-id="76d98-113">The first technique uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to combine the functionality of an <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object and an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object into one propagator block.</span></span> <span data-ttu-id="76d98-114">第二項技術會定義一個類別，衍生自<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>和結合現有的功能來執行自訂行為。</span><span class="sxs-lookup"><span data-stu-id="76d98-114">The second technique defines a class that derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> and combines existing functionality to perform custom behavior.</span></span>  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="76d98-115">使用封裝來定義滑動視窗資料流程區塊的方法</span><span class="sxs-lookup"><span data-stu-id="76d98-115">Using the Encapsulate Method to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="76d98-116">下列範例會使用<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>方法來建立從目標及資料來源的傳播程式區塊。</span><span class="sxs-lookup"><span data-stu-id="76d98-116">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to create a propagator block from a target and a source.</span></span> <span data-ttu-id="76d98-117">傳播程式區塊可讓來源區塊和目標區塊做為收件者和寄件者的資料。</span><span class="sxs-lookup"><span data-stu-id="76d98-117">A propagator block enables a source block and a target block to act as a receiver and sender of data.</span></span>  
  
 <span data-ttu-id="76d98-118">當您需要自訂的資料流程功能，但您不需要提供額外的方法、 屬性或欄位的類型時，這個技術非常有用。</span><span class="sxs-lookup"><span data-stu-id="76d98-118">This technique is useful when you require custom dataflow functionality, but you do not require a type that provides additional methods, properties, or fields.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="76d98-119">衍生自 IPropagatorBlock 定義滑動視窗資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="76d98-119">Deriving from IPropagatorBlock to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="76d98-120">下列範例所示`SlidingWindowBlock`類別。</span><span class="sxs-lookup"><span data-stu-id="76d98-120">The following example shows the `SlidingWindowBlock` class.</span></span> <span data-ttu-id="76d98-121">此類別衍生自<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>，讓它可以做為來源和目標的資料。</span><span class="sxs-lookup"><span data-stu-id="76d98-121">This class derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> so that it can act as both a source and a target of data.</span></span> <span data-ttu-id="76d98-122">如同先前的範例，`SlidingWindowBlock`類別建置在現有的資料流程區塊類型。</span><span class="sxs-lookup"><span data-stu-id="76d98-122">As in the previous example, the `SlidingWindowBlock` class is built on existing dataflow block types.</span></span> <span data-ttu-id="76d98-123">不過，`SlidingWindowBlock`類別也會實作所需的方法<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>， <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>，和<xref:System.Threading.Tasks.Dataflow.IDataflowBlock>介面。</span><span class="sxs-lookup"><span data-stu-id="76d98-123">However, the `SlidingWindowBlock` class also implements the methods that are required by the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, and <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces.</span></span> <span data-ttu-id="76d98-124">向前復原所有這些方法將工作加入預先定義的資料流程區塊類型成員。</span><span class="sxs-lookup"><span data-stu-id="76d98-124">These methods all forward work to the predefined dataflow block type members.</span></span> <span data-ttu-id="76d98-125">例如，`Post`方法會延後到工作`m_target`資料成員，這也是<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>物件。</span><span class="sxs-lookup"><span data-stu-id="76d98-125">For example, the `Post` method defers work to the `m_target` data member, which is also an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object.</span></span>  
  
 <span data-ttu-id="76d98-126">當您需要自訂的資料流程功能，然後也需要提供額外的方法、 屬性或欄位的類型時，這個技術非常有用。</span><span class="sxs-lookup"><span data-stu-id="76d98-126">This technique is useful when you require custom dataflow functionality, and also require a type that provides additional methods, properties, or fields.</span></span> <span data-ttu-id="76d98-127">例如，`SlidingWindowBlock`類別也衍生自<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>，讓它能夠提供<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>和<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="76d98-127">For example, the `SlidingWindowBlock` class also derives from <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> so that it can provide the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> and <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> methods.</span></span> <span data-ttu-id="76d98-128">`SlidingWindowBlock`類別也會示範擴充性提供`WindowSize`屬性，擷取滑動視窗中的項目數目。</span><span class="sxs-lookup"><span data-stu-id="76d98-128">The `SlidingWindowBlock` class also demonstrates extensibility by providing the `WindowSize` property, which retrieves the number of elements in the sliding window.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a><span data-ttu-id="76d98-129">完整範例</span><span class="sxs-lookup"><span data-stu-id="76d98-129">The Complete Example</span></span>  
 <span data-ttu-id="76d98-130">下列範例將示範本逐步解說的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="76d98-130">The following example shows the complete code for this walkthrough.</span></span> <span data-ttu-id="76d98-131">它也會示範如何使用這兩個滑動視窗區塊中的方法，將區塊寫入、 讀取它，會列印到主控台的結果。</span><span class="sxs-lookup"><span data-stu-id="76d98-131">It also demonstrates how to use the both sliding window blocks in a method that writes to the block, reads from it, and prints the results to the console.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76d98-132">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="76d98-132">Compiling the Code</span></span>  
 <span data-ttu-id="76d98-133">範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`SlidingWindowBlock.cs`(`SlidingWindowBlock.vb`如[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])，然後在 Visual Studio 命令提示字元視窗中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="76d98-133">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="76d98-134">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span><span class="sxs-lookup"><span data-stu-id="76d98-134">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="76d98-135">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span><span class="sxs-lookup"><span data-stu-id="76d98-135">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="76d98-136">後續步驟</span><span class="sxs-lookup"><span data-stu-id="76d98-136">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d98-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76d98-137">See Also</span></span>  
 [<span data-ttu-id="76d98-138">資料流程</span><span class="sxs-lookup"><span data-stu-id="76d98-138">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
