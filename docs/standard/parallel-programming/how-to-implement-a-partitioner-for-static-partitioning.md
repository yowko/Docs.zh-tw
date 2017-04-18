---
title: "How to: Implement a Partitioner for Static Partitioning | Microsoft Docs"
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
  - "tasks, how to create a static partitioner"
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# How to: Implement a Partitioner for Static Partitioning
下列範例示範其中一種實作 PLINQ 的簡單自訂 Partitioner，以執行靜態分割的方式。  因為 Partitioner 並不支援動態磁碟分割，所以無法從 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 使用 Partitioner。  對於每個項目都需要增加處理時間的資料來源，這個特定的 Partitioner 可提供比預設定界 Partitioner 更佳的加速效果。  
  
## 範例  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 這個範例中的磁碟分割假設每個項目都會讓處理時間線性遞增。  在真實世界中，則很難以此方式預測處理時間。  如果您要將靜態 Partitioner 用於特定資料來源，可以針對該來源將分割公式最佳化、加入負載平衡邏輯，或使用 [How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)中所示範的區塊分割 \(Chunk Partitioning\) 方法。  
  
## 請參閱  
 [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)