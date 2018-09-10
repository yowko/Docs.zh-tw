---
title: 資料流程 (工作平行程式庫)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library
ms.assetid: 643575d0-d26d-4c35-8de7-a9c403e97dd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d44ec0e0601383133e6c59e44cd81031918d4b6d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43385854"
---
# <a name="dataflow-task-parallel-library"></a>資料流程 (工作平行程式庫)
<a name="top"></a> 工作平行程式庫 (TPL) 提供資料流程元件，協助讓啟用並行的應用程式更強固。 這些資料流程元件合稱為「TPL 資料流程程式庫」。 此資料流程模型以提供針對廣泛資料流程以及管線工作的同處理序訊息傳遞，將以行動為基礎的程式撰寫升級。 資料流程元件會在 TPL 的類型與排程基礎結構上建置，並整合 C#、Visual Basic 以及 F# 語言對非同步程式設計的支援。 當您有多個必須非同步式互相溝通的作業時，或當您因為資料變為可用而要處理資料時，這些資料流程元件就會相當實用。 例如，請考慮一個應用程式，它會處理來自網路攝影機的影像資料。 使用資料流模型，應用程式就可以在影像畫面可用時處理它們。 例如，如果應用程式因執行光源修正或消除紅眼而增強影像畫面，則您可以建立資料流程元件的「管線」。 此管線的每個階段都可能使用更廣泛的平行處理原則功能 (例如 TPL 提供的功能) 來轉換該影像。  
  
 本文件提供 TPL 資料流程程式庫的概觀。 此文件描述程式設計模型、預先定義的資料流程區塊類型，以及描述如何設定資料流程區塊以符合應用程式的特定需求。  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
 本文件包含下列章節：  
  
-   [程式設計模型](#model)  
  
-   [預先定義的資料流程區塊類型](#predefined_types)  
  
-   [設定資料流程區塊行為](#behavior)  
  
-   [自訂資料流程區塊](#custom)  
  
<a name="model"></a>   
## <a name="programming-model"></a>程式設計模型  
 TPL 資料流程程式庫提供了訊息傳遞之基礎，也是平行處理具有高輸送量與低延遲、需要大量 CPU 與 I/O 的應用程式之基礎。 這也可以讓您明確地控制資料如何緩衝以及如何在系統中移動。 若要進一步了解資料流程程式撰寫模型，請考慮以非同步方式從磁碟載入影像並建立這些影像組合的應用程式。 傳統的程式設計模型通常需要您使用回呼和同步處理物件 (例如鎖定)，來協調工作與存取共用資料。 您可以使用資料流程程式撰寫模型來建立資料流程物件，從磁碟讀取影像時，該資料流程物件可以處理影像。 在資料流程模型下，您宣告資料的處理方式、宣告其可使用的時機，以及資料之間的相依性。 由於執行階段會處理資料之間的相依性，您通常可以避免存取共用資料之同步處理的需求。 此外，因為執行階段排程是依據資料的非同步抵達來運作，所以資料流程可以藉由有效管理基礎執行緒以改善回應性和輸送量。 如需在 Windows Forms 應用程式中使用資料流程程式撰寫模型來實作影像處理的範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
### <a name="sources-and-targets"></a>來源和目標  
 TPL 資料流程程式庫由「資料流程區塊」所組成，其為緩衝及處理資料的資料結構。 TPL 定義三種資料流程區塊：「來源區塊」、「目標區塊」和「傳播程式區塊」。 來源區塊可當做資料來源，可以從中讀取。 目標區塊可當做資料接收器，可以寫入。 傳播程式區塊可當做來源區塊和目標區塊，而且可以從中讀取和寫入。 TPL 定義 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> 介面代表來源、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> 代表目標，以及 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602?displayProperty=nameWithType> 代表傳播程式。 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> 繼承自 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>。  
  
 TPL 資料流程程式庫提供幾種預先定義的資料流程區塊類型，這些類型會實作 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> 介面。 本文件的[預先定義的資料流程區塊類型](#predefined_types)一節描述這些資料流程區塊類型。  
  
### <a name="connecting-blocks"></a>連接區塊  
 您也可以連接資料流程區塊來形成「管線」(資料流程區塊的線性序列) 或「網路」(資料流程區塊的圖形)。 管線是網路的一種格式。 在管線或網路中，當資料可供使用時，來源會非同步散佈資料至目標。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> 方法將來源資料流程區塊連結至目標區塊。 來源可以連接至零或多個目標；目標可以從零或更多個來源連接。 您可以同時在管線或網路中加入或移除資料流程區塊。 預先定義的資料流程區塊類型會處理連結和取消連結的所有執行緒安全性層面。  
  
 如需連接資料流程區塊以形成基本管線的範例，請參閱[逐步解說：建立資料流程管線](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)。 如需連接資料流程區塊以形成更複雜網路的範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。 如需在來源提供目標訊息後將目標從來源取消連結的範例，請參閱[如何：取消連結資料流程區塊](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)。  
  
#### <a name="filtering"></a>篩選  
 當您呼叫 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=nameWithType> 方法來連結來源與目標時，您可以提供委派，根據訊息值來判斷目標區塊接受或拒絕訊息。 篩選機制是確保資訊流程區塊只接收特定值的實用方式。 對於大部分預先定義的資料流程區塊類型而言，如果來源區塊連接到多個目標區塊，則當目標區塊拒絕訊息時，來源就會提供該訊息給下一個目標。 來源提供訊息給目標的順序是由該來源所定義，而且可能會根據該來源類型而有所不同。 大部分的來源區塊類型在目標接受訊息之後，就會停止提供訊息。 此規則的唯一例外是 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 類別，即使有一些目標拒絕了訊息，其仍為所有目標提供每一個訊息。 如需使用篩選來只處理特定訊息的範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
> [!IMPORTANT]
>  由於每個預先定義來源資料流程區塊類型確保訊息都會按照收到訊息的順序來散佈，所以每個訊息都必須由來源區塊所讀取，之後來源區塊才可處理下一個訊息。 因此，當您使用篩選以連接多個目標至來源時，請確定至少有一個目標區塊會接收每一個訊息。 否則，您的應用程式可能會發生死結。  
  
### <a name="message-passing"></a>訊息傳遞  
 資料流程程式設計模型與「訊息傳遞」的概念有關，其中程式的獨立元件可藉由傳送訊息相互通訊。 在應用程式元件之間散佈訊息的其中一種方式，為呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 和 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> 方法，來將訊息傳送至目標資料流程區塊通知 (<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 會同步動作；<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 會非同步動作)，以及呼叫 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 和 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A> 方法，以接收來自來源區塊的訊息。 您可以傳送輸入資料至管線的前端節點 (目標區塊)，並接收來自管線的終端節點或網路 (一個或多個來源區塊) 的終端節點之輸出資料，將這些方法結合資料流程管線或網路。 您也可以使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Choose%2A> 方法，從第一個具有可用資料並在此資料中執行動作之提供的來源讀取。  
  
 來源區塊會呼叫 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A?displayProperty=nameWithType> 方法，以提供資料給目標區塊。 目標區塊對於所提供的訊息會採取三種回應之一：它可以接受該訊息、拒絕該訊息或延後該訊息。 當目標接受該訊息時，<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> 方法會傳回 <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Accepted>。 當目標拒絕該訊息時，<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> 方法會傳回 <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Declined>。 當目標要求不再接收來自來源的任何訊息時，<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> 會傳回 <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.DecliningPermanently>。 在接收這類傳回值之後，以及從這類目標自動取消連結之後，預先定義的來源區塊類型就不會傳遞訊息給連結的目標。  
  
 當目標區塊延後該訊息以供稍後使用時，<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A> 方法會傳回 <xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus.Postponed>。 延後訊息的目標區塊可以於稍後呼叫 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReserveMessage%2A?displayProperty=nameWithType> 方法，以嘗試保留所提供的訊息。 此時訊息仍為可用，而且可由目標區塊所使用，或者訊息已由另一個目標所採用。 當目標區塊於稍後要求此訊息，或者不再需要此訊息時，便會分別呼叫 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> 或 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReleaseReservation%2A> 方法。 訊息保留通常由在非窮盡模式下操作的資料流程區塊型別所使用。 本文稍後將說明非窮盡模式。 除了保留已延後的訊息之外，目標區塊也可以使用 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=nameWithType> 方法，來嘗試直接使用其他延後的訊息。  
  
### <a name="dataflow-block-completion"></a>資料流程區塊的完成  
 資料流程區塊也支援「完成」的概念。 在已完成狀態中的資料流程區塊並不會執行任何進一步的工作。 每個資料流程區塊都具有相關聯的 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 物件，稱為*完成工作*，代表該區塊的完成狀態。 由於您可以使用完成工作來等候 <xref:System.Threading.Tasks.Task> 物件結束，所以可以等候資料流程網路的一或多個終端節點完成。 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> 介面定義了 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> 方法，該方法會通知為其所要求的資料流程區塊完成，以及定義了 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> 屬性，該屬性會傳回資料流程區塊的完成工作。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 這兩者都是繼承自 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> 介面。  
  
 有兩種方式用來判斷資料流程區塊是否完成而沒有錯誤，還是遇到一或多個錯誤或已取消。 第一種方式為在 `try`-`catch` 區塊 (在 Visual Basic 中為 `Try`-`Catch`) 中的完成工作上呼叫 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 方法。 下列範例會建立一個會在其輸入值小於零時擲回 <xref:System.ArgumentOutOfRangeException> 的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。 當這個範例呼叫完成工作上的 <xref:System.Threading.Tasks.Task.Wait%2A> 時，會擲回 <xref:System.AggregateException>。 可透過 <xref:System.AggregateException> 物件的 <xref:System.AggregateException.InnerExceptions%2A> 屬性存取 <xref:System.ArgumentOutOfRangeException>。  
  
 [!code-csharp[TPLDataflow_Overview#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#10)]
 [!code-vb[TPLDataflow_Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#10)]  
  
 這個範例示範在執行資料流程區塊的委派中有例外狀況未受處理的案例。 建議您在這類區塊的主體中處理例外狀況。 然而，假如您無法這樣做，區塊會表現得就像已經取消，而不會處理傳入的訊息。  
  
 當資料流程區塊已明確地取消時，<xref:System.AggregateException> 物件包含 <xref:System.AggregateException.InnerExceptions%2A> 屬性中的 <xref:System.OperationCanceledException>。 如需取消資料流程的詳細資訊，請參閱[啟用取消](#enabling-cancellation)一節。  
  
 第二種判斷資料流程區塊完成狀態的方式為使用此完成工作的接續，或使用 C# 和 Visual Basic 的非同步語言功能來非同步等候此完成工作。 您提供給 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> 方法的委派會採用代表前項工作的 <xref:System.Threading.Tasks.Task> 物件。 在 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> 屬性的案例中，接續的委派本身會採用完成工作。 下列範例與上一則範例很相似，不同之處在於它也會使用 <xref:System.Threading.Tasks.Task.ContinueWith%2A> 方法建立會列印整個資料流程作業狀態的接續工作。  
  
 [!code-csharp[TPLDataflow_Overview#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#11)]
 [!code-vb[TPLDataflow_Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#11)]  
  
 您也可以使用在接續工作主體中的屬性 (例如 <xref:System.Threading.Tasks.Task.IsCanceled%2A>)，判斷資料流程區塊完成狀態中的其他資訊。 如需接續工作及其與取消跟錯誤處理之關聯的詳細資訊，請參閱[使用接續工作鏈結工作](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)、[工作取消](../../../docs/standard/parallel-programming/task-cancellation.md)和[例外狀況處理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)。  
  
 [回到頁首](#top)  
  
<a name="predefined_types"></a>   
## <a name="predefined-dataflow-block-types"></a>預先定義的資料流程區塊類型  
 TPL 資料流程程式庫提供幾種預先定義的資料流程區塊類型。 這些類型分為三類：「緩衝區塊」、「執行區塊」和「群組區塊」。 下列章節描述組成這些類別的區塊類型。  
  
### <a name="buffering-blocks"></a>緩衝區塊  
 緩衝區塊保存供資料消費者使用的資料。 TPL 資料流程程式庫提供三個緩衝區塊類型：<xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601?displayProperty=nameWithType>。  
  
#### <a name="bufferblockt"></a>BufferBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別代表一般用途的非同步傳訊結構。 這個類別會儲存可由多個來源寫入或由多個目標讀取之訊息的先進先出 (FIFO) 佇列。 當目標從 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件接收到訊息時，就會從訊息佇列中移除該訊息。 因此，雖然 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件可以具有多個目標，只有一個目標會接收到每則訊息。 當您想要將多則訊息傳遞給其他元件，而且該元件必須接收每則訊息時，<xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 類別就很有用。  
  
 下列基本範例會張貼數個 <xref:System.Int32> 值至 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件，接著從該物件讀取這些值。  
  
 [!code-csharp[TPLDataflow_Overview#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#1)]
 [!code-vb[TPLDataflow_Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#1)]  
  
 如需示範如何撰寫訊息到 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件，並從其中讀取訊息的完整範例，請參閱[如何：寫入訊息至資料流程區塊及讀取資料流程區塊中的訊息](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)。  
  
#### <a name="broadcastblockt"></a>BroadcastBlock(T)  
 當您需要將多則訊息傳遞給其他元件，但是該元件只需要最新的值時，<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 類別就很有用。 當您想要將訊息廣播至多個元件時，這個類別也很有用。  
  
 下列基本範例會將 <xref:System.Double> 值傳遞至 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 物件，然後從該物件讀取該值數次。 因為在已讀取值之後並不會從 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 物件中移除這些值，所以每次可用此相同的值。  
  
 [!code-csharp[TPLDataflow_Overview#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#2)]
 [!code-vb[TPLDataflow_Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#2)]  
  
 如需示範如何使用 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 來將訊息廣播到多個目標區塊的完整範例，請參閱[如何：在資料流程區塊中指定工作排程器](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)。  
  
#### <a name="writeonceblockt"></a>WriteOnceBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 類別類似於 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 類別，但是 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件只能被寫入一次。 您可以將 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 視為類似 C# [readonly](~/docs/csharp/language-reference/keywords/readonly.md) (在 Visual Basic 中為 [ReadOnly](~/docs/visual-basic/language-reference/modifiers/readonly.md)) 關鍵字，不過當 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件接收到值 (而非建構) 時，它就會變成不可變。 與 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 類別相同的是，當目標從 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件收到訊息時，並不會從此物件中移除該訊息。 因此，多個目標會接收此訊息的複本。 當您只想要散佈眾多訊息中的第一個時，<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 類別會很有用。  
  
 下列基本範例傳遞多個 <xref:System.String> 值至 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件，然後從該物件讀取值。 由於 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件只能被寫入一次，所以 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 物件接收到訊息之後，就會捨棄後續訊息。  
  
 [!code-csharp[TPLDataflow_Overview#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#3)]
 [!code-vb[TPLDataflow_Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#3)]  
  
 如需示範如何使用 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> 接收第一個結束作業之值的完整範例，請參閱[如何：取消連結資料流程區塊](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)。  
  
### <a name="execution-blocks"></a>執行區塊  
 執行區塊會為已接受資料的每個部分呼叫使用者提供的委派。 TPL 資料流程程式庫提供三個執行區塊類型：<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>。  
  
#### <a name="actionblockt"></a>ActionBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 類別是在接收到資料時呼叫委派的目標區塊。 可將 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件視為在資料可用時會非同步執行的委派。 您提供給 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件的委派可以是 <xref:System.Action%601> 類型或 `System.Func<TInput, Task>` 類型。 當您搭配 <xref:System.Action%601> 使用 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件時，會將每個輸入項目的處理在委派傳回時視為完成。 當您搭配 `System.Func<TInput, Task>` 使用 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件時，只有在傳回的 <xref:System.Threading.Tasks.Task> 物件已完成時，才會將每個輸入項目的處理視為已完成。 使用這兩種機制，您可以使用 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 為每個輸入項目作同步與非同步處理。  
  
 下列基本範例會張貼多個 <xref:System.Int32> 值到 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件會列印這些值到主控台。 這個範例接著會設定此區塊為完成狀態，並等候所有資料流程工作完成。  
  
 [!code-csharp[TPLDataflow_Overview#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#4)]
 [!code-vb[TPLDataflow_Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#4)]  
  
 如需示範如何使用具有 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 類別之委派的完整範例，請參閱[如何：在資料流程區塊收到資料時執行動作](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)。  
  
#### <a name="transformblocktinput-toutput"></a>TransformBlock(TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 類別類似於 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 類別，不同處在於它可同時作為來源和目標。 您傳遞給 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件的委派會傳回類型 `TOutput` 的值。 您提供給 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件的委派可以是類型 `System.Func<TInput, TOutput>` 或類型 `System.Func<TInput, Task<TOutput>>`。 當您搭配 `System.Func<TInput, TOutput>` 使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件時，會將每個輸入項目的處理在委派傳回時視為完成。 當您搭配 `System.Func<TInput, Task<TOutput>>` 使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件時，只有在傳回的 <xref:System.Threading.Tasks.Task%601> 物件已完成時，才會將每個輸入項目的處理視為已完成。 如同 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>，使用這兩種機制，您就可以使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 為每個輸入項目作同步與非同步處理。  
  
 下列基本範例會建立 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件，該物件會計算其輸入的平方根。 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 物件會使用 <xref:System.Int32> 值做為輸入，並產生 <xref:System.Double> 值做為輸出。  
  
 [!code-csharp[TPLDataflow_Overview#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#5)]
 [!code-vb[TPLDataflow_Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#5)]  
  
 如需在於 Windows Forms 應用程式中執行影像處理的資料流程區塊網路中使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 的完整範例，請參閱[逐步解說：在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
#### <a name="transformmanyblocktinput-toutput"></a>TransformManyBlock(TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 類別相似於 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 類別，不同處在於 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 對每個輸入值會產生零或多個輸出值，而不是只有一個。 您提供給 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件的委派可以是類型 `System.Func<TInput, IEnumerable<TOutput>>` 或類型 `System.Func<TInput, Task<IEnumerable<TOutput>>>`。 當您搭配 `System.Func<TInput, IEnumerable<TOutput>>` 使用 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件時，會將每個輸入項目的處理在委派傳回時視為完成。 當您搭配 `System.Func<TInput, Task<IEnumerable<TOutput>>>` 使用 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件時，只有在傳回的 `System.Threading.Tasks.Task<IEnumerable<TOutput>>` 物件已完成時，才會將每個輸入項目的處理視為已完成。  
  
 下列基本範例會建立 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件，該物件會將字串分割成獨立字元的序列。 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件會使用 <xref:System.String> 值做為輸入，並產生 <xref:System.Char> 值做為輸出。  
  
 [!code-csharp[TPLDataflow_Overview#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#6)]
 [!code-vb[TPLDataflow_Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#6)]  
  
 如需使用 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 為資料流程管線中的每個輸入產生多組獨立輸出的完整範例，請參閱[逐步解說：建立資料流程管線](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)。  
  
#### <a name="degree-of-parallelism"></a>平行處理原則的刻度  
 每個 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件會緩衝輸入訊息，直到此區塊已準備好處理它們。 這些類別預設會按照接收到訊息的順序，一次處理一個訊息。 您也可以指定平行處理原則的刻度以啟動 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件同時處理多個訊息。 如需同時執行的詳細資訊，請參閱本文稍後的＜指定平行處理原則的刻度＞一節。 如需設定平行處理原則的刻度，讓執行資料流程區塊一次可處理一個以上訊息的範例，請參閱[如何：在資料流程區塊中指定平行處理原則的刻度](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)。  
  
#### <a name="summary-of-delegate-types"></a>委派類型摘要  
 下表摘要說明您可以提供給 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 物件的委派類型。 表中也會指出委派類型是以同步或非同步方式運作。  
  
|類型|同步委派類型|非同步委派類型|  
|----------|-------------------------------|--------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|`System.Action`|`System.Func<TInput, Task>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|`System.Func<TInput, TOutput>`|`System.Func<TInput, Task<TOutput>>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|`System.Func<TInput, IEnumerable<TOutput>>`|`System.Func<TInput, Task<IEnumerable<TOutput>>>`|  
  
 當您使用執行區塊類型時，也可以使用 Lambda 運算式。 如需示範如何使用 Lambda 運算式搭配執行區塊的範例，請參閱[如何：在資料流程區塊收到資料時執行動作](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)。  
  
### <a name="grouping-blocks"></a>群組區塊  
 群組區塊合併來自一個或多個來源、以及在各種條件約束下的資料。 TPL 資料流程式庫提供三個聯結區塊類型：<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>、<xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>。  
  
#### <a name="batchblockt"></a>BatchBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別將稱為批次的輸入資料集合併為輸出資料陣列。 在建立 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件時，請指定每一批次的大小。 當 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件接收指定的輸入項目計數時，會非同步散佈包含這些項目的陣列。 如果 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件設定為完成狀態，但未包含足夠構成批次的項目，則會散佈包含剩餘輸入項目的最後一個陣列。  
  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別會在*窮盡*或*非窮盡*模式下運作。 在窮盡模式 (這是預設值)，<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件接受每則提供的訊息，並在接收指定的項目計數後散佈陣列。 在非窮盡模式，<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件延後所有傳入訊息，直到來源提供給區塊的訊息足以形成批次。 因為窮盡模式需要較少的處理額外負荷，通常其效能優於非窮盡模式。 不過，在您必須以不可部分完成的方式協調來自多個來源之消耗時，可以使用非窮盡模式。 在 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601.%23ctor%2A> 建構函式的 `dataflowBlockOptions` 參數中，設定 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> 為 `False`，來指定非窮盡模式。  
  
 下列基本範例傳遞數個 <xref:System.Int32> 值至 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件，該物件會在一個批次中保存十個項目。 為了保證所有的值都會從 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 散佈，此範例會呼叫 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> 方法。 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> 方法會將 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件設定為完成狀態，因此，<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件會散佈任何的剩餘項目做為最後的批次。  
  
 [!code-csharp[TPLDataflow_Overview#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#7)]
 [!code-vb[TPLDataflow_Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#7)]  
  
 如需使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 改善資料庫插入作業效率的完整範例，請參閱[逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)。  
  
#### <a name="joinblockt1-t2-"></a>JoinBlock(T1, T2, ...)  
 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> 類別會收集輸入項目，並散佈包含這些項目的 <xref:System.Tuple%602?displayProperty=nameWithType> 或 <xref:System.Tuple%603?displayProperty=nameWithType> 物件。 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> 類別不會繼承自 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>。 相反地，它們提供了實作 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 的屬性：<xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target1%2A>、<xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target2%2A> 和 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603.Target3%2A>。  
  
 就像是 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>、<xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603>，在窮盡或非窮盡模式下操作。 在窮盡模式 (這是預設值)，<xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 或 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> 物件會接受每則提供給它的訊息，並在其目標接收到至少一個訊息之後散佈 Tuple。 在非窮盡模式，<xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 或 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> 物件延後所有傳入訊息，直到建立 Tuple 所需的資料已提供至所有目標。 此時，該區塊會使用兩階段認可通訊協定，從來源以不可分割方式擷取所有必要的項目。 這項延遲使得其他實體可以同時使用資料，讓整個系統繼續進行。  
  
 下列基本範例示範 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> 物件要求多個資料來計算一個值的案例。 這個範例會建立需要兩個 <xref:System.Int32> 值和一個 <xref:System.Char> 值來執行算術運算的 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603> 物件。  
  
 [!code-csharp[TPLDataflow_Overview#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#8)]
 [!code-vb[TPLDataflow_Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#8)]  
  
 如需在非窮盡模式中使用 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件以合作方式共用資源的完整範例，請參閱[如何：使用 JoinBlock 從多個來源讀取資料](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)。  
  
#### <a name="batchedjoinblockt1-t2-"></a>BatchedJoinBlock(T1, T2, ...)  
 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%603> 類別會收集輸入項目的批次，並散佈包含這些項目的 `System.Tuple(IList(T1), IList(T2))` 或 `System.Tuple(IList(T1), IList(T2), IList(T3))` 物件。 請將 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 視為 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 的組合。 當您建立 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 物件時，請指定每一批次的大小。 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 也提供會實作 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 的屬性：<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> 和 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>。 當收到來自所有目標的指定輸入項目計數時，<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 物件會非同步散佈包含這些項目的 `System.Tuple(IList(T1), IList(T2))` 物件。  
  
 下列基本範例建立會保存結果的 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 物件、<xref:System.Int32> 值，以及為 <xref:System.Exception> 物件的錯誤。 這個範例執行多個作業，並將結果寫入 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 物件的 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A> 屬性，將錯誤寫入 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A> 屬性。 由於事先不知道成功和失敗的作業計數，<xref:System.Collections.Generic.IList%601> 物件可讓每個目標接收零或多個值。  
  
 [!code-csharp[TPLDataflow_Overview#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#9)]
 [!code-vb[TPLDataflow_Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#9)]  
  
 如需使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 來擷取程式從資料庫讀取時所發生的結果和任何例外狀況的完整範例，請參閱[逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)。  
  
 [回到頁首](#top)  
  
<a name="behavior"></a>   
## <a name="configuring-dataflow--block-behavior"></a>設定資料流程區塊行為  
 您可以對資料流程區塊類型建構函式提供 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType> 物件來啟用其他選項。 這些選項可控制行為，例如會管理基礎工作和平行處理原則刻度的排程器。 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions> 也衍生出會指定某些資料流程區塊類型特定行為的類型。 下表摘要說明與各資料流程區塊類型相關聯的選項類型。  
  
|資料流程區塊類型|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions> 類型|  
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
  
 下列章節提供可用於 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions?displayProperty=nameWithType> 類別中重要的資料流程選項種類之其他資訊。  
  
### <a name="specifying-the-task-scheduler"></a>指定工作排程器  
 每個預先定義的資料流程區塊使用 TPL 工作排程機制來執行活動，例如當資料可用時散佈資料至目標、接收來自來源的資料和執行使用者定義的委派。 <xref:System.Threading.Tasks.TaskScheduler> 是一種抽象類別，代表在執行緒上將工作排入佇列的工作排程器。 預設工作排程器 <xref:System.Threading.Tasks.TaskScheduler.Default%2A> 使用 <xref:System.Threading.ThreadPool> 類別將工作排入佇列並執行。 您可以在建構資料流程區塊物件時設定 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 屬性，來覆寫預設工作排程器。  
  
 在同一個工作排程器管理多個資料流程區塊時，它可以跨區塊強制執行原則。 例如，如果多個資料流程區塊分別設定為以相同 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 物件的獨佔排程器為目標，則會將所有跨區塊執行的的工作序列化。 同樣地，如果這些區塊設定為以相同 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 物件的並行排程器為目標，且該排程器已設定為具有最大並行層級，則所有來自這些區塊的工作都受限於並行作業的數目。 如需使用 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 類別來使讀取作業以平行方式發生，但使寫入作業僅會針對所有其他作業發生的範例，請參閱[如何：在資料流程區塊中指定工作排程器](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)。 如需 TPL 中工作排程器的詳細資訊，請參閱 <xref:System.Threading.Tasks.TaskScheduler> 類別主題。  
  
### <a name="specifying-the-degree-of-parallelism"></a>指定平行處理原則的刻度  
 根據預設，TPL 資料流程程式庫所提供的三個執行區塊類型 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>，一次處理一個訊息。 這些資料流程區塊類型也都會按照接收到訊息的順序處理訊息。 在建構資料流程區塊物件時，要讓這些資料流程區塊同時處理訊息，請設定 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> 屬性。  
  
 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> 的預設值為 1，以保證該資料流程區塊一次處理一個訊息。 設定此屬性為大於 1 的值可讓資料流程區塊同時處理多個訊息。 設定此屬性為 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType> 可啟用基本的工作排程器來管理最大並行刻度。  
  
> [!IMPORTANT]
>  當您指定大於 1 的最大平行處理原則刻度時，將會同時處理多個訊息，因此訊息可能不會依照接收到的順序處理。 不過，訊息從區塊輸出的順序和收到的順序一樣。  
  
 因為 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> 屬性表示平行處理原則的最大刻度，所以資料流程區塊可能會以比您所指定刻度更小的平行處理原則來執行。 資料流程區塊可能使用較低刻度的平行處理以符合其功能需求，或者是因為缺乏可用的系統資源。 資料流程區塊絕不選擇高於您所指定的平行處理。  
  
 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> 屬性的值對每個資料流程區塊物件是獨佔的。 例如，如果四個資料流程區塊物件每一個都為平行處理原則的最大刻度指定為 1，則全部四個資料流程區塊物件都可以平行執行。  
  
 如需設定平行處理原則的最大刻度，讓長時間作業平行處理的範例，請參閱[如何：在資料流程區塊中指定平行處理原則刻度](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)。  
  
### <a name="specifying-the-number-of-messages-per-task"></a>指定每項工作的訊息數量  
 預先定義的資料流程區塊類型使用工作以處理多個輸入項目。 這有助於減少被要求處理資料的工作物件數目，使得應用程式更有效率地執行。 不過，當來自一組工作資料流程區塊的工作正在處理資料時，來自其他資料流程區塊的工作可能需要將訊息加入佇列來等候處理時間。 若要提升資料流程中工作的公平性，請設定 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> 屬性。 當 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> 設定為 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=nameWithType> (預設) 時，由資料流程區塊所使用的工作會盡可能多地處理訊息。 在 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> 設定為除了 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded> 以外的值時，即為資料流程區塊對每個 <xref:System.Threading.Tasks.Task> 物件至多處理的訊息數量。 雖然設定 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A> 屬性可能會在工作之間提升公平性，但它可能造成系統建立更多超出所需的工作，反而可能會降低效能。  
  
### <a name="enabling-cancellation"></a>啟用取消  
 TPL 提供一種讓工作以合作方式協調取消的機制。 若要讓資料流程區塊參與此取消機制，請設定 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 屬性。 當此 <xref:System.Threading.CancellationToken> 物件設定為已取消狀態時，所有監視此語彙基元的資料流程區塊會結束執行其目前項目，但不開始處理後續項目。 這些資料流程區塊也會清除任何緩衝訊息，釋放連結給任何來源區塊和目標區塊，並轉換為取消狀態。 除非在處理期間發生例外狀況，不然 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A> 屬性將透過轉換到已取消的狀態，將 <xref:System.Threading.Tasks.Task.Status%2A> 屬性設定為 <xref:System.Threading.Tasks.TaskStatus.Canceled>。 在此情況下，<xref:System.Threading.Tasks.Task.Status%2A> 會設定為 <xref:System.Threading.Tasks.TaskStatus.Faulted>。  
  
 如需示範如何在 Windows Forms 應用程式中使用取消的範例，請參閱[如何：取消資料流程區塊](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)。 如需 TPL 中取消的詳細資訊，請參閱[工作取消](../../../docs/standard/parallel-programming/task-cancellation.md)。  
  
### <a name="specifying-greedy-versus-non-greedy-behavior"></a>指定窮盡與非窮盡的行為  
 許多群組資料流程區塊類型可以在「窮盡」或「非窮盡」模式中運作。 預先定義的資料流程區塊類型預設會在窮盡模式下運作。  
  
 對於聯結區塊類型 (例如 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>)，窮盡模式表示即使與其相聯結的對應資料尚未可用，區塊會立即接受資料。 非窮盡模式則表示區塊會延後處理所有傳入訊息，直到其中之一在其每個目標上可用於完成聯結。 如果任何延後的訊息皆不再可用，則聯結區塊會釋出所有延後的訊息，並重新啟動此程序。 對於 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別，窮盡和非窮盡的行為類似，但是在非窮盡模式下，<xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件將所有傳入訊息延後，直到來自不同來源的訊息足夠可用，以完成批次。  
  
 若要為資料流程區塊指定非窮盡模式，請將 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> 設為 `False`。 如需示範如何使用非窮盡模式，讓多個聯結區塊更有效率共用資料來源的範例，請參閱[如何：使用 JoinBlock 從多個來源讀取資料](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)。  
  
 [回到頁首](#top)  
  
<a name="custom"></a>   
## <a name="custom-dataflow-blocks"></a>自訂資料流程區塊  
 雖然 TPL 資料流程程式庫提供許多預先定義的區塊類型，但您可以建立會執行自訂行為的其他區塊類型。 直接實作 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 或 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 介面，或是使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> 方法來建立封裝現有區塊類型行為的複雜區塊。 如需示範如何實作自訂資料流程區塊功能的範例，請參閱[逐步解說：建立自訂資料流程區塊類型](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)。  
  
 [回到頁首](#top)  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[操作說明：對資料流程區塊寫入訊息和讀取訊息](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)|示範如何寫入訊息至 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 物件及讀取該物件中的訊息。|  
|[操作說明：實作產生者-取用者資料流程模式](../../../docs/standard/parallel-programming/how-to-implement-a-producer-consumer-dataflow-pattern.md)|描述如何使用此資料流程模型以實作生產者-消費者模式，其中生產者傳送訊息至資料流程區塊，而消費者從該區塊讀取訊息。|  
|[操作說明：在資料流程區塊收到資料時執行動作](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)|說明如何提供委派給執行資料流程區塊類型 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>。|  
|[逐步解說：建立資料流程管線](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)|描述如何建立可以從網路下載文字並對該文字執行作業的資料流程管線。|  
|[操作說明：取消連結資料流程區塊](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)|示範如何使用 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法，來在來源為目標提供訊息之後，將目標區塊與其來源取消連結。|  
|[逐步解說：在 Windows Forms 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)|示範如何建立資料流程區塊網路，其可以在 Windows Form 應用程式中執行影像處理。|  
|[如何：取消資料流程區塊](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)|示範如何在 Windows Form 應用程式中使用取消。|  
|[操作說明：使用 JoinBlock 從多個來源讀取資料](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)|說明如何在資料可取自多重來源時使用 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 類別執行作業，以及如何使用非窮盡模式使得多重聯結區塊可以更有效率地共用資料來源。|  
|[操作說明：在資料流程區塊中指定平行處理原則刻度](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)|描述如何設定 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> 屬性使執行資料流程區塊可以同時處理一個以上的訊息。|  
|[操作說明：在資料流程區塊中指定工作排程器](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)|示範當您在應用程式中使用資料流程時，要如何與特定工作排程器建立關聯。|  
|[逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)|說明如何使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別來改善資料庫插入作業的效率，以及說明如何使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 類別在程式讀取資料庫時擷取結果和發生的任何例外狀況。|  
|[逐步解說：建立自訂資料流程區塊類型](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)|示範建立會實作自訂行為的資料流程區塊類型之兩種方式。|  
|[工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|介紹 TPL，一種在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 應用程式中簡化平行和並行程式設計的程式庫。|
