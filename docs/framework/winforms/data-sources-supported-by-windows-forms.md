---
title: 支援的資料來源
ms.date: 03/30/2017
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
ms.openlocfilehash: 83ce4bb0d6f0bf81bcad4e38af212dccc3483ca5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742307"
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows Form 支援的資料來源
傳統上，已在應用程式中使用資料系結，以利用儲存在資料庫中的資料。 使用 Windows Forms 的資料系結，您可以從資料庫以及其他結構（例如陣列和集合）中的資料存取資料，只要符合特定的最低需求即可。  
  
## <a name="structures-to-bind-to"></a>要系結的結構  
 在 Windows Forms 中，您可以系結至各種不同的結構，從簡單物件（簡單系結）到複雜清單（例如 ADO.NET 資料表（複雜系結））。 針對簡單系結，Windows Forms 支援系結至簡單物件上的公用屬性。 Windows Forms 以清單為基礎的系結通常會要求物件支援 <xref:System.Collections.IList> 介面或 <xref:System.ComponentModel.IListSource> 介面。 此外，如果您透過 <xref:System.Windows.Forms.BindingSource> 元件系結，您可以系結至支援 <xref:System.Collections.IEnumerable> 介面的物件。 如需與資料系結相關之介面的詳細資訊，請參閱與資料系結[相關的介面](interfaces-related-to-data-binding.md)。  
  
 下列清單顯示您可以在 Windows Forms 中系結的結構。  
  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingSource> 是最常見的 Windows Forms 資料來源，並可在資料來源和 Windows Forms 控制項之間進行 proxy。 一般 <xref:System.Windows.Forms.BindingSource> 使用模式是將控制項系結至 <xref:System.Windows.Forms.BindingSource>，並將 <xref:System.Windows.Forms.BindingSource> 系結至資料來源（例如，ADO.NET 資料表或商務物件）。 <xref:System.Windows.Forms.BindingSource> 提供可啟用及改善資料系結支援層級的服務。 例如，Windows Forms 清單型控制項（例如 <xref:System.Windows.Forms.DataGridView> 和 <xref:System.Windows.Forms.ComboBox> 並不會直接支援系結至 <xref:System.Collections.IEnumerable> 資料來源，不過您可以透過 <xref:System.Windows.Forms.BindingSource>系結來啟用此案例。 在此情況下，<xref:System.Windows.Forms.BindingSource> 會將資料來源轉換成 <xref:System.Collections.IList>。  
  
 簡單物件  
 Windows Forms 使用 <xref:System.Windows.Forms.Binding> 類型，支援資料系結控制項屬性至物件實例上的公用屬性。 Windows Forms 也支援系結清單型控制項，例如使用 <xref:System.Windows.Forms.BindingSource> 時，物件實例的 <xref:System.Windows.Forms.ListControl>。  
  
 陣列或集合  
 若要作為資料來源，清單必須執行 <xref:System.Collections.IList> 介面;其中一個範例是 <xref:System.Array> 類別之實例的陣列。 如需陣列的詳細資訊，請參閱[如何：建立物件的陣列（Visual Basic）](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100))。  
  
 一般而言，當您建立資料系結的物件清單時，應該使用 <xref:System.ComponentModel.BindingList%601>。 <xref:System.ComponentModel.BindingList%601> 是 <xref:System.ComponentModel.IBindingList> 介面的泛型版本。 <xref:System.ComponentModel.IBindingList> 介面會藉由加入雙向資料系結所需的屬性、方法和事件來擴充 <xref:System.Collections.IList> 介面。  
  
 <xref:System.Collections.IEnumerable>  
 Windows Forms 控制項可以系結至僅支援 <xref:System.Collections.IEnumerable> 介面的資料來源（如果它們是透過 <xref:System.Windows.Forms.BindingSource> 元件所系結）。  
  
 ADO.NET 資料物件  
 ADO.NET 提供了一些適用于系結至的資料結構。 每個都有其複雜和複雜度的差異。  
  
- <xref:System.Data.DataColumn>。 <xref:System.Data.DataColumn> 是 <xref:System.Data.DataTable>的基本建立區塊，其中有一些資料行組成資料表。 每個 <xref:System.Data.DataColumn> 都有一個 <xref:System.Data.DataColumn.DataType%2A> 屬性，可決定資料行所保留的資料類型（例如，在描述汽車的資料表中建立汽車）。 您可以簡單地將控制項（例如 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性）系結至資料表中的資料行。  
  
- <xref:System.Data.DataTable>。 <xref:System.Data.DataTable> 是資料表的表示，其中包含資料列和資料行，在 ADO.NET 中。 資料表包含兩個集合： <xref:System.Data.DataColumn>，代表給定資料表中的資料行（最終會決定可以輸入該資料表的資料類型），並 <xref:System.Data.DataRow>，代表給定資料表中的資料列。 您可以將控制項複雜地系結至資料表中包含的資訊（例如，將 <xref:System.Windows.Forms.DataGridView> 控制項系結至資料表）。 不過，當您系結至 <xref:System.Data.DataTable>時，您實際上就是系結至資料表的預設 view。  
  
- <xref:System.Data.DataView>。 <xref:System.Data.DataView> 是單一資料表的自訂視圖，可以篩選或排序。 資料檢視是複雜繫結控制項所使用的「快照集」資料。 您可以簡單地系結或複雜系結至資料檢視內的資料，但請注意，您會系結至資料的固定「圖片」，而不是「清除」的「更新資料來源」。  
  
- <xref:System.Data.DataSet>。 <xref:System.Data.DataSet> 是資料庫中資料的資料表、關聯性和條件約束的集合。 您可以簡單地系結或複雜系結至資料集內的資料，但請注意，您會系結至 <xref:System.Data.DataSet> 的預設 <xref:System.Data.DataViewManager> （請參閱下一個專案符號點）。  
  
- <xref:System.Data.DataViewManager>。 <xref:System.Data.DataViewManager> 是整個 <xref:System.Data.DataSet>的自訂視圖，類似于 <xref:System.Data.DataView>，但包含關聯性。 有了 <xref:System.Data.DataViewManager.DataViewSettings%2A> 集合，您可以針對 <xref:System.Data.DataViewManager> 對指定資料表具有的任何視圖，設定預設的篩選準則和排序選項。  
  
## <a name="see-also"></a>請參閱

- [Windows Forms 資料繫結中的變更告知](change-notification-in-windows-forms-data-binding.md)
- [資料繫結和 Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
