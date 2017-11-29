---
title: "如何：以唯讀形式擷取資訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a9765d8d8330c7ad2a6e8cb25166427cdd9414a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-information-as-read-only"></a>如何：以唯讀形式擷取資訊
不想要變更資料時，可以搜尋唯讀結果以增加查詢效能。  
  
 將 <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 設定為 `false`，即可實作唯讀處理。  
  
> [!NOTE]
>  <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 設定為 `false` 時，<xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 會隱含地設定為 `false`。  
  
## <a name="example"></a>範例  
 下列程式碼會擷取員工雇用日期的唯讀集合。  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [查詢資料庫](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [延後執行與立即載入](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
