---
title: "如何：從 BlockingCollection 個別加入和擷取項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
caps.latest.revision: 7
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 66b4e921a4c7285976694f4633ce1eeaadcb7cf9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/19/2017

---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a>如何：從 BlockingCollection 個別加入和擷取項目
本範例示範如何利用封鎖方式和非封鎖方式，在 <xref:System.Collections.Concurrent.BlockingCollection%601> 中加入和移除項目。 如需 <xref:System.Collections.Concurrent.BlockingCollection%601> 的詳細資訊，請參閱 [BlockingCollection 概觀](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)。  
  
 如需如何列舉 <xref:System.Collections.Concurrent.BlockingCollection%601> 直到其為空的以及無法再新增項目的範例，請參閱[如何：使用 ForEach 來移除 BlockingCollection 中的項目](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)。  
  
## <a name="example"></a>範例  
 第一個範例示範如何加入和擷取項目，以便在集合暫時空白 (擷取時)、達到最大容量 (加入時) 或超過指定的逾時期限時封鎖作業。 請注意，只有在已建立 BlockingCollection，並在建構函式中指定最大容量時，才會啟用最大容量封鎖。  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a>範例  
 第二個範例示範如何加入和擷取項目，而不會封鎖作業。 如果沒有任何項目、已達到界限集合的最大容量或超過逾時期限，則 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 或 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 作業會傳回 false。 如此便可讓執行緒在一段時間內先執行其他一些有用的工作，再於稍後重試擷取新的項目，或嘗試加入之前無法加入的相同項目。 這個程式也會示範如何在存取 <xref:System.Collections.Concurrent.BlockingCollection%601> 時實作取消作業。  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [BlockingCollection 概觀](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)

