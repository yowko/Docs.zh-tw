---
title: 作法：藉由保留資料庫值來解決衝突
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: b6f9b0308bcbf53a89ae0690ed44db0a364aef0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191693"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>作法：藉由保留資料庫值來解決衝突

若要先協調預期和實際資料庫值之間的差異再重新送出變更，可以使用 <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> 將找到的值保留在資料庫中。 這樣會覆寫物件模型 (Object Model) 中的目前值。 如需詳細資訊，請參閱 [開放式平行存取：總覽](optimistic-concurrency-overview.md)。  
  
> [!NOTE]
> 在所有情況下，擷取資料庫中更新過的資料會先重新整理用戶端上的資料錄。 這個動作可確保下一次嘗試更新時，不會在相同的並行存取檢查時失敗。  
  
## <a name="example"></a>範例  

 在這個案例下，當 User1 嘗試送出變更時，因為 User2 同時變更了 Assistant 和 Department 資料行，所以會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況。 下表顯示這個情況。  
  
||Manager|Assistant|department|  
|------|-------------|---------------|----------------|  
|User1 和 User2 查詢時的原始資料庫狀態。|Alfreds|Maria|Sales|  
|User1 準備送出這些變更。|Alfred||Marketing|  
|User2 已送出這些變更。||Mary|服務|  
  
 User1 決定讓較新的資料庫值覆寫物件模型中的目前值，來解決這個衝突。  
  
 User1 使用 <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> 解決衝突時，資料庫中的結果會如同下表：  
  
||Manager|Assistant|department|  
|------|-------------|---------------|----------------|  
|解決衝突後的新狀態。|Alfreds<br /><br /> (原始)|Mary<br /><br /> (來自 User2)|服務<br /><br /> (來自 User2)|  
  
 下列範例程式碼顯示如何使用資料庫值來覆寫物件模型中的目前值  (但不會對個別成員衝突進行任何檢查或自訂處理)。  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [作法：管理變更衝突](how-to-manage-change-conflicts.md)
