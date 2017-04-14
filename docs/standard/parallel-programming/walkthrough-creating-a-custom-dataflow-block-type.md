---
title: "Walkthrough: Creating a Custom Dataflow Block Type | Microsoft Docs"
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
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, creating custom dataflow blocks"
  - "dataflow blocks, creating custom in TPL"
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Walkthrough: Creating a Custom Dataflow Block Type
雖然 TPL 資料流程式庫提供各種功能的幾個資料流程區塊類型，您也可以建立自訂區塊類型。  本文件說明如何建立實作自訂行為區塊類型的資料流。  
  
## 必要條件  
 閱讀文件，請參閱 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) 。  
  
> [!TIP]
>  TPL 資料流程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並沒有和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 配置在一起。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[**管理 NuGet 封裝**\]，並且線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
## 定義滑動視窗資料流程區塊。  
 考慮要求的資料流應用程式輸入值被緩衝區然後輸出以滑動視窗模式。  例如，如果輸入值{0， 1， 2， 3， 4， 5}和視窗大小的第三個，滑動視窗資料流程區塊產生輸出陣列{0， 1， 2}， {1， 2， 3}， {2， 3， 4}，和{3， 4， 5}。  下列章節將說明兩種方式可以建立實作自訂行為區塊類型的資料流。  第一種技巧是使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> 方法將 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 物件和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 物件的功能將會傳回者區塊。  第二種技術定義衍生自 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> 並合併現有功能執行自訂行為的類別。  
  
## 使用定義封裝的方法滑動視窗資料流程區塊。  
 下列範例會使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> 方法從目標和來源的宣告會者區塊。  會傳回者區塊使來源區塊和目標區塊當做資料接收者和寄件者。  
  
 這項技術會很有用，在您需要自訂資料流功能時，不過，您不需要提供其他的方法、屬性或欄位的型別。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## 從 IPropagatorBlock 定義滑動視窗資料流程區塊的衍生  
 下列範例會示範 `SlidingWindowBlock` 類別。  這個類別衍生自 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> ，以做為來源資料物件。  在上述範例中， `SlidingWindowBlock` 類別在現有資料流程區塊類型所建立。  不過， `SlidingWindowBlock` 類別也會實作 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>和 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> 介面所需的方法。  這些方法為預先定義的資料流程區塊型別成員的所有向前工作。  例如， `Post` 方法將工作指派給 `m_target` 資料成員，也就是 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 物件。  
  
 這項技術會很有用，在您需要自訂資料流功能時，且需要提供其他的方法、屬性或欄位的型別。  例如， `SlidingWindowBlock` 類別也會從 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> 衍生，以便提供 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 和 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> 方法。  `SlidingWindowBlock` 類別會提供 `WindowSize` 屬性也示範擴充性，擷取項目的數目在滑動視窗的。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## 完整的範例  
 下列範例顯示完整程式碼。  它會在區塊中撰寫，讀取，並列印結果至主控台的方法也示範如何使用兩個滑動視窗區塊。  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `SlidingWindowBlock.cs`的檔案中 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 `SlidingWindowBlock.vb` \) ，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  
  
## 後續步驟  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)