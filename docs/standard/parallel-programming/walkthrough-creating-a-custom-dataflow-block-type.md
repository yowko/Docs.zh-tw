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
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>逐步解說：建立自訂資料流程區塊類型
雖然 TPL 資料流程式庫提供數個資料流程區塊類型，可讓各種不同的功能，但是您也可以建立自訂的區塊類型。 本文件說明如何建立會實作自訂行為的資料流程區塊類型。  
  
## <a name="prerequisites"></a>必要條件  
 讀取[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)閱讀這份文件之前。  
  
> [!TIP]
>  TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。 若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。  
  
## <a name="defining-the-sliding-window-dataflow-block"></a>定義滑動視窗資料流程區塊  
 請考慮要求輸入的值必須緩衝處理，並接著在滑動視窗的方式輸出的資料流程應用程式。 例如，{0、 1、 2、 3、 4，5} 的輸入的值和視窗大小為三個，滑動視窗資料流程區塊會產生輸出陣列 {0，1，2}，{1，2，3}，{2，3，4} 和 {3，4，5}。 下列各節說明兩種方式可建立會實作這個自訂行為的資料流程區塊類型。 第一種技術會使用<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>方法來結合的功能<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>物件和<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>成一個傳播程式區塊的物件。 第二項技術會定義一個類別，衍生自<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>和結合現有的功能來執行自訂行為。  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>使用封裝來定義滑動視窗資料流程區塊的方法  
 下列範例會使用<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>方法來建立從目標及資料來源的傳播程式區塊。 傳播程式區塊可讓來源區塊和目標區塊做為收件者和寄件者的資料。  
  
 當您需要自訂的資料流程功能，但您不需要提供額外的方法、 屬性或欄位的類型時，這個技術非常有用。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>衍生自 IPropagatorBlock 定義滑動視窗資料流程區塊  
 下列範例所示`SlidingWindowBlock`類別。 此類別衍生自<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>，讓它可以做為來源和目標的資料。 如同先前的範例，`SlidingWindowBlock`類別建置在現有的資料流程區塊類型。 不過，`SlidingWindowBlock`類別也會實作所需的方法<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>， <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>，和<xref:System.Threading.Tasks.Dataflow.IDataflowBlock>介面。 向前復原所有這些方法將工作加入預先定義的資料流程區塊類型成員。 例如，`Post`方法會延後到工作`m_target`資料成員，這也是<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>物件。  
  
 當您需要自訂的資料流程功能，然後也需要提供額外的方法、 屬性或欄位的類型時，這個技術非常有用。 例如，`SlidingWindowBlock`類別也衍生自<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>，讓它能夠提供<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>和<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A>方法。 `SlidingWindowBlock`類別也會示範擴充性提供`WindowSize`屬性，擷取滑動視窗中的項目數目。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>完整範例  
 下列範例將示範本逐步解說的完整程式碼。 它也會示範如何使用這兩個滑動視窗區塊中的方法，將區塊寫入、 讀取它，會列印到主控台的結果。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`SlidingWindowBlock.cs`(`SlidingWindowBlock.vb`如[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  
  
## <a name="next-steps"></a>後續步驟  
  
## <a name="see-also"></a>另請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
