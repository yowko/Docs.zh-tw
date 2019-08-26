---
title: Mutex
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b2edf1f06873796bd63fceaca9a4bb99e509589
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910351"
---
# <a name="mutexes"></a>Mutex
您可以使用 <xref:System.Threading.Mutex> 物件來提供獨佔的資源存取權。 <xref:System.Threading.Mutex> 類別所使用的系統資源比 <xref:System.Threading.Monitor> 類別還多，但前者可跨越應用程式定義域的界限進行封送處理、可搭配多個等候使用，並可用來同步處理不同處理序內的執行緒。 如需受管理之同步處理機制的比較，請參閱[同步處理原始物件概觀](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 如需程式碼範例，請參閱 <xref:System.Threading.Mutex.%23ctor%2A> 建構函式的參考文件。  
  
## <a name="using-mutexes"></a>使用 Mutex  
 執行緒會呼叫 Mutex 的 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法來要求擁有權。 該呼叫會封鎖起來，直到 Mutex 可供使用或直到選擇性的逾時間隔時間過去。 如果沒有任何執行緒擁有 Mutex，則 Mutex 的狀態為已發出訊號。  
  
 執行緒會藉由呼叫 Mutex 的 <xref:System.Threading.Mutex.ReleaseMutex%2A> 方法來釋放它。 Mutex 具有執行緒相似性；也就是說，Mutex 的釋放只能由擁有該 Mutex 的執行緒來執行。 如果執行緒釋放非它擁有的 Mutex，執行緒中就會擲回 <xref:System.ApplicationException>。  
  
 因為 <xref:System.Threading.Mutex> 類別衍生自 <xref:System.Threading.WaitHandle>，您也可以呼叫 <xref:System.Threading.WaitHandle> 的靜態 <xref:System.Threading.WaitHandle.WaitAll%2A> 或 <xref:System.Threading.WaitHandle.WaitAny%2A> 方法，搭配其他等候控制代碼來要求 <xref:System.Threading.Mutex> 的擁有權。  
  
 如果執行緒擁有 <xref:System.Threading.Mutex>，該執行緒就能在重複的等候要求呼叫中指定相同的 <xref:System.Threading.Mutex>，而不需封鎖其執行；但是，它也必須進行相同次數的 <xref:System.Threading.Mutex> 釋放作業，以釋放擁有權。  
  
## <a name="abandoned-mutexes"></a>遭到放棄的 Mutex  
 如果執行緒終止時未釋放 <xref:System.Threading.Mutex>，就表示已放棄 Mutex。 這通常代表程式在設計上有嚴重錯誤，因為 Mutex 所保護的資源可能仍處於不一致的狀態。 在 .NET Framework 2.0 版中，下一個取得 Mutex 的執行緒中會擲回 <xref:System.Threading.AbandonedMutexException>。  
  
> [!NOTE]
> 在 .NET Framework 1.0 和 1.1 版中，會將遭到放棄的 <xref:System.Threading.Mutex> 設為已發出信號的狀態，下一個等候中的執行緒則會取得擁有權。 如果沒有執行緒在等候，<xref:System.Threading.Mutex> 就會保持已發出信號的狀態。 不會有例外狀況擲回。  
  
 如果是全系統 Mutex，遭到放棄的 Mutex 可能表示應用程式已意外終止 (例如，透過使用「Windows 工作管理員」)。  
  
## <a name="local-and-system-mutexes"></a>本機和系統 Mutex  
 Mutex 有兩種類型︰本機 Mutex 和具名的系統 Mutex。 如果您使用可接受名稱的建構函式來建立 <xref:System.Threading.Mutex> 物件，該物件便會與該名稱的作業系統物件相關聯。 具名的系統 Mutex 能在整個作業系統中看到，而且可用來同步處理處理序的活動。 您可以建立多個 <xref:System.Threading.Mutex> 物件來代表同一個具名系統 Mutex，而且可以使用 <xref:System.Threading.Mutex.OpenExisting%2A> 方法來開啟現有的具名系統 Mutex。  
  
 本機 Mutex只存在於您的處理序內。 在處理序內，只要是參考了本機 <xref:System.Threading.Mutex> 物件的執行緒，就可使用本機 Mutex。 每個 <xref:System.Threading.Mutex> 物件都是獨立的本機 Mutex。  
  
### <a name="access-control-security-for-system-mutexes"></a>系統 Mutex 的存取控制安全性  
 .NET Framework 2.0 版可讓您查詢及設定具名系統物件的 Windows 存取控制安全性。 我們會建議您在建立系統 Mutex 後就為其提供保護，因為系統物件為全域所有，因此非您所擁有的程式碼也可將其鎖定。  
  
 如需適用於 Mutex 的存取控制安全性相關資訊，請參閱 <xref:System.Security.AccessControl.MutexSecurity> 和 <xref:System.Security.AccessControl.MutexAccessRule> 類別、<xref:System.Security.AccessControl.MutexRights> 列舉、<xref:System.Threading.Mutex.GetAccessControl%2A>、<xref:System.Threading.Mutex.SetAccessControl%2A>、<xref:System.Threading.Mutex> 類別的 <xref:System.Threading.Mutex.OpenExisting%2A> 方法，以及 <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> 建構函式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [執行緒物件和功能](threading-objects-and-features.md)
- [執行緒與執行緒處理](threads-and-threading.md)
- [執行緒處理](index.md)
