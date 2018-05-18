---
title: Reader-Writer 鎖定
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f829fc0b399f5cfd10d98f6b7439de757674f11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="reader-writer-locks"></a>Reader-Writer 鎖定
<xref:System.Threading.ReaderWriterLockSlim> 類別可讓多個執行緒同時讀取資源，但是會要求執行緒等候獨佔鎖定，才能寫入至資源。  
  
 您可能會在您的應用程式中使用 <xref:System.Threading.ReaderWriterLockSlim>，以提供存取共用資源之執行緒之間的合作式同步處理。 鎖定會在 <xref:System.Threading.ReaderWriterLockSlim> 本身上採用。  
  
 因為任何執行緒的同步處理機制，您必須確定沒有任何執行緒略過 <xref:System.Threading.ReaderWriterLockSlim> 所提供的鎖定。 要確保這麼做的一個方法，就是設計一個會封裝共用資源的類別。 這個類別會提供成員存取私用的共用資源，以及使用私用的 <xref:System.Threading.ReaderWriterLockSlim> 進行同步處理。 如需範例，請參閱 <xref:System.Threading.ReaderWriterLockSlim> 類別的程式碼範例。 <xref:System.Threading.ReaderWriterLockSlim> 很有效率，足以用來同步處理個別物件。  
  
 建置您應用程式的結構，以最小化讀取及寫入作業的持續時間。 長時間的寫入作業會直接影響輸送量，因為寫入是獨佔鎖定。 長時間的讀取作業會封鎖等候寫入器，且如果至少有一個執行緒正在等候寫入權限，要求讀取權限的執行緒也將會被封鎖。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 擁有 <xref:System.Threading.ReaderWriterLockSlim> 和 <xref:System.Threading.ReaderWriterLock> 這兩個 Reader-Writer 鎖定。 建議針對所有新的開發使用 <xref:System.Threading.ReaderWriterLockSlim>。 <xref:System.Threading.ReaderWriterLockSlim> 類似於 <xref:System.Threading.ReaderWriterLock>，但是它有遞迴以及升級和降級鎖定狀態的簡化規則。 <xref:System.Threading.ReaderWriterLockSlim> 可避免可能發生死結的許多情況。 此外，<xref:System.Threading.ReaderWriterLockSlim> 的效能明顯優於 <xref:System.Threading.ReaderWriterLock>。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
