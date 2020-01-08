---
title: 資料繫結和 LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 2b49e2a3ff0d95dcbceff8099f51993c0f08d64e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634868"
---
# <a name="data-binding-and-linq-to-dataset"></a>資料繫結和 LINQ to DataSet
*資料*系結是在應用程式 UI 與商務邏輯之間建立連接的進程。 如果繫結具有正確的設定而且資料提供了適當的通知，當資料變更其值時，繫結至資料的項目就會自動反映變更。 <xref:System.Data.DataSet> 是記憶體中的資料表示，可提供一致的關聯式程式撰寫模型 (Programming Model)，不論它所包含的資料來源為何都一樣。 ADO.NET 2.0 <xref:System.Data.DataView> 可讓您排序和篩選儲存在 <xref:System.Data.DataTable> 中的資料。 這項功能通常用於資料繫結的應用程式。 您可以透過使用 <xref:System.Data.DataView>，以不同排序順序公開 (Expose) 資料表中的資料，而且可以按照資料列狀態或根據篩選條件運算式來篩選資料。 如需 <xref:System.Data.DataView> 物件的詳細資訊，請參閱[dataview](./dataset-datatable-dataview/dataviews.md)。  
  
 LINQ to DataSet 可讓開發人員使用語言整合式查詢（LINQ），在 <xref:System.Data.DataSet> 上建立複雜且功能強大的查詢。 不過，LINQ to DataSet 查詢會傳回 <xref:System.Data.DataRow> 物件的列舉，這在系結案例中不容易使用。 若要更輕鬆地進行系結，您可以從 LINQ to DataSet 查詢建立 <xref:System.Data.DataView>。 這個 <xref:System.Data.DataView> 會使用查詢中指定的篩選和排序，但是較適合資料系結。 LINQ to DataSet 藉由提供以 LINQ 運算式為基礎的篩選和排序，來擴充 <xref:System.Data.DataView> 的功能，讓您可以比以字串為基礎的篩選和排序更複雜且功能強大的篩選和排序作業。  
  
 請注意，<xref:System.Data.DataView> 代表查詢本身而不是查詢頂端的檢視。 <xref:System.Data.DataView> 會繫結至 UI 控制項 (例如 <xref:System.Windows.Forms.DataGrid> 或 <xref:System.Windows.Forms.DataGridView>)，以便提供簡單的資料繫結模型。 <xref:System.Data.DataView> 也可以從 <xref:System.Data.DataTable> 中建立，以便提供該資料表的預設檢視。  
  
## <a name="in-this-section"></a>本章節內容  
 [建立 DataView 物件](creating-a-dataview-object-linq-to-dataset.md)  
 提供有關建立 <xref:System.Data.DataView> 的資訊。  
  
 [使用 DataView 進行篩選](filtering-with-dataview-linq-to-dataset.md)  
 說明如何使用 <xref:System.Data.DataView> 進行篩選。  
  
 [使用 DataView 進行排序](sorting-with-dataview-linq-to-dataset.md)  
 說明如何使用 <xref:System.Data.DataView> 進行排序。  
  
 [查詢 DataView 中的 DataRowView 集合](querying-the-datarowview-collection-in-a-dataview.md)  
 提供查詢由 <xref:System.Data.DataRowView> 所公開之 <xref:System.Data.DataView> 集合的相關資訊。  
  
 [DataView 效能](dataview-performance.md)  
 提供有關 <xref:System.Data.DataView> 和效能的資訊。  
  
 [如何：將 DataView 物件繫結至 Windows Form DataGridView 控制項](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 說明如何將 <xref:System.Data.DataView> 物件繫結至 <xref:System.Windows.Forms.DataGridView>。  
  
## <a name="see-also"></a>請參閱

- [程式設計手冊](programming-guide-linq-to-dataset.md)
