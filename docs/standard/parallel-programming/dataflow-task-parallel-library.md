---
title: "資料流程 (工作平行程式庫) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工作平行程式庫, 資料流程"
  - "TPL 資料流程式庫"
ms.assetid: 643575d0-d26d-4c35-8de7-a9c403e97dd6
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# 資料流程 (工作平行程式庫)
<a name="top"></a>工作平行程式庫 (TPL) 提供資料流程元件來協助增加啟用並行存取的應用程式的穩定性。 這些資料流程元件合稱為*TPL 資料流程程式庫*。 此資料流程模型以提供針對廣泛資料流程以及管線工作的同處理序訊息傳遞，將以行動為基礎的程式撰寫升級。 資料流程元件會在 TPL 的類型與排程基礎結構上建置，並整合 C#、[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 以及 F# 語言對非同步程式設計的支援。 當您有多個必須非同步式互相溝通的作業時，或當您因為資料變為可用而要處理資料時，這些資料流程元件就會相當實用。 例如，請考慮一個應用程式，它會處理來自網路攝影機的影像資料。 使用資料流模型，應用程式就可以在影像畫面可用時處理它們。 如果應用程式增強影像畫面，比方說，藉由執行淺的修正或消除紅眼而減少，您可以建立*管線*的資料流程元件。 此管線的每個階段都可能使用更廣泛的平行處理原則功能 (例如 TPL 提供的功能) 來轉換該影像。  
  
 本文件提供 TPL 資料流程程式庫的概觀。 此文件描述程式設計模型、預先定義的資料流程區塊類型，以及描述如何設定資料流程區塊以符合應用程式的特定需求。  
  
> [!TIP]
>  TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName>命名空間) 並未隨附於[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。 若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇 **管理 NuGet 封裝**從 [專案] 功能表，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。  
  
 本文件包含下列章節：  
  
-   [程式設計模型](#model)  
  
-   [預先定義的資料流程區塊類型](#predefined_types)  
  
-   [設定資料流程區塊行為](#behavior)  
  
-   [自訂資料流程區塊](#custom)  
  
<a name="model"></a>   
## <a name="programming-model"></a>程式設計模型  
 TPL 資料流程程式庫提供了訊息傳遞之基礎，也是平行處理具有高輸送量與低延遲、需要大量 CPU 與 I/O 的應用程式之基礎。 這也可以讓您明確地控制資料如何緩衝以及如何在系統中移動。 若要進一步了解資料流程程式撰寫模型，請考慮以非同步方式從磁碟載入影像並建立這些影像組合的應用程式。 傳統的程式設計模型通常需要您使用回呼和同步處理物件 (例如鎖定)，來協調工作與存取共用資料。 您可以使用資料流程程式撰寫模型來建立資料流程物件，從磁碟讀取影像時，該資料流程物件可以處理影像。 在資料流程模型下，您宣告資料的處理方式、宣告其可使用的時機，以及資料之間的相依性。 由於執行階段會處理資料之間的相依性，您通常可以避免存取共用資料之同步處理的需求。 此外，因為執行階段排程是依據資料的非同步抵達來運作，所以資料流程可以藉由有效管理基礎執行緒以改善回應性和輸送量。 如需使用資料流程程式撰寫模型來實作影像處理的 Windows Form 應用程式中的範例，請參閱[逐步解說︰ 在 Windows Form 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
### <a name="sources-and-targets"></a>來源和目標  
 TPL 資料流程程式庫包含*資料流程區塊*，這是資料結構緩衝及處理資料。 TPL 會定義三種類型的資料流程區塊︰*來源區塊*，*目標區塊*，和*傳播程式區塊*。 來源區塊可當做資料來源，可以從中讀取。 目標區塊可當做資料接收器，可以寫入。 傳播程式區塊可當做來源區塊和目標區塊，而且可以從中讀取和寫入。 TPL 定義<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=fullName>介面代表來源、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=fullName>代表目標，以及<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602?displayProperty=fullName>代表傳播程式。</TInput, TOutput> <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>同時繼承自<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>，和<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>。\</TInput, TOutput>  
  
 TPL 資料流程程式庫提供數個預先定義的資料流程區塊類型，實作<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>， <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>，和<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>介面。\</TInput, TOutput> 這一節中的文件中詳述這些資料流程區塊類型[預先定義的資料流程區塊類型](#predefined_types)。  
  
### <a name="connecting-blocks"></a>連接區塊  
 您可以連接資料流程區塊組成*管線*，這是資料流程區塊的線性序列或*網路*，這是資料流程區塊的圖形。 管線是網路的一種格式。 在管線或網路中，當資料可供使用時，來源會非同步散佈資料至目標。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=fullName>方法連結至目標區塊將來源資料流程區塊。 來源可以連接至零或多個目標；目標可以從零或更多個來源連接。 您可以同時在管線或網路中加入或移除資料流程區塊。 預先定義的資料流程區塊類型會處理連結和取消連結的所有執行緒安全性層面。  
  
 如需連接資料流程區塊以形成基本管線的範例，請參閱[逐步解說︰ 建立資料流程管線](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)。 如需連接資料流程區塊形成更複雜的網路的範例，請參閱[逐步解說︰ 在 Windows Form 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。 如需來源提供目標訊息後取消連結來源的資料為目標的範例，請參閱[如何︰ 取消連結資料流程區塊](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)。  
  
#### <a name="filtering"></a>篩選  
 當您呼叫<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=fullName>方法來連結來源與目標時，您可以提供委派用來決定目標區塊接受或拒絕該訊息的值為基礎的訊息。 篩選機制是確保資訊流程區塊只接收特定值的實用方式。 對於大部分預先定義的資料流程區塊類型而言，如果來源區塊連接到多個目標區塊，則當目標區塊拒絕訊息時，來源就會提供該訊息給下一個目標。 來源提供訊息給目標的順序是由該來源所定義，而且可能會根據該來源類型而有所不同。 大部分的來源區塊類型在目標接受訊息之後，就會停止提供訊息。 此規則的唯一例外是<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>類別，提供給所有的目標，每一個訊息，即使一些目標拒絕該訊息。 如需使用篩選來處理特定訊息的範例，請參閱[逐步解說︰ 在 Windows Form 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。  
  
> [!IMPORTANT]
>  由於每個預先定義來源資料流程區塊類型確保訊息都會按照收到訊息的順序來散佈，所以每個訊息都必須由來源區塊所讀取，之後來源區塊才可處理下一個訊息。 因此，當您使用篩選以連接多個目標至來源時，請確定至少有一個目標區塊會接收每一個訊息。 否則，您的應用程式可能會發生死結。  
  
### <a name="message-passing"></a>訊息傳遞  
 資料流程程式設計模型與相關的概念*訊息傳遞*，其中程式的獨立元件之間的通訊方式是傳送訊息。 應用程式元件之間散佈訊息的一種方式是呼叫<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>和<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=fullName>方法，以將訊息傳送到目標資料流程區塊通知 (<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>會同步動作;<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A>會非同步動作) 和<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>， <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>，和<xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A>方法來從來源區塊接收訊息。 您可以傳送輸入資料至管線的前端節點 (目標區塊)，並接收來自管線的終端節點或網路 (一個或多個來源區塊) 的終端節點之輸出資料，將這些方法結合資料流程管線或網路。 您也可以使用<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Choose%2A>方法來讀取從第一個具有可用資料，並在該資料上執行動作的提供來源。  
  
 來源區塊提供資料給目標區塊，藉由呼叫<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A?displayProperty=fullName>方法。 目標區塊對於所提供的訊息會採取三種回應之一：它可以接受該訊息、拒絕該訊息或延後該訊息。 當目標接受訊息， <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A>方法會傳回<xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus>。 當目標拒絕該訊息， <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A>方法會傳回<xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus>。 當目標要求它不再接收任何訊息來源的<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A>傳回<xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus>。 在接收這類傳回值之後，以及從這類目標自動取消連結之後，預先定義的來源區塊類型就不會傳遞訊息給連結的目標。  
  
 當目標區塊延後的訊息，供日後使用， <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A>方法會傳回<xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus>。 延後訊息的目標區塊可以稍後呼叫<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReserveMessage%2A?displayProperty=fullName>方法，嘗試保留所提供的訊息。 此時訊息仍為可用，而且可由目標區塊所使用，或者訊息已由另一個目標所採用。 當目標區塊稍後要求此訊息，或者不再需要訊息時，它會呼叫<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=fullName>或<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReleaseReservation%2A>方法中，分別。 訊息保留通常由在非窮盡模式下操作的資料流程區塊型別所使用。 本文稍後將說明非窮盡模式。 不保留已延後的訊息，目標區塊也可以使用<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=fullName>方法來嘗試直接使用延後的訊息。  
  
### <a name="dataflow-block-completion"></a>資料流程區塊的完成  
 資料流程區塊也支援的概念*完成*。 在已完成狀態中的資料流程區塊並不會執行任何進一步的工作。 每個資料流程區塊都有相關聯<xref:System.Threading.Tasks.Task?displayProperty=fullName>物件，稱為*完成工作*，表示區塊的完成狀態。 因為您可以等候<xref:System.Threading.Tasks.Task>物件來完成，請使用完成工作，您可以等候一個或完成的資料流程的多個終端節點的網路。 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock>介面會定義<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>方法，它會通知為其完成所要求的資料流程區塊，而<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A>屬性，會傳回資料流程區塊的完成工作。 同時<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>和<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>繼承<xref:System.Threading.Tasks.Dataflow.IDataflowBlock>介面。  
  
 有兩種方式用來判斷資料流程區塊是否完成而沒有錯誤，還是遇到一或多個錯誤或已取消。 第一種方式是呼叫<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName>方法中完成工作上的`try` - `catch`區塊 (`Try` - `Catch`在 Visual Basic 中)。 下列範例會建立<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件，則會擲回<xref:System.ArgumentOutOfRangeException>如果其輸入的值小於零。 <xref:System.AggregateException>時，這個範例會呼叫擲回<xref:System.Threading.Tasks.Task.Wait%2A>上完成工作。 <xref:System.ArgumentOutOfRangeException>存取透過<xref:System.AggregateException.InnerExceptions%2A>屬性<xref:System.AggregateException>物件。  
  
 [!code-csharp[TPLDataflow_Overview#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#10)]
 [!code-vb[TPLDataflow_Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#10)]  
  
 這個範例示範在執行資料流程區塊的委派中有例外狀況未受處理的案例。 建議您在這類區塊的主體中處理例外狀況。 然而，假如您無法這樣做，區塊會表現得就像已經取消，而不會處理傳入的訊息。  
  
 明確地取消資料流程區塊時<xref:System.AggregateException>物件包含<xref:System.OperationCanceledException>中<xref:System.AggregateException.InnerExceptions%2A>屬性。 如需取消資料流程的詳細資訊，請在文件稍後參閱＜啟用取消＞。  
  
 第二種判斷資料流程區塊完成狀態的方式為使用此完成工作的接續，或使用 C# 和 Visual Basic 的非同步語言功能來非同步等候此完成工作。 您所提供的委派<xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=fullName>方法會採用<xref:System.Threading.Tasks.Task>代表前項工作的物件。 如果是<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A>屬性，接續的委派會完成工作本身。 下列範例類似，不同之處在於它也會使用<xref:System.Threading.Tasks.Task.ContinueWith%2A>方法來建立列印整個資料流程作業的狀態完成工作。  
  
 [!code-csharp[TPLDataflow_Overview#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#11)]
 [!code-vb[TPLDataflow_Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#11)]  
  
 您也可以如使用屬性<xref:System.Threading.Tasks.Task.IsCanceled%2A>接續工作來判斷資料流程區塊的完成狀態的其他資訊的主體中。 如需接續工作，以及它們與取消和錯誤處理的詳細資訊，請參閱[使用接續工作鏈結工作](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)，[工作取消](../../../docs/standard/parallel-programming/task-cancellation.md)，[例外狀況處理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)，和[NIB: How to︰ 處理的例外狀況擲回的工作](http://msdn.microsoft.com/zh-tw/d6c47ec8-9de9-4880-beb3-ff19ae51565d)。  
  
 [[go to top](#top)]  
  
<a name="predefined_types"></a>   
## <a name="predefined-dataflow-block-types"></a>預先定義的資料流程區塊類型  
 TPL 資料流程程式庫提供幾種預先定義的資料流程區塊類型。 這些類型可分為三個類別︰*緩衝區塊*，*執行區塊*，和*群組區塊*。 下列章節描述組成這些類別的區塊類型。  
  
### <a name="buffering-blocks"></a>緩衝區塊  
 緩衝區塊保存供資料消費者使用的資料。 TPL 資料流程程式庫提供了三個緩衝區塊類型︰ <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=fullName>， <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601?displayProperty=fullName>，和<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601?displayProperty=fullName>。  
  
#### <a name="bufferblockt"></a>BufferBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>類別代表一般用途的非同步傳訊結構。 這個類別會儲存可由多個來源寫入或由多個目標讀取之訊息的先進先出 (FIFO) 佇列。 當目標收到來自訊息<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>物件，從訊息佇列中移除該訊息。 因此，雖然<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>物件可以有多個目標，只有一個目標就會收到每個訊息。 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>類別就很有用，當您想要將多個訊息傳遞至另一個元件，而該元件必須接收每個訊息。  
  
 下列的基本範例傳遞數個<xref:System.Int32>值<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>物件，然後從該物件讀取這些值。  
  
 [!code-csharp[TPLDataflow_Overview#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#1)]
 [!code-vb[TPLDataflow_Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#1)]  
  
 如需完整範例，示範如何將訊息寫入和讀取訊息的<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>物件，請參閱[如何︰ 寫入和讀取訊息從資料流程區塊](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)。  
  
#### <a name="broadcastblockt"></a>BroadcastBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>類別時，您必須將多個訊息傳遞至另一個元件，但該元件需要最新的值。 當您想要將訊息廣播至多個元件時，這個類別也很有用。  
  
 下列基本範例文章<xref:System.Double>值<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>物件，然後讀取該值從該物件數次。 由於值不會移除從<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>物件讀取之後，相同的值就可以每次。  
  
 [!code-csharp[TPLDataflow_Overview#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#2)]
 [!code-vb[TPLDataflow_Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#2)]  
  
 如需完整範例，示範如何使用<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>若要將訊息廣播至多個目標區塊，請參閱[How to︰ 在資料流程區塊中指定工作排程器](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)。  
  
#### <a name="writeonceblockt"></a>WriteOnceBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>類別類似於<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>類別，但是<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>物件只能被寫入一次。 您可以將<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>視為類似 C# [readonly](../Topic/readonly%20\(C%23%20Reference\).md) ([ReadOnly](../Topic/ReadOnly%20\(Visual%20Basic\).md)中[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 關鍵字，只<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>接收值，而不是在建構後，物件會變成不變。 像<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>類別，當目標收到來自訊息<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>物件，該訊息不會從該物件中移除。 因此，多個目標會接收此訊息的複本。 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>類別就很有用，當您想要傳播的多個訊息的第一個。  
  
 下列的基本範例傳遞多個<xref:System.String>值<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>物件，然後讀取值從該物件。 因為<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>物件只能寫入一次之後, <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>物件收到訊息時，它會捨棄後續訊息。  
  
 [!code-csharp[TPLDataflow_Overview#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#3)]
 [!code-vb[TPLDataflow_Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#3)]  
  
 如需完整範例，示範如何使用<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>接收值的第一個完成的作業，請參閱[如何︰ 取消連結資料流程區塊](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)。  
  
### <a name="execution-blocks"></a>執行區塊  
 執行區塊會為已接受資料的每個部分呼叫使用者提供的委派。 TPL 資料流程程式庫提供三個執行區塊類型︰ <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>， <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=fullName>，和<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=fullName>。\</TInput, TOutput> \</TInput, TOutput>  
  
#### <a name="actionblockt"></a>ActionBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>類別是接收資料時呼叫委派的目標區塊。 想像成<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件做為資料可供使用時以非同步方式執行委派。 您所提供的委派<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件可以是類型<xref:System.Action>或型別`System.Func\<TInput, Task>`。 當您使用<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件<xref:System.Action>，每個輸入項目的處理視為完成委派傳回時。 當您使用<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件`System.Func\<TInput, Task>`，會將每個輸入項目的處理視為已完成的時，才傳回<xref:System.Threading.Tasks.Task>物件已完成。 藉由使用這兩種機制，您可以使用<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>同步和非同步處理的每個輸入項目。  
  
 下列的基本範例傳遞多個<xref:System.Int32>值<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件。 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件列印到主控台的這些值。 這個範例接著會設定此區塊為完成狀態，並等候所有資料流程工作完成。  
  
 [!code-csharp[TPLDataflow_Overview#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#4)]
 [!code-vb[TPLDataflow_Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#4)]  
  
 完整的範例，示範如何使用委派的方式<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>類別，請參閱[How to︰ 執行動作時資料流程區塊收到資料](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)。  
  
#### <a name="transformblocktinput-toutput"></a>TransformBlock(TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>類別類似於<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>類別中，不同之處在於它可同時做為來源和目標。\</TInput, TOutput> 您傳遞給委派<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>物件會傳回型別的值`TOutput`。</TInput, TOutput> 您所提供的委派<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>物件可以是類型`System.Func<TInput, TOutput>`或型別`System.Func<TInput, Task>`。\</TInput, TOutput> 當您使用<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>物件`System.Func\<TInput, TOutput>`，每個輸入項目的處理視為完成委派傳回時。</TInput, TOutput> 當您使用<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>物件搭配`System.Func<TInput, Task<TOutput>>`，會將每個輸入項目的處理視為已完成的時，才傳回<xref:System.Threading.Tasks.Task>物件已完成。\</TInput, TOutput> 如同<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>，藉由使用這兩種機制，您可以使用<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>同步和非同步處理的每個輸入項目。\</TInput, TOutput>  
  
 下列基本範例會建立<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>物件，會計算其輸入的平方根。</TInput, TOutput> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>物件會<xref:System.Int32>值做為輸入，並產生<xref:System.Double>值做為輸出。\</TInput, TOutput>  
  
 [!code-csharp[TPLDataflow_Overview#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#5)]
 [!code-vb[TPLDataflow_Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#5)]  
  
 完整範例，如<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>在執行映像處理 Windows Form 應用程式中的資料流程區塊網路，請參閱[逐步解說︰ 在 Windows Form 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)。\</TInput, TOutput>  
  
#### <a name="transformmanyblocktinput-toutput"></a>TransformManyBlock(TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>類別類似於<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>類別，但是<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>會產生零個或多個輸出值，每個輸入值，而不是只有一個輸入的每個值的值。</TInput, TOutput> </TInput, TOutput> </TInput, TOutput> 您所提供的委派<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>物件可以是類型`System.Func<TInput, IEnumerable<TOutput>>`或`type System.Func<TInput, Task<IEnumerable<TOutput>>>`。\</TInput, TOutput> 當您使用<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>物件`System.Func<TInput, IEnumerable<TOutput>>`，每個輸入項目的處理視為完成委派傳回時。</TInput, TOutput> 當您使用<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>物件`System.Func<TInput, Task<IEnumerable<TOutput>>>`，會將每個輸入項目的處理視為完成時，才傳回`System.Threading.Tasks.Task<IEnumerable<TOutput>>`物件已完成。\</TInput, TOutput>  
  
 下列基本範例會建立<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>將字串分割成其個別的字元序列的物件。</TInput, TOutput> <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>物件會<xref:System.String>值做為輸入，並產生<xref:System.Char>值做為輸出。\</TInput, TOutput>  
  
 [!code-csharp[TPLDataflow_Overview#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#6)]
 [!code-vb[TPLDataflow_Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#6)]  
  
 如需使用的完整範例<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>產生多個獨立的輸出，每個輸入的資料流程管線，請參閱[逐步解說︰ 建立資料流程管線](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)。\</TInput, TOutput>  
  
#### <a name="degree-of-parallelism"></a>平行處理原則的刻度  
 每個<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>， <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>，和<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>物件會緩衝輸入訊息，直到此區塊已準備好處理它們。</TInput, TOutput> </TInput, TOutput> 這些類別預設會按照接收到訊息的順序，一次處理一個訊息。 您也可以指定要啟用的平行處理原則程度<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>， <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>和<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>同時處理多個訊息的物件。\</TInput, TOutput> \</TInput, TOutput> 如需同時執行的詳細資訊，請參閱本文稍後的＜指定平行處理原則的刻度＞一節。 如需設定以啟用執行資料流程區塊一次處理多個訊息的平行處理原則程度的範例，請參閱[How to︰ 在資料流程區塊中指定平行處理原則刻度](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)。  
  
#### <a name="summary-of-delegate-types"></a>委派類型摘要  
 下表摘要說明您可以提供給委派型別<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>， <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>，和<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>物件。\</TInput, TOutput> \</TInput, TOutput> 表中也會指出委派類型是以同步或非同步方式運作。  
  
|類型|同步委派類型|非同步委派類型|  
|----------|-------------------------------|--------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|`System.Action`|`System.Func\<TInput, Task>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602></TInput, TOutput>|`System.Func\<TInput, TOutput>`2`|`System.Func<TInput, Task<TOutput>>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602></TInput, TOutput>|`System.Func<TInput, IEnumerable<TOutput>>`|`System.Func<TInput, Task<IEnumerable<TOutput>>>`|  
  
 當您使用執行區塊類型時，也可以使用 Lambda 運算式。 如需示範如何搭配執行區塊使用 lambda 運算式的範例，請參閱[How to︰ 執行動作時資料流程區塊收到資料](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)。  
  
### <a name="grouping-blocks"></a>群組區塊  
 群組區塊合併來自一個或多個來源、以及在各種條件約束下的資料。 TPL 資料流程程式庫提供三個聯結區塊類型︰ <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>， <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>，和<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>。\</T1, T2> \</T1, T2>  
  
#### <a name="batchblockt"></a>BatchBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>類別會結合到輸出資料的陣列稱為批次中的輸入資料集。 在建立時指定的每個批次大小<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件。 當<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件收到指定的輸入項目計數時，會非同步散佈包含這些項目的陣列。 如果<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件設定為已完成狀態，但未包含足夠構成批次的項目，則會散佈包含剩餘輸入項目的最後一個陣列。  
  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>類別會在*窮盡*或*非窮盡*模式。 在窮盡模式，這是預設值， <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件接受每個訊息，它會提供與它接收到指定的項目計數後散佈陣列。 在非窮盡模式下， <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件延後所有傳入訊息，直到足夠來源提供給區塊構成批次的訊息。 因為窮盡模式需要較少的處理額外負荷，通常其效能優於非窮盡模式。 不過，在您必須以不可部分完成的方式協調來自多個來源之消耗時，可以使用非窮盡模式。 設定指定非窮盡模式<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A>至`False`中`dataflowBlockOptions`中的參數<xref:System.Threading.Tasks.Dataflow.BatchBlock%601.%23ctor%2A>建構函式。  
  
 下列的基本範例傳遞數個<xref:System.Int32>值<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>批次中保存十個項目物件。 若要保證所有的值傳播超出<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>，這個範例會呼叫<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>方法。 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>方法會設定<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件已完成的狀態，因此<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件做為最後一個批次會散佈任何其餘的項目。  
  
 [!code-csharp[TPLDataflow_Overview#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#7)]
 [!code-vb[TPLDataflow_Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#7)]  
  
 如需完整的範例使用<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>改善資料庫插入作業的效率，請參閱[逐步解說︰ 使用 BatchBlock 和 BatchedJoinBlock 以改善效率](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)。  
  
#### <a name="joinblockt1-t2-"></a>JoinBlock(T1, T2, ...)  
 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>和<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>類別會收集輸入項目，並向外傳播<xref:System.Tuple%602?displayProperty=fullName>或<xref:System.Tuple%603?displayProperty=fullName>包含這些項目的物件。\</T1, T2, T3> \</T1, T2> \</T1, T2, T3> \</T1, T2> <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>和<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>類別不是繼承自<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>。</T1, T2, T3> </T1, T2> 相反地，它們提供的屬性， <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target1%2A>， <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target2%2A>，和<xref:System.Threading.Tasks.Dataflow.JoinBlock%603.Target3%2A>，實作<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>。  
  
 像<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>， <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>和<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>在窮盡或非窮盡模式下運作。</T1, T2, T3> </T1, T2> 在窮盡模式，這是預設值， <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>或<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>物件接受每個訊息，它會提供和其每個目標接收至少一個訊息之後散佈 tuple。</T1, T2, T3> </T1, T2> 在非窮盡模式下， <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>或<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>物件延後所有傳入訊息，直到已提供所有的目標建立 tuple 所需的資料。\</T1, T2, T3> \</T1, T2> 此時，該區塊會使用兩階段認可通訊協定，從來源以不可分割方式擷取所有必要的項目。 這項延遲使得其他實體可以同時使用資料，讓整個系統繼續進行。  
  
 下列基本範例示範的案例<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>物件需要多個資料來計算值。</T1, T2, T3> 這個範例會建立<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>需要兩個物件<xref:System.Int32>值和<xref:System.Char>值來執行算術運算。\</T1, T2, T3>  
  
 [!code-csharp[TPLDataflow_Overview#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#8)]
 [!code-vb[TPLDataflow_Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#8)]  
  
 如需完整的範例使用<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>物件在非窮盡模式下以合作方式共用資源，請參閱[How to︰ 使用 JoinBlock 從來源讀取資料多個](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)。\</T1, T2>  
  
#### <a name="batchedjoinblockt1-t2-"></a>BatchedJoinBlock(T1, T2, ...)  
 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>和<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%603>類別會收集批次的輸入項目，並向外傳播`System.Tuple(IList(T1), IList(T2))`或`System.Tuple(IList(T1), IList(T2), IList(T3))`包含這些項目的物件。\</T1, T2, T3> \</T1, T2> 想像成<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>的組合為<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>和<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>。</T1, T2> </T1, T2> 在建立時指定的每個批次大小<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>物件。\</T1, T2> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>也提供屬性， <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A>和<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>，實作<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>。\</T1, T2> 當指定的輸入項目計數會收到來自所有目標， <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>物件非同步散佈`System.Tuple(IList(T1), IList(T2))`物件，其中包含這些項目。\</T1, T2>  
  
 下列基本範例會建立<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>物件，其中保存結果， <xref:System.Int32>值和錯誤<xref:System.Exception>物件。</T1, T2> 此範例執行多項作業，並將寫入結果<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A>屬性，而且錯誤<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>屬性的<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>物件。\</T1, T2> 因為事先是未知的成功和失敗的作業計數<xref:System.Collections.Generic.IList%601>物件可讓每個目標接收零或多個值。  
  
 [!code-csharp[TPLDataflow_Overview#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#9)]
 [!code-vb[TPLDataflow_Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#9)]  
  
 如需完整的範例使用<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>擷取結果和程式從資料庫讀取時所發生的任何例外狀況，請參閱[逐步解說︰ 使用 BatchBlock 和 BatchedJoinBlock 以改善效率](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)。\</T1, T2>  
  
 [[go to top](#top)]  
  
<a name="behavior"></a>   
## <a name="configuring-dataflow--block-behavior"></a>設定資料流程區塊行為  
 您可以藉由啟用其他選項<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=fullName>資料流程區塊類型建構函式的物件。 這些選項可控制行為，例如會管理基礎工作和平行處理原則刻度的排程器。 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>也有衍生的類型指定某些資料流程區塊類型特定的行為。 下表摘要說明與各資料流程區塊類型相關聯的選項類型。  
  
|資料流程區塊類型|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>類型|  
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>\</TInput, TOutput>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>\</TInput, TOutput>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>\</T1, T2>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>\</T1, T2>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
  
 下列各節提供的額外資訊的重要的一種資料流程區塊選項可透過使用<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=fullName>， <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions?displayProperty=fullName>，和<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions?displayProperty=fullName>類別。  
  
### <a name="specifying-the-task-scheduler"></a>指定工作排程器  
 每個預先定義的資料流程區塊使用 TPL 工作排程機制來執行活動，例如當資料可用時散佈資料至目標、接收來自來源的資料和執行使用者定義的委派。 <xref:System.Threading.Tasks.TaskScheduler>是抽象類別代表的工作排程器執行緒到工作排入佇列。 預設工作排程器<xref:System.Threading.Tasks.TaskScheduler.Default%2A>，會使用<xref:System.Threading.ThreadPool>排入佇列，和執行工作的類別。 您可以藉由設定覆寫預設工作排程器<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A>屬性在建構資料流程區塊物件時。  
  
 在同一個工作排程器管理多個資料流程區塊時，它可以跨區塊強制執行原則。 例如，如果多個資料流程區塊分別設定為目標的相同獨佔排程器<xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>物件時，皆可運作，跨區塊執行會進行序列化。 同樣地，如果這些區塊設定為目標的相同的並行排程器<xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>物件，而該排程器設定為具有最大並行層級，則來自這些區塊的所有工作都僅限於並行作業的數字。 如需範例，會使用<xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>類別，讓讀取的作業平行進行，但寫入作業專用的所有其他作業就會發生，請參閱[How to︰ 在資料流程區塊中指定工作排程器](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)。 如需 TPL 中的工作排程器的詳細資訊，請參閱<xref:System.Threading.Tasks.TaskScheduler>類別主題。  
  
### <a name="specifying-the-degree-of-parallelism"></a>指定平行處理原則的刻度  
 根據預設，TPL 資料流程程式庫提供三個執行區塊類型<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>， <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>，和<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>，每次處理一個訊息。\</TInput, TOutput> \</TInput, TOutput> 這些資料流程區塊類型也都會按照接收到訊息的順序處理訊息。 若要讓這些資料流程區塊同時處理訊息，請設定<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=fullName>屬性在建構資料流程區塊物件時。  
  
 預設值的<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>是 1，以保證資料流程區塊一次處理一個訊息。 設定此屬性為大於 1 的值可讓資料流程區塊同時處理多個訊息。 此屬性設定為<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=fullName>可讓基礎的工作排程器，來管理並行存取的最大程度。  
  
> [!IMPORTANT]
>  當您指定大於 1 的最大平行處理原則刻度時，會同時處理多個訊息，因此訊息可能不會依照接收到的順序處理。 然而，從該區塊輸出訊息的順序會正確地排列。  
  
 因為<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>屬性表示平行處理原則的最大程度，資料流程區塊可能比您指定執行的平行處理原則程度較小者。 資料流程區塊可能使用較低刻度的平行處理以符合其功能需求，或者是因為缺乏可用的系統資源。 資料流程區塊絕不選擇高於您所指定的平行處理。  
  
 值<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>屬性是專為每個資料流程區塊物件。 例如，如果四個資料流程區塊物件每一個都為平行處理原則的最大刻度指定為 1，則全部四個資料流程區塊物件都可以平行執行。  
  
 如需設定平行處理原則，以讓長時間作業平行處理的最大程度的範例，請參閱[How to︰ 在資料流程區塊中指定平行處理原則刻度](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)。  
  
### <a name="specifying-the-number-of-messages-per-task"></a>指定每項工作的訊息數量  
 預先定義的資料流程區塊類型使用工作以處理多個輸入項目。 這有助於減少被要求處理資料的工作物件數目，使得應用程式更有效率地執行。 不過，當來自一組工作資料流程區塊的工作正在處理資料時，來自其他資料流程區塊的工作可能需要將訊息加入佇列來等候處理時間。 若要啟用更好的公平性之間的資料流程工作， <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>屬性。 當<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>設為<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=fullName>、 預設、 資料流程區塊所用的工作處理可用的訊息。 當<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>以外的其他設定值為<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded>，資料流程區塊最多處理每個訊息的這個數字<xref:System.Threading.Tasks.Task>物件。 雖然設定<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>屬性可提高工作之間的公平性，它可能會造成系統建立更多的工作比必要的這可能會降低效能。  
  
### <a name="enabling-cancellation"></a>啟用取消  
 TPL 提供一種讓工作以合作方式協調取消的機制。 若要讓資料流程區塊參與此取消機制，請設定<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>屬性。 當這<xref:System.Threading.CancellationToken>物件設定為 已取消狀態時，所有監視此語彙基元的資料流程區塊完成執行其目前的項目，但不是開始處理後續項目。 這些資料流程區塊也會清除任何緩衝訊息，釋放連結給任何來源區塊和目標區塊，並轉換為取消狀態。 轉換成已取消狀態，<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A>屬性具有<xref:System.Threading.Tasks.Task.Status%2A>屬性設定為<xref:System.Threading.Tasks.TaskStatus>，除非您在處理期間發生例外狀況。 在此情況下，<xref:System.Threading.Tasks.Task.Status%2A>設為<xref:System.Threading.Tasks.TaskStatus>。  
  
 如需示範如何在 Windows Form 應用程式中使用取消的範例，請參閱[如何︰ 取消資料流程區塊](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)。 如需 TPL 中取消的詳細資訊，請參閱[工作取消](../../../docs/standard/parallel-programming/task-cancellation.md)。  
  
### <a name="specifying-greedy-versus-non-greedy-behavior"></a>指定窮盡與非窮盡的行為  
 許多群組資料流程區塊類型可以在其中運作*窮盡*或*非窮盡*模式。 預先定義的資料流程區塊類型預設會在窮盡模式下運作。  
  
 對於聯結區塊類型例如<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>，窮盡模式表示即使對應要聯結的資料尚無法使用，該區塊立即接受資料。</T1, T2> 非窮盡模式則表示區塊會延後處理所有傳入訊息，直到其中之一在其每個目標上可用於完成聯結。 如果任何延後的訊息皆不再可用，則聯結區塊會釋出所有延後的訊息，並重新啟動此程序。 如<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>類別，窮盡和非窮盡的行為會類似，但是在非窮盡模式下， <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件延後所有傳入訊息，直到足夠可用來自不同來源，以完成批次。  
  
 若要指定非窮盡模式資料流程區塊，請設定<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A>到`False`。 如需示範如何使用非窮盡模式，讓多個聯結區塊更有效率地共用資料來源的範例，請參閱[How to︰ 使用 JoinBlock 從來源讀取資料多個](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)。  
  
 [[go to top](#top)]  
  
<a name="custom"></a>   
## <a name="custom-dataflow-blocks"></a>自訂資料流程區塊  
 雖然 TPL 資料流程程式庫提供許多預先定義的區塊類型，但您可以建立會執行自訂行為的其他區塊類型。 實作<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>或<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>介面直接或使用<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>方法來建立封裝的現有區塊類型行為的複雜區塊。\</TInput, TOutput> 如需示範如何實作自訂資料流程區塊功能的範例，請參閱[逐步解說︰ 建立自訂資料流程區塊類型](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)。  
  
 [[go to top](#top)]  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[如何︰ 將訊息寫入及讀取資料流程區塊中的訊息](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)|示範如何將訊息寫入和讀取訊息的<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>物件。|  
|[How to︰ 實作生產者-消費者資料流程模式](../../../docs/standard/parallel-programming/how-to-implement-a-producer-consumer-dataflow-pattern.md)|描述如何使用此資料流程模型以實作生產者-消費者模式，其中生產者傳送訊息至資料流程區塊，而消費者從該區塊讀取訊息。|  
|[如何︰ 在資料流程區塊收到資料時執行動作](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)|描述如何提供委派給執行資料流程區塊類型， <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>， <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>，和<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>。\</TInput, TOutput> \</TInput, TOutput>|  
|[逐步解說︰ 建立資料流程管線](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)|描述如何建立可以從網路下載文字並對該文字執行作業的資料流程管線。|  
|[如何︰ 取消連結資料流程區塊](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)|示範如何使用<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>來源提供目標訊息之後，中斷連結目標區塊與其來源的方法。|  
|[逐步解說︰ 在 Windows Form 應用程式中使用資料流程](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)|示範如何建立資料流程區塊網路，其可以在 Windows Form 應用程式中執行影像處理。|  
|[如何︰ 取消資料流程區塊](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)|示範如何在 Windows Form 應用程式中使用取消。|  
|[如何︰ 使用 JoinBlock 從多個來源讀取資料](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)|說明如何使用<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>資料可從多個來源，以及如何使用非窮盡模式，讓多個聯結區塊更有效率地共用資料來源時執行作業的類別。\</T1, T2>|  
|[如何︰ 在資料流程區塊中指定平行處理原則程度](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)|描述如何設定<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>屬性，讓執行資料流程區塊一次處理一個以上的訊息。|  
|[如何︰ 在資料流程區塊中指定工作排程器](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)|示範當您在應用程式中使用資料流程時，要如何與特定工作排程器建立關聯。|  
|[逐步解說︰ 使用 BatchBlock 和 BatchedJoinBlock 以改善效率](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)|描述如何使用<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>類別來改善效率的資料庫插入作業，以及如何使用<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>類別來擷取結果和程式從資料庫讀取時所發生的任何例外狀況。\</T1, T2>|  
|[逐步解說︰ 建立自訂資料流程區塊類型](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)|示範建立會實作自訂行為的資料流程區塊類型之兩種方式。|  
|[工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|介紹 TPL，一種在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 應用程式中簡化平行和並行程式設計的程式庫。|