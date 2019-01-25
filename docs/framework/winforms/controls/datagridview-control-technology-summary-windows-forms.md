---
title: DataGridView 控制項技術摘要 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: efa567e6f8a91b40d2710b4cef0d1a56d38650c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737828"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView 控制項技術摘要 (Windows Form)
本主題提供有關 `DataGridView` 控制項及支援這些控制項之類別的摘要資訊。  
  
 以表格格式顯示資料是您就可以經常執行的工作。 `DataGridView`控制項的設計目的，將資料呈現在方格中的全方位解決方案。  
  
## <a name="keywords"></a>關鍵字  
 DataGridView、 BindingSource、 資料表、 資料格、 資料繫結、 虛擬模式  
  
## <a name="namespaces"></a>命名空間  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>相關技術  
 `BindingSource`  
  
## <a name="background"></a>背景  
 使用者介面 (UI) 設計工具通常會發現需要向使用者顯示表格式資料。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供數種方式，在資料表或方格中顯示資料。 `DataGridView`控制項所代表的 Windows Form 應用程式的這項技術的最新發展。  
  
 `DataGridView`控制項可以顯示從資料存放區的資料列。 支援許多類型的資料存放區。 資料存放區可以保存簡單且不具類型的資料，例如一維陣列，或它可以保留型別的資料，例如<xref:System.Data.DataSet>。 如需詳細資訊，請參閱[＜How to：資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
 `DataGridView` 控制項以表格式顯示資料，是一項功能強大、有彈性的方式。 您可以使用控制項來顯示小型到大型資料集的唯讀或可編輯的檢視。  
  
 您可以擴充`DataGridView`數種方式在您的應用程式中建置自訂行為的控制項。 例如，您可以程式設計方式指定自己的排序演算法，而且也可以建立自己的儲存格類型。 您可以在數種屬性間做選擇，輕鬆自訂 `DataGridView` 控制項的外觀。 許多類型的資料存放區可用來當做資料來源，或`DataGridView`控制項可以在沒有資料來源繫結至該操作。  
  
## <a name="implementing-datagridview-classes"></a>實作 DataGridView 類別  
 有幾種方式可以善用`DataGridView`控制項的擴充性功能。 您可以自訂事件和屬性，透過控制項的許多層面，但有些自訂需要您建立新的類別衍生自現有`DataGridView`類別。  
  
 最常用的基底類別都`DataGridViewCell`和`DataGridViewColumn`。 您可以衍生自己的儲存格類別，從`DataGridViewCell`或任何它的子類別。 雖然您可以新增任何資料格類型的任何資料行，您會通常也衍生隨附資料行類別從`DataGridViewColumn`預設在裝載您的自訂儲存格類型的儲存格。  
  
 您可以實作`IDataGridViewEditingCell`介面，在您的衍生資料格類別，來建立具有 編輯功能，但未裝載的控制項處於編輯模式的資料格類型。 若要建立的控制項，您可以裝載儲存格處於編輯模式中，您可以實作`IDataGridViewEditingControl`類別中的介面衍生自<xref:System.Windows.Forms.Control>。  
  
 如需詳細資訊，請參閱[＜How to：自訂資料格資料行中的 Windows Form DataGridView 控制項和擴充其行為和外觀](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)和[How to:Windows Forms DataGridView 儲存格主控制項](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## <a name="datagridview-classes-at-a-glance"></a>DataGridView 類別簡介  
 <xref:System.Windows.Forms>  
  
|技術範圍|類別/介面/組態項目|  
|---------------------|-------------------------------------------------|  
|資料繫結|<xref:System.Windows.Forms.BindingSource>|  
|資料簡報|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> 擴充性|<xref:System.Windows.Forms.DataGridViewCell> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>新功能  
 <xref:System.Windows.Forms.DataGridView>控制項用來顯示 Windows form 的表格式資料的全方位解決方案。 您應該考慮使用<xref:System.Windows.Forms.DataGridView>控制之前其他解決方案，例如<xref:System.Windows.Forms.DataGrid>，當您撰寫新的應用程式。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 <xref:System.Windows.Forms.DataGridView>控制項可以在關閉搭配運作<xref:System.Windows.Forms.BindingSource>元件。 此元件設計為表單的主要資料來源。 它可以管理之間的互動<xref:System.Windows.Forms.DataGridView>控制項和其資料來源，不論資料來源類型。  
  
## <a name="see-also"></a>另請參閱
- [DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
- [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)
- [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)
