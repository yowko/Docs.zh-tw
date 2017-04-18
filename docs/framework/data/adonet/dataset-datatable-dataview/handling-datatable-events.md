---
title: "處理 DataTable 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 處理 DataTable 事件
<xref:System.Data.DataTable> 物件提供一系列可由應用程式處理的事件。  下表說明 `DataTable` 事件。  
  
|事件|描述|  
|--------|--------|  
|<xref:System.Data.DataTable.Initialized>|發生在呼叫 `DataTable` 的 <xref:System.Data.DataTable.EndInit%2A> 方法之後。  這個事件主要是為了支援設計階段案例而提供。|  
|<xref:System.Data.DataTable.ColumnChanged>|發生在成功變更 <xref:System.Data.DataColumn> 中的值之後。|  
|<xref:System.Data.DataTable.ColumnChanging>|發生在 `DataColumn` 的值送出之時。|  
|<xref:System.Data.DataTable.RowChanged>|發生在 `DataTable` 中的 `DataColumn` 值或 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRow.RowState%2A> 成功變更之後。|  
|<xref:System.Data.DataTable.RowChanging>|發生在 `DataTable` 中的 `DataColumn` 值或`DataRow` 的 `RowState` 變更送出之時。|  
|<xref:System.Data.DataTable.RowDeleted>|發生在 `DataTable` 中的 `DataRow` 標記為 `Deleted` 之後。|  
|<xref:System.Data.DataTable.RowDeleting>|發生在 `DataTable` 中的 `DataRow` 標記為 `Deleted` 之前。|  
|<xref:System.Data.DataTable.TableCleared>|發生在 `DataTable` 的 <xref:System.Data.DataTable.Clear%2A> 方法成功清除每個 `DataRow` 之後。|  
|<xref:System.Data.DataTable.TableClearing>|發生在呼叫 `Clear` 方法之後，但在 `Clear` 作業開始之前。|  
|<xref:System.Data.DataTable.TableNewRow>|發生在藉由呼叫 `DataTable` 的 `NewRow` 方法而建立新的 `DataRow` 之後。|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|發生在 `DataTable` 為 `Disposed` 時。  繼承自 <xref:System.ComponentModel.MarshalByValueComponent>。|  
  
> [!NOTE]
>  大多數加入或刪除資料列的作業都不會引發 `ColumnChanged` 和 `ColumnChanging` 事件。  不過，`ReadXml` 方法不會引發 `ColumnChanged` 和 `ColumnChanging` 事件，除非正在讀取的 XML 文件是 `DiffGram`，而 `XmlReadMode` 是設為 `DiffGram` 或 `Auto`。  
  
> [!WARNING]
>  如果從中引發 `RowChanged` 事件的 `DataSet` 已修改了資料，就可能會發生資料損毀。  如果發生這類資料損毀，就不會引發任何例外狀況 \(Exception\)。  
  
## 其他相關事件  
 <xref:System.Data.DataTable.Constraints%2A> 屬性會保存 <xref:System.Data.ConstraintCollection> 執行個體 \(Instance\)。  <xref:System.Data.ConstraintCollection> 類別會公開 <xref:System.Data.ConstraintCollection.CollectionChanged> 事件。  從 `ConstraintCollection` 加入、修改或移除條件約束 \(Constraint\) 時，就會引發這個事件。  
  
 <xref:System.Data.DataTable.Columns%2A> 屬性會保存 <xref:System.Data.DataColumnCollection> 執行個體 \(Instance\)。  `DataColumnCollection` 類別會公開 <xref:System.Data.DataColumnCollection.CollectionChanged> 事件。  從 `DataColumnCollection` 加入、修改或移除 `DataColumn` 時，就會引發這個事件。  對名稱、型別、運算式或資料行序數位置所做的變更，都屬於會導致引發此事件的修改作業。  
  
 <xref:System.Data.DataSet> 的 <xref:System.Data.DataSet.Tables%2A> 屬性會保存 <xref:System.Data.DataTableCollection> 執行個體。  `DataTableCollection` 類別會公開 `CollectionChanged` 和 `CollectionChanging` 事件。  從 `DataSet` 加入或移除 `DataTable` 時，就會引發這些事件。  
  
 對 `DataRows` 所做的變更也可能觸發相關 <xref:System.Data.DataView> 的事件。  `DataView` 類別會公開 <xref:System.Data.DataView.ListChanged> 事件，此事件會在 `DataColumn` 值變更或檢視的組合或排序次序變更時引發。  <xref:System.Data.DataRowView> 類別會公開 <xref:System.Data.DataRowView.PropertyChanged> 事件，此事件會在相關的 `DataColumn` 值變更時引發。  
  
## 作業序列  
 這是發生在加入、修改或刪除 `DataRow` 後的作業序列：  
  
1.  建立建議的記錄並套用任何變更。  
  
2.  請檢查非運算式資料行的條件約束。  
  
3.  依需要引發 `RowChanging` 或 `RowDeleting` 事件。  
  
4.  將建議的記錄設定為目前的記錄。  
  
5.  更新任何相關的索引。  
  
6.  針對相關的 `DataView` 物件引發 `ListChanged` 事件；針對相關的 `DataRowView` 物件引發 `PropertyChanged` 事件。  
  
7.  評估所有的運算式資料行，但延遲檢查這些資料行上所有的條件約束。  
  
8.  針對相關的 `DataView` 物件引發 `ListChanged` 事件；針對受到運算式資料行評估影響的相關 `DataRowView` 物件引發 `PropertyChanged` 事件。  
  
9. 依需要引發 `RowChanged` 或 `RowDeleted` 事件。  
  
10. 請檢查運算式資料行的條件約束。  
  
> [!NOTE]
>  對運算式資料行的變更永遠不會引發 `DataTable` 事件。  對運算式資料行的變更僅會引發 `DataView` 和 `DataRowView` 事件。  運算式資料行可能會相依於其他多個資料行，而且可在單一的 `DataRow` 作業期間進行多次評估。  每個運算式評估都會引發事件；在運算式資料行受到影響時，單一的 `DataRow` 作業則可能會引發多個 `ListChanged` 和 `PropertyChanged` 事件，而相同的運算式資料行則可能會包含多個事件。  
  
> [!WARNING]
>  請勿在 `RowChanged` 事件處理常式內部擲回 <xref:System.NullReferenceException>。  如果在 `DataTable` 的 `RowChanged` 事件內部擲回 <xref:System.NullReferenceException>，將會損毀 `DataTable`。  
  
### 範例  
 下列範例示範如何建立 `RowChanged`、`RowChanging`、`RowDeleted`、`RowDeleting`、`ColumnChanged`、`ColumnChanging`、`TableNewRow`、`TableCleared` 和 `TableClearing` 事件的事件處理常式。  每個事件處理常式在引發時，都會將輸出顯示在主控台視窗中。  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## 請參閱  
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [處理 DataAdapter 事件](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)   
 [處理 DataSet 的事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)