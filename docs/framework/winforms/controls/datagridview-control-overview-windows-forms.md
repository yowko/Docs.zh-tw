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
ms.openlocfilehash: 03ba4e13cb014ca03f80781e6630d41c01ae6251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529960"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView 控制項概觀 (Windows Form)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 與<xref:System.Windows.Forms.DataGridView>控制項，您可以顯示和編輯從許多不同種類的資料來源的表格式資料。  
  
 資料繫結至<xref:System.Windows.Forms.DataGridView>控制項的簡單而直覺，以及在許多情況下很簡單，只設定<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性。 當您繫結至資料來源包含多個清單或資料表時，設定<xref:System.Windows.Forms.DataGridView.DataMember%2A>屬性設為指定之清單或繫結至資料表的字串。  
  
 <xref:System.Windows.Forms.DataGridView>控制項支援標準的 Windows Form 資料繫結模型，因此它會繫結至下列清單所述類別的執行個體：  
  
-   任何實作類別<xref:System.Collections.IList>介面，包括一維陣列。  
  
-   任何實作類別<xref:System.ComponentModel.IListSource>介面，例如<xref:System.Data.DataTable>和<xref:System.Data.DataSet>類別。  
  
-   任何實作類別<xref:System.ComponentModel.IBindingList>介面，例如<xref:System.ComponentModel.BindingList%601>類別。  
  
-   任何實作類別<xref:System.ComponentModel.IBindingListView>介面，例如<xref:System.Windows.Forms.BindingSource>類別。  
  
 <xref:System.Windows.Forms.DataGridView>控制項支援這些介面所傳回之物件的公用屬性或屬性集合所傳回的資料繫結<xref:System.ComponentModel.ICustomTypeDescriptor>介面，如果傳回的物件上實作。  
  
 一般而言，您會繫結，以<xref:System.Windows.Forms.BindingSource>元件，並繫結<xref:System.Windows.Forms.BindingSource>元件至另一個資料來源，或使用商務物件填入。 <xref:System.Windows.Forms.BindingSource>元件是慣用的資料來源，因為它可以繫結至各種資料來源，並自動解決許多資料繫結問題。 如需詳細資訊，請參閱[BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)。  
  
 <xref:System.Windows.Forms.DataGridView>控制項也可用在*未繫結*模式中的，不包含基礎資料存放區。 使用未繫結的程式碼範例<xref:System.Windows.Forms.DataGridView>控制，請參閱[逐步解說： 建立未繫結的 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)。  
  
 <xref:System.Windows.Forms.DataGridView>控制項高度可設定且可延伸的而且它會提供許多屬性、 方法和事件，以自訂其外觀和行為。 當您想要 Windows Forms 應用程式顯示表格式資料時，請考慮使用<xref:System.Windows.Forms.DataGridView>再其他控制項 (例如， <xref:System.Windows.Forms.DataGrid>)。 如果您要顯示小型的唯讀值方格，或如果您正在啟用使用者編輯數百萬筆記錄，與資料表<xref:System.Windows.Forms.DataGridView>控制項提供您隨時可程式化、 記憶體有效率的解決方案。  
  
## <a name="in-this-section"></a>本節內容  
 [DataGridView 控制項技術摘要](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 摘要說明<xref:System.Windows.Forms.DataGridView>控制概念和相關的類別使用。  
  
 [DataGridView 控制項架構](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 描述的架構<xref:System.Windows.Forms.DataGridView>控制項，並說明其型別階層架構和繼承結構。  
  
 [DataGridView 控制項案例](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 描述最常見的案例中<xref:System.Windows.Forms.DataGridView>控制項可用。  
  
 [DataGridView 控制項程式碼目錄](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 提供不同的文件中的程式碼範例的連結<xref:System.Windows.Forms.DataGridView>工作。 這些範例是以工作類型分類。  
  
## <a name="related-sections"></a>相關章節  
 [Windows Forms DataGridView 控制項中的資料行類型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 討論 Windows Form 中的資料行類型<xref:System.Windows.Forms.DataGridView>控制項用來顯示資訊，並允許使用者修改或新增資訊。  
  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 提供主題描述如何以手動方式或從外部資料來源將資料填入控制項。  
  
 [自訂 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 提供主題描述自訂繪製 <xref:System.Windows.Forms.DataGridView> 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。  
  
 [Windows Forms DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 提供主題描述處理大量資料時，如何有效率地使用控制項來避免發生效能問題。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Windows Forms DataGridView 控制項的預設功能](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠處理](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
