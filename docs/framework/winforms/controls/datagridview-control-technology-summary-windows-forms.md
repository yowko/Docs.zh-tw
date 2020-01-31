---
title: DataGridView 控制項技術摘要
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: 18eebd067df9768e14cc81258184551d00dd1402
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742472"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView 控制項技術摘要 (Windows Form)
本主題提供有關 `DataGridView` 控制項及支援這些控制項之類別的摘要資訊。  
  
 以表格格式顯示資料是您可能經常執行的工作。 `DataGridView` 控制項的設計，是在方格中呈現資料的完整解決方案。  
  
## <a name="keywords"></a>關鍵字  
 DataGridView、BindingSource、table、cell、資料系結、虛擬模式  
  
## <a name="namespaces"></a>命名空間  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>相關技術  
 `BindingSource`  
  
## <a name="background"></a>背景  
 使用者介面（UI）設計工具經常會發現需要向使用者顯示表格式資料。 .NET Framework 提供數種方式來顯示資料表或方格中的資料。 `DataGridView` 控制項代表這項技術適用于 Windows Forms 應用程式的最新進化。  
  
 `DataGridView` 控制項可以顯示資料存放區中的資料列。 支援許多類型的資料存放區。 資料存放區可以保存簡單、不具類型的資料（例如一維陣列），或者可以保存具類型的資料，例如 <xref:System.Data.DataSet>。 如需詳細資訊，請參閱[如何：將資料系結至 Windows Forms DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
 `DataGridView` 控制項以表格式顯示資料，是一項功能強大、有彈性的方式。 您可以使用控制項來顯示對非常大型資料集的唯讀或可編輯的視圖。  
  
 您可以透過數種方式來擴充 `DataGridView` 控制項，以在應用程式中建立自訂行為。 例如，您可以程式設計方式指定自己的排序演算法，而且也可以建立自己的儲存格類型。 您可以在數種屬性間做選擇，輕鬆自訂 `DataGridView` 控制項的外觀。 許多類型的資料存放區都可以當做資料來源使用，或者 `DataGridView` 控制項可以在沒有系結資料來源的情況下運作。  
  
## <a name="implementing-datagridview-classes"></a>執行 DataGridView 類別  
 有數種方式可讓您利用 `DataGridView` 控制項的擴充性功能。 您可以透過事件和屬性來自訂控制項的許多層面，但有些自訂需要您建立衍生自現有 `DataGridView` 類別的新類別。  
  
 最常使用的基類是 `DataGridViewCell` 和 `DataGridViewColumn`。 您可以從 `DataGridViewCell` 或其任何子類別衍生您自己的資料格類別。 雖然您可以將任何資料格類型加入任何資料行，但您通常也會從裝載自訂資料格類型之資料格的 `DataGridViewColumn` 衍生附屬資料行類別。  
  
 您可以在衍生的資料格類別中執行 `IDataGridViewEditingCell` 介面，以建立具有編輯功能但不會在編輯模式中裝載控制項的資料格類型。 若要建立可在編輯模式中裝載于儲存格中的控制項，您可以在衍生自 <xref:System.Windows.Forms.Control>的類別中，執行 `IDataGridViewEditingControl` 介面。  
  
 如需詳細資訊，請參閱 how [to：在 Windows Forms Datagridview 控制項中自訂儲存格和資料行，方法是擴充其行為和外觀](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)，以及[如何： Windows Forms DataGridView 儲存格中的主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## <a name="datagridview-classes-at-a-glance"></a>DataGridView 類別一覽  
 <xref:System.Windows.Forms>  
  
|技術範圍|類別/介面/組態項目|  
|---------------------|-------------------------------------------------|  
|資料繫結|<xref:System.Windows.Forms.BindingSource>|  
|資料呈現|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> 和衍生類別<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> 和衍生類別<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 和衍生類別<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> 擴充性|<xref:System.Windows.Forms.DataGridViewCell> 和衍生類別<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 和衍生類別<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>新功能  
 <xref:System.Windows.Forms.DataGridView> 控制項的設計，是以 Windows Forms 顯示表格式資料的完整解決方案。 當您撰寫新的應用程式時，您應該考慮使用 <xref:System.Windows.Forms.DataGridView> 控制項，就像 <xref:System.Windows.Forms.DataGrid>等其他解決方案。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項可以與 <xref:System.Windows.Forms.BindingSource> 元件緊密搭配使用。 此元件設計成表單的主要資料來源。 無論資料來源類型為何，它都可以管理 <xref:System.Windows.Forms.DataGridView> 控制項與其資料來源之間的互動。  
  
## <a name="see-also"></a>請參閱

- [DataGridView 控制項概觀](datagridview-control-overview-windows-forms.md)
- [DataGridView 控制項架構](datagridview-control-architecture-windows-forms.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)
