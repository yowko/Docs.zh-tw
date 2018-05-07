---
title: 使用內建主控描繪支援的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: a5cbdc733a2f1cda3e708ceaae8604297f8da58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="controls-with-built-in-owner-drawing-support"></a>使用內建主控描繪支援的控制項
Windows Forms 中的主控描繪也稱為自訂繪圖，是變更特定控制項的視覺外觀的技術。  
  
> [!NOTE]
>  本主題中的 「 控制項 」 這個字用來表示類別衍生自<xref:System.Windows.Forms.Control>或<xref:System.ComponentModel.Component>。  
  
 一般而言，Windows 繪製自動使用處理屬性設定，例如<xref:System.Windows.Forms.Control.BackColor%2A>以判斷控制項的外觀。 運用主控描繪，您可接手繪製程序，來變更使用屬性無法取得的外觀項目。 例如，許多控制項都可讓您設定所顯示文字的色彩，但您只能使用單一色彩。 主控描繪可讓您執行作業，例如以黑色顯示文字的一部分，並以紅色顯示文字的一部分。  
  
 實際上，主控描繪與在表單上繪製圖形類似。 例如，您可以處理常式中使用圖形方法的表單<xref:System.Windows.Forms.Control.Paint>事件，以模擬`ListBox`控制項，但是您必須撰寫您自己的程式碼來處理所有使用者互動。 運用主控描繪，此控制項會使用您的程式碼來繪製其內容，但保有其所有內建功能。 您可以使用圖形方法來繪製控制項中的每個項目，或在使用每個項目之其他層面的預設外觀時自訂每個項目的某些層面。  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Windows Forms 控制項中的主控描繪  
 若要在支援主控描繪的控制項中執行主控描繪，您通常會設定一個屬性，並處理一或多個事件。  
  
 支援主控描繪的大部分控制項都會有 `OwnerDraw` 或 `DrawMode` 屬性，以指出控制項是否會在繪製它自己時引發其繪圖相關事件。  
  
 沒有 `OwnerDraw` 或 `DrawMode` 屬性的控制項，包括可提供自動發生的繪圖事件的 `DataGridView` 控制項，以及使用具有其主控描繪相關事件的外部轉譯類別所繪製的 `ToolStrip` 控制項。  
  
 有許多不同類型的繪圖事件，但若要在控制項內繪製單一項目，就會發生一般繪圖事件。 事件處理常式會接收 `EventArgs` 物件，此物件包含所繪製項目和其繪製工具的相關資訊。 例如，此物件通常會包含的項目，其父系集合內的索引編號<xref:System.Drawing.Rectangle>，指出項目的顯示界限，和<xref:System.Drawing.Graphics>呼叫 [小畫家] 方法的物件。 針對部分事件，`EventArgs` 物件提供項目和方法的其他資訊，而您預設可以呼叫這些項目和方法來繪製項目的某些層面 (例如背景或焦點矩形)。  
  
 若要建立包含主控描繪自訂的可重複使用控制項，請建立新的類別，而此類別衍生自支援主控描繪的控制項類別。 請在新類別之適當 `On`*EventName* 方法的覆寫中包括主控描繪程式碼，而不是處理繪圖事件。 在此情況下，請確定呼叫基底類別 `On`*EventName* 方法，讓控制項的使用者可以處理主控描繪事件，並提供其他自訂。  
  
 下列 Windows Forms 控制項支援所有 .NET Framework 版本中的主控描繪：  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (使用<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 下列控制項只有在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中才支援主控描繪：  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 下列控制項支援主控描繪，而且是 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中的新項目：  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 下列各節提供所有這些控制項的其他詳細資料。  
  
### <a name="listbox-and-combobox-controls"></a>ListBox 和 ComboBox 控制項  
 <xref:System.Windows.Forms.ListBox>和<xref:System.Windows.Forms.ComboBox>控制項可讓您在一種大小，或在不同大小的控制項中繪製的個別項目。  
  
> [!NOTE]
>  雖然<xref:System.Windows.Forms.CheckedListBox>控制項衍生自<xref:System.Windows.Forms.ListBox>控制項，它不支援主控描繪。  
  
 若要繪製每個項目相同的大小，設定`DrawMode`屬性<xref:System.Windows.Forms.DrawMode.OwnerDrawFixed>及處理`DrawItem`事件。  
  
 若要繪製每個使用不同大小的項目，設定`DrawMode`屬性<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>和處理這兩`MeasureItem`和`DrawItem`事件。 `MeasureItem` 事件可讓您指出該項目在發生 `DrawItem` 事件之前的大小。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列主題：  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [操作說明：在 ComboBox 控制項中建立各種大小的文字](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem 元件  
 <xref:System.Windows.Forms.MenuItem>元件表示的單一功能表項目<xref:System.Windows.Forms.MainMenu>或<xref:System.Windows.Forms.ContextMenu>元件。  
  
 要繪製<xref:System.Windows.Forms.MenuItem>，將其`OwnerDraw`屬性`true`並處理其`DrawItem`事件。 若要自訂功能表項目在發生 `DrawItem` 事件之前的大小時，請處理項目的 `MeasureItem` 事件。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl 控制項  
 <xref:System.Windows.Forms.TabControl>控制項可讓您在控制項中繪製的個別索引標籤。 主控描繪會影響索引標籤。<xref:System.Windows.Forms.TabPage>內容不會受到影響。  
  
 若要繪製每個索引標籤<xref:System.Windows.Forms.TabControl>，將`DrawMode`屬性<xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>及處理`DrawItem`事件。 只有在控制項中顯示索引標籤時，才會針對該索引標籤發生此事件一次。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip 元件  
 <xref:System.Windows.Forms.ToolTip>元件可讓您繪製整個工具提示顯示時。  
  
 要繪製<xref:System.Windows.Forms.ToolTip>，將其`OwnerDraw`屬性`true`並處理其`Draw`事件。 若要自訂的大小<xref:System.Windows.Forms.ToolTip>之前`Draw`事件發生時，處理`Popup`事件以及組<xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A>事件處理常式中的屬性。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView 控制項  
 <xref:System.Windows.Forms.ListView>控制項可讓您在控制項中繪製的個別項目、 子項目和資料行標頭。  
  
 若要在控制項中啟用主控描繪，請將 `OwnerDraw` 屬性設定為 `true`。  
  
 若要繪製控制項中的每個項目，請處理 `DrawItem` 事件。  
  
 若要在控制項中繪製每一個子項目或資料行的標頭時<xref:System.Windows.Forms.ListView.View%2A>屬性設定為<xref:System.Windows.Forms.View.Details>，處理`DrawSubItem`和`DrawColumnHeader`事件。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView 控制項  
 <xref:System.Windows.Forms.TreeView>控制項可讓您在控制項中繪製的個別節點。  
  
 若要繪製只會顯示每個節點中的文字，設定`DrawMode`屬性<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText>及處理`DrawNode`來繪製文字的事件。  
  
 若要繪製的每個節點的所有項目，設定`DrawMode`屬性<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll>及處理`DrawNode`事件，以繪製任何所需項目，例如文字、 圖示、 核取方塊，加號和減號，以及連接節點的線條。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView 控制項  
 <xref:System.Windows.Forms.DataGridView>控制項可讓您在控制項中繪製的個別資料格和資料列。  
  
 若要繪製個別儲存格，請處理 `CellPainting` 事件。  
  
 若要繪製個別資料列或是資料列的項目，請處理 `RowPrePaint` 和 `RowPostPaint` 事件中的其中一或兩個。 繪製資料列中的儲存格之前會發生 `RowPrePaint` 事件，而在繪製儲存格之後會發生 `RowPostPaint` 事件。 您可以處理這兩個事件和 `CellPainting` 事件來分別繪製資料列背景、個別儲存格和資料列前景，也可以提供所需的特定自訂，並使用資料列之其他項目的預設顯示。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列主題：  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [操作說明：在 Windows Forms DataGridView 控制項中自訂儲存格的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [如何：在 Windows Forms DataGridView 控制項中自訂資料列的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip 控制項  
 <xref:System.Windows.Forms.ToolStrip> 衍生的控制項可讓您自訂其外觀的任何層面。  
  
 若要提供的自訂轉譯<xref:System.Windows.Forms.ToolStrip>控制項設定`Renderer`屬性<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.ToolStripManager>， <xref:System.Windows.Forms.ToolStripPanel>，或<xref:System.Windows.Forms.ToolStripContentPanel>至`ToolStripRenderer`物件，並處理一個或多個所提供的許多繪製事件`ToolStripRenderer`類別。 或者，設定`Renderer`您自己的類別執行個體的屬性衍生自`ToolStripRenderer`， <xref:System.Windows.Forms.ToolStripProfessionalRenderer>，或<xref:System.Windows.Forms.ToolStripSystemRenderer>所實作或覆寫特定`On` *EventName*方法。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列主題：  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [操作說明：建立和設定 Windows Forms 中的 ToolStrip 控制項自訂產生器](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [如何：自訂繪製 ToolStrip 控制項](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>另請參閱  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
