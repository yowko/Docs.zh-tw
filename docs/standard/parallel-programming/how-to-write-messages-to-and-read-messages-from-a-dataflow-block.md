---
title: 如何：寫入訊息至資料流程區塊及讀取資料流程區塊中的訊息
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47a61a1d01984eeefb2f1f09774374dc29a774d3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087805"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>如何：寫入訊息至資料流程區塊及讀取資料流程區塊中的訊息
本文件將說明如何使用 TPL 資料流程程式庫，在資料流程區塊中寫物和讀取訊息。 TPL 資料流程程式庫提供了在資料流程區塊中寫入和讀取訊息的同步和非同步方法。 本文件將使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> 類別。 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別會緩衝訊息，並且同時做為訊息來源和訊息目標。  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>在資料流程區塊中同步寫入和讀取  
 下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 資料流程區塊，以及使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> 方法從同一個物件讀取。  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 您也可以使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法從資料流程區塊中讀取，如下列範例所示。 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法不會封鎖目前執行緒，當您偶爾輪詢資料時很有用。  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 由於 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法會同步執行，因此先前範例中的 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件會在第二個迴圈讀取資料前接收所有資料。 下列範例會使用 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 擴充第一個範例，以並行方式讀取和寫入訊息區塊。 由於 <xref:System.Threading.Tasks.Parallel.Invoke%2A> 會以並行方式執行動作，因此值不會依照特定順序寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件中。  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>在資料流程區塊中非同步寫入和讀取  
 下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法以非同步方式寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件，以及使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法以非同步方式從同一個物件讀取。 這個範例會使用 [async](~/docs/csharp/language-reference/keywords/async.md) 和 [await](~/docs/csharp/language-reference/keywords/await.md) 運算子 (在 Visual Basic 中為 [Async](~/docs/visual-basic/language-reference/modifiers/async.md) 和 [Await](~/docs/visual-basic/language-reference/operators/await-operator.md)) 以非同步方式對目標區塊傳送和讀取資料。 當您必須讓資料流程區塊延後訊息時，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法會很有用。 當您想要在有資料可用時處理資料時，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法會很有用。 如需訊息如何在訊息區塊之間傳播的詳細資訊，請參閱[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)中的＜訊息傳遞＞一節。  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>完整範例  
 下列範例將示範本文件的完整程式碼。  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請複製範例程式碼，並將它貼入 Visual Studio 專案中，或是貼入名為 `DataflowReadWrite.cs` 的檔案中 (在 Visual Basic 中為 `DataflowReadWrite.vb`)，然後在 Visual Studio 的 [命令提示字元] 視窗中執行下列命令。  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>後續步驟  
 這個範例將示範如何直接讀取和寫入訊息區塊。 您也可以連接資料流程區塊組成「管線」，這是資料流程區塊的線性序列，或是組成「網路」，這是資料流程區塊的圖形。 在管線或網路中，當資料可供使用時，來源會非同步散佈資料至目標。 如需建立基本資料流程管線的範例，請參閱[逐步解說：建立資料流程管線](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)。 如需建立更複雜的資料流程網路的範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
## <a name="see-also"></a>另請參閱

- [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
