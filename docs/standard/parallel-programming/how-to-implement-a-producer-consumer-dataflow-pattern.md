---
title: 如何：實作生產者-消費者資料流程模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f15374fd7fd131256cdeb89dcb16ba13827c232
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298379"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="63545-102">如何：實作生產者-消費者資料流程模式</span><span class="sxs-lookup"><span data-stu-id="63545-102">How to: Implement a Producer-Consumer Dataflow Pattern</span></span>
<span data-ttu-id="63545-103">本文件將說明如何使用 TPL 資料流程程式庫實作生產者-消費者模式。</span><span class="sxs-lookup"><span data-stu-id="63545-103">This document describes how to use the TPL Dataflow Library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="63545-104">在此模式中，「生產者」會將訊息傳送至訊息區塊，而「消費者」會從該區塊讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="63545-104">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a><span data-ttu-id="63545-105">範例</span><span class="sxs-lookup"><span data-stu-id="63545-105">Example</span></span>  
 <span data-ttu-id="63545-106">下列範例將示範使用資料流程的基本生產者-消費者模型。</span><span class="sxs-lookup"><span data-stu-id="63545-106">The following example demonstrates a basic producer- consumer model that uses dataflow.</span></span> <span data-ttu-id="63545-107">`Produce` 方法會將包含隨機位元組資料的陣列寫入 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> 物件中，而 `Consume` 方法會從 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> 物件中讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="63545-107">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="63545-108">藉由處理 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 介面而不是其衍生類型，您就可以撰寫可重複使用的程式碼來處理各種資料流程區塊類型。</span><span class="sxs-lookup"><span data-stu-id="63545-108">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="63545-109">這個範例會使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別。</span><span class="sxs-lookup"><span data-stu-id="63545-109">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="63545-110">由於 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別會同時做為來源區塊和目標區塊，因此生產者和消費者可以使用共用物件來傳輸資料。</span><span class="sxs-lookup"><span data-stu-id="63545-110">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>  
  
 <span data-ttu-id="63545-111">`Produce` 方法會在迴圈中呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法，將資料同步寫入目標區塊中。</span><span class="sxs-lookup"><span data-stu-id="63545-111">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="63545-112">`Produce` 方法將所有資料寫入目標區塊之後會呼叫 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> 方法，指出區塊將不會再提供任何額外的資料。</span><span class="sxs-lookup"><span data-stu-id="63545-112">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="63545-113">`Consume` 方法會使用 [async](~/docs/csharp/language-reference/keywords/async.md) 和 [await](~/docs/csharp/language-reference/keywords/await.md) 運算子 (在 Visual Basic 中為 [Async](~/docs/visual-basic/language-reference/modifiers/async.md) 和 [Await](~/docs/visual-basic/language-reference/operators/await-operator.md)) 以非同步方式計算從 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 物件接收的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="63545-113">The `Consume` method uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="63545-114">若要以非同步方式執行，`Consume` 方法會呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> 方法在來源區塊有可用資料，以及來源區塊永遠不再提供其他可用資料時收到通知。</span><span class="sxs-lookup"><span data-stu-id="63545-114">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63545-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="63545-115">Compiling the Code</span></span>  
 <span data-ttu-id="63545-116">請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `DataflowProducerConsumer.cs` 的檔案中 (在 Visual Basic 中為 `DataflowProducerConsumer.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="63545-116">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="63545-117">Visual C#</span><span class="sxs-lookup"><span data-stu-id="63545-117">Visual C#</span></span>  
  
 <span data-ttu-id="63545-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span><span class="sxs-lookup"><span data-stu-id="63545-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span></span>  
  
 <span data-ttu-id="63545-119">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63545-119">Visual Basic</span></span>  
  
 <span data-ttu-id="63545-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span><span class="sxs-lookup"><span data-stu-id="63545-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="63545-121">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="63545-121">Robust Programming</span></span>  
 <span data-ttu-id="63545-122">前面的範例會使用單一消費者處理來源資料。</span><span class="sxs-lookup"><span data-stu-id="63545-122">The preceding example uses just one consumer to process the source data.</span></span> <span data-ttu-id="63545-123">如果您的應用程式中有多個消費者，請使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法從來源區塊讀取資料，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="63545-123">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <span data-ttu-id="63545-124">沒有可用資料時，<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法會回傳 `False`。</span><span class="sxs-lookup"><span data-stu-id="63545-124">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="63545-125">如果多個消費者必須同時存取來源區塊，這個機制就能確保在呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> 之後資料仍然可用。</span><span class="sxs-lookup"><span data-stu-id="63545-125">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63545-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="63545-126">See Also</span></span>  
 [<span data-ttu-id="63545-127">資料流程</span><span class="sxs-lookup"><span data-stu-id="63545-127">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
