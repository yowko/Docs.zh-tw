---
title: 物件狀態和變更追蹤
ms.date: 03/30/2017
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
ms.openlocfilehash: 89e9f44a6cd3579a5ef9cc2078609ca26e0d2ae5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683306"
---
# <a name="object-states-and-change-tracking"></a>物件狀態和變更追蹤
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件一律會處於某種*狀態*。 例如，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 建立新物件時，該物件會是 `Unchanged` 狀態。 您自己建立的新物件不知道<xref:System.Data.Linq.DataContext>且位於`Untracked`狀態。 順利執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 之後，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 得知的所有物件都會是 `Unchanged` 狀態  (唯一的例外是已順利從資料庫中刪除的物件，這些物件是 `Deleted` 狀態，而且無法在該 <xref:System.Data.Linq.DataContext> 執行個體中使用)。  
  
## <a name="object-states"></a>物件狀態  
 下表列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件的可能狀態。  
  
|狀態|描述|  
|-----------|-----------------|  
|`Untracked`|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 無法追蹤的物件。 範例包含下列：<br /><br /> -未透過目前查詢物件<xref:System.Data.Linq.DataContext>（例如新建立的物件）。<br />-建立透過還原序列化的物件<br />-透過不同的查詢物件<xref:System.Data.Linq.DataContext>。|  
|`Unchanged`|使用 <xref:System.Data.Linq.DataContext> 擷取而且已知自建立後尚未修改的物件。|  
|`PossiblyModified`|物件，即*附加*至<xref:System.Data.Linq.DataContext>。 如需詳細資訊，請參閱 <<c0> [ 資料擷取和 CUD 作業 (LINQ to SQL) 的多層式架構應用程式中](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)。|  
|`ToBeInserted`|未使用目前 <xref:System.Data.Linq.DataContext> 擷取的物件。 這會導致 `INSERT` 期間執行資料庫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 動作。|  
|`ToBeUpdated`|已知自擷取後曾經修改的物件。 這會導致 `UPDATE` 期間執行資料庫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 動作。|  
|`ToBeDeleted`|標記要刪除的物件，這會導致在 `DELETE` 期間執行資料庫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 動作。|  
|`Deleted`|已在資料庫中刪除的物件。 這個狀態為最終狀態，不允許進行其他轉換。|  
  
## <a name="inserting-objects"></a>插入物件  
 您可以使用 `Inserts` 明確要求執行 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>。 或者，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]可以推斷`Inserts`尋找連接至其中一個必須更新的已知物件的物件。 比方說，如果您加入`Untracked`物件至<xref:System.Data.Linq.EntitySet%601>或設定<xref:System.Data.Linq.EntityRef%601>要`Untracked`物件，`Untracked`可透過圖形中的追蹤物件的物件。 在處理過程<xref:System.Data.Linq.DataContext.SubmitChanges%2A>，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]周遊已追蹤的物件，並會探索並不會追蹤任何連線到持續性物件。 這些物件會成為等候插入資料庫中的項目。  
  
 繼承階層架構中的類別<xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>(`o`) 也會指定為成員的值設定*鑑別子*來比對的物件型別`o`。 當型別符合預設鑑別子值時，這個動作會導致鑑別子值遭預設值覆寫。 如需詳細資訊，請參閱 <<c0> [ 繼承支援](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)。  
  
> [!IMPORTANT]
>  已加入至 `Table` 的物件不會出現在識別 (Identity) 快取中。 識別快取只會反映從資料庫擷取的物件。 呼叫 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> 之後，除非 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 順利完成，否則加入的實體都不會出現在對資料庫的查詢中。  
  
## <a name="deleting-objects"></a>刪除物件  
 您可以在適當的 `o` 上呼叫 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>(o)，將已追蹤的物件 <xref:System.Data.Linq.Table%601> 標記為要刪除。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 考慮從物件移除<xref:System.Data.Linq.EntitySet%601>為更新作業，並對應的外部索引鍵值設定為 null。 作業的目標 (`o`) 並不會從其資料表中刪除。 例如，`cust.Orders.DeleteOnSubmit(ord)` 所表示的更新，是將外部索引鍵 `cust` 設為 null 來切斷 `ord` 和 `ord.CustomerID` 之間的關聯性 (Relationship)。 這並不會刪除 `ord` 所對應的資料列。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 執行下列的處理時刪除物件 (<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>) 從其資料表：  
  
-   呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，會對該物件執行 `DELETE` 作業。  
  
-   不論是否已載入相關物件，移除作業都不會擴及相關物件。 具體來說，並不會載入相關物件來更新關聯性屬性。  
  
-   順利執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 之後，物件會設為 `Deleted` 狀態。 因此，您無法使用該物件也無法使用其在該 `id` 中的 <xref:System.Data.Linq.DataContext>。 由 <xref:System.Data.Linq.DataContext> 執行個體維護的內部快取並不會刪除已擷取或新加入的物件，即使物件已從資料庫中刪除也一樣。  
  
 您只可以對 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> 所追蹤的物件呼叫 <xref:System.Data.Linq.DataContext>。 至於 `Untracked` 物件，您必須先呼叫 <xref:System.Data.Linq.Table%601.Attach%2A>，然後再呼叫 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>。 對 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> 物件呼叫 `Untracked` 會擲回例外狀況。  
  
> [!NOTE]
>  從資料表中移除物件會告訴[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]來產生對應的 SQL`DELETE`命令時<xref:System.Data.Linq.DataContext.SubmitChanges%2A>。 這個動作並不會從快取中移除物件，也不會將刪除作業擴及相關的物件。  
>   
>  若要回收已刪除物件的 `id`，請使用新的 <xref:System.Data.Linq.DataContext> 執行個體。 清除的相關物件，您可以使用*串聯刪除*功能的資料庫，或自行手動刪除相關聯的物件。  
>   
>  刪除相關的物件時不必按照任何特定順序 (不像在資料庫中)。  
  
## <a name="updating-objects"></a>更新物件  
 您可以藉由觀察有沒有變更告知來偵測 `Updates`。 告知是透過屬性 setter 中的 <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> 事件來提供。 當 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 獲知物件第一次受到變更時，它會建立物件的複本並且將此物件列為要產生 `Update` 陳述式的對象。  
  
 物件不會實作<xref:System.ComponentModel.INotifyPropertyChanging>，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]會保留一份他們已初次具體化時，已有物件的值。 當您呼叫<xref:System.Data.Linq.DataContext.SubmitChanges%2A>，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]比較來決定物件是否已變更的最大值目前和原始值。  
  
 如果是要更新關聯性，則子系 (Child) 對父代 (Parent) 的參考 (也就是對應於外部索引鍵的參考) 會是最主要的參考。 反方向 (也就是父代對子系的參考) 的參考則為選擇性的。 關聯性類別 (<xref:System.Data.Linq.EntitySet%601> 和 <xref:System.Data.Linq.EntityRef%601>) 會保證一對多和一對一關聯性中的雙向參考都是一致的。 如果物件模型未使用 <xref:System.Data.Linq.EntitySet%601> 或 <xref:System.Data.Linq.EntityRef%601>，而反向參考存在，您就有責任使它在更新關聯性後，與向前參考 (Forward Reference) 一致。  
  
 如果要同時更新必要的參考和對應的外部索引鍵，就必須確定兩者一致。 如果在您呼叫 <xref:System.InvalidOperationException> 時這兩者並未同步，則會擲回 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 例外狀況。 雖然只要變更外部索引鍵值就能更新基礎資料列，但您仍應該變更參考，以維護物件圖形中的連接並保持雙向關聯性的一致性。  
  
## <a name="see-also"></a>另請參閱
- [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [插入、更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)
