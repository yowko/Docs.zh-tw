---
title: Mutex
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1d69c1b943d15b9ad8c80b4d7dbafebc54990ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mutexes"></a>Mutex
您可以使用<xref:System.Threading.Mutex>來提供資源的獨佔存取的物件。 <xref:System.Threading.Mutex>類別會使用更多系統資源比<xref:System.Threading.Monitor>類別，但它可以封送處理跨應用程式定義域界限、 搭配多個等待，和它可以用於同步處理不同的處理序中執行緒。 如需受管理之同步處理機制的比較，請參閱[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 如需程式碼範例，請參閱參考文件<xref:System.Threading.Mutex.%23ctor%2A>建構函式。  
  
## <a name="using-mutexes"></a>使用 Mutex  
 執行緒呼叫<xref:System.Threading.WaitHandle.WaitOne%2A>要求擁有權的 mutex 的方法。 該呼叫會封鎖起來，直到 Mutex 可供使用或直到選擇性的逾時間隔時間過去。 如果沒有任何執行緒擁有 Mutex，則 Mutex 的狀態為已發出訊號。  
  
 執行緒釋放 mutex 藉由呼叫其<xref:System.Threading.Mutex.ReleaseMutex%2A>方法。 Mutex 具有執行緒相似性；也就是說，Mutex 的釋放只能由擁有該 Mutex 的執行緒來執行。 如果執行緒釋放的 mutex 並未擁有，<xref:System.ApplicationException>執行緒擲回。  
  
 因為<xref:System.Threading.Mutex>類別衍生自<xref:System.Threading.WaitHandle>，您也可以呼叫靜態<xref:System.Threading.WaitHandle.WaitAll%2A>或<xref:System.Threading.WaitHandle.WaitAny%2A>方法<xref:System.Threading.WaitHandle>要求擁有權<xref:System.Threading.Mutex>搭配其他等候控制代碼。  
  
 如果執行緒擁有<xref:System.Threading.Mutex>，執行緒可以指定相同<xref:System.Threading.Mutex>中重複的等候要求呼叫，而不會封鎖其執行中; 不過，它必須釋放<xref:System.Threading.Mutex>次數釋出擁有權。  
  
## <a name="abandoned-mutexes"></a>遭到放棄的 Mutex  
 如果執行緒終止而未釋放<xref:System.Threading.Mutex>，就會放棄 mutex。 這通常代表程式在設計上有嚴重錯誤，因為 Mutex 所保護的資源可能仍處於不一致的狀態。 在.NET Framework 2.0 版中，<xref:System.Threading.AbandonedMutexException>取得 mutex 的下一個執行緒中擲回。  
  
> [!NOTE]
>  在.NET framework 1.0 和 1.1 中，已放棄的<xref:System.Threading.Mutex>正在等候執行緒取得擁有權設為收到信號的狀態和下一步。 如果有任何執行緒正在不等待，<xref:System.Threading.Mutex>會保留在收到信號的狀態。 不會有例外狀況擲回。  
  
 如果是全系統 Mutex，遭到放棄的 Mutex 可能表示應用程式已意外終止 (例如，透過使用「Windows 工作管理員」)。  
  
## <a name="local-and-system-mutexes"></a>本機和系統 Mutex  
 Mutex 有兩種類型︰本機 Mutex 和具名的系統 Mutex。 如果您建立<xref:System.Threading.Mutex>物件使用的建構函式接受名稱，它是與作業系統物件，該名稱的關聯。 具名的系統 Mutex 能在整個作業系統中看到，而且可用來同步處理處理序的活動。 您可以建立多個<xref:System.Threading.Mutex>物件，代表相同的具名系統 mutex，而且您可以使用<xref:System.Threading.Mutex.OpenExisting%2A>方法來開啟現有的具名系統 mutex。  
  
 本機 Mutex只存在於您的處理序內。 可供您參考到本機的程序中的任何執行緒<xref:System.Threading.Mutex>物件。 每個<xref:System.Threading.Mutex>物件是另一個本機 mutex。  
  
### <a name="access-control-security-for-system-mutexes"></a>系統 Mutex 的存取控制安全性  
 .NET Framework 2.0 版可讓您查詢及設定具名系統物件的 Windows 存取控制安全性。 我們會建議您在建立系統 Mutex 後就為其提供保護，因為系統物件為全域所有，因此非您所擁有的程式碼也可將其鎖定。  
  
 Mutex 的存取控制安全性的相關資訊，請參閱<xref:System.Security.AccessControl.MutexSecurity>和<xref:System.Security.AccessControl.MutexAccessRule>類別，<xref:System.Security.AccessControl.MutexRights>列舉型別， <xref:System.Threading.Mutex.GetAccessControl%2A>， <xref:System.Threading.Mutex.SetAccessControl%2A>，和<xref:System.Threading.Mutex.OpenExisting%2A>方法<xref:System.Threading.Mutex>類別和<xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>建構函式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [執行緒物件和功能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [監視](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)
