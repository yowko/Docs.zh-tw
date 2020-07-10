---
title: DataGridView 和 DataGrid 控制項之間的差異
description: 瞭解 Windows Forms DataGridView 和 DataGrid 控制項功能之間的各種差異，以及其架構的差異。
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 1438182d764097ae4f8fd7df046ad72c9213da19
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174584"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows Form DataGridView 和 DataGrid 控制項之間的差異
<xref:System.Windows.Forms.DataGridView>控制項是取代控制項的新控制項 <xref:System.Windows.Forms.DataGrid> 。 <xref:System.Windows.Forms.DataGridView>控制項提供了許多控制項中遺漏的基本和先進功能 <xref:System.Windows.Forms.DataGrid> 。 此外，控制項的架構 <xref:System.Windows.Forms.DataGridView> 可讓您更容易擴充和自訂，而不是 <xref:System.Windows.Forms.DataGrid> 控制項。  
  
 下表描述控制項中遺漏的一些主要功能，控制項中 <xref:System.Windows.Forms.DataGridView> 會有這些功能 <xref:System.Windows.Forms.DataGrid> 。  
  
|DataGridView 控制項功能|描述|  
|----------------------------------|-----------------|  
|多個資料行類型|<xref:System.Windows.Forms.DataGridView>控制項提供比控制項更多的內建資料行類型 <xref:System.Windows.Forms.DataGrid> 。 這些資料行類型符合最常見案例的需求，但也比控制項中的資料行類型更容易擴充或取代 <xref:System.Windows.Forms.DataGrid> 。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)。|  
|顯示資料的多種方式|<xref:System.Windows.Forms.DataGrid>控制項僅限於顯示來自外部資料源的資料。 <xref:System.Windows.Forms.DataGridView>不過，控制項可以顯示儲存在控制項中的未系結資料、來自系結資料來源的資料，或一起系結和未系結的資料。 您也可以在控制項中執行虛擬模式 <xref:System.Windows.Forms.DataGridView> ，以提供自訂資料管理。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)。|  
|有多種方式可自訂資料的顯示|<xref:System.Windows.Forms.DataGridView>控制項提供許多屬性和事件，可讓您指定如何格式化和顯示資料。 例如，您可以變更資料格、資料列和資料行的外觀（視其所包含的資料而定），或者，您可以使用另一種類型的相等資料來取代其中一個資料類型的資料。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)。|  
|變更儲存格、資料列、資料行和標題外觀和行為的多個選項|<xref:System.Windows.Forms.DataGridView>控制項可讓您以許多方式使用個別的方格元件。 例如，您可以凍結資料列和資料行，以防止它們進行滾動;隱藏資料列、資料行和標頭;變更資料列、資料行和標頭大小的調整方式;變更使用者進行選取的方式;和提供個別資料格、資料列和資料行的工具提示和快捷方式功能表。|  
  
 針對回溯 <xref:System.Windows.Forms.DataGrid> 相容性和特殊需求，會保留控制項。 對於幾乎所有的用途，您都應該使用 <xref:System.Windows.Forms.DataGridView> 控制項。 控制項中未提供的唯一可用功能， <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridView> 就是從單一控制項中的兩個相關資料表的階層式顯示資訊。 您必須使用兩個 <xref:System.Windows.Forms.DataGridView> 控制項來顯示主要/詳細資料關聯性中兩個數據表的資訊。  
  
## <a name="upgrading-to-the-datagridview-control"></a>升級至 DataGridView 控制項  
 如果您現有的應用程式 <xref:System.Windows.Forms.DataGrid> 在簡單的資料系結案例中使用控制項，但沒有自訂，則您可以直接將舊控制項取代為新的控制項。 這兩個控制項都使用標準 Windows Forms 資料系結架構，因此 <xref:System.Windows.Forms.DataGridView> 控制項將會顯示您系結的資料，而不需要額外的設定。 不過，您可能會想要利用資料系結改進功能，方法是將您的資料系結至 <xref:System.Windows.Forms.BindingSource> 元件，然後您就可以將它系結至 <xref:System.Windows.Forms.DataGridView> 控制項。 如需詳細資訊，請參閱[BindingSource Component](bindingsource-component.md)。  
  
 由於 <xref:System.Windows.Forms.DataGridView> 控制項有全新的架構，因此沒有直接的轉換路徑可讓您使用 <xref:System.Windows.Forms.DataGrid> 控制項的自訂 <xref:System.Windows.Forms.DataGridView> 。 <xref:System.Windows.Forms.DataGrid>但控制項不需要進行許多自訂， <xref:System.Windows.Forms.DataGridView> 因為新控制項中提供了內建的功能。 如果您已建立 <xref:System.Windows.Forms.DataGrid> 要與控制項搭配使用之控制項的自訂資料行類型 <xref:System.Windows.Forms.DataGridView> ，就必須使用新的架構再次執行它們。 如需詳細資訊，請參閱[自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
- [BindingSource 元件](bindingsource-component.md)
- [Windows Form DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Form DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Windows Form DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料行排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的選取模式](selection-modes-in-the-windows-forms-datagridview-control.md)
- [自訂 Windows Form DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)
