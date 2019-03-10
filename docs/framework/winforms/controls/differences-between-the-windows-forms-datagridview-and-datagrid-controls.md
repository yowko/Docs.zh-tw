---
title: Windows Form DataGridView 和 DataGrid 控制項之間的差異
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: b7d97431bfdbdafd5e87bfbfb9c5badd9ba273ea
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720484"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows Form DataGridView 和 DataGrid 控制項之間的差異
<xref:System.Windows.Forms.DataGridView>控制項是新的控制項，它會取代<xref:System.Windows.Forms.DataGrid>控制項。 <xref:System.Windows.Forms.DataGridView>控制項提供許多基本和進階功能中遺漏<xref:System.Windows.Forms.DataGrid>控制項。 此外，架構<xref:System.Windows.Forms.DataGridView>控制項讓它更容易擴充和自訂比<xref:System.Windows.Forms.DataGrid>控制項。  
  
 下表描述可用的主要功能一些<xref:System.Windows.Forms.DataGridView>缺少的控制項<xref:System.Windows.Forms.DataGrid>控制項。  
  
|DataGridView 控制項的功能|描述|  
|----------------------------------|-----------------|  
|多個資料行類型|<xref:System.Windows.Forms.DataGridView>控制項提供更多內建的資料行類型，比<xref:System.Windows.Forms.DataGrid>控制項。 這些資料行類型的最常見的案例需求，但也是您更輕鬆地擴充或取代中的資料行類型比<xref:System.Windows.Forms.DataGrid>控制項。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)。|  
|多個方式來顯示資料|<xref:System.Windows.Forms.DataGrid>控制受限於從外部資料來源顯示資料。 <xref:System.Windows.Forms.DataGridView>控制項，不過，可以顯示未繫結的資料一起儲存在控制項、 資料繫結的資料來源或繫結和解除繫結的資料。 您也可以實作虛擬模式中的<xref:System.Windows.Forms.DataGridView>控制項來提供自訂的資料管理。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)。|  
|多個自訂資料的顯示方式|<xref:System.Windows.Forms.DataGridView>控制項提供許多屬性和事件，讓您指定如何格式化和顯示資料。 比方說，您可以變更資料格、 資料列和資料行，根據及其包含的資料外觀，或您可以使用另一種類型的對等的資料來取代一個資料類型的資料。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)。|  
|多個變更資料格、 資料列、 資料行和標頭的外觀和行為的選項|<xref:System.Windows.Forms.DataGridView>控制項可讓您使用個別的方格元件有許多種。 例如，您可以凍結資料列和資料行，以防止捲動;隱藏資料列、 資料行和標頭;變更資料列、 資料行和標頭的大小會調整; 的方式變更使用者進行選擇; 的方式並提供個別的資料格、 資料列和資料行的工具提示和捷徑功能表。|  
  
 <xref:System.Windows.Forms.DataGrid>保留回溯相容性以及特殊的需求。 對於幾乎所有的目的，您應該使用<xref:System.Windows.Forms.DataGridView>控制項。 唯一的功能，可用於<xref:System.Windows.Forms.DataGrid>控制項，就無法用於<xref:System.Windows.Forms.DataGridView>控制項是階層式顯示的兩個相關資料表中的單一控制項的資訊。 您必須使用兩個<xref:System.Windows.Forms.DataGridView>控制項以顯示具有一對多關聯性的兩個資料表的資訊。  
  
## <a name="upgrading-to-the-datagridview-control"></a>升級至 DataGridView 控制項  
 如果您有現有的應用程式使用<xref:System.Windows.Forms.DataGrid>控制項在簡單資料繫結案例中不含自訂項目，您可以直接將舊的控制項的新控制項。 這兩個控制項使用標準 Windows Form 資料繫結的架構，因此<xref:System.Windows.Forms.DataGridView>控制項會顯示您繫結的資料，不需要的其他設定。 您可能要考慮使用資料繫結的改進，不過，藉由繫結至資料<xref:System.Windows.Forms.BindingSource>元件，您可以再繫結至<xref:System.Windows.Forms.DataGridView>控制項。 如需詳細資訊，請參閱 < [BindingSource 元件](bindingsource-component.md)。  
  
 因為<xref:System.Windows.Forms.DataGridView>控制項的全新架構，沒有簡單的轉換路徑，可讓您使用<xref:System.Windows.Forms.DataGrid>使用自訂<xref:System.Windows.Forms.DataGridView>控制項。 許多<xref:System.Windows.Forms.DataGrid>自訂項目不需要使用<xref:System.Windows.Forms.DataGridView>控制，不過，因為新的控制項中的可用內建的功能。 如果您已建立的自訂資料行類型<xref:System.Windows.Forms.DataGrid>您想要使用的控制項<xref:System.Windows.Forms.DataGridView>控制項，您必須實作它們一次使用新的架構。 如需詳細資訊，請參閱 <<c0> [ 自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [BindingSource 元件](bindingsource-component.md)
- [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料行排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的選取模式](selection-modes-in-the-windows-forms-datagridview-control.md)
- [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)
