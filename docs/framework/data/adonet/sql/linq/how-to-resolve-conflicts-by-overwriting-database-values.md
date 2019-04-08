---
title: HOW TO：藉由覆寫資料庫值來解決衝突
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 7b8d7cf8ab2335c064062ed3ab4072d81e8042fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189114"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>HOW TO：藉由覆寫資料庫值來解決衝突
若要先協調預期和實際資料庫值之間的差異再重新送出變更，可以使用 <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> 覆寫資料庫值。 如需詳細資訊，請參閱[開放式並行存取：概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。  
  
> [!NOTE]
>  在所有情況下，擷取資料庫中更新過的資料會先重新整理用戶端上的資料錄。 這個動作可確保下一次嘗試更新時，不會在相同的並行存取檢查時失敗。  
  
## <a name="example"></a>範例  
 在這個案例下，當 User1 嘗試送出變更時，因為 User2 同時變更了 Assistant 和 Department 資料行，所以會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況。 下表顯示這個情況。  
  
||主管|Assistant|部門|  
|------|-------------|---------------|----------------|  
|User1 和 User2 查詢時的原始資料庫狀態。|Alfreds|Maria|Sales|  
|User1 準備送出這些變更。|Alfred||行銷|  
|User2 已送出這些變更。||Mary|服務|  
  
 User1 決定以目前的用戶端成員值覆寫資料庫值，來解決這個衝突。  
  
 User1 使用 <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> 解決衝突時，資料庫中的結果會如同下表：  
  
||主管|Assistant|部門|  
|------|-------------|---------------|----------------|  
|解決衝突後的新狀態。|Alfred<br /><br /> (來自 User1)|Maria<br /><br /> (原始)|行銷<br /><br /> (來自 User1)|  
  
 下列範例程式碼顯示如何以目前的用戶端成員值來覆寫資料庫值  (但不會對個別成員衝突進行任何檢查或自訂處理)。  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
