---
title: Windows Form DataGridView 和 DataGrid 控制項之間的差異
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: d0a82d5724ebe142ae080fc930665733e701e237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528705"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows Form DataGridView 和 DataGrid 控制項之間的差異
<xref:System.Windows.Forms.DataGridView>控制項是新的控制項，以取代<xref:System.Windows.Forms.DataGrid>控制項。 <xref:System.Windows.Forms.DataGridView>控制項提供許多基本和進階功能中遺漏<xref:System.Windows.Forms.DataGrid>控制項。 此外，架構的<xref:System.Windows.Forms.DataGridView>控制項可以擴充和自訂比更容易<xref:System.Windows.Forms.DataGrid>控制項。  
  
 下表描述一些可用的主要功能<xref:System.Windows.Forms.DataGridView>控制項缺少<xref:System.Windows.Forms.DataGrid>控制項。  
  
|DataGridView 控制項的功能|描述|  
|----------------------------------|-----------------|  
|多個資料行類型|<xref:System.Windows.Forms.DataGridView>控制項提供更多內建的資料行類型與<xref:System.Windows.Forms.DataGrid>控制項。 這些資料行類型符合需求的最常見的案例，但也更輕鬆地擴充或取代中的資料行類型比<xref:System.Windows.Forms.DataGrid>控制項。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)。|  
|多個方法來顯示資料|<xref:System.Windows.Forms.DataGrid>控制會受限於從外部資料來源顯示資料。 <xref:System.Windows.Forms.DataGridView>控制項，不過，可以顯示未繫結中，資料繫結的資料來源的控制項繫結和繫結的資料儲存在一起的資料。 您也可以實作中的虛擬模式<xref:System.Windows.Forms.DataGridView>控制項來提供自訂的資料管理。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)。|  
|多個方式可以自訂資料的顯示|<xref:System.Windows.Forms.DataGridView>控制項提供許多屬性和事件，讓您指定如何格式化及顯示資料。 比方說，您可以變更資料格、 資料列和資料行的資料，根據外觀，或您可以使用對等的另一種類型的資料取代一個資料類型的資料。 如需詳細資訊，請參閱[Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)。|  
|多個變更資料格、 資料列、 資料行和標頭的外觀和行為的選項|<xref:System.Windows.Forms.DataGridView>控制項可讓您能夠以多種方式個別格線元件使用。 例如，您可以凍結資料列和資料行，以防止捲動時。隱藏資料列、 資料行和標頭。變更資料列、 資料行和標頭的大小會進行調整; 的方式變更使用者進行選擇; 的方式並為個別資料格、 列和資料行提供工具提示和捷徑功能表。|  
  
 <xref:System.Windows.Forms.DataGrid>控制保留為回溯相容性與特殊需求。 幾乎所有的目的，您應該用於<xref:System.Windows.Forms.DataGridView>控制項。 唯一的功能所提供之<xref:System.Windows.Forms.DataGrid>不提供的控制項<xref:System.Windows.Forms.DataGridView>控制項是階層式顯示單一控制項中的兩個相關資料表中的資訊。 您必須使用兩個<xref:System.Windows.Forms.DataGridView>控制項以顯示兩個資料表中的主要/詳細資料關聯性的資訊。  
  
## <a name="upgrading-to-the-datagridview-control"></a>升級至 DataGridView 控制項  
 如果您有現有的應用程式使用<xref:System.Windows.Forms.DataGrid>控制項在簡單資料繫結案例中不含自訂項目，您可以只取代舊的控制項新的控制項。 這兩個控制項可使用標準的 Windows Form 資料繫結架構，所以<xref:System.Windows.Forms.DataGridView>控制項會顯示繫結的資料，不需要其他設定。 您可能要考慮利用資料繫結改良功能，不過，透過您的資料繫結<xref:System.Windows.Forms.BindingSource>元件，您可以再繫結至<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱[BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)。  
  
 因為<xref:System.Windows.Forms.DataGridView>控制項全新的架構，可讓您使用沒有直接的轉換路徑<xref:System.Windows.Forms.DataGrid>與自訂<xref:System.Windows.Forms.DataGridView>控制項。 許多<xref:System.Windows.Forms.DataGrid>自訂化內容有不必要的<xref:System.Windows.Forms.DataGridView>控制項，不過，由於可在新控制項的內建功能。 如果您已經建立自訂的資料行類型<xref:System.Windows.Forms.DataGrid>您想要使用的控制項<xref:System.Windows.Forms.DataGridView>控制項，您必須實作一次使用新的架構。 如需詳細資訊，請參閱[自訂 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Windows Forms DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的選取模式](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 [自訂 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
