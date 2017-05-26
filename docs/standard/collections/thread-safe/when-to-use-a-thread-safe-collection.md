---
title: "使用安全執行緒集合的時機 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 87898a4a6ba3d3ef4c53fd1c6b8f94ff353f10e4
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="when-to-use-a-thread-safe-collection"></a>使用安全執行緒集合的時機
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] 引進五種悉的集合類型，特別設計來支援多執行緒新增和移除作業。 若要達到執行緒安全，這些新的類型會使用各種有效率的鎖定和無鎖定同步處理機制。 同步處理會增加作業的負荷。 負荷量取決於使用的同步處理類型、執行的作業類型，以及其他因素 (例如，嘗試同時存取集合的執行緒數目)。  
  
 在某些情況下，同步處理負荷會顯得微不足道，並且在受到外部鎖定保護時，讓多執行緒類型執行速度大幅加快，而且擴充的狀況遠優於其非安全執行緒對等項目。 在其他情況下，負荷可能會讓安全執行緒類型的執行和擴充速度等於甚於比外部鎖定之非安全執行緒版本的類型還要慢。  
  
 下列各節所提供的一般指引是有關何時使用安全執行緒集合，與其具有使用者所提供之讀取和寫入作業鎖定的非安全執行緒對等項目。 因為效能可能會因許多因素而不同，所以本指南不是特定的，也不一定適用於所有情況。 如果效能十分重要，則決定要使用之集合類型的最佳方式是根據代表性電腦組態和負載來測量效能。 本範例使用下列詞彙：  
  
 *單純生產者-消費者案例*  
 任何指定的執行緒都是新增或移除元素，而非同時執行兩項作業。  
  
 *混合生產者-消費者案例*  
 任何指定的執行緒都是新增和移除元素。  
  
 *加速*  
 相對於相同案例中的另一種類型，具有較快速的演算法效能。  
  
 *擴充性*  
 效能會隨著電腦上的核心數目等比例地增加。 在八個核心上進行擴充之演算法的執行速度，比兩個核心還要快。  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) 與 Queue(T) 的比較  
 在每個元素的處理時間都很小 (僅幾個指示) 的單純生產者-消費者案例中，比起具有外部鎖定的 <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>，<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> 能夠提供適度的效能優勢。 在此案例中，如果一個專用執行緒正在置入佇列，而且一個專用執行緒正在移出佇列，則 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 的執行效果最好。 如果您未強制執行這項規則，則 <xref:System.Collections.Generic.Queue%601> 的執行速度甚至會略高於具有多個核心之電腦上的 <xref:System.Collections.Concurrent.ConcurrentQueue%601>。  
  
 處理時間約 500 個 FLOPS (浮點作業) 或以上時，雙執行緒規則不適用於 <xref:System.Collections.Concurrent.ConcurrentQueue%601>，因此具有極佳的擴充性。 在此案例中，<xref:System.Collections.Generic.Queue%601> 不會加以適當調整。  
  
 在混合生產者-消費者案例中，處理時間很小時，具有外部鎖定的 <xref:System.Collections.Generic.Queue%601> 所進行的擴充優於 <xref:System.Collections.Concurrent.ConcurrentQueue%601>。 不過，處理時間大約 500 FLOPS 或以上時，則 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 會進行較佳的擴充。  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack 與堆疊  
 在處理時間很小的單純生產者-消費者案例中，<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName> 和具有外部鎖定的 <xref:System.Collections.Generic.Stack%601?displayProperty=fullName> 的效能可能會相同，都是具有一個專門推送的執行緒，以及另一個專門輸出的執行緒。 不過，執行緒數目增加時，兩種類型都會因競爭增加而變慢，而且 <xref:System.Collections.Generic.Stack%601> 的執行效果可能會優於 <xref:System.Collections.Concurrent.ConcurrentStack%601>。 處理時間大約 500 FLOPS 或以上時，兩種類型幾乎會以相同的速率進行擴充。  
  
 在混合生產者-消費者案例中，針對大型和小型工作負載，<xref:System.Collections.Concurrent.ConcurrentStack%601> 較為快速。  
  
 使用 <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> 和 <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> 可能會大幅加速存取時間。  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary 與字典  
 一般而言，請在同時從多個執行緒新增和更新索引鍵或值的所有案例中使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>。 在經常更新且讀取相對較少的情況下，<xref:System.Collections.Concurrent.ConcurrentDictionary%602> 一般會提供適度優點。 在進行許多讀取和更新的情況下，<xref:System.Collections.Concurrent.ConcurrentDictionary%602> 在具有任意數目之核心的電腦上明顯較快。  
  
 在需要經常更新的情況下，您可以增加 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 中的並行程度，然後測量以查看具有更多核心之電腦的效能是否增加。 如果您變更並行層級，請盡可能避免全域作業。  
  
 如果您只是要讀取索引鍵或值，則 <xref:System.Collections.Generic.Dictionary%602> 的速度會較快，原因是沒有任何執行緒修改字典時就不需要進行同步處理。  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 在單純生產者-消費者案例中，<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> 的執行速度可能會比其他並行集合類型還要慢。  
  
 在混合生產者-消費者案例中，針對大型和小型工作負載，<xref:System.Collections.Concurrent.ConcurrentBag%601> 一般都會比任何其他並行集合類型更為快速也更具擴充性。  
  
## <a name="blockingcollection"></a>BlockingCollection  
 需要界限和封鎖語意時，<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> 的執行速度可能會比任何自訂實作還要快。 它也支援大量取消、列舉和例外狀況處理。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Thread-Safe Collections](../../../../docs/standard/collections/thread-safe/index.md)   
 [平行程式設計](../../../../docs/standard/parallel-programming/index.md)
