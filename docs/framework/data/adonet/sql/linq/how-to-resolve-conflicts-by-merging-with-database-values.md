---
title: "如何：藉由與資料庫值合併來解決衝突"
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
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8e5114052951950c5866d80c974555678b1d040a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>如何：藉由與資料庫值合併來解決衝突
若要先協調預期和實際資料庫值之間的差異再重新送出變更，可以使用 <xref:System.Data.Linq.RefreshMode.KeepChanges> 來合併資料庫值與目前用戶端成員值。 如需詳細資訊，請參閱[開放式並行存取： 概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。  
  
> [!NOTE]
>  在所有情況下，擷取資料庫中更新過的資料會先重新整理用戶端上的資料錄。 這個動作可確保下一次嘗試更新時，不會在相同的並行存取檢查時失敗。  
  
## <a name="example"></a>範例  
 在這個案例下，當 User1 嘗試送出變更時，因為 User2 同時變更了 Assistant 和 Department 資料行，所以會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況。 下表顯示這個情況。  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|User1 和 User2 查詢時的原始資料庫狀態。|Alfreds|Maria|Sales|  
|User1 準備送出這些變更。|Alfred||Marketing|  
|User2 已送出這些變更。||Mary|服務|  
  
 User1 決定合併資料庫值與目前用戶端成員值，來解決這個衝突。 這樣只有在目前變更集也修改該值時，才會覆寫資料庫值。  
  
 User1 使用 <xref:System.Data.Linq.RefreshMode.KeepChanges> 解決衝突時，資料庫中的結果會如同下表：  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|解決衝突後的新狀態。|Alfred<br /><br /> (來自 User1)|Mary<br /><br /> (來自 User2)|Marketing<br /><br /> (來自 User1)|  
  
 下列範例顯示如何合併資料庫值與目前用戶端成員值 (除非用戶端也變更該值)。 但不會對個別成員衝突進行任何檢查或自訂處理。  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 覆寫資料庫值來解決衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [如何： 解決衝突，藉由保留資料庫值](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [如何： 管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
