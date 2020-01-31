---
title: DataGridView 控制項架構
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742536"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView 控制項架構 (Windows Form)
<xref:System.Windows.Forms.DataGridView> 控制項和其相關類別的設計，是彈性且可擴充的系統，可用於顯示和編輯表格式資料。 這些類別全都包含在 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間中，而且全都以 "DataGridView" 前置詞命名。  
  
## <a name="architecture-elements"></a>架構項目  
 主要 <xref:System.Windows.Forms.DataGridView> 隨附類別衍生自 <xref:System.Windows.Forms.DataGridViewElement>。 下列物件模型說明 <xref:System.Windows.Forms.DataGridViewElement> 繼承階層架構。  
  
 ![顯示 DataGridViewElement 物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewElement> 類別會提供父 <xref:System.Windows.Forms.DataGridView> 控制項的參考，並具有 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 屬性，它會保存一個值，表示來自 <xref:System.Windows.Forms.DataGridViewElementStates> 列舉的值組合。  
  
 下列各節會更詳細地說明 <xref:System.Windows.Forms.DataGridView> 附屬類別。  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates> 列舉包含下列值：  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 這個列舉的值可以與位邏輯運算子結合，因此 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 屬性可以同時表示一次以上的狀態。 例如，<xref:System.Windows.Forms.DataGridViewElement> 可以同時 <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>、<xref:System.Windows.Forms.DataGridViewElementStates.Selected>和 <xref:System.Windows.Forms.DataGridViewElementStates.Visible>。  
  
### <a name="cells-and-bands"></a>資料格和頻帶  
 <xref:System.Windows.Forms.DataGridView> 控制項包含兩種基本的物件：資料格和波段。 所有資料格都衍生自 <xref:System.Windows.Forms.DataGridViewCell> 基類。 兩種類型的群組（<xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.DataGridViewRow>）皆衍生自 <xref:System.Windows.Forms.DataGridViewBand> 基類。  
  
 <xref:System.Windows.Forms.DataGridView> 控制項與數個類別交互操作，但最常遇到的是 <xref:System.Windows.Forms.DataGridViewCell>、<xref:System.Windows.Forms.DataGridViewColumn>和 <xref:System.Windows.Forms.DataGridViewRow>。  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 資料格是 <xref:System.Windows.Forms.DataGridView>的互動基礎單位。 顯示是以儲存格為中心，而資料輸入通常是透過儲存格來執行。 您可以使用 <xref:System.Windows.Forms.DataGridViewRow> 類別的 <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> 集合來存取資料格，而且可以使用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 集合來存取選取的儲存格。 下列物件模型說明這種用法，並顯示 <xref:System.Windows.Forms.DataGridViewCell> 繼承階層架構。  
  
 ![顯示 DataGridViewCell 物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewCell> 類型是抽象基類，所有的資料格類型都會從中衍生。 <xref:System.Windows.Forms.DataGridViewCell> 及其衍生型別不是 Windows Forms 控制項，但是某些主機 Windows Forms 控制項。 資料格支援的任何編輯功能通常是由裝載的控制項所處理。  
  
 <xref:System.Windows.Forms.DataGridViewCell> 物件無法以 Windows Forms 控制項的相同方式來控制自己的外觀和繪製功能。 相反地，<xref:System.Windows.Forms.DataGridView> 會負責其 <xref:System.Windows.Forms.DataGridViewCell> 物件的外觀。 您可以藉由與 <xref:System.Windows.Forms.DataGridView> 控制項的屬性和事件互動，大幅影響資料格的外觀和行為。 當您對於超出 <xref:System.Windows.Forms.DataGridView> 控制項功能的自訂有特殊需求時，您可以實作為衍生自 <xref:System.Windows.Forms.DataGridViewCell> 或其其中一個子類別的類別。  
  
 下列清單顯示衍生自 <xref:System.Windows.Forms.DataGridViewCell>的類別：  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- 您的自訂資料格類型  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 <xref:System.Windows.Forms.DataGridView> 控制項之附加資料存放區的架構，會以 <xref:System.Windows.Forms.DataGridView> 控制項的資料行表示。 您可以使用 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合來存取 <xref:System.Windows.Forms.DataGridView> 控制項的資料行。 您可以使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 集合來存取選取的資料行。 下列物件模型說明這種用法，並顯示 <xref:System.Windows.Forms.DataGridViewColumn> 繼承階層架構。  
  
 ![顯示 DataGridViewColumn 物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 某些索引鍵資料格類型具有對應的資料行類型。 這些衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 基類。  
  
 下列清單顯示衍生自 <xref:System.Windows.Forms.DataGridViewColumn>的類別：  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- 您的自訂資料行類型  
  
### <a name="datagridview-editing-controls"></a>DataGridView 編輯控制項  
 支援先進編輯功能的儲存格通常會使用衍生自 Windows Forms 控制項的裝載控制項。 這些控制項也會執行 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面。 下列物件模型說明這些控制項的使用方式。  
  
 ![顯示 DataGridView 編輯控制項物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridView> 控制項提供下列編輯控制項：  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 如需建立您自己的編輯控制項的詳細資訊，請參閱[如何： Windows Forms DataGridView 儲存格中的主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
 下表說明資料格類型、資料行類型和編輯控制項之間的關聯性。  
  
|資料格類型|Hosted 控制項|資料行類型|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N/A|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|N/A|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|N/A|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N/A|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow> 類別會從附加 <xref:System.Windows.Forms.DataGridView> 控制項的資料存放區中，顯示記錄的資料欄位。 您可以使用 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合來存取 <xref:System.Windows.Forms.DataGridView> 控制項的資料列。 您可以使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 集合來存取選取的資料列。 下列物件模型說明這種用法，並顯示 <xref:System.Windows.Forms.DataGridViewRow> 繼承階層架構。  
  
 ![顯示 DataGridViewRow 物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 您可以從 <xref:System.Windows.Forms.DataGridViewRow> 類別衍生自己的型別，雖然這通常不是必要的。 <xref:System.Windows.Forms.DataGridView> 控制項有數個與資料列相關的事件和屬性，可自訂其 <xref:System.Windows.Forms.DataGridViewRow> 物件的行為。  
  
 如果您啟用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性，加入新資料列的特殊資料列就會顯示為最後一個資料列。 這個資料列是 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合的一部分，但它有特殊功能需要您的注意。 如需詳細資訊，請參閱在[Windows Forms DataGridView 控制項中使用資料列做為新記錄](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>請參閱

- [DataGridView 控制項概觀](datagridview-control-overview-windows-forms.md)
- [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)
- [使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
