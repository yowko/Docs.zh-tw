---
title: 如何：在 ConcurrentDictionary 中加入和移除項目
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6aa309f2c6c44934f491229ac43003a05301bacb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569742"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>如何：在 ConcurrentDictionary 中加入和移除項目
這個範例示範如何新增、擷取、更新和移除 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> 中的項目。 這個集合類別是安全執行緒實作。 只要多個執行緒可能嘗試同時存取元素，就建議您使用它。  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>供幾種便利的方法，讓程式碼不需要在嘗試新增或移除資料之前，先檢查索引鍵存在與否。 下表列出這些便利方法，並描述其使用時機。  
  
|方法|使用時機...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|您想要新增所指定索引鍵的新值，如果已經有索引鍵，則您會想要取代它的值。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|您想要擷取所指定索引鍵的現有值，如果索引鍵不存在，則您會想要指定索引鍵/值組。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|您想要新增、取得、更新或移除索引鍵/值組，如果已經有索引鍵，或嘗試因任何其他原因而失敗，則您會想要採取一些替代動作。|  
  
## <a name="example"></a>範例  
 下列範例使用兩個 <xref:System.Threading.Tasks.Task> 執行個體同時將一些項目新增至 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>，然後輸出所有內容以顯示已成功新增項目。 此範例也會示範如何使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 方法，在集合中加入、更新和擷取項目。  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 是針對多執行緒案例所設計。 您不需要在程式碼中使用鎖定，即可新增或移除集合中的項目。 不過，其中一個執行緒一定要可以擷取一個值，而另一個執行緒要將新的值提供給相同的索引鍵來立即更新集合。  
  
 此外，雖然 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的所有方法都是安全執行緒，但是並非所有方法都是不可部分完成，尤其是 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>。 傳遞給這些方法的使用者委派是在字典內部鎖定外部進行叫用 (完成這項作業是要防止未知程式碼封鎖所有執行緒)。因此，可能會發生這系列的事件︰  
  
 1\) threadA 會呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>、找不到項目，並叫用 valueFactory 委派來建立要新增的新項目。  
  
 2\) threadB 同時呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>、叫用其 valueFactory 委派，並且在 threadA 之前到達內部鎖定，因此會將其新的索引鍵/值組新增至字典。  
  
 3\) threadA 的使用者委派完成，而且執行緒到達鎖定，但現在會看到這個項目已存在。  
  
 4\) threadA 執行 "Get"，並傳回 threadB 先前所加入的資料。  
  
 因此，不保證 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 所傳回的資料就是執行緒 valueFactory 所建立的相同資料。 呼叫 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> 時，可能會發生一系列類似的事件。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [安全執行緒集合](../../../../docs/standard/collections/thread-safe/index.md)
