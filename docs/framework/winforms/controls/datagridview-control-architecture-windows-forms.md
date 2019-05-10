---
title: DataGridView 控制項架構 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 15d10ed2ec0bc78acfe887fe583d4850425eeab9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648102"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView 控制項架構 (Windows Form)
<xref:System.Windows.Forms.DataGridView>控制項以及與其相關的類別都是設計成有彈性、 可擴充的系統，來顯示和編輯表格式資料。 這些類別包含在<xref:System.Windows.Forms?displayProperty=nameWithType>命名空間，而且它們所有以"DataGridView"前置詞命名。  
  
## <a name="architecture-elements"></a>架構項目  
 主要<xref:System.Windows.Forms.DataGridView>附屬類別衍生自<xref:System.Windows.Forms.DataGridViewElement>。 下列物件模型說明<xref:System.Windows.Forms.DataGridViewElement>繼承階層架構。  
  
 ![顯示 DataGridViewElement 物件模型階層架構的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewElement>類別提供的參考至父代<xref:System.Windows.Forms.DataGridView>控制項，並具有<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性，其中包含值，表示從值的組合<xref:System.Windows.Forms.DataGridViewElementStates>列舉型別。  
  
 下列各節說明<xref:System.Windows.Forms.DataGridView>附屬類別中更多詳細資料。  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates>列舉型別包含下列值：  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 這個列舉型別的值可以結合這些位元的邏輯運算子，因此<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性可以用來表示多個狀態一次。 例如，<xref:System.Windows.Forms.DataGridViewElement>可以同時<xref:System.Windows.Forms.DataGridViewElementStates.Frozen>， <xref:System.Windows.Forms.DataGridViewElementStates.Selected>，和<xref:System.Windows.Forms.DataGridViewElementStates.Visible>。  
  
### <a name="cells-and-bands"></a>儲存格和群組列  
 <xref:System.Windows.Forms.DataGridView>控制項包含兩個基本類型的物件： 資料格和群組列。 所有資料格衍生自<xref:System.Windows.Forms.DataGridViewCell>基底類別。 這兩種帶狀<xref:System.Windows.Forms.DataGridViewColumn>並<xref:System.Windows.Forms.DataGridViewRow>，都是衍生自<xref:System.Windows.Forms.DataGridViewBand>基底類別。  
  
 <xref:System.Windows.Forms.DataGridView>控制項互通的數個類別，但是最常遇到<xref:System.Windows.Forms.DataGridViewCell>， <xref:System.Windows.Forms.DataGridViewColumn>，和<xref:System.Windows.Forms.DataGridViewRow>。  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 儲存格是互動的基本單位<xref:System.Windows.Forms.DataGridView>。 顯示為置中對齊資料格，並輸入資料通常會執行到的資料格。 您可以使用來存取資料格<xref:System.Windows.Forms.DataGridViewRow.Cells%2A>的集合<xref:System.Windows.Forms.DataGridViewRow>類別，而您可以使用存取選取的資料格<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>的集合<xref:System.Windows.Forms.DataGridView>控制項。 下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewCell>繼承階層架構。  
  
 ![顯示 DataGridViewCell 物件模型階層架構的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewCell>型別是抽象的基底類別，從其中衍生所有的資料格類型。 <xref:System.Windows.Forms.DataGridViewCell> 和其衍生型別不是 Windows Forms 控制項，而某些主機的 Windows Form 控制項。 裝載的控制項通常會處理任何支援的資料格的編輯功能。  
  
 <xref:System.Windows.Forms.DataGridViewCell> Windows Form 控制項，物件相同的方式控制自己的外觀和繪製功能。 相反地，<xref:System.Windows.Forms.DataGridView>負責的外觀及其<xref:System.Windows.Forms.DataGridViewCell>物件。 您可以大幅影響的外觀和行為的資料格與互動<xref:System.Windows.Forms.DataGridView>控制項的屬性和事件。 當您有特殊需求的功能，自訂<xref:System.Windows.Forms.DataGridView>控制項，您可以實作自己的類別衍生自<xref:System.Windows.Forms.DataGridViewCell>或其中一個子類別。  
  
 下列清單顯示衍生自的類別<xref:System.Windows.Forms.DataGridViewCell>:  
  
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
  
- 您的自訂儲存格型別  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 結構描述<xref:System.Windows.Forms.DataGridView>控制的連接的資料存放區以表示<xref:System.Windows.Forms.DataGridView>控制項的資料行。 您可以存取<xref:System.Windows.Forms.DataGridView>控制項的資料行使用<xref:System.Windows.Forms.DataGridView.Columns%2A>集合。 您可以使用來存取所選資料行<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>集合。 下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewColumn>繼承階層架構。  
  
 ![顯示 DataGridViewColumn 物件模型階層架構的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 某些索引鍵的資料格類型有對應的資料行類型。 這些衍生自<xref:System.Windows.Forms.DataGridViewColumn>基底類別。  
  
 下列清單顯示衍生自的類別<xref:System.Windows.Forms.DataGridViewColumn>:  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- 您的自訂資料行類型  
  
### <a name="datagridview-editing-controls"></a>DataGridView 編輯控制項  
 通常支援進階的編輯功能的資料格會使用裝載的控制項是衍生自 Windows Forms 控制項。 這些控制項也會實作<xref:System.Windows.Forms.IDataGridViewEditingControl>介面。 下列物件模型會說明這些控制項的用法。  
  
 ![此圖表顯示 DataGridView 編輯控制項物件模型階層架構。](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 下列的編輯控制項所提供的<xref:System.Windows.Forms.DataGridView>控制項：  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 如需建立自己的編輯控制項的資訊，請參閱[How to:Windows Forms DataGridView 儲存格主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
 下表說明資料格類型、 資料行類型，以及編輯控制項之間的關聯性。  
  
|資料格類型|裝載的控制項|資料行類型|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N/A|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|N/A|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|N/A|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N/A|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow>類別會顯示記錄的資料欄位從資料存放區複製到其中<xref:System.Windows.Forms.DataGridView>控制項所附加的。 您可以存取<xref:System.Windows.Forms.DataGridView>控制項的資料列，使用<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。 您可以使用來存取選取的資料列<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>集合。 下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewRow>繼承階層架構。  
  
 ![顯示 DataGridViewRow 物件模型階層架構的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 您可以衍生自己的型別，從<xref:System.Windows.Forms.DataGridViewRow>類別，雖然這通常不是必要的。 <xref:System.Windows.Forms.DataGridView>控制項有數個資料列相關的事件和自訂的行為的屬性其<xref:System.Windows.Forms.DataGridViewRow>物件。  
  
 如果您啟用<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>屬性，加入新資料列的特殊資料列會顯示為最後一個資料列。 此資料列屬於<xref:System.Windows.Forms.DataGridView.Rows%2A>集合，但它有可能需要注意的特殊功能。 如需詳細資訊，請參閱 <<c0> [ 使用 Windows Form DataGridView 控制項中的新資料錄的資料列](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- [DataGridView 控制項概觀](datagridview-control-overview-windows-forms.md)
- [自訂 Windows Forms DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)
- [使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
