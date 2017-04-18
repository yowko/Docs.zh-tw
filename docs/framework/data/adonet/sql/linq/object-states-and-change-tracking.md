---
title: "物件狀態和變更追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a808b00-9c3c-479a-aa94-717280fefd71
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 物件狀態和變更追蹤
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件一律會處於某種「*狀態*」\(State\)。  例如，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 建立新物件時，該物件會是 `Unchanged` 狀態。  您自己建立新的物件時，由於 <xref:System.Data.Linq.DataContext> 還不知道該物件，所以該物件會是 `Untracked` 狀態。  順利執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 之後，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 得知的所有物件都會是 `Unchanged` 狀態   \(唯一的例外是已順利從資料庫中刪除的物件，這些物件是 `Deleted` 狀態，而且無法在該 <xref:System.Data.Linq.DataContext> 執行個體中使用\)。  
  
## 物件狀態  
 下表列出 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件的可能狀態。  
  
|狀態|描述|  
|--------|--------|  
|`Untracked`|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 無法追蹤的物件。  範例包含下列：<br /><br /> -   未透過目前 <xref:System.Data.Linq.DataContext> 查詢的物件 \(例如新建立的物件\)。<br />-   透過還原序列化 \(Deserialization\) 建立的物件。<br />-   透過不同 <xref:System.Data.Linq.DataContext> 查詢的物件。|  
|`Unchanged`|使用 <xref:System.Data.Linq.DataContext> 擷取而且已知自建立後尚未修改的物件。|  
|`PossiblyModified`|「*附加*」\(Attached\) 至 <xref:System.Data.Linq.DataContext> 的物件。  如需詳細資訊，請參閱[N\-Tier 應用程式中的資料擷取和 CUD 作業 \(LINQ to SQL\)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)。|  
|`ToBeInserted`|未使用目前 <xref:System.Data.Linq.DataContext> 擷取的物件。  這會導致 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 期間執行資料庫 `INSERT` 動作。|  
|`ToBeUpdated`|已知自擷取後曾經修改的物件。  這會導致 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 期間執行資料庫 `UPDATE` 動作。|  
|`ToBeDeleted`|標記要刪除的物件，這會導致在 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 期間執行資料庫 `DELETE` 動作。|  
|`Deleted`|已在資料庫中刪除的物件。  這個狀態為最終狀態，不允許進行其他轉換。|  
  
## 插入物件  
 您可以使用 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> 明確要求執行 `Inserts`。  此外，如果有物件連接至已知必須要更新的物件，則 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會在發現該物件時推斷要執行 `Inserts`。  例如，如果您將 `Untracked` 物件加入至 <xref:System.Data.Linq.EntitySet%601> 或將 <xref:System.Data.Linq.EntityRef%601> 設為 `Untracked` 物件，則 `Untracked` 物件會變成可以經由圖形中的已追蹤物件被接觸到。  處理 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會周遊已追蹤的物件並且搜尋任何可接觸到的未追蹤持續性 \(Persistent\) 物件。  這些物件會成為等候插入資料庫中的項目。  
  
 對於在繼承階層架構 \(Inheritance Hierarchy\) 中的類別，<xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>\(`o`\) 也會將類別中已指定為「*鑑別子*」\(Discriminator\) 之成員的值，設定為符合物件 `o` 的型別。  當型別符合預設鑑別子值時，這個動作會導致鑑別子值遭預設值覆寫。  如需詳細資訊，請參閱[繼承支援](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)。  
  
> [!IMPORTANT]
>  已加入至 `Table` 的物件不會出現在識別 \(Identity\) 快取中。  識別快取只會反映從資料庫擷取的物件。  呼叫 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> 之後，除非 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 順利完成，否則加入的實體都不會出現在對資料庫的查詢中。  
  
## 刪除物件  
 您可以在適當的 <xref:System.Data.Linq.Table%601> 上呼叫 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>\(o\)，將已追蹤的物件 `o` 標記為要刪除。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將從 <xref:System.Data.Linq.EntitySet%601> 中移除物件的動作視為更新作業，而且對應的外部索引鍵值會設為 null。  作業的目標 \(`o`\) 並不會從其資料表中刪除。  例如，`cust.Orders.DeleteOnSubmit(ord)` 所表示的更新，是將外部索引鍵 `ord.CustomerID` 設為 null 來切斷 `cust` 和 `ord` 之間的關聯性 \(Relationship\)。  這並不會刪除 `ord` 所對應的資料列。  
  
 從資料表中刪除 \(<xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>\) 物件時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會執行下列處理：  
  
-   呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，會對該物件執行 `DELETE` 作業。  
  
-   不論是否已載入相關物件，移除作業都不會擴及相關物件。  具體來說，並不會載入相關物件來更新關聯性屬性。  
  
-   順利執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 之後，物件會設為 `Deleted` 狀態。  因此，您無法使用該物件也無法使用其在該 <xref:System.Data.Linq.DataContext> 中的 `id`。  由 <xref:System.Data.Linq.DataContext> 執行個體維護的內部快取並不會刪除已擷取或新加入的物件，即使物件已從資料庫中刪除也一樣。  
  
 您只可以對 <xref:System.Data.Linq.DataContext> 所追蹤的物件呼叫 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>。  至於 `Untracked` 物件，您必須先呼叫 <xref:System.Data.Linq.Table%601.Attach%2A>，然後再呼叫 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>。  對 `Untracked` 物件呼叫 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> 會擲回例外狀況。  
  
> [!NOTE]
>  從資料表中移除物件，會告訴 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 要在執行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時產生對應的 SQL `DELETE` 命令。  這個動作並不會從快取中移除物件，也不會將刪除作業擴及相關的物件。  
>   
>  若要回收已刪除物件的 `id`，請使用新的 <xref:System.Data.Linq.DataContext> 執行個體。  若要清除相關的物件，您可以使用資料庫的「*串聯刪除*」\(Cascade Delete\) 功能，或自行手動刪除相關物件。  
>   
>  刪除相關的物件時不必按照任何特定順序 \(不像在資料庫中\)。  
  
## 更新物件  
 您可以藉由觀察有沒有變更告知來偵測 `Updates`。  告知是透過屬性 setter 中的 <xref:System.ComponentModel.INotifyPropertyChanging.PropertyChanging> 事件來提供。  當 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 獲知物件第一次受到變更時，它會建立物件的複本並且將此物件列為要產生 `Update` 陳述式的對象。  
  
 如果是未實作 <xref:System.ComponentModel.INotifyPropertyChanging> 的物件，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會記錄物件初次具體化時具有的值。  當您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 就會比較目前的值與原始值，以判斷物件是否已變更。  
  
 如果是要更新關聯性，則子系 \(Child\) 對父代 \(Parent\) 的參考 \(也就是對應於外部索引鍵的參考\) 會是最主要的參考。  反方向 \(也就是父代對子系的參考\) 的參考則為選擇性的。  關聯性類別 \(<xref:System.Data.Linq.EntitySet%601> 和 <xref:System.Data.Linq.EntityRef%601>\) 會保證一對多和一對一關聯性中的雙向參考都是一致的。  如果物件模型未使用 <xref:System.Data.Linq.EntitySet%601> 或 <xref:System.Data.Linq.EntityRef%601>，而反向參考存在，您就有責任使它在更新關聯性後，與向前參考 \(Forward Reference\) 一致。  
  
 如果要同時更新必要的參考和對應的外部索引鍵，就必須確定兩者一致。  如果在您呼叫 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 時這兩者並未同步，則會擲回 <xref:System.InvalidOperationException> 例外狀況。  雖然只要變更外部索引鍵值就能更新基礎資料列，但您仍應該變更參考，以維護物件圖形中的連接並保持雙向關聯性的一致性。  
  
## 請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [插入、更新和刪除作業](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)