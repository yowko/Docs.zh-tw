---
title: DataGridView 控制項技術摘要 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: cafd832e7105540ae684dd1feb4b33ab74f72836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528869"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView 控制項技術摘要 (Windows Form)
本主題提供有關 `DataGridView` 控制項及支援這些控制項之類別的摘要資訊。  
  
 以表格格式顯示資料是可能更常執行的工作。 `DataGridView`控制項的設計是完整的解決方案，資料呈現在方格中。  
  
## <a name="keywords"></a>關鍵字  
 DataGridView、 BindingSource、 資料表、 資料格、 資料繫結、 虛擬模式  
  
## <a name="namespaces"></a>命名空間  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>相關技術  
 `BindingSource`  
  
## <a name="background"></a>背景  
 使用者介面 (UI) 設計工具通常會發現有必要向使用者顯示表格式資料。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供幾種方法在資料表或方格中顯示資料。 `DataGridView`控制項代表這項技術的 Windows Form 應用程式的最新發展。  
  
 `DataGridView`控制項可以顯示從資料存放區的資料列。 支援的許多類型的資料存放區。 資料存放區可以保存簡單、 不具類型的資料，例如一維陣列，或它能容納具類型的資料，例如<xref:System.Data.DataSet>。 如需詳細資訊，請參閱[How to： 將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
 `DataGridView` 控制項以表格式顯示資料，是一項功能強大、有彈性的方式。 您可以使用控制項來顯示小型到大型資料集的唯讀或可編輯的檢視。  
  
 您可以擴充`DataGridView`幾種方式來建立自訂行為到您的應用程式的控制項。 例如，您可以程式設計方式指定自己的排序演算法，而且也可以建立自己的儲存格類型。 您可以在數種屬性間做選擇，輕鬆自訂 `DataGridView` 控制項的外觀。 許多類型的資料存放區可用來當做資料來源，或`DataGridView`控制項可以在沒有資料來源繫結至該操作。  
  
## <a name="implementing-datagridview-classes"></a>實作 DataGridView 類別  
 有數種方式，讓您充分利用`DataGridView`控制項的擴充性功能。 您可以自訂事件和屬性，透過控制項的許多層面，但某些自訂都需要您建立新的類別衍生自現有`DataGridView`類別。  
  
 最常用的基底類別是`DataGridViewCell`和`DataGridViewColumn`。 您也可以衍生您自己的儲存格類別，從`DataGridViewCell`或其任何子類別。 雖然您可以新增任何資料格類型的任何資料行，您將通常也衍生從 companion column 類別`DataGridViewColumn`預設裝載儲存格的自訂儲存格類型。  
  
 您可以實作`IDataGridViewEditingCell`在您的衍生資料格類別，來建立資料格類型編輯功能，但不會裝載在編輯模式的控制項的介面。 若要建立您可以在儲存格處於編輯模式中裝載的控制項，您可以實作`IDataGridViewEditingControl`類別中的介面衍生自<xref:System.Windows.Forms.Control>。  
  
 如需詳細資訊，請參閱[How to： 自訂資料格和擴充其行為和外觀的 Windows Form DataGridView 控制項中的資料行](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)和[如何： 在 Windows Form DataGridView 儲存格主控制項](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="datagridview-classes-at-a-glance"></a>DataGridView 類別簡介  
 <xref:System.Windows.Forms>  
  
|技術範圍|類別/介面/組態項目|  
|---------------------|-------------------------------------------------|  
|資料繫結|<xref:System.Windows.Forms.BindingSource>|  
|資料簡報|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> 擴充性|<xref:System.Windows.Forms.DataGridViewCell> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 類別和衍生的類別<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>新功能  
 <xref:System.Windows.Forms.DataGridView>控制項的設計是完整的解決方案，可顯示搭配 Windows Form 的表格式資料。 您應該考慮使用<xref:System.Windows.Forms.DataGridView>控制之前其他方案，例如<xref:System.Windows.Forms.DataGrid>，當您撰寫新的應用程式。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 <xref:System.Windows.Forms.DataGridView>控制項可以關閉搭配運作<xref:System.Windows.Forms.BindingSource>元件。 此元件設計為表單的主要資料來源。 它可以管理之間的互動<xref:System.Windows.Forms.DataGridView>控制項和其資料來源，不論資料來源類型。  
  
## <a name="see-also"></a>另請參閱  
 [DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)
