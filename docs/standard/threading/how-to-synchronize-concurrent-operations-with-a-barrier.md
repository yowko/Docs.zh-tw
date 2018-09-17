---
title: 如何：使用屏障同步處理並行作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dc60fa9cd8782efbe1b6028413138b5991839e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45624836"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>如何：使用屏障同步處理並行作業
下列範例示範如何使用 <xref:System.Threading.Barrier> 同步處理並行工作。  
  
## <a name="example"></a>範例  
 下列程式的目的是計算兩個執行緒需要多少反覆項目 (或階段)，才能讓兩者透過使用隨機演算法重新排列文字，來找到其另外一半的解決方案。 在各執行緒打散其文字之後，屏障的後續階段作業會比較兩個結果，以查看完整的句子是否已以正確的文字順序顯示。  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <xref:System.Threading.Barrier> 是一種物件，可防止平行作業中的個別工作繼續執行，直到所有的工作都到達屏障為止。 當階段中發生平行作業，且各階段要求在工作之間進行同步處理時，它會很有用。 在此範例中，作業有兩個階段。 在第一個階段中，每個工作都會使用資料填入其緩衝區區段。 當每個工作完成填入其區段時，工作會向屏障發出訊號，告知它已準備好繼續進行，然後等候。 當所有的工作都已向屏障發出訊號，就會將工作解除封鎖，並開始第二階段。 屏障是必要的，因為第二階段要求每個工作都擁有此點已產生之所有資料的存取權。 若沒有屏障，第一個要完成的工作可能會嘗試從其他工作尚未填入的緩衝區讀取。 您可以此種方式同步處理任何數目的階段。  
  
## <a name="see-also"></a>另請參閱

- [適用於平行程式設計的資料結構](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
