---
title: 如何：使用 SpinWait 實作兩階段等候作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af6e4e8d0d754b97478788422b4dd84eeddc6491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>如何：使用 SpinWait 實作兩階段等候作業
下列範例示範如何使用 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 物件來實作兩階段等候作業。 在第一個階段中，同步處理物件 `Latch` 會在它檢查鎖定是否已變成可用時，進行數個週期的微調。 在第二個階段中，如果鎖定已變成可用，則 `Wait` 方法會傳回，而不需使用 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 來執行等候；否則 `Wait` 會執行等候。  
  
## <a name="example"></a>範例  
 此範例示範非常基本的閂鎖同步處理原始物件實作。 預期等候時間很短時，您就能使用這個資料結構。 此範例僅供示範之用。 如果您在程式中需要閂鎖類型功能，請考慮使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>。  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 閂鎖只會使用 <xref:System.Threading.SpinWait> 物件就地微調，直到下一個對 `SpinOnce` 的呼叫導致 <xref:System.Threading.SpinWait> 讓出執行緒的時間配量。 此時，閂鎖會藉由呼叫 <xref:System.Threading.ManualResetEvent> 上的 <xref:System.Threading.WaitHandle.WaitOne%2A> 並傳入逾時值的其餘部分，以使它自己進行內容切換。  
  
 記錄輸出會藉由取得鎖定，而不使用 <xref:System.Threading.ManualResetEvent>，來顯示閂鎖能夠提升效能的頻率。  
  
## <a name="see-also"></a>請參閱  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
