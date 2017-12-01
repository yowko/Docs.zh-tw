---
title: "如何：使用 SpinWait 實作兩階段等候作業"
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
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>如何：使用 SpinWait 實作兩階段等候作業
下列範例示範如何使用<xref:System.Threading.SpinWait?displayProperty=nameWithType>來實作兩階段等候作業的物件。 在第一個階段中，同步處理物件， `Latch`，它會檢查是否鎖定已變成可用時少數週期旋轉。 在第二個階段中，如果鎖定可用，然後在`Wait`方法傳回時不使用<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>執行等待; 否則`Wait`執行等候。  
  
## <a name="example"></a>範例  
 此範例示範基本的閂鎖同步處理的基本實作。 預期的等候時間很短時，您可以使用這個資料結構。 這個範例是僅針對示範目的。 如果您在程式中需要閂鎖類型功能，請考慮使用<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>。  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 使用閂鎖<xref:System.Threading.SpinWait>就地啟動只到下一個呼叫的物件`SpinOnce`導致<xref:System.Threading.SpinWait>產生執行緒的時間配量。 此時，閂鎖會使它自己的內容切換藉由呼叫<xref:System.Threading.WaitHandle.WaitOne%2A>上<xref:System.Threading.ManualResetEvent>並傳入逾時值的其餘部分。  
  
 記錄輸出會顯示頻率閂鎖來提升效能所取得的鎖定，而不使用<xref:System.Threading.ManualResetEvent>。  
  
## <a name="see-also"></a>另請參閱  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
