---
title: DataGridView 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 992bf57642c955a87cd7675e0bbe7c52131e8039
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969141"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView 控制項概觀 (Windows Form)
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 <xref:System.Windows.Forms.DataGridView>使用控制項, 您可以從許多不同類型的資料來源顯示和編輯表格式資料。  
  
 將資料系結<xref:System.Windows.Forms.DataGridView>至控制項既簡單又直覺, 而且在許多情況下, 它就像<xref:System.Windows.Forms.DataGridView.DataSource%2A>設定屬性一樣簡單。 當您系結至包含多個清單或資料表的資料來源時, <xref:System.Windows.Forms.DataGridView.DataMember%2A>請將屬性設定為指定要系結之清單或資料表的字串。  
  
 <xref:System.Windows.Forms.DataGridView>控制項支援標準 Windows Forms 資料系結模型, 因此它會系結至下列清單中所述類別的實例:  
  
- 任何會<xref:System.Collections.IList>執行介面的類別, 包括一維陣列。  
  
- 任何會<xref:System.ComponentModel.IListSource>執行介面的類別, 例如<xref:System.Data.DataTable>和<xref:System.Data.DataSet>類別。  
  
- 任何會<xref:System.ComponentModel.IBindingList>執行介面的類別, 例如<xref:System.ComponentModel.BindingList%601>類別。  
  
- 任何會<xref:System.ComponentModel.IBindingListView>執行介面的類別, 例如<xref:System.Windows.Forms.BindingSource>類別。  
  
 控制項支援將資料系結至這些介面所傳回之物件的公用屬性或<xref:System.ComponentModel.ICustomTypeDescriptor>介面所傳回的屬性集合 (如果在傳回的物件上執行)。 <xref:System.Windows.Forms.DataGridView>  
  
 一般來說, 您會系結至<xref:System.Windows.Forms.BindingSource>元件, 並<xref:System.Windows.Forms.BindingSource>將元件系結至另一個資料來源, 或將它填入商務物件。 <xref:System.Windows.Forms.BindingSource>元件是慣用的資料來源, 因為它可以系結至各種不同的資料來源, 而且可以自動解決許多資料系結問題。 如需詳細資訊, 請參閱[BindingSource Component](bindingsource-component.md)。  
  
 控制項也可以在未系結模式中使用, 但不含基礎資料存放區。 <xref:System.Windows.Forms.DataGridView> 如需使用未<xref:System.Windows.Forms.DataGridView>系結控制項的程式碼範例, 請參閱[逐步解說:建立未系結的 Windows Forms](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)DataGridView 控制項。  
  
 此<xref:System.Windows.Forms.DataGridView>控制項可高度設定和擴充, 並提供許多屬性、方法和事件來自訂其外觀和行為。 當您想要 Windows Forms 應用程式顯示表格式資料時, 請考慮<xref:System.Windows.Forms.DataGridView>在其他人之前使用控制項 ( <xref:System.Windows.Forms.DataGrid>例如)。 如果您要顯示唯讀值的小型方格, 或如果您要讓使用者編輯含有數百萬筆記錄的資料表, 此<xref:System.Windows.Forms.DataGridView>控制項將提供您容易程式化、記憶體有效率的解決方案。  
  
## <a name="in-this-section"></a>本節內容  
 [DataGridView 控制項技術摘要](datagridview-control-technology-summary-windows-forms.md)  
 摘要<xref:System.Windows.Forms.DataGridView>說明控制項概念和相關類別的使用。  
  
 [DataGridView 控制項架構](datagridview-control-architecture-windows-forms.md)  
 描述<xref:System.Windows.Forms.DataGridView>控制項的架構, 說明其類型階層和繼承結構。  
  
 [DataGridView 控制項案例](datagridview-control-scenarios-windows-forms.md)  
 描述使用<xref:System.Windows.Forms.DataGridView>控制項的最常見案例。  
  
 [DataGridView 控制項程式碼目錄](datagridview-control-code-directory-windows-forms.md)  
 提供各種<xref:System.Windows.Forms.DataGridView>工作檔中程式碼範例的連結。 這些範例是以工作類型分類。  
  
## <a name="related-sections"></a>相關章節  
 [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)  
 討論用來顯示資訊的 Windows Forms <xref:System.Windows.Forms.DataGridView>控制項中的資料行類型, 並允許使用者修改或加入資訊。  
  
 [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)  
 提供主題描述如何以手動方式或從外部資料來源將資料填入控制項。  
  
 [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)  
 提供主題描述自訂繪製 <xref:System.Windows.Forms.DataGridView> 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。  
  
 [Windows Forms DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 提供主題描述處理大量資料時，如何有效率地使用控制項來避免發生效能問題。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView 控制項的預設功能](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠處理](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
