---
title: 合併資料集內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: 38d716552c4a52e01ef803ce197e4d588ed562c3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44202267"
---
# <a name="merging-dataset-contents"></a>合併資料集內容
您可以使用 <xref:System.Data.DataSet.Merge%2A> 方法，將 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 陣列的內容合併至現有的 `DataSet` 中。 有許多因素和選項會影響新資料合併至現有 `DataSet` 的方式。  
  
## <a name="primary-keys"></a>主索引鍵  
 如果從合併接收新資料和結構描述的資料表有主索引鍵，則來自內送資料的新資料列會與現有資料列 (與內送資料中的資料列具有相同的 <xref:System.Data.DataRowVersion.Original> 主索引鍵值) 進行比對。 如果來自內送結構描述的資料行與現有結構描述相符，則會修改現有資料列內的資料。 系統會根據 <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> 參數來忽略或加入與現有結構描述不符的資料行。 主索引鍵值不符合任何現有資料列的新資料列會附加至現有的資料表。  
  
 如果內送或現有資料列的資料列狀態為 <xref:System.Data.DataRowState.Added>，系統就會使用 <xref:System.Data.DataRowVersion.Current> 資料列的 `Added` 主索引鍵值來比對其主索引鍵值，因為沒有任何 `Original` 資料列版本存在。  
  
 如果內送資料表和現有資料表包含名稱相同但資料型別不同的資料行，則會擲回例外狀況，而且會引發 <xref:System.Data.DataSet.MergeFailed> 的 `DataSet` 事件。 如果內送資料表和現有資料表都已定義索引鍵，但主索引鍵用於不同的資料行，則會擲回例外狀況，而且會引發 `MergeFailed` 的 `DataSet` 事件。  
  
 如果在合併時接收新資料的資料表沒有主索引鍵，則來自內送資料的新資料列將無法與資料表中的現有資料列對應，反而會附加至現有資料表。  
  
## <a name="table-names-and-namespaces"></a>資料表名稱和命名空間  
 您可以選擇性地指派 <xref:System.Data.DataTable> 屬性值給 <xref:System.Data.DataTable.Namespace%2A> 物件。 當您指派 <xref:System.Data.DataTable.Namespace%2A> 值時，<xref:System.Data.DataSet> 可以包含多個具有相同 <xref:System.Data.DataTable> 值的 <xref:System.Data.DataTable.TableName%2A> 物件。 進行合併作業期間，<xref:System.Data.DataTable.TableName%2A> 和 <xref:System.Data.DataTable.Namespace%2A> 都會用於識別合併的目標。 如果沒有指派任何 <xref:System.Data.DataTable.Namespace%2A>，系統就只會使用 <xref:System.Data.DataTable.TableName%2A> 來識別合併的目標。  
  
> [!NOTE]
>  這個行為在 .NET Framework 2.0 版中已變更。 在 1.1 版中，雖然系統支援命名空間 (Namespace)，但是會在合併作業期間忽略命名空間。 因此，使用 <xref:System.Data.DataSet> 屬性值的 <xref:System.Data.DataTable.Namespace%2A> 將根據您正在執行的 .NET Framework 版本而具有不同的行為。 例如，假設您有兩個 `DataSets`，其中包含 `DataTables` 屬性值相同但 <xref:System.Data.DataTable.TableName%2A> 屬性值不同的 <xref:System.Data.DataTable.Namespace%2A>。 在 .NET Framework 1.1 版中，當您合併這兩個 <xref:System.Data.DataTable.Namespace%2A> 物件時，系統會忽略不同的 <xref:System.Data.DataSet> 名稱。 不過，從 2.0 版開始，合併會導致系統在目標 `DataTables` 中建立兩個新的 <xref:System.Data.DataSet>。 原始 `DataTables` 將不會受到合併的影響。  
  
## <a name="preservechanges"></a>PreserveChanges  
 當您將 `DataSet`、`DataTable` 或 `DataRow` 陣列傳遞給 `Merge` 方法時，可以包含選擇性參數來指定是否要保留現有 `DataSet` 的變更，以及如何處理內送資料中發現的新結構描述項目。 內送資料後續參數中的第一個參數是布林值 (Boolean) 旗標 <xref:System.Data.LoadOption.PreserveChanges>，它可指定是否要保留現有 `DataSet` 的變更。 如果 `PreserveChanges` 旗標設定為 `true`，內送值就不會覆寫現有資料列之 `Current` 資料列版本中現有的值。 如果 `PreserveChanges` 旗標設定為 `false`，內送值就會覆寫現有資料列之 `Current` 資料列版本中現有的值。 如果您沒有指定 `PreserveChanges` 旗標，它預設會設定為 `false`。 如需有關資料列版本的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
 當 `PreserveChanges` 為 `true` 時，現有資料列的資料會保留在現有資料列的 <xref:System.Data.DataRowVersion.Current> 資料列版本中，而現有資料列之 <xref:System.Data.DataRowVersion.Original> 資料列版本的資料則會以內送資料列之 `Original` 資料列版本的資料加以覆寫。 現有資料列的 <xref:System.Data.DataRow.RowState%2A> 會設定為 <xref:System.Data.DataRowState.Modified>。 下列情況則例外：  
  
-   如果現有資料列的 `RowState` 為 `Deleted`，則這個 `RowState` 會維持 `Deleted` 而不會設定為 `Modified`。 在這種情況下，內送資料列的資料仍然會儲存在現有資料列的 `Original` 資料列版本中，並覆寫現有資料列的 `Original` 資料列版本 (除非內送資料列的 `RowState` 為 `Added`)。  
  
-   如果內送資料列的 `RowState` 為 `Added`，現有資料列之 `Original` 資料列版本的資料將不會以內送資料列的資料加以覆寫，因為內送資料列沒有 `Original` 資料列版本。  
  
 當 `PreserveChanges` 為 `false` 時，現有資料列中的 `Current` 和 `Original` 資料列版本都會以內送資料列的資料加以覆寫，而且現有資料列的 `RowState` 會設定為內送資料列的 `RowState`。 下列情況則例外：  
  
-   如果內送資料列的 `RowState` 為 `Unchanged` 而且現有資料列的 `RowState` 為 `Modified`、`Deleted` 或 `Added`，則現有資料列的 `RowState` 會設定為 `Modified`。  
  
-   如果內送資料列的 `RowState` 為 `Added`，而且現有資料列的 `RowState` 為 `Unchanged`、`Modified` 或 `Deleted`，則現有資料列的 `RowState` 會設定為 `Modified`。 此外，現有資料列之 `Original` 資料列版本的資料不會以內送資料列的資料加以覆寫，因為內送資料列沒有 `Original` 資料列版本。  
  
## <a name="missingschemaaction"></a>MissingSchemaAction  
 您可以使用 <xref:System.Data.MissingSchemaAction> 方法的選擇性 `Merge` 參數來指定 `Merge` 該如何處理不屬於現有 `DataSet` 之內送資料中的結構描述項目。  
  
 下表將說明 `MissingSchemaAction` 的選項。  
  
|MissingSchemaAction 選項|描述|  
|--------------------------------|-----------------|  
|<xref:System.Data.MissingSchemaAction.Add>|將新的結構描述資訊加入至 `DataSet`，並將內送值填入新資料行。 這是預設值。|  
|<xref:System.Data.MissingSchemaAction.AddWithKey>|將新的結構描述和主索引鍵資訊加入至 `DataSet`，並將內送值填入新資料行。|  
|<xref:System.Data.MissingSchemaAction.Error>|若有不相符的結構描述資訊，則會發生例外狀況。|  
|<xref:System.Data.MissingSchemaAction.Ignore>|忽略新的結構描述資訊。|  
  
## <a name="constraints"></a>條件約束  
 使用 `Merge` 方法時，系統要等到所有的新資料都已經加入至現有 `DataSet` 之後，才會檢查條件約束。 一旦資料加入後，條件約束會強制執行於 `DataSet` 中目前的值。 您必須確保程式碼可處理任何因條件約束違規而造成的例外狀況。  
  
 假設 `DataSet` 中的現有資料列是主索引鍵值為 1 的 `Unchanged` 資料列。 當它與 `Modified` 主索引鍵值為 2 而 `Original` 主索引鍵值為 1 的 `Current` 內送資料列進行合併時，現有資料列和內送資料列不會被視為相符，因為 `Original` 主索引鍵值不同。 但是，在合併完成而且檢查過條件約束之後，系統會擲回例外狀況，因為該 `Current` 主索引鍵值違反了主索引鍵資料行的唯一條件約束。  
  
> [!NOTE]
>  當資料列插入含有自動遞增資料行 (例如識別資料行) 的資料庫資料表時，插入作業所傳回的識別資料行值可能會與 `DataSet` 中的值不符，因而導致系統附加而非合併傳回的資料列。 如需詳細資訊，請參閱 <<c0> [ 擷取識別或自動編號值](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)。  
  
 下列程式碼範例會將兩個具有不同結構描述的 `DataSet` 物件合併成結合了兩個內送 `DataSet` 物件之結構描述的單一 `DataSet`。  
  
 [!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]  
  
 下列程式碼範例會採取含有更新的現有 `DataSet`，並將這些更新傳遞至要在資料來源中處理的 `DataAdapter`。 接著，結果會合併至原始 `DataSet` 中。 在拒絕導致錯誤發生的變更後，即可透過 `AcceptChanges` 認可已合併的變更。  
  
 [!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]  
  
 [!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
 [!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [DataAdapter 和 DataReader](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [在 ADO.NET 中擷取和修改資料](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [擷取身分識別或自動編號值](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
