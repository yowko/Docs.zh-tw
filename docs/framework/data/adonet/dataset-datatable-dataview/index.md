---
title: DataSet、DataTable 和 DataView
description: 瞭解許多使用 ADO.NET 資料集的方法，這是可提供一致關聯式程式設計模型之資料的記憶體常駐表示。
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 4e1c0ea5f1de1715ad8e862e6a3ed7370b53c6ce
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555860"
---
# <a name="datasets-datatables-and-dataviews"></a>DataSet、DataTable 和 DataView

ADO.NET <xref:System.Data.DataSet> 是以常駐記憶體表示的資料，不論內含資料來源為何，都可提供一致的關聯式程式設計模型。 <xref:System.Data.DataSet> 表示一組完整的資料，包括內含、排序和約束資料的資料表，以及資料表間的關聯性。  
  
<xref:System.Data.DataSet> 的使用方式有幾種，可以獨立或組合套用。 您可以：  
  
- 以程式設計方式在 <xref:System.Data.DataTable> 內建立 <xref:System.Data.DataRelation>、<xref:System.Data.Constraint> 和 <xref:System.Data.DataSet>，並填入資料表的資料。  
  
- 使用 <xref:System.Data.DataSet>，將來自現有關聯式資料來源之資料的資料表填入 `DataAdapter`。  
  
- 使用 XML 載入並保存 <xref:System.Data.DataSet> 內容。 如需詳細資訊，請參閱[在 DataSet 中使用 XML](using-xml-in-a-dataset.md)。  
  
也可以使用 XML Web Service 傳輸強型別的 <xref:System.Data.DataSet>。 <xref:System.Data.DataSet> 的設計非常適合使用 XML Web Service 來傳輸資料。 如需 XML Web Service 的概觀，請參閱 [XML Web Service 概觀](/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100))。 如需使用來自 XML Web Service 之 <xref:System.Data.DataSet> 的範例，請參閱[從 XML Web Service 使用 DataSet](consuming-a-dataset-from-an-xml-web-service.md)。  
  
## <a name="in-this-section"></a>本節內容

 [安全性指導](security-guidance.md)  
 提供和的安全性 <xref:System.Data.DataSet> 指引 <xref:System.Data.DataTable> 。

 [建立資料集](creating-a-dataset.md)  
 說明建立 <xref:System.Data.DataSet> 執行個體的語法。  
  
 [將 DataTable 加入至資料集](adding-a-datatable-to-a-dataset.md)  
 說明如何建立資料表和資料行，並將它們加入 <xref:System.Data.DataSet>。  
  
 [加入 DataRelation](adding-datarelations.md)  
 說明如何在 <xref:System.Data.DataSet> 的資料表之間建立關聯性。  
  
 [導覽 DataRelation](navigating-datarelations.md)  
 說明如何使用 <xref:System.Data.DataSet> 之資料表間的關聯性，傳回父子關係的子資料列或父資料列。  
  
 [合併資料集內容](merging-dataset-contents.md)  
 說明如何將一個 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或 <xref:System.Data.DataRow> 陣列的內容合併到另一個 <xref:System.Data.DataSet>。  
  
 [複製資料集內容](copying-dataset-contents.md)  
 說明如何建立 <xref:System.Data.DataSet> 的複本，而此複本包含結構描述和指定的資料。  
  
 [處理 DataSet 的事件](handling-dataset-events.md)  
 說明 <xref:System.Data.DataSet> 的事件和使用方式。  
  
 [具類型資料集](typed-datasets.md)  
 說明何謂具型別的 <xref:System.Data.DataSet> 以及它們的建立和使用方式。  
  
 [DataTables](datatables.md)  
 說明如何建立 <xref:System.Data.DataTable>、定義結構描述，以及管理資料。  
  
 [DataTableReader](datatablereaders.md)  
 說明如何建立及使用 <xref:System.Data.DataTableReader>。  
  
 [DataView](dataviews.md)  
 說明如何建立並使用 `DataViews`，以及使用 <xref:System.Data.DataView> 事件。  
  
 [在資料集中使用 XML](using-xml-in-a-dataset.md)  
 說明 <xref:System.Data.DataSet> 如何將 XML 當成資料來源進行互動，包括將 <xref:System.Data.DataSet> 的內容載入和保存為 XML 資料。  
  
 [從 XML Web Service 使用資料集](consuming-a-dataset-from-an-xml-web-service.md)  
 說明如何建立可透過 <xref:System.Data.DataSet> 傳輸資料的 XML Web Service。  
  
## <a name="related-sections"></a>相關章節

 [ADO.NET 的新功能](../whats-new.md)  
 簡介 ADO.NET 的新功能。  
  
 [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)  
 提供 ADO.NET 的設計和元件的簡介。  
  
 [從 DataAdapter 填入資料集](../populating-a-dataset-from-a-dataadapter.md)  
 描述如何自資料來源載入具有資料的 **DataSet**。  
  
 [使用 DataAdapter 更新資料來源](../updating-data-sources-with-dataadapters.md)  
 描述如何將 **DataSet** 中的資料變更解析回資料來源。  
  
 [將現有條件約束加入至資料集](../adding-existing-constraints-to-a-dataset.md)  
 描述如何將來自資料來源的主索引鍵資訊填入 **DataSet**。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET](../index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
