---
title: "How to: Use JoinBlock to Read Data From Multiple Sources | Microsoft Docs"
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
  - "TPL dataflow library, joining blocks in"
  - "dataflow blocks, joining in TPL"
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Use JoinBlock to Read Data From Multiple Sources
當資料來源時，可取得這份文件說明如何使用 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 類別執行作業。  它也示範如何使用非窮盡聯結的方式以啟用多重聯結區塊而更有效率地共用資料來源的範例。  
  
> [!TIP]
>  TPL 資料流程式庫 \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 命名空間\) 並沒有和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 配置在一起。  若要安裝 <xref:System.Threading.Tasks.Dataflow> 命名空間，請在 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 中開啟您的專案，從 \[專案\] 功能表中選擇 \[**管理 NuGet 封裝**\]，並且線上搜尋 `Microsoft.Tpl.Dataflow` 封裝。  
  
## 範例  
 當資源可供使用時，下列範例定義三個資源類型、 `NetworkResource`、 `FileResource`和 `MemoryResource`，以及執行作業。  這個範例需要名為的 `NetworkResource` 和 `MemoryResource` 為執行第一個作業和 `FileResource` 和 `MemoryResource` 為執行第二個作業。  使這些作業發生時，所有必要的資源可用，這個範例會使用 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 類別。  當 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件接收來自任何來源中的資料時，它會傳送資料至其目標，在此例中為 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。  從 `MemoryResource` 共用集區讀取的兩個 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件。  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 若要讓 `MemoryResource` 物件共用集區的有效使用，這個範例會指定將 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> 屬性設定為 `False` 建立 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件在非窮盡模式下執行之動作的 <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> 物件。  非窮盡聯結區塊將所有傳入訊息，直到其中一個從每個來源中取得。  如果任何延後訊息由其他區塊接受，聯結區塊重新啟動處理序。  非窮盡模式啟用聯結共用一個或更多來源區塊取得順向進度的區塊，而其他區塊等待資料。  在此範例中，如果 `MemoryResource` 物件加入至 `memoryResources` 的集區，第一個聯結區塊收到第二個資料來源可以取得順向進度。  如果這個範例是使用窮盡模式，也就是預設值，會將區塊可能採用 `MemoryResource` 物件並等待第二個資源可供使用。  不過，如果其他聯結區塊都有自己的第二個資料來源可用就無法取得順向進度，因為 `MemoryResource` 物件由其他採用聯結區塊。  
  
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為  `DataflowNonGreedyJoin.cs`的檔案中 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 `DataflowNonGreedyJoin.vb` \) ，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## 穩固程式設計  
 使用非窮盡聯結也可以協助您避免在應用程式中的死結。  在軟體應用程式中，如果有兩個以上的處理序各擁有一項資源，而互相等候另一個處理序釋放另一項資源，即會發生「*死結*」\(Deadlock\)。  考量的應用程式定義兩個 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> 物件。  兩個物件都讀取從兩個共用來源區塊中的資料。  在窮盡模式，如果有一個關聯的區塊是第一個來源讀取，而第二個聯結區塊是第二個來源讀取，應用程式可能會發生死結，因為兩個聯結區塊互相等候其他釋放其資源。  在非窮盡模式，其中每個聯結區塊會從來源讀取，只有在所有資料可用時，因此會消除死結的風險。  
  
## 請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)