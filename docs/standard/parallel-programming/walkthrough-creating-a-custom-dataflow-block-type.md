---
title: 逐步解說：建立自訂資料流程區塊類型
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fdb6bde99ac5e15fb07010f3a73aba7c09bd4834
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a><span data-ttu-id="cbf06-102">逐步解說：建立自訂資料流程區塊類型</span><span class="sxs-lookup"><span data-stu-id="cbf06-102">Walkthrough: Creating a Custom Dataflow Block Type</span></span>
<span data-ttu-id="cbf06-103">雖然 TPL 資料流程式庫提供數個啟用各種不同功能的資料流程區塊類型，但您也可以建立自訂的區塊類型。</span><span class="sxs-lookup"><span data-stu-id="cbf06-103">Although the TPL Dataflow Library provides several dataflow block types that enable a variety of functionality, you can also create custom block types.</span></span> <span data-ttu-id="cbf06-104">本文件說明如何建立會實作自訂行為的資料流程區塊類型之兩種方式。</span><span class="sxs-lookup"><span data-stu-id="cbf06-104">This document describes how to create a dataflow block type that implements custom behavior.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cbf06-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="cbf06-105">Prerequisites</span></span>  
 <span data-ttu-id="cbf06-106">在您閱讀本文件之前，請閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)。</span><span class="sxs-lookup"><span data-stu-id="cbf06-106">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you read this document.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a><span data-ttu-id="cbf06-107">定義滑動視窗資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="cbf06-107">Defining the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="cbf06-108">請考慮要求緩衝處理輸入值，然後以滑動視窗的方式輸出的資料流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="cbf06-108">Consider a dataflow application that requires that input values be buffered and then output in a sliding window manner.</span></span> <span data-ttu-id="cbf06-109">例如，針對輸入值 {0, 1, 2, 3, 4, 5} 且視窗大小為三個，滑動視窗資料流程區塊會產生輸出陣列 {0, 1, 2}、{1, 2, 3}、{2, 3, 4} 和 {3, 4, 5}。</span><span class="sxs-lookup"><span data-stu-id="cbf06-109">For example, for the input values {0, 1, 2, 3, 4, 5} and a window size of three, a sliding window dataflow block produces the output arrays {0, 1, 2}, {1, 2, 3}, {2, 3, 4}, and {3, 4, 5}.</span></span> <span data-ttu-id="cbf06-110">下列各節將說明建立會實作自訂行為的資料流程區塊類型之兩種方式。</span><span class="sxs-lookup"><span data-stu-id="cbf06-110">The following sections describe two ways to create a dataflow block type that implements this custom behavior.</span></span> <span data-ttu-id="cbf06-111">第一種技術會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> 方法，將 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 物件和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 物件的功能結合為單一傳播程式區塊。</span><span class="sxs-lookup"><span data-stu-id="cbf06-111">The first technique uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to combine the functionality of an <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object and an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object into one propagator block.</span></span> <span data-ttu-id="cbf06-112">第二種技術會定義一個衍生自 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> 的類別，並結合現有的功能以執行自訂行為。</span><span class="sxs-lookup"><span data-stu-id="cbf06-112">The second technique defines a class that derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> and combines existing functionality to perform custom behavior.</span></span>  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="cbf06-113">使用封裝方法來定義滑動視窗資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="cbf06-113">Using the Encapsulate Method to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="cbf06-114">下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>方法，從目標與來源建立一個傳播程式區塊。</span><span class="sxs-lookup"><span data-stu-id="cbf06-114">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to create a propagator block from a target and a source.</span></span> <span data-ttu-id="cbf06-115">傳播程式區塊可讓來源區塊和目標區塊作為資料的接收者與傳送者。</span><span class="sxs-lookup"><span data-stu-id="cbf06-115">A propagator block enables a source block and a target block to act as a receiver and sender of data.</span></span>  
  
 <span data-ttu-id="cbf06-116">當您需要自訂的資料流程功能，但您不需要提供額外方法、屬性或欄位的類型時，這個技術非常有用。</span><span class="sxs-lookup"><span data-stu-id="cbf06-116">This technique is useful when you require custom dataflow functionality, but you do not require a type that provides additional methods, properties, or fields.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="cbf06-117">衍生自 IPropagatorBlock 以定義滑動視窗資料流程區塊</span><span class="sxs-lookup"><span data-stu-id="cbf06-117">Deriving from IPropagatorBlock to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="cbf06-118">下列範例顯示 `SlidingWindowBlock` 類別。</span><span class="sxs-lookup"><span data-stu-id="cbf06-118">The following example shows the `SlidingWindowBlock` class.</span></span> <span data-ttu-id="cbf06-119">此類別衍生自 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>，如此一來它就可以同時作為資料來源與目標。</span><span class="sxs-lookup"><span data-stu-id="cbf06-119">This class derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> so that it can act as both a source and a target of data.</span></span> <span data-ttu-id="cbf06-120">如同先前的範例，`SlidingWindowBlock` 類別建置於現有的資料流程區塊類型上。</span><span class="sxs-lookup"><span data-stu-id="cbf06-120">As in the previous example, the `SlidingWindowBlock` class is built on existing dataflow block types.</span></span> <span data-ttu-id="cbf06-121">不過，`SlidingWindowBlock` 類別也會實作 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> 介面所需的方法。</span><span class="sxs-lookup"><span data-stu-id="cbf06-121">However, the `SlidingWindowBlock` class also implements the methods that are required by the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, and <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces.</span></span> <span data-ttu-id="cbf06-122">這些方法全都會將工作轉寄給預先定義的資料流程區塊類型成員。</span><span class="sxs-lookup"><span data-stu-id="cbf06-122">These methods all forward work to the predefined dataflow block type members.</span></span> <span data-ttu-id="cbf06-123">例如，`Post` 方法會將工作延後到 `m_target` 資料成員，這也是一個 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="cbf06-123">For example, the `Post` method defers work to the `m_target` data member, which is also an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object.</span></span>  
  
 <span data-ttu-id="cbf06-124">當您需要自訂的資料流程功能，也需要提供額外方法、屬性或欄位的類型時，這個技術非常有用。</span><span class="sxs-lookup"><span data-stu-id="cbf06-124">This technique is useful when you require custom dataflow functionality, and also require a type that provides additional methods, properties, or fields.</span></span> <span data-ttu-id="cbf06-125">例如，`SlidingWindowBlock` 類別也衍生自 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>，如此一來它就可以提供 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 和 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="cbf06-125">For example, the `SlidingWindowBlock` class also derives from <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> so that it can provide the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> and <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> methods.</span></span> <span data-ttu-id="cbf06-126">`SlidingWindowBlock` 類別也會透過提供 `WindowSize` 屬性來示範擴充性，該屬性會擷取滑動視窗中的項目數目。</span><span class="sxs-lookup"><span data-stu-id="cbf06-126">The `SlidingWindowBlock` class also demonstrates extensibility by providing the `WindowSize` property, which retrieves the number of elements in the sliding window.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a><span data-ttu-id="cbf06-127">完整範例</span><span class="sxs-lookup"><span data-stu-id="cbf06-127">The Complete Example</span></span>  
 <span data-ttu-id="cbf06-128">下列範例將示範本逐步解說的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="cbf06-128">The following example shows the complete code for this walkthrough.</span></span> <span data-ttu-id="cbf06-129">它也會示範如何使用寫入區塊、從區塊讀取，並將結果列印至主控台之方法中的兩個滑動視窗區塊。</span><span class="sxs-lookup"><span data-stu-id="cbf06-129">It also demonstrates how to use the both sliding window blocks in a method that writes to the block, reads from it, and prints the results to the console.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cbf06-130">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="cbf06-130">Compiling the Code</span></span>  
 <span data-ttu-id="cbf06-131">請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `SlidingWindowBlock.cs` 的檔案中 (在 Visual Basic 中為 `SlidingWindowBlock.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="cbf06-131">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` for Visual Basic) and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="cbf06-132">Visual C#</span><span class="sxs-lookup"><span data-stu-id="cbf06-132">Visual C#</span></span>  
  
 <span data-ttu-id="cbf06-133">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span><span class="sxs-lookup"><span data-stu-id="cbf06-133">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span></span>  
  
 <span data-ttu-id="cbf06-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbf06-134">Visual Basic</span></span>  
  
 <span data-ttu-id="cbf06-135">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span><span class="sxs-lookup"><span data-stu-id="cbf06-135">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="cbf06-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf06-136">See Also</span></span>  
 [<span data-ttu-id="cbf06-137">資料流程</span><span class="sxs-lookup"><span data-stu-id="cbf06-137">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
