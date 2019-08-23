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
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930185"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>使用內建主控描繪支援的控制項
Windows Forms 中的主控描繪也稱為自訂繪圖，是變更特定控制項的視覺外觀的技術。  
  
> [!NOTE]
> 本主題中的「控制項」一詞是用來表示衍生自<xref:System.Windows.Forms.Control>或<xref:System.ComponentModel.Component>的類別。  
  
 通常, Windows 會使用屬性設定 (例如) <xref:System.Windows.Forms.Control.BackColor%2A>來自動處理繪製, 以決定控制項的外觀。 運用主控描繪，您可接手繪製程序，來變更使用屬性無法取得的外觀項目。 例如，許多控制項都可讓您設定所顯示文字的色彩，但您只能使用單一色彩。 主控描繪可讓您執行作業，例如以黑色顯示文字的一部分，並以紅色顯示文字的一部分。  
  
 實際上，主控描繪與在表單上繪製圖形類似。 例如, 您可以在表單<xref:System.Windows.Forms.Control.Paint>事件的處理常式中使用圖形方法來`ListBox`模擬控制項, 但您必須撰寫自己的程式碼來處理所有使用者互動。 運用主控描繪，此控制項會使用您的程式碼來繪製其內容，但保有其所有內建功能。 您可以使用圖形方法來繪製控制項中的每個項目，或在使用每個項目之其他層面的預設外觀時自訂每個項目的某些層面。  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Windows Forms 控制項中的主控描繪  
 若要在支援主控描繪的控制項中執行主控描繪，您通常會設定一個屬性，並處理一或多個事件。  
  
 支援主控描繪的大部分控制項都會有 `OwnerDraw` 或 `DrawMode` 屬性，以指出控制項是否會在繪製它自己時引發其繪圖相關事件。  
  
 沒有 `OwnerDraw` 或 `DrawMode` 屬性的控制項，包括可提供自動發生的繪圖事件的 `DataGridView` 控制項，以及使用具有其主控描繪相關事件的外部轉譯類別所繪製的 `ToolStrip` 控制項。  
  
 有許多不同類型的繪圖事件，但若要在控制項內繪製單一項目，就會發生一般繪圖事件。 事件處理常式會接收 `EventArgs` 物件，此物件包含所繪製項目和其繪製工具的相關資訊。 例如, 這個物件通常<xref:System.Drawing.Rectangle>會在其父集合中包含專案的索引編號、表示專案的顯示界限的, <xref:System.Drawing.Graphics>以及用於呼叫繪製方法的物件。 針對部分事件，`EventArgs` 物件提供項目和方法的其他資訊，而您預設可以呼叫這些項目和方法來繪製項目的某些層面 (例如背景或焦點矩形)。  
  
 若要建立包含主控描繪自訂的可重複使用控制項，請建立新的類別，而此類別衍生自支援主控描繪的控制項類別。 請在新類別之適當 `On`*EventName* 方法的覆寫中包括主控描繪程式碼，而不是處理繪圖事件。 在此情況下，請確定呼叫基底類別 `On`*EventName* 方法，讓控制項的使用者可以處理主控描繪事件，並提供其他自訂。  
  
 下列 Windows Forms 控制項支援所有 .NET Framework 版本中的主控描繪：  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem>(由<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>使用)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 下列控制項僅支援在 .NET Framework 2.0 中的擁有者繪圖:  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 下列控制項支援主控描繪, 而且是 .NET Framework 2.0 中的新功能:  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 下列各節提供所有這些控制項的其他詳細資料。  
  
### <a name="listbox-and-combobox-controls"></a>ListBox 和 ComboBox 控制項  
 <xref:System.Windows.Forms.ListBox> 和<xref:System.Windows.Forms.ComboBox>控制項可讓您在控制項中繪製個別專案, 不論是在單一大小或不同的大小。  
  
> [!NOTE]
> 雖然控制項是<xref:System.Windows.Forms.ListBox>從控制項衍生而來, 但不支援擁有者繪圖。 <xref:System.Windows.Forms.CheckedListBox>  
  
 若要以相同的大小繪製每個專案`DrawMode` , 請<xref:System.Windows.Forms.DrawMode.OwnerDrawFixed>將屬性設定`DrawItem`為, 並處理事件。  
  
 若要使用不同的大小繪製每個專案, `DrawMode`請將<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>屬性設定為, `MeasureItem`並`DrawItem`同時處理和事件。 `MeasureItem` 事件可讓您指出該項目在發生 `DrawItem` 事件之前的大小。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列主題：  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [如何：在 ComboBox 控制項中建立可變大小的文字](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem 元件  
 元件代表<xref:System.Windows.Forms.MainMenu> 或<xref:System.Windows.Forms.ContextMenu>元件中的單一功能表項目。 <xref:System.Windows.Forms.MenuItem>  
  
 若要繪製<xref:System.Windows.Forms.MenuItem>, 請將`OwnerDraw`其屬性`true`設為, `DrawItem`並處理其事件。 若要自訂功能表項目在發生 `DrawItem` 事件之前的大小時，請處理項目的 `MeasureItem` 事件。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl 控制項  
 <xref:System.Windows.Forms.TabControl>控制項可讓您在控制項中繪製個別的索引標籤。 擁有者繪圖只會影響索引標籤;<xref:System.Windows.Forms.TabPage>內容不會受到影響。  
  
 若<xref:System.Windows.Forms.TabControl>要在中繪製每個索引標籤, 請`DrawMode`將`DrawItem`屬性設定為<xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> , 並處理事件。 只有在控制項中顯示索引標籤時，才會針對該索引標籤發生此事件一次。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip 元件  
 <xref:System.Windows.Forms.ToolTip>元件可讓您在顯示整個工具提示時進行繪製。  
  
 若要繪製<xref:System.Windows.Forms.ToolTip>, 請將`OwnerDraw`其屬性`true`設為, `Draw`並處理其事件。 <xref:System.Windows.Forms.ToolTip>若要自訂`Draw` <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A>事件發生之前的大小, 請處理事件,並在事件處理常式中設定屬性。`Popup`  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView 控制項  
 <xref:System.Windows.Forms.ListView>控制項可讓您在控制項中繪製個別的專案、子項和資料行標頭。  
  
 若要在控制項中啟用主控描繪，請將 `OwnerDraw` 屬性設定為 `true`。  
  
 若要繪製控制項中的每個項目，請處理 `DrawItem` 事件。  
  
 當<xref:System.Windows.Forms.ListView.View%2A>屬性設定為<xref:System.Windows.Forms.View.Details>時, 若要在控制項中繪製每個子欄位或資料行標`DrawSubItem`頭`DrawColumnHeader` , 請處理和事件。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView 控制項  
 <xref:System.Windows.Forms.TreeView>控制項可讓您在控制項中繪製個別節點。  
  
 若只要繪製每個節點中顯示的文字, 請`DrawMode`將屬性<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText>設定為, `DrawNode`並處理事件以繪製文字。  
  
 若要繪製每個節點的所有元素, `DrawMode`請將<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll>屬性設定為`DrawNode` , 並處理事件以繪製您所需的任何專案, 例如文字、圖示、核取方塊、加號和減號, 以及連接節點的線條。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列參考主題：  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView 控制項  
 <xref:System.Windows.Forms.DataGridView>控制項可讓您在控制項中繪製個別的儲存格和資料列。  
  
 若要繪製個別儲存格，請處理 `CellPainting` 事件。  
  
 若要繪製個別資料列或是資料列的項目，請處理 `RowPrePaint` 和 `RowPostPaint` 事件中的其中一或兩個。 繪製資料列中的儲存格之前會發生 `RowPrePaint` 事件，而在繪製儲存格之後會發生 `RowPostPaint` 事件。 您可以處理這兩個事件和 `CellPainting` 事件來分別繪製資料列背景、個別儲存格和資料列前景，也可以提供所需的特定自訂，並使用資料列之其他項目的預設顯示。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列主題：  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [如何：在 Windows Forms DataGridView 控制項中自訂儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [如何：在 Windows Forms DataGridView 控制項中自訂資料列的外觀](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip 控制項  
 <xref:System.Windows.Forms.ToolStrip>和衍生的控制項可讓您自訂其外觀的任何層面。  
  
 若<xref:System.Windows.Forms.ToolStrip>要提供控制項的自訂轉譯, `Renderer`請將<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripManager>、 <xref:System.Windows.Forms.ToolStripPanel>或<xref:System.Windows.Forms.ToolStripContentPanel>的屬性設定為`ToolStripRenderer`物件, 並處理由所提供之多個繪製事件的一個或多個`ToolStripRenderer`類別。 `Renderer`或者, 將屬性設定為您自己的類別實例, 衍生自`ToolStripRenderer`、 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>或<xref:System.Windows.Forms.ToolStripSystemRenderer> , 以執行或覆寫`On`特定的*事件名稱*方法。  
  
 如需詳細資訊 (包括程式碼範例)，請參閱下列主題：  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [如何：在 Windows Forms 中建立和設定 ToolStrip 控制項的自訂轉譯器](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [如何：自訂繪製 ToolStrip 控制項](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>另請參閱

- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
