---
title: "資料繫結"
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
ms.assetid: cbec8b02-a1e8-4ae8-a83b-bb5190413ac5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7405cf37aaa21f8773952c9e7ed941bc8ae3150b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="data-binding"></a>資料繫結
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]支援與通用控制項，如方格控制項繫結。 具體來說，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]定義繫結至資料方格以及處理主從式繫結，都可以進行顯示和更新的基本模式。  
  
## <a name="underlying-principle"></a>基礎準則  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]將轉譯[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]to SQL 查詢，以便在資料庫上執行。 而產生的結果會是強型別 (Strongly Typed) `IEnumerable`。 因為這些物件是一般 common language runtime (CLR) 物件，所以一般物件資料繫結可用來顯示結果。 另一方面，變更作業 (插入、更新和刪除) 則需要額外的步驟。  
  
## <a name="operation"></a>運算  
 實作 <xref:System.ComponentModel.IListSource>，就可以隱含地繫結至 Windows Forms 控制項。 C# 中的資料來源泛型 <xref:System.Data.Linq.Table%601> (C# 中的 `Table<T>` 或 `Table(Of T)` 中的 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) 和泛型 `DataQuery` 已更新為實作 <xref:System.ComponentModel.IListSource>。 使用者介面 (UI) 資料繫結引擎 (Windows Form 和 Windows Presentation Foundation) 兩者都會測試其資料來源是否實作 <xref:System.ComponentModel.IListSource>。 因此，撰寫查詢直接對資料來源控制項的隱含地呼叫[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]集合產生，如下列範例所示：  
  
 [!code-csharp[DLinqDataBinding#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#1)]
 [!code-vb[DLinqDataBinding#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#1)]  
  
 而 Windows Presentation Foundation 也會發生相同的狀況：  
  
 [!code-csharp[DLinqDataBinding#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDataBinding/cs/Program.cs#2)]
 [!code-vb[DLinqDataBinding#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDataBinding/vb/Module1.vb#2)]  
  
 集合產生是透過 <xref:System.Data.Linq.Table%601> 中的泛型 `DataQuery` 和泛型 <xref:System.ComponentModel.IListSource.GetList%2A> 予以實作。  
  
## <a name="ilistsource-implementation"></a>IListSource 實作  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]實作<xref:System.ComponentModel.IListSource>在兩個位置：  
  
-   資料來源是<xref:System.Data.Linq.Table%601>:[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]瀏覽資料表以填入`DataBindingList`集合會保存在資料表上的參考。  
  
-   資料來源是 <xref:System.Linq.IQueryable%601>。 有兩種案例：  
  
    -   如果[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]找到基礎<xref:System.Data.Linq.Table%601>從<xref:System.Linq.IQueryable%601>、 來源會允許進行編輯，而且狀況與第一點相同。  
  
    -   如果[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]找不到基礎<xref:System.Data.Linq.Table%601>，來源不允許進行編輯 (例如， `groupby`)。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]瀏覽查詢以填入泛型`SortableBindingList`，這是簡單<xref:System.ComponentModel.BindingList%601>實作之 T 實體的給定屬性的排序功能。  
  
## <a name="specialized-collections"></a>特定的集合  
 <xref:System.ComponentModel.BindingList%601> 已針對本文件之前描述的許多功能，特殊化為一些不同類別。 這些類別是泛型 `SortableBindingList` 和泛型 `DataBindingList`。 這兩種類別都是宣告為內部。  
  
### <a name="generic-sortablebindinglist"></a>泛型 SortableBindingList  
 這個類別繼承自 <xref:System.ComponentModel.BindingList%601>，而且是 <xref:System.ComponentModel.BindingList%601> 的可排序版本。 排序動作僅在記憶體中執行，並不會連絡資料庫本身。 <xref:System.ComponentModel.BindingList%601> 會實作 <xref:System.ComponentModel.IBindingList>，但是預設不支援排序。 不過，<xref:System.ComponentModel.BindingList%601>實作<xref:System.ComponentModel.IBindingList>虛擬*核心*方法。 您可以輕鬆地覆寫這些方法。 泛型 `SortableBindingList` 會覆寫 <xref:System.ComponentModel.BindingList%601.SupportsSortingCore%2A>、<xref:System.ComponentModel.BindingList%601.SortPropertyCore%2A>、<xref:System.ComponentModel.BindingList%601.SortDirectionCore%2A> 和 <xref:System.ComponentModel.BindingList%601.ApplySortCore%2A>。 `ApplySortCore` 是透過 <xref:System.ComponentModel.IBindingList.ApplySort%2A> 進行呼叫，而且會排序所指定屬性的 T 項目清單。  
  
 如果屬性不屬於 T，則會引發例外狀況 (Exception)。  
  
 為了進行排序，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]建立泛型`SortableBindingList.PropertyComparer`繼承自泛型類別<xref:System.Collections.Generic.Comparer%601.System%23Collections%23IComparer%23Compare%2A>和實作指定的型別 T 的預設比較子、 `PropertyDescriptor`，和方向。 這個類別會動態建立 T 的 `Comparer`，其中 T 是 `PropertyType` 的 `PropertyDescriptor`。 然後，會從靜態泛型 `Comparer` 中擷取預設比較子。 而預設執行個體是使用反映 (Reflection) 取得。  
  
 泛型 `SortableBindingList` 也是 `DataBindingList` 的基底類別。 泛型 `SortableBindingList` 提供兩種虛擬方法，以暫止或繼續項目的新增/移除追蹤 (Tracking)。 這兩種方法都適用於排序這類的基本功能，但是會由泛型 `DataBindingList` 這類的上層類別實際實作。  
  
### <a name="generic-databindinglist"></a>泛型 DataBindingList  
 這個類別繼承自泛型 `SortableBindingLIst`。 泛型 `DataBindingList` 會保存對泛型 `Table` 之基礎泛型 `IQueryable` (用於初始填入集合) 的參考。 泛型 `DatabindingList` 會覆寫 `InsertItem`() 和 `RemoveItem`()，以將項目新增/移除的追蹤加入至集合。 也會實作抽象的暫止/繼續追蹤功能，讓追蹤具有條件性。 這個功能可以讓泛型 `DataBindingList` 利用父類別之追蹤功能的所有多型使用。  
  
## <a name="binding-to-entitysets"></a>繫結至 EntitySet  
 因為 `EntitySet` 已經是實作 `EntitySet` 的集合，所以繫結至 <xref:System.ComponentModel.IBindingList> 是特殊情況。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]加入排序和取消 (<xref:System.ComponentModel.ICancelAddNew>) 支援。 `EntitySet` 類別會使用內部清單來儲存實體。 這份清單是以泛型陣列 (泛型 `ItemList` 類別) 為基礎的低階集合。  
  
### <a name="adding-a-sorting-feature"></a>加入排序功能  
 陣列提供的排序方法 (`Array.Sort()`) 可以與 T 的 `Comparer` 搭配使用。而 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會使用本主題之前所述的泛型 `SortableBindingList.PropertyComparer` 類別，來取得屬性的這個 `Comparer` 以及排序方向。 `ApplySort` 方法會加入至泛型 `ItemList`，以呼叫這個功能。  
  
 您現在必須在 `EntitySet` 端上宣告排序支援：  
  
-   <xref:System.ComponentModel.IBindingList.SupportsSorting%2A> 會傳回 `true`。  
  
-   <xref:System.ComponentModel.IBindingList.ApplySort%2A> 會呼叫 `entities.ApplySort()`，然後呼叫 `OnListChanged()`。  
  
-   <xref:System.ComponentModel.IBindingList.SortDirection%2A> 和 <xref:System.ComponentModel.IBindingList.SortProperty%2A> 屬性會公開 (Expose) 目前儲存在本機成員中的排序定義。  
  
 當您使用 System.Windows.Forms.BindingSource 並繫結 EntitySet\<TEntity > 至 system.windows.forms.bindingsource.datasource 時，您必須呼叫 EntitySet\<Tentity >。GetNewBindingList 來更新 BindingSource.List。  
  
 如果您使用 System.Windows.Forms.BindingSource 並設定 BindingSource.DataMember 屬性，將 BindingSource.DataSource 設定為具有名為 bindingsource.datamember 之公開 EntitySet 屬性的類別，\<TEntity >，您不必呼叫 EntitySet\<Tentity >。GetNewBindingList 來更新 BindingSource.List，但您會遺失排序功能。  
  
## <a name="caching"></a>快取  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]查詢實作<xref:System.ComponentModel.IListSource.GetList%2A>。 Windows Forms BindingSource 類別符合這個介面時，會針對單一連接呼叫三次 GetList()。 若要解決此情況下，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]實作每個執行個體以儲存且一律傳回相同的產生集合的快取。  
  
## <a name="cancellation"></a>取消  
 <xref:System.ComponentModel.IBindingList> 定義 <xref:System.ComponentModel.IBindingList.AddNew%2A> 方法，讓控制項用來從繫結集合建立新項目。 `DataGridView` 控制項會在最後一個可見資料列的標頭顯示星號，能充分地呈現這個功能特徵。 星號表示您可以加入新的項目。  
  
 除了這個功能之外，集合也可以實作 <xref:System.ComponentModel.ICancelAddNew>。 這個功能允許控制項取消或驗證是否已驗證過新的編輯過項目。  
  
 <xref:System.ComponentModel.ICancelAddNew> 是在所有 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 資料繫結集合中實作 (泛型 `SortableBindingList` 和泛型 `EntitySet`)。 在這兩個實作中，程式碼執行如下：  
  
-   允許項目插入後又從集合中移除。  
  
-   只要 UI 未認可編輯，就不追蹤變更。  
  
-   只要取消編輯，就不追蹤變更 (<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>)。  
  
-   允許在認可編輯時進行追蹤 (<xref:System.ComponentModel.ICancelAddNew.EndNew%2A>)。  
  
-   如果新項目不是來自 <xref:System.ComponentModel.IBindingList.AddNew%2A>，則讓集合正常運作。  
  
## <a name="troubleshooting"></a>疑難排解  
 本節會呼叫數個項目，協助您疑難排解 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 資料繫結應用程式。  
  
-   您必須使用屬性，只使用欄位是不夠的。 Windows Forms 需要這種使用方式。  
  
-   根據預設， `image`， `varbinary`，和`timestamp`資料庫型別對應至位元組陣列。 因為此案例不支援 `ToString()`，所以無法顯示這些物件。  
  
-   對應到主索引鍵的類別成員會有 setter，但是[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]不支援物件識別變更。 因此，無法更新資料庫中用於對應的主/唯一索引鍵。 在方格中的變更會造成例外狀況，當您呼叫<xref:System.Data.Linq.DataContext.SubmitChanges%2A>。  
  
-   如果實體是繫結在兩個不同方格中 (例如，一個是主版方格，而另一個詳細方格)，則主版方格中的 `Delete` 不會散佈至詳細方格。  
  
## <a name="see-also"></a>另請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
