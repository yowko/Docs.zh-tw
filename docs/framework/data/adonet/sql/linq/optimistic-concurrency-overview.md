---
title: 開放式並行存取：總覽
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: a6e654ea1ae199cb086e9377454d05e6eaa03ad6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64609958"
---
# <a name="optimistic-concurrency-overview"></a>開放式並行存取：總覽
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援開放式並行存取 (Optimistic Concurrency) 控制。 下表描述中的開放式並行存取的條款[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文件：  
  
|詞彙|描述|  
|-----------|-----------------|  
|並行|兩位以上的使用者同時嘗試更新相同資料庫資料列的情況。|  
|並行衝突|兩位以上的使用者同時嘗試將衝突值送出給資料列的一個或多個資料行的情況。|  
|並行控制|用來解決並行衝突的技術。|  
|開放式並行存取控制項|此種技術會先檢查資料列中的其他異動是否已變更值，才允許送出變更。<br /><br /> 與相反*封閉式並行控制*，後者會鎖定資料錄，避免並行存取衝突。<br /><br /> *開放式*因為認為干擾另一個可能的一筆交易的機會，因此則稱為控制項。|  
|衝突的解決方式|透過再次查詢資料庫，然後調整差異，以重新整理衝突項目的處理流程。<br /><br /> 重新整理物件時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 變更 Tracker 會保留下列資料：<br /><br /> -原本從資料庫取得，並用於更新值 核取。<br />來自後續查詢-新資料庫值。<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 接著會判斷物件是否發生衝突 (也就是，它的其中一個或多個成員值是否變更)。 如果物件是在發生衝突，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]接下來會判斷哪些成員為衝突。<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 發現的所有成員衝突都會加入至衝突清單中。|  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]物件模型*開放式並行存取衝突*下列兩個條件都成立時，就會發生：  
  
- 用戶端嘗試將變更送出給資料庫。  
  
- 資料庫中的一個或多個更新檢查值，自用戶端最後一次讀取之後已更新過。  
  
 解決這項衝突包括探索哪些物件成員發生衝突，然後決定要採取的動作。  
  
> [!NOTE]
>  只有對應成 <xref:System.Data.Linq.Mapping.UpdateCheck.Always> 或 <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> 的成員才會參與開放式並行存取檢查。 而不會檢查標記為 <xref:System.Data.Linq.Mapping.UpdateCheck.Never> 的成員。 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.UpdateCheck>。  
  
## <a name="example"></a>範例  
 例如，在下列案例中，User1 查詢資料庫中的資料列，開始準備更新。 User1 會接收到值為 Alfreds、Maria 和 Sales 的一個資料列。  
  
 User1 想將 Manager 資料行的值變更為 Alfred，並將 Department 資料行的值變更為 Marketing。 但是在 User1 送出那些變更之前，User2 就已經先送出變更給資料庫。 因此，現在 Assistant 資料行的值已變更為 Mary，而 Department 資料行的值已變更為 Service。  
  
 如果 User1 現在嘗試送出變更，則送出會失敗，而且會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況。 因為 Assistant 資料行和 Department 資料行的資料庫值並不是所預期的值，所以會發生這種結果。 因此表示 Assistant 和 Department 資料行的成員會產生衝突。 下表將摘要說明這種情況。  
  
||主管|Assistant|部門|  
|------|-------------|---------------|----------------|  
|原始狀態|Alfreds|Maria|Sales|  
|User1|Alfred||行銷|  
|User2||Mary|服務|  
  
 您可以使用不同方式來解決這類衝突。 如需詳細資訊，請參閱[如何：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)。  
  
## <a name="conflict-detection-and-resolution-checklist"></a>衝突偵測和解決檢查清單  
 您可以偵測和解決任何精細度等級的衝突。 其中一種極端的做法是，使用三種方式的其中一種方式來解決所有的衝突 (請參閱 <xref:System.Data.Linq.RefreshMode>)，而不考慮其他事項。 另一種極端的做法是，指定每個衝突成員之每種衝突類型的特定動作。  
  
- 指定或修訂物件模型中的 <xref:System.Data.Linq.Mapping.UpdateCheck> 選項。  
  
     如需詳細資訊，請參閱[如何：指定的成員會用於測試並行衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)。  
  
- 在 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 呼叫的 try/catch 區塊中，指定何時擲回例外狀況。  
  
     如需詳細資訊，請參閱[如何：指定時的並行存取例外狀況的擲回](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)。  
  
- 決定想要擷取的衝突詳細資料量，並據此將程式碼併入 try/catch 區域。  
  
     如需詳細資訊，請參閱[如何：擷取實體衝突資訊](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)和[How to:擷取成員衝突資訊](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)。  
  
- 包含在您`try` / `catch`您要如何解決發現之各種衝突的程式碼。  
  
     如需詳細資訊，請參閱[如何：保留資料庫值來解決衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)， [How to:覆寫資料庫值來解決衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)，和[How to:與資料庫值合併來解決衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)。  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>支援衝突探索和解決的 LINQ to SQL 型別  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中支援開放式並行存取衝突解決的類別和功能包括：  
  
- <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>另請參閱

- [如何：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
