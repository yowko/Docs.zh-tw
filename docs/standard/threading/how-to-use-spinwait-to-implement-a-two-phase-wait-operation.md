---
title: "How to: Use SpinWait to Implement a Two-Phase Wait Operation | Microsoft Docs"
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
  - "SpinWait, how to synchronize two-phase wait"
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Use SpinWait to Implement a Two-Phase Wait Operation
下列範例將示範如何使用 <xref:System.Threading.SpinWait?displayProperty=fullName> 物件來實作兩階段等候作業。  在第一個階段中，當同步處理物件 `Latch` 檢查鎖定是否變成可用時，它會空轉少數循環。  在第二個階段中，如果鎖定變成可用，`Wait` 方法就會傳回而不使用 <xref:System.Threading.ManualResetEvent?displayProperty=fullName> 來執行其等候。否則，`Wait` 就會執行等候。  
  
## 範例  
 這個範例會示範 Latch 同步處理原始物件非常基本的實作。  當等候時間應該非常短暫時，您就可以使用這種資料結構。  這個範例僅供示範使用。  如果您需要在程式中使用閂鎖類型功能，請考慮使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName>。  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 此閂鎖只會使用 <xref:System.Threading.SpinWait> 物件來就地空轉，直到下一次呼叫 `SpinOnce` 讓 <xref:System.Threading.SpinWait> 產生執行緒的時間量為止。  此時，閂鎖就會針對 <xref:System.Threading.ManualResetEvent> 呼叫 <xref:System.Threading.WaitHandle.WaitOne%2A> 並傳入逾時值的餘數，藉以進行自訂內容切換。  
  
 記錄輸出會顯示 Latch 能夠透過取得鎖定而不使用 <xref:System.Threading.ManualResetEvent> 來提升效能的頻率。  
  
## 請參閱  
 [SpinWait](../../../docs/standard/threading/spinwait.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)