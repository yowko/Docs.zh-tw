---
title: "使用安全執行緒集合的時機 | Microsoft Docs"
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
  - "安全執行緒集合，升級時機"
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 使用安全執行緒集合的時機
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]引入了五個新的集合型別，而這些型別是特別針對支援多執行緒加入和移除作業所設計的。  為了達到執行緒安全性，這些新的型別會使用各種有效率的鎖定和無鎖定同步處理機制。  但是，同步處理會增加作業的額外負荷。  額外負荷量取決於所使用的同步處理種類、所執行的作業種類，以及其他因素，例如嘗試以並行方式存取集合的執行緒數目。  
  
 在某些案例中，同步處理額外負荷可忽略而且可讓多執行緒型別的執行速度和延展性超過其非安全執行緒對等項目 \(受到外部鎖定所保護時\)。  在其他案例中，額外負荷可能會導致安全執行緒型別的執行速度和延展性與此型別的外部鎖定且非安全執行緒版本相同，甚至更低。  
  
 下列各節將針對安全執行緒集合與其非安全執行緒對等項目 \(在其讀取和寫入作業周圍具有使用者提供的鎖定\) 的使用時機提供一般指引。  因為效能可能會根據許多因素而不同，所以指引並非特定而且不一定適用於所有情況。  如果效能非常重要，則判斷要使用哪個集合型別的最佳方式，就是根據代表性電腦組態和負載測量效能。  本文將使用下列詞彙：  
  
 *單純的生產者\-消費者案例*  
 任何給定的執行緒都會加入或移除項目，但不會同時進行。  
  
 *混合的生產者\-消費者案例*  
 任何給定的執行緒都會同時加入和移除項目。  
  
 *加速*  
 在相同案例中，速度較快的演算法效能相對於另一個型別而言。  
  
 *延展性*  
 與電腦上核心數目成正比的效能提升。  可延展的演算法在八個核心上執行的速度會超過在兩個核心上執行的速度。  
  
## ConcurrentQueue\(T\) vs. Queue\(T\)  
 在單純的生產者\-消費者案例中，如果每個項目的處理時間非常少 \(少數指令\)，則 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> 所提供的適度效能優勢可能會超過具有外部鎖定的 <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>。  在這個案例中，當某個專屬執行緒正排入佇列而另一個專屬執行緒正清除佇列時，<xref:System.Collections.Concurrent.ConcurrentQueue%601> 的執行效能最好。  如果您沒有強制執行此規則，在具有多個核心的電腦上，<xref:System.Collections.Generic.Queue%601> 的執行速度可能會稍微超過 <xref:System.Collections.Concurrent.ConcurrentQueue%601>。  
  
 當處理時間大約為 500 FLOPS \(浮點運算\) 或以上時，雙執行緒規則就不會套用至 <xref:System.Collections.Concurrent.ConcurrentQueue%601>，因而具有非常好的延展性。  在這個案例中，<xref:System.Collections.Generic.Queue%601> 不會有效延展。  
  
 在混合的生產者\-消費者案例中，當處理時間非常少時，具有外部鎖定之 <xref:System.Collections.Generic.Queue%601> 的延展性會超過 <xref:System.Collections.Concurrent.ConcurrentQueue%601>。  不過，當處理時間大約為 500 FLOPS 或以上時，<xref:System.Collections.Concurrent.ConcurrentQueue%601> 的延展性較佳。  
  
## ConcurrentStack vs. Stack  
 在單純的生產者\-消費者案例中，當處理時間非常少時，則具有外部鎖定之<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName> 和 <xref:System.Collections.Generic.Stack%601?displayProperty=fullName> 的執行效能可能會大約與單一專屬推送執行緒和單一專屬提取執行緒相同。  不過，隨著執行緒數目增加，這兩個型別的執行速度會由於爭用增加而降低，而且 <xref:System.Collections.Generic.Stack%601> 的效能可能會優於 <xref:System.Collections.Concurrent.ConcurrentStack%601>。  當處理時間大約為 500 FLOPS 或以上時，這兩個型別的延展性大約相同。  
  
 在混合的生產者\-消費者案例中，不論工作負載高低，<xref:System.Collections.Concurrent.ConcurrentStack%601> 的速度都比較快。  
  
 使用 <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> 可能會大幅加快存取速度。  
  
## ConcurrentDictionary vs. Dictionary  
 一般而言，當您要以並行方式從多個執行緒加入和更新機碼或值時，請使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>。  在包含經常更新和相當少讀取的案例中，<xref:System.Collections.Concurrent.ConcurrentDictionary%602> 通常會提供適度的優勢。  在包含許多讀取和許多更新的案例中，在具有任何核心數目的電腦上，<xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的執行速度通常比較快。  
  
 在包含經常更新的案例中，您可以在 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 中提高並行程度，然後進行測量，以便查看具有更多核心的電腦效能是否提升。  如果您變更並行層級，請盡可能避免進行全域作業。  
  
 如果您只要讀取機碼或值，而且字典沒有被任何執行緒修改，<xref:System.Collections.Generic.Dictionary%602> 的速度比較快，因為不需要進行同步處理。  
  
## ConcurrentBag  
 在單純的生產者\-消費者案例中，<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> 的執行速度可能會比其他並行集合型別更慢。  
  
 在混合的生產者\-消費者案例中，不論工作負載高低，<xref:System.Collections.Concurrent.ConcurrentBag%601> 的執行速度和延展性通常會超過任何其他並行集合型別。  
  
## BlockingCollection  
 需要使用界限和封鎖語意時，<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 的執行速度可能會超過任何自訂實作。  它也支援豐富的取消、列舉和例外狀況處理。  
  
## 請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)   
 [Parallel Programming](../../../../docs/standard/parallel-programming/index.md)