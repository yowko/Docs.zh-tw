---
title: DataGridView 和 DataGrid 控制項之間的差異
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 3552abe55d8e2c1cb4ae372ca64c7ca21f1fed0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745965"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows Form DataGridView 和 DataGrid 控制項之間的差異
<xref:System.Windows.Forms.DataGridView> 控制項是取代 <xref:System.Windows.Forms.DataGrid> 控制項的新控制項。 <xref:System.Windows.Forms.DataGridView> 控制項提供了許多在 <xref:System.Windows.Forms.DataGrid> 控制項中遺漏的基本和先進功能。 此外，<xref:System.Windows.Forms.DataGridView> 控制項的架構可讓您更輕鬆地擴充和自訂，而不是 <xref:System.Windows.Forms.DataGrid> 控制項。  
  
 下表描述 <xref:System.Windows.Forms.DataGrid> 控制項中遺漏的 <xref:System.Windows.Forms.DataGridView> 控制項中的一些主要功能。  
  
|DataGridView 控制項功能|描述|  
|----------------------------------|-----------------|  
|多個資料行類型|<xref:System.Windows.Forms.DataGridView> 控制項提供比 <xref:System.Windows.Forms.DataGrid> 控制項更多的內建資料行類型。 這些資料行類型符合最常見案例的需求，但也比 <xref:System.Windows.Forms.DataGrid> 控制項中的資料行類型更容易擴充或取代。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)。|  
|顯示資料的多種方式|<xref:System.Windows.Forms.DataGrid> 控制項僅限於顯示來自外部資料源的資料。 不過，<xref:System.Windows.Forms.DataGridView> 控制項可以顯示儲存在控制項中的未系結資料、來自系結資料來源的資料，或一起系結和未系結的資料。 您也可以在 <xref:System.Windows.Forms.DataGridView> 控制項中執行虛擬模式，以提供自訂資料管理。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)。|  
|有多種方式可自訂資料的顯示|<xref:System.Windows.Forms.DataGridView> 控制項提供許多屬性和事件，可讓您指定如何格式化和顯示資料。 例如，您可以變更資料格、資料列和資料行的外觀（視其所包含的資料而定），或者，您可以使用另一種類型的相等資料來取代其中一個資料類型的資料。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)。|  
|變更儲存格、資料列、資料行和標題外觀和行為的多個選項|<xref:System.Windows.Forms.DataGridView> 控制項可讓您以多種方式使用個別的方格元件。 例如，您可以凍結資料列和資料行，以防止它們進行滾動;隱藏資料列、資料行和標頭;變更資料列、資料行和標頭大小的調整方式;變更使用者進行選取的方式;和提供個別資料格、資料列和資料行的工具提示和快捷方式功能表。|  
  
 針對回溯相容性和特殊需求，會保留 <xref:System.Windows.Forms.DataGrid> 控制項。 就幾乎所有的用途而言，您都應該使用 <xref:System.Windows.Forms.DataGridView> 控制項。 在 <xref:System.Windows.Forms.DataGridView> 控制項中無法使用的 <xref:System.Windows.Forms.DataGrid> 控制項中唯一可用的功能，是從單一控制項中的兩個相關資料表的階層式顯示資訊。 您必須使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項來顯示主要/詳細資料關聯性中兩個數據表的資訊。  
  
## <a name="upgrading-to-the-datagridview-control"></a>升級至 DataGridView 控制項  
 如果您現有的應用程式在簡單的資料系結案例中使用 <xref:System.Windows.Forms.DataGrid> 控制項，但沒有自訂，則只要以新的控制項取代舊的控制項即可。 這兩個控制項都使用標準 Windows Forms 資料系結架構，因此 <xref:System.Windows.Forms.DataGridView> 控制項將會顯示您系結的資料，而不需要額外的設定。 不過，您可能會想要利用資料系結改進功能，方法是將您的資料系結至 <xref:System.Windows.Forms.BindingSource> 元件，然後您就可以將它系結至 <xref:System.Windows.Forms.DataGridView> 控制項。 如需詳細資訊，請參閱[BindingSource Component](bindingsource-component.md)。  
  
 由於 <xref:System.Windows.Forms.DataGridView> 控制項有全新的架構，因此沒有直接的轉換路徑可讓您使用 <xref:System.Windows.Forms.DataGrid> 自訂與 <xref:System.Windows.Forms.DataGridView> 控制項。 不過，<xref:System.Windows.Forms.DataGridView> 控制項不需要許多 <xref:System.Windows.Forms.DataGrid> 自訂，因為新控制項中提供了內建的功能。 如果您已針對要與 <xref:System.Windows.Forms.DataGridView> 控制項搭配使用的 <xref:System.Windows.Forms.DataGrid> 控制項建立自訂資料行類型，您必須使用新的架構再次執行這些專案。 如需詳細資訊，請參閱[自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>請參閱

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
