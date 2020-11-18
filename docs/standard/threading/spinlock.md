---
title: SpinLock
ms.date: 03/30/2017
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: 071bde6e8b32d5712256e24c83d713cd63f2bffb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819002"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> 結構是一個低階、互斥的同步處理基本類型，會在等候取得鎖定期間進行微調。 在多核心電腦上，預期等候時間很短且競爭最少時，<xref:System.Threading.SpinLock> 可以優於其他類型鎖定的方式執行。 不過，我們建議您只有在藉由分析 <xref:System.Threading.Monitor?displayProperty=nameWithType> 方法進行判斷時，或 <xref:System.Threading.Interlocked> 方法大幅減慢程式的效能，才使用 <xref:System.Threading.SpinLock>。  
  
 即使 <xref:System.Threading.SpinLock> 尚未取得鎖定，還是可能會讓出執行緒的時間配量。 它會執行此作業來避免執行緒優先順序反轉，並使記憶體回收行程繼續有進展。 當您使用 <xref:System.Threading.SpinLock> 時，確保沒有任何執行緒可以保留鎖定超過一個非常短暫的時間範圍，而且沒有執行緒可以在保留鎖定時加以封鎖。  
  
 由於 SpinLock 是一個實值類型，因此，如果您想要讓兩個複本參考同一個鎖定，就必須明確地以傳址方式傳遞它。  
  
 如需如何使用此類型的詳細資訊，請參閱 <xref:System.Threading.SpinLock?displayProperty=nameWithType>。 如需範例，請參閱[如何：使用 SpinLock 進行低階同步處理](how-to-use-spinlock-for-low-level-synchronization.md)。  
  
 <xref:System.Threading.SpinLock>支援 *執行緒* - *追蹤* 模式，可讓您在開發階段使用，以協助追蹤在特定時間保留鎖定的執行緒。 執行緒追蹤模式非常適用於偵錯，但我們建議您在程式的發行版本中關閉此模式，因為它可能會降低效能。 如需詳細資訊，請參閱[如何：啟用 SpinLock 中的執行緒追蹤模式](how-to-enable-thread-tracking-mode-in-spinlock.md)。  
  
## <a name="see-also"></a>請參閱

- [執行緒物件和功能](threading-objects-and-features.md)
