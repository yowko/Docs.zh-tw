---
title: "How to: Enable Thread-Tracking Mode in SpinLock | Microsoft Docs"
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
  - "SpinLock, how to enable thread-tracking"
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Enable Thread-Tracking Mode in SpinLock
<xref:System.Threading.SpinLock?displayProperty=fullName> 是一種低階互斥鎖定，可讓您用於等候時間非常短的案例。  <xref:System.Threading.SpinLock> 不可重新進入。  在執行緒進入鎖定之後，它就必須先正確結束鎖定，然後才能再次進入。  一般而言，任何嘗試重新進入鎖定的行為都會導致死結，而且死結非常難以偵錯。  為了協助開發，<xref:System.Threading.SpinLock?displayProperty=fullName> 支援執行緒追蹤模式，可讓系統在執行緒嘗試重新進入已經持有的鎖定時擲回例外狀況。  這種模式可讓您更輕鬆地找出鎖定沒有正確結束的點。  您可以使用採用布林值輸入參數的 <xref:System.Threading.SpinLock> 建構函式並傳入 `true` 引數，藉以開啟執行緒追蹤模式。  在您完成開發和測試階段之後，請關閉執行緒追蹤模式以提高效能。  
  
## 範例  
 下列範例示範執行緒追蹤模式。  正確結束鎖定的行會標記為註解，以便模擬導致下列其中一種結果的程式碼錯誤：  
  
-   如果 <xref:System.Threading.SpinLock> 是使用 `true` \(Visual Basic 中的 `True`\) 引數建立的，就會擲回例外狀況。  
  
-   如果 <xref:System.Threading.SpinLock> 是使用 `false` \(Visual Basic 中的 `False`\) 引數建立的，就會發生死結。  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## 請參閱  
 [SpinLock](../../../docs/standard/threading/spinlock.md)