---
title: 作法：以唯讀形式擷取資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
ms.openlocfilehash: 399bf44ef5536a9adebf1cad590439741df998f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793310"
---
# <a name="how-to-retrieve-information-as-read-only"></a>作法：以唯讀形式擷取資訊
不想要變更資料時，可以搜尋唯讀結果以增加查詢效能。  
  
 將 <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 設定為 `false`，即可實作唯讀處理。  
  
> [!NOTE]
> <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 設定為 `false` 時，<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 會隱含地設定為 `false`。  
  
## <a name="example"></a>範例  
 下列程式碼會擷取員工雇用日期的唯讀集合。  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [查詢概念](query-concepts.md)
- [查詢資料庫](querying-the-database.md)
- [延後與立即載入的比較](deferred-versus-immediate-loading.md)
