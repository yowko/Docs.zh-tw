---
title: "Reader-Writer Locks | Microsoft Docs"
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
  - "ReaderWriterLock class, about ReaderWriterLock class"
  - "threading [.NET Framework], ReaderWriterLock class"
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Reader-Writer Locks
<xref:System.Threading.ReaderWriterLockSlim> 類別可讓多執行緒並行讀取資源，但是需要有一個執行緒等待獨佔的鎖定，以便將它寫入資源中。  
  
 您可以在應用程式中使用 <xref:System.Threading.ReaderWriterLockSlim>，以提供存取共用資源的執行緒之間的合作同步處理。  鎖定會發生在 <xref:System.Threading.ReaderWriterLockSlim> 本身。  
  
 如同任何執行緒同步處理機制，您必須確定所有執行緒都不會略過 <xref:System.Threading.ReaderWriterLockSlim> 提供的鎖定。  確定的方法之一，是設計封裝共用資源的類別。  此類別會提供存取私用共用資源的成員，以及使用私用 <xref:System.Threading.ReaderWriterLockSlim> 進行同步處理的成員。  如需範例，請參閱 <xref:System.Threading.ReaderWriterLockSlim> 類別的程式碼範例。  <xref:System.Threading.ReaderWriterLockSlim> 的效率已足夠用來同步處理個別物件。  
  
 請將應用程式結構化，讓讀寫作業的時間縮為最短。  長時間的寫入作業會直接影響處理量，因為寫入鎖定是獨佔的。  長時間的讀取作業則會封鎖等待的寫入器，如果有至少一個執行緒等待寫入存取，則需要讀取存取的執行緒也會被封鎖。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 有兩個讀取器\-寫入器鎖定：<xref:System.Threading.ReaderWriterLockSlim> 和 <xref:System.Threading.ReaderWriterLock>。  <xref:System.Threading.ReaderWriterLockSlim> 建議用於所有新的程式開發。  <xref:System.Threading.ReaderWriterLockSlim> 與 <xref:System.Threading.ReaderWriterLock> 相似，但前者採取簡化的遞迴規則及升級和降級鎖定狀態。  <xref:System.Threading.ReaderWriterLockSlim> 會避免許多可能發生的死結狀況。  此外，<xref:System.Threading.ReaderWriterLockSlim> 的效能大幅優於 <xref:System.Threading.ReaderWriterLock>。  
  
## 請參閱  
 <xref:System.Threading.ReaderWriterLockSlim>   
 <xref:System.Threading.ReaderWriterLock>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)