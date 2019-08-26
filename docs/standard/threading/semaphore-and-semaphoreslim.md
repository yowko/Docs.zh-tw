---
title: Semaphore 和 SemaphoreSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- counting semaphores
- semaphores
- threading [.NET Framework], cross-process synchronization
- Semaphore class, about Semaphore class
- SemaphoreSlim class, about SemaphoreSlim class
- threading [.NET Framework], Semaphore class
ms.assetid: 7722a333-b974-47a2-a7c0-f09097fb644e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25121ea2b089df49efa77dcf363e2a0e400b3bff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968432"
---
# <a name="semaphore-and-semaphoreslim"></a>Semaphore 和 SemaphoreSlim
<xref:System.Threading.Semaphore?displayProperty=nameWithType> 類別代表具名 (系統) 或區域號誌。 它是 Win32 號誌物件周圍的精簡型包裝函式。 Win32 號誌是計算的號誌，可以用來控制資源集區的存取。  
  
 <xref:System.Threading.SemaphoreSlim> 類別表示輕量型、快速的號誌，可以用於在預期等候時間較短的單一處理序內進行等候。 <xref:System.Threading.SemaphoreSlim> 會盡可能依賴通用語言執行階段 (CLR) 所提供的同步處理原始物件。 不過，它也提供延遲初始化、核心架構的等候控制代碼，視需要支援等待多個號誌。 <xref:System.Threading.SemaphoreSlim> 也支援使用取消語彙基元，但它不支援具名號誌或使用等候控制代碼進行同步處理。  
  
## <a name="managing-a-limited-resource"></a>管理有限的資源  
 執行緒進入旗號的方法是呼叫 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法，它是繼承自 <xref:System.Threading.WaitHandle> 類別 (如果是 <xref:System.Threading.Semaphore?displayProperty=nameWithType> 物件)，或是 <xref:System.Threading.SemaphoreSlim.Wait%2A?displayProperty=nameWithType> 或 <xref:System.Threading.SemaphoreSlim.WaitAsync%2A?displayProperty=nameWithType> 方法 (如果是 <xref:System.Threading.SemaphoreSlim> 物件)。 當呼叫傳回時，號誌計數會遞減。 當執行緒要求進入，而計數為零時，則執行緒會封鎖。 當執行緒藉由呼叫 <xref:System.Threading.Semaphore.Release%2A?displayProperty=nameWithType> 或 <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> 方法釋放號誌時，會允許封鎖的執行緒進入。 封鎖的執行緒進入號誌時沒有任何保證的順序，例如先進先出 (FIFO) 或後進先出 (LIFO)。  
  
 執行緒可以重複呼叫 <xref:System.Threading.Semaphore?displayProperty=nameWithType> 物件的 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法或 <xref:System.Threading.SemaphoreSlim> 物件的 <xref:System.Threading.SemaphoreSlim.Wait%2A> 方法，多次進入號誌。 若要釋放號誌，執行緒可以呼叫 <xref:System.Threading.Semaphore.Release?displayProperty=nameWithType> 或 <xref:System.Threading.SemaphoreSlim.Release?displayProperty=nameWithType> 方法多載相同的次數，或呼叫 <xref:System.Threading.Semaphore.Release%28System.Int32%29?displayProperty=nameWithType> 或 <xref:System.Threading.SemaphoreSlim.Release%28System.Int32%29?displayProperty=nameWithType> 方法多載，並指定要釋放的項目數。  
  
### <a name="semaphores-and-thread-identity"></a>號誌和執行緒識別  
 兩種號誌類型不會在 <xref:System.Threading.WaitHandle.WaitOne%2A>、<xref:System.Threading.SemaphoreSlim.Wait%2A>、<xref:System.Threading.Semaphore.Release%2A> 和 <xref:System.Threading.SemaphoreSlim.Release%2A?displayProperty=nameWithType> 方法的呼叫上強制執行執行緒識別。 例如，一個號誌的常見使用案例，其涉及一個產生者執行緒和一個消費者執行緒，之中一個執行緒始終都會遞增號誌計數，另一個則始終遞減它。  
  
 程式設計人員要負責確保執行緒不會釋放號誌太多次。 例如，假設某個號誌的最大計數為 2，且執行緒 A 和執行緒 B 都進入號誌。 如果執行緒 B 中的程式設計錯誤導致呼叫 `Release` 兩次，兩次呼叫都會成功。 此時號誌計數已滿，當執行緒 A 終於呼叫 `Release` 時，就會擲回 <xref:System.Threading.SemaphoreFullException>。  
  
## <a name="named-semaphores"></a>具名號誌  
 Windows 作業系統允許有名稱的號誌。 具名號誌是全系統性的。 也就是說，一旦建立具名號誌，所有處理序中的所有執行緒都可看到它。 因此，具名號誌可以用來同步處理序及執行緒的活動。  
  
 您可以建立 <xref:System.Threading.Semaphore> 物件，使用其中一個指定名稱的建構函式來代表具名系統號誌。  
  
> [!NOTE]
> 由於具名號誌是全系統性的，因此可能有多個 <xref:System.Threading.Semaphore> 物件，代表相同的具名號誌。 每次呼叫建構函式或 <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> 方法時，便會建立新的 <xref:System.Threading.Semaphore> 物件。 重複指定相同的名稱，會建立多個代表相同具名號誌的物件。  
  
 使用具名號誌時請小心。 因為它們是全系統性的，使用相同名稱的另一個處理序可能會意外地進入您的號誌。 在同一部電腦上執行的惡意程式碼便可使用此點作為拒絕服務攻擊的基礎。  
  
 使用存取控制安全性來保護代表具名號誌的 <xref:System.Threading.Semaphore> 物件，最好是使用指定 <xref:System.Security.AccessControl.SemaphoreSecurity?displayProperty=nameWithType> 物件的建構函式。 您也可以使用 <xref:System.Threading.Semaphore.SetAccessControl%2A?displayProperty=nameWithType> 方法套用存取控制安全性，但這會在建立號誌的時間與它受保護的時間之間留下弱點時段。 使用存取控制安全性來保護號誌，有助於防止惡意攻擊，但不能解決意外名稱衝突的問題。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Semaphore>
- <xref:System.Threading.SemaphoreSlim>
- [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
