---
title: 如何：為靜態分割實作 Partitioner
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8de4884c43b99c50313d33f683d8634d12043c59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>如何：為靜態分割實作 Partitioner
下列範例示範如何為執行靜態分割的 PLINQ 實作簡單的自訂 Partitioner。 Partitioner 不支援動態分割，因此無法從 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 中使用。 對於每個元素需要增加處理時間量的資料來源，這個特定 Partitioner 的執行速度可能會比預設的範圍 Partitioner 來得快。  
  
## <a name="example"></a>範例  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 對於此範例中的分割區，我們假設每個元素的處理時間以線性增加。 在真實世界中，可能很難以這種方式來預測處理時間。 如果您正在使用包含特定資料來源的靜態 Partitioner，您可以最佳化來源的分割公式、加入負載平衡邏輯，或使用[如何： 實作動態分割](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)中示範的區塊分割方法。  
  
## <a name="see-also"></a>請參閱  
 [PLINQ 和 TPL 的自訂 Partitioner](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
