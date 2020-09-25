---
title: 作法：關閉延後載入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: b2193e7e8bda396451274d2da96e7cb86774fd03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196958"
---
# <a name="how-to-turn-off-deferred-loading"></a>作法：關閉延後載入

您可以將 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 設定為 `false`，以關閉延後載入。 如需詳細資訊，請參閱 [延後和立即載入](deferred-versus-immediate-loading.md)。  
  
> [!NOTE]
> 關閉物件追蹤時，也會隱含地關閉延後載入。 如需詳細資訊，請參閱 [如何：以唯讀形式取出資訊](how-to-retrieve-information-as-read-only.md)。  
  
## <a name="example"></a>範例  

 下列範例顯示如何將 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 設定為 `false`，以關閉延後載入。  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [查詢概念](query-concepts.md)
- [查詢資料庫](querying-the-database.md)
