---
title: "SpinLock | Microsoft Docs"
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
  - "synchronization primitives, SpinLock"
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# SpinLock
<xref:System.Threading.SpinLock> 結構屬於低階、互斥同步處理原始物件，在等候取得鎖定時進行旋轉。  在多核心電腦上，當等待週期預計不長並且爭用最小時，<xref:System.Threading.SpinLock> 可以提供較其他鎖定更優越的效能。  但是，我們建議只有在進行程式碼剖析後確定 <xref:System.Threading.Monitor?displayProperty=fullName> 方法或 <xref:System.Threading.Interlocked> 方法會大幅降低程式效能時，才使用 <xref:System.Threading.SpinLock>。  
  
 <xref:System.Threading.SpinLock> 可以產生執行緒的時間量，即使它尚未取得鎖定也一樣。  這樣做會避免執行緒優先權顛倒，並啟用記憶體回收行程來繼續執行。  使用 <xref:System.Threading.SpinLock> 時，請確保沒有執行緒能夠在短時間範圍內維持鎖定，也沒有執行緒能夠在維持鎖定時進行封鎖。  
  
 因為 SpinLock 是實值型別，因此如果想要兩份複本參考同一鎖定，必須明確以傳址方式進行傳遞。  
  
 如需如何使用此型別的詳細資訊，請參閱 <xref:System.Threading.SpinLock?displayProperty=fullName>。  如需範例，請參閱 [How to: Use SpinLock for Low\-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)。  
  
 <xref:System.Threading.SpinLock> 支援「*執行緒* *追蹤*」\(Thread Tracking\) 模式，該模式可以在開發階段期間使用，用來協助追蹤在特定時間維持鎖定的執行緒。  執行緒追蹤模式對於偵錯非常有用，但是建議在程式的發行版本中關閉該模式，因為它會降低效能。  如需詳細資訊，請參閱 [How to: Enable Thread\-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md)。  
  
## 請參閱  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)