---
title: "Mutexes | Microsoft Docs"
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
  - "wait handles"
  - "threading [.NET Framework], Mutex class"
  - "Mutex class, about Mutex class"
  - "threading [.NET Framework], cross-process synchronization"
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Mutexes
您可以使用 <xref:System.Threading.Mutex> 物件來提供資源的獨佔存取權。  <xref:System.Threading.Mutex> 類別所使用的系統資源比 <xref:System.Threading.Monitor> 類別多，但它可以跨應用程式定義域界限進行封送處理、可以搭配多個等候來使用，並且可以用來同步處理不同處理序中的執行緒。  如需 Managed 同步處理機制的比較，請參閱[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)。  
  
 如需程式碼範例，請參閱 <xref:System.Threading.Mutex.%23ctor%2A> 建構函式的參考文件。  
  
## 使用 Mutex  
 執行緒會呼叫 Mutex 的 <xref:System.Threading.WaitHandle.WaitOne%2A> 方法以要求擁有權。  呼叫會封鎖，直到 Mutex 可供使用為止，或直到選用的逾時間隔過去為止。  如果沒有執行緒擁有 Mutex，就會收到 Mutex 狀態的信號。  
  
 執行緒經由呼叫 Mutex 的 <xref:System.Threading.Mutex.ReleaseMutex%2A> 方法來釋放它。  Mutex 具有執行緒相似性；也就是說，只有擁有 Mutex 的執行緒才能釋放該 Mutex。  如果執行緒釋放了不屬於它的 Mutex，執行緒中會擲回 <xref:System.ApplicationException>。  
  
 因為 <xref:System.Threading.Mutex> 類別是衍生自 <xref:System.Threading.WaitHandle>，所以您也可以呼叫 <xref:System.Threading.WaitHandle> 的靜態 <xref:System.Threading.WaitHandle.WaitAll%2A> 或 <xref:System.Threading.WaitHandle.WaitAny%2A> 方法，以便同時要求 <xref:System.Threading.Mutex> 的擁有權與其他等候處理常式。  
  
 如果有執行緒擁有 <xref:System.Threading.Mutex>，則該執行緒可在重複的等候要求呼叫中指定同一個 <xref:System.Threading.Mutex>，而不用封鎖其執行；然而，它必須多次釋放 <xref:System.Threading.Mutex>，直到釋放擁有權為止。  
  
## 放棄的 Mutex  
 如果執行緒沒有釋放 <xref:System.Threading.Mutex> 隨即終止，則此 Mutex 就稱為放棄的 Mutex。  這通常表示一個嚴重的程式設計錯誤，因為 Mutex 所保護的資源可能會以不一致的狀態遺留下來。  在 .NET Framework 2.0 版中，下一個獲取 Mutex 的執行緒中會擲回 <xref:System.Threading.AbandonedMutexException>。  
  
> [!NOTE]
>  在 .NET Framework 1.0 和 1.1 版中，放棄的 <xref:System.Threading.Mutex> 會設為收到信號的狀態，而下一個等候的執行緒會取得擁有權。  如果沒有等候的執行緒，<xref:System.Threading.Mutex> 會維持收到信號的狀態，  不會擲回例外狀況。  
  
 在系統範圍 Mutex 的情況中，已放棄的 Mutex 可能表示應用程式已突然終止 \(例如，透過使用 \[Windows 工作管理員\] 的方式\)。  
  
## 區域與系統 Mutex  
 Mutex 有兩種類型：區域 Mutex 和具名系統 Mutex。  如果您使用接受名稱的建構函式 \(Constructor\) 建立 <xref:System.Threading.Mutex> 物件，它便會關聯到該名稱的作業系統物件。  在整個作業系統中都可以看到具名系統 Mutex，而且這種 Mutex 也可以用於同步化處理序的活動。  您可以建立多個 <xref:System.Threading.Mutex> 物件來表示同一個具名的系統 Mutex，並可使用 <xref:System.Threading.Mutex.OpenExisting%2A> 方法開啟現有的具名系統 Mutex。  
  
 區域 Mutex 只存在於您的處理序之內。  您處理序中的任何執行緒，只要有對區域 <xref:System.Threading.Mutex> 物件的參考，均可使用區域 Mutex。  每一個 <xref:System.Threading.Mutex> 都是一個獨立的區域 Mutex。  
  
### 系統 Mutex 的存取控制安全性  
 .NET Framework 2.0 版可讓您查詢及設定具名系統物件的 Windows 存取控制安全性。  建議您從建立系統 Mutex 開始就要保護它，因為系統物件是全域性的，所以可能會被其他程式碼鎖定。  
  
 如需 Mutex 的存取控制安全性的詳細資訊，請參閱 <xref:System.Security.AccessControl.MutexSecurity> 和 <xref:System.Security.AccessControl.MutexAccessRule> 類別、<xref:System.Security.AccessControl.MutexRights> 列舉型別、<xref:System.Threading.Mutex> 類別的 <xref:System.Threading.Mutex.GetAccessControl%2A>、<xref:System.Threading.Mutex.SetAccessControl%2A> 和 <xref:System.Threading.Mutex.OpenExisting%2A> 方法，以及 <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> 建構函式。  
  
## 請參閱  
 <xref:System.Threading.Mutex>   
 <xref:System.Threading.Mutex.%23ctor%2A>   
 <xref:System.Security.AccessControl.MutexSecurity>   
 <xref:System.Security.AccessControl.MutexAccessRule>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [監視器](../Topic/Monitors.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)