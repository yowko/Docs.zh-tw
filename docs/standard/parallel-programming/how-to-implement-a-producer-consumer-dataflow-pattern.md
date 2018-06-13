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
ms.openlocfilehash: d94cfeecc9556fb01dd3d72649d960ce68f929d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580893"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>如何：實作生產者-消費者資料流程模式
本文件將說明如何使用 TPL 資料流程程式庫實作生產者-消費者模式。 在此模式中，「生產者」會將訊息傳送至訊息區塊，而「消費者」會從該區塊讀取訊息。  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>範例  
 下列範例將示範使用資料流程的基本生產者-消費者模型。 `Produce` 方法會將包含隨機位元組資料的陣列寫入 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> 物件中，而 `Consume` 方法會從 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> 物件中讀取位元組。 藉由處理 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 介面而不是其衍生類型，您就可以撰寫可重複使用的程式碼來處理各種資料流程區塊類型。 這個範例會使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別。 由於 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別會同時做為來源區塊和目標區塊，因此生產者和消費者可以使用共用物件來傳輸資料。  
  
 `Produce` 方法會在迴圈中呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法，將資料同步寫入目標區塊中。 `Produce` 方法將所有資料寫入目標區塊之後會呼叫 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> 方法，指出區塊將不會再提供任何額外的資料。 `Consume` 方法會使用 [async](~/docs/csharp/language-reference/keywords/async.md) 和 [await](~/docs/csharp/language-reference/keywords/await.md) 運算子 (在 Visual Basic 中為 [Async](~/docs/visual-basic/language-reference/modifiers/async.md) 和 [Await](~/docs/visual-basic/language-reference/operators/await-operator.md)) 以非同步方式計算從 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 物件接收的位元組總數。 若要以非同步方式執行，`Consume` 方法會呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> 方法在來源區塊有可用資料，以及來源區塊永遠不再提供其他可用資料時收到通知。  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `DataflowProducerConsumer.cs` 的檔案中 (在 Visual Basic 中為 `DataflowProducerConsumer.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>穩固程式設計  
 這個範例會使用單一消費者處理來源資料。 如果您的應用程式中有多個消費者，請使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法從來源區塊讀取資料，如下列範例所示。  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 沒有可用資料時，<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法會回傳 `False`。 如果多個消費者必須同時存取來源區塊，這個機制就能確保在呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> 之後資料仍然可用。  
  
## <a name="see-also"></a>請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
