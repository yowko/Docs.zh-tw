---
title: "Reader-Writer 鎖定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df06e83165906199774f99de4140ace9b7396cbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="reader-writer-locks"></a>Reader-Writer 鎖定
<xref:System.Threading.ReaderWriterLockSlim>類別可讓多個執行緒同時也會讀取資源，但需要等候獨佔鎖定，才能寫入至資源的執行緒。  
  
 您可能會使用<xref:System.Threading.ReaderWriterLockSlim>提供存取共用的資源的執行緒之間的合作式同步處理的應用程式中。 所持有的鎖定<xref:System.Threading.ReaderWriterLockSlim>本身。  
  
 因為任何執行緒的同步處理機制，您必須確定沒有任何執行緒略過所提供的鎖定<xref:System.Threading.ReaderWriterLockSlim>。 若要確保這一個方法是設計封裝共用的資源的類別。 這個類別會提供可存取私用的共用的資源，並使用私用成員<xref:System.Threading.ReaderWriterLockSlim>進行同步處理。 如需範例，請參閱的程式碼範例<xref:System.Threading.ReaderWriterLockSlim>類別。 <xref:System.Threading.ReaderWriterLockSlim>很有效率，足以用來同步處理個別物件。  
  
 最小化的持續時間的讀取和寫入作業將應用程式的結構。 長的寫入作業直接影響輸送量，因為獨佔寫入鎖定。 長時間的讀取作業封鎖等候寫入器，如果至少一個執行緒正在等候寫入權限，要求讀取權限的執行緒會被如此封鎖。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]有兩個讀取器-寫入器鎖定，<xref:System.Threading.ReaderWriterLockSlim>和<xref:System.Threading.ReaderWriterLock>。 <xref:System.Threading.ReaderWriterLockSlim>建議所有新的開發。 <xref:System.Threading.ReaderWriterLockSlim>類似於<xref:System.Threading.ReaderWriterLock>，但它已簡化遞迴以及升級和降級鎖定狀態的規則。 <xref:System.Threading.ReaderWriterLockSlim>可避免可能發生死結的許多情況。 此外，效能<xref:System.Threading.ReaderWriterLockSlim>明顯優於<xref:System.Threading.ReaderWriterLock>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
