---
title: "如何：使用屏障同步處理並行作業"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>如何：使用屏障同步處理並行作業
下列範例示範如何同步處理並行的工作與<xref:System.Threading.Barrier>。  
  
## <a name="example"></a>範例  
 下列程式的目的是方案的，計算多少反覆項目 （或階段） 所需的每個尋找兩個執行緒及其半 「 相同 」 階段使用 randomizing 演算法 reshuffle 單字。 每個執行緒有打散其文字之後，屏障的後續階段作業會比較兩個結果，以查看完整的句子若已呈現正確的字順序。  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A<xref:System.Threading.Barrier>是可防止平行作業無法繼續，直到所有工作都到達屏障中的個別工作的物件。 會很有用時，平行作業中階段，就必須同步處理工作之間，每個階段。 在此範例中，有兩個階段作業。 在第一個階段中，每項工作會填滿的緩衝區的資料 > 一節。 每個工作完成時填入 > 一節，工作會表示屏障可準備好繼續進行，然後等候。 所有工作有收到都信號時屏障，它們會解除封鎖，第二個階段開始。 屏障是必要的因為第二個階段需要每個工作有已產生到這個點的存取權的所有資料。 屏障沒有完成的第一個工作可能會嘗試從已不填入尚未由其他工作的緩衝區讀取。 您可以將任意數目的階段以這種方式同步處理。  
  
## <a name="see-also"></a>另請參閱  
 [適用於平行程式設計的資料結構](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
