---
title: 如何：寫入和讀取資料流程區塊中的訊息
ms.date: 09/10/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: 8eb92d917bb2b03c2a505a2ba238598e0c1a450c
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022853"
---
# <a name="how-to-write-and-read-messages-from-a-dataflow-block"></a>如何：寫入和讀取資料流程區塊中的訊息

本文說明如何使用工作平行程式庫 (TPL) 資料流程程式庫，將訊息寫入至資料流程區塊並從中讀取訊息。 TPL 資料流程程式庫提供了在資料流程區塊中寫入和讀取訊息的同步和非同步方法。 本文說明如何使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> 類別。 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>類別會緩衝訊息，並以訊息來源和訊息目標的形式來運作。

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-and-reading-synchronously"></a>以同步方式寫入和讀取

下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 資料流程區塊，以及使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> 方法從同一個物件讀取。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="2":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="2":::

您也可以使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法從資料流程區塊中讀取，如下列範例所示。 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法不會封鎖目前執行緒，當您偶爾輪詢資料時很有用。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="3":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="3":::

由於 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法會同步執行，因此先前範例中的 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件會在第二個迴圈讀取資料前接收所有資料。 下列範例會使用 <xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> 擴充第一個範例，以並行方式讀取和寫入訊息區塊。 由於 <xref:System.Threading.Tasks.Task.WhenAll%2A> 會以並行方式執行動作，因此值不會依照特定順序寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件中。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="4":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="4":::

## <a name="writing-and-reading-asynchronously"></a>以非同步方式撰寫和讀取

下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法以非同步方式寫入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件，以及使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法以非同步方式從同一個物件讀取。 這個範例會使用 [async](../../csharp/language-reference/keywords/async.md) 和 [await](../../csharp/language-reference/operators/await.md) 運算子 (在 Visual Basic 中為 [Async](../../visual-basic/language-reference/modifiers/async.md) 和 [Await](../../visual-basic/language-reference/operators/await-operator.md)) 以非同步方式對目標區塊傳送和讀取資料。 當您必須讓資料流程區塊延後訊息時，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法會很有用。 當您想要在有資料可用時處理資料時，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法會很有用。 如需訊息如何在訊息區塊之間傳播的詳細資訊，請參閱[資料流程](dataflow-task-parallel-library.md)中的＜訊息傳遞＞一節。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="5":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="5":::

## <a name="a-complete-example"></a>完整範例

下列範例顯示本文的所有程式碼。

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="1":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="1":::

## <a name="next-steps"></a>後續步驟

這個範例將示範如何直接讀取和寫入訊息區塊。 您也可以連接資料流程區塊組成「管線」**，這是資料流程區塊的線性序列，或是組成「網路」**，這是資料流程區塊的圖形。 在管線或網路中，當資料可供使用時，來源會非同步散佈資料至目標。 如需建立基本資料流程管線的範例，請參閱[逐步解說：建立資料流程管線](walkthrough-creating-a-dataflow-pipeline.md)。 如需建立更複雜的資料流程網路的範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](walkthrough-using-dataflow-in-a-windows-forms-application.md)。

## <a name="see-also"></a>另請參閱

- [資料流程 (工作平行程式庫)](dataflow-task-parallel-library.md)
