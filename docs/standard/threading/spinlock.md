---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock>結構是低階、 互斥同步處理基本類型，在等候取得鎖定期間的旋轉。 在多核心電腦時應該等候時間很短且競爭時最少，<xref:System.Threading.SpinLock>可以優於其他類型的鎖定。 不過，我們建議您改用<xref:System.Threading.SpinLock>只有當您判斷程式碼剖析，<xref:System.Threading.Monitor?displayProperty=nameWithType>方法或<xref:System.Threading.Interlocked>方法會大幅減慢程式的效能。  
  
 <xref:System.Threading.SpinLock>可能會產生即使它不尚未取得鎖定之執行緒的時間配量。 它會以避免執行緒優先權反轉，並啟用進行記憶體回收行程。 當您使用<xref:System.Threading.SpinLock>，確保任何執行緒可以保留鎖定，非常短暫的時間範圍內，已超過和任何執行緒可以封鎖時，它會持有鎖定。  
  
 由於單一執行緒存取鎖是實值類型，您必須明確地將傳遞它參考如果您想要參考相同的鎖定，兩個複本。  
  
 如需如何使用這種類型的詳細資訊，請參閱<xref:System.Threading.SpinLock?displayProperty=nameWithType>。 如需範例，請參閱[How to： 使用 SpinLock 進行低階同步處理](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)。  
  
 <xref:System.Threading.SpinLock>支援*執行緒*-*追蹤*模式可讓您在開發階段，協助追蹤在特定時間持有鎖定的執行緒。 執行緒追蹤模式是非常適用於偵錯，但我們建議您關閉該程式的發行版本中因為它可能會降低效能。 如需詳細資訊，請參閱[How to： 啟用執行緒追蹤模式，在單一執行緒存取鎖](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)
