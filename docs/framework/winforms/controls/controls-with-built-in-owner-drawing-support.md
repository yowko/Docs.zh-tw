---
title: "使用內建主控描繪支援的控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "繪圖，擁有者"
  - "繪製、 自訂"
  - "變更外觀的控制項 [Windows Form]"
  - "自訂繪圖"
  - "主控描繪"
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 使用內建主控描繪支援的控制項
主控描繪在 Windows Form，也就是自訂繪圖，是變更某些控制項的視覺外觀的技術。  
  
> [!NOTE]
>  本主題中的 「 控制項 」 這個字就會用來表示類別衍生自<xref:System.Windows.Forms.Control>或<xref:System.ComponentModel.Component>。  
  
 一般而言，Windows 會處理繪製自動使用屬性設定，例如<xref:System.Windows.Forms.Control.BackColor%2A>來判斷控制項的外觀。 主控描繪您接管繪製程序中，變更的外觀不使用屬性的項目。 例如，許多控制項讓您設定，會顯示文字的色彩，但您受限於單一色彩。 主控描繪可讓您執行作業，例如在黑白部分以紅色顯示文字的一部分。  
  
 實際上，主控描繪是類似於表單上繪製圖形。 例如，您可以處理常式中使用圖形方法在表單<xref:System.Windows.Forms.Control.Paint>事件，以模擬`ListBox`控制項，但是您必須撰寫自己的程式碼來處理所有的使用者互動。 主控描繪控制項來繪製其內容會使用您的程式碼，但是保有其所有的內建功能。 繪製控制項中的每個項目，或自訂的每個項目的某些層面，每個項目的其他部分使用的預設外觀時，您可以使用圖形方法。  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>主控描繪在 Windows Form 控制項  
 若要執行主控描繪支援的控制項中，您將通常設定一個屬性，並處理一個或多個事件。  
  
 大部分控制項都有該支援主控描繪`OwnerDraw`或`DrawMode`屬性，指出控制項是否會引發其繪圖相關之事件或事件時，它可以繪製本身。  
  
 不需要的控制項`OwnerDraw`或`DrawMode`屬性包含`DataGridView`控制項，提供自動發生的繪製事件，而`ToolStrip`控制項，會繪製使用外部轉譯的類別具有其本身繪圖相關的事件。  
  
 有許多不同種類的繪製事件，但若要繪製的控制項中的單一項目就會發生一般的繪製事件。 事件處理常式會接收`EventArgs`物件，包含要繪製項目的相關資訊及工具，您可以用來繪製。 比方說，這個物件通常包含它的父集合中項目的索引編號<xref:System.Drawing.Rectangle>，指出項目的顯示界限，以及<xref:System.Drawing.Graphics>呼叫 [小畫家] 方法的物件。 以及某些事件`EventArgs`物件提供的項目和方法，您可以呼叫以根據預設，例如背景或焦點矩形中繪製項目的某些層面的其他資訊。  
  
 若要建立可重複使用的控制項，其中包含您為主控描繪的自訂設定，建立衍生自支援主控描繪控制項類別的新類別。 而不是處理繪製事件，包括您的主控描繪程式碼中適當的覆寫`On` *EventName*方法或新的類別中的方法。 請確定呼叫基底類別`On` *EventName*方法或方法，在此情況下，讓控制項的使用者可以處理主控描繪事件，並提供其他的自訂。  
  
 下列 Windows Form 控制項支援主控描繪中所有.NET Framework 版本︰  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (由<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 下列控制項支援主控描繪只能在[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 下列控制項支援主控描繪且新[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 下列各節會提供其他詳細資料，每個這些控制項。  
  
### <a name="listbox-and-combobox-controls"></a>清單方塊和下拉式方塊控制項  
 <xref:System.Windows.Forms.ListBox>和<xref:System.Windows.Forms.ComboBox>控制項可讓您繪製控制項全都放在一個大小，或在不同大小的個別項目。  
  
> [!NOTE]
>  雖然<xref:System.Windows.Forms.CheckedListBox>控制項衍生自<xref:System.Windows.Forms.ListBox>控制項，它不支援主控描繪。  
  
 若要繪製每個項目相同的大小，設定`DrawMode`屬性<xref:System.Windows.Forms.DrawMode>及處理`DrawItem`事件。  
  
 若要繪製每個使用不同大小的項目，設定`DrawMode`屬性<xref:System.Windows.Forms.DrawMode>和處理這兩`MeasureItem`和`DrawItem`事件。 `MeasureItem`事件可讓您指出之前項目的大小`DrawItem`該項目就會發生事件。  
  
 如需詳細資訊，包括程式碼範例，請參閱下列主題︰  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=fullName>  
  
-   [如何︰ 在 ComboBox 控制項中建立各種大小的文字](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>功能表項目元件  
 <xref:System.Windows.Forms.MenuItem>元件表示的單一功能表項目<xref:System.Windows.Forms.MainMenu>或<xref:System.Windows.Forms.ContextMenu>元件。  
  
 要繪製<xref:System.Windows.Forms.MenuItem>、 設定其`OwnerDraw`屬性`true`並處理其`DrawItem`事件。 若要自訂的功能表項目之前大小`DrawItem`事件發生時，處理的項目`MeasureItem`事件。  
  
 如需詳細資訊，包括程式碼範例，請參閱下列參考主題︰  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=fullName>  
  
### <a name="tabcontrol-control"></a>TabControl 控制項  
 <xref:System.Windows.Forms.TabControl>控制項可讓您在控制項中繪製個別索引標籤。 主控描繪會影響索引標籤。<xref:System.Windows.Forms.TabPage>不會影響內容。  
  
 繪製每個索引標籤<xref:System.Windows.Forms.TabControl>，請將`DrawMode`屬性<xref:System.Windows.Forms.TabDrawMode>及處理`DrawItem`事件。 此事件才會發生一次針對每個索引標籤會顯示在控制項中的索引標籤。  
  
 如需詳細資訊，包括程式碼範例，請參閱下列參考主題︰  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=fullName>  
  
### <a name="tooltip-component"></a>ToolTip 元件  
 <xref:System.Windows.Forms.ToolTip>元件可讓您繪製整個工具提示出現時。  
  
 要繪製<xref:System.Windows.Forms.ToolTip>、 設定其`OwnerDraw`屬性`true`並處理其`Draw`事件。 若要自訂的大小<xref:System.Windows.Forms.ToolTip>之前`Draw`事件發生時，處理`Popup`事件以及組<xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A>事件處理常式中的屬性。  
  
 如需詳細資訊，包括程式碼範例，請參閱下列參考主題︰  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=fullName>  
  
### <a name="listview-control"></a>ListView 控制項  
 <xref:System.Windows.Forms.ListView>控制項可讓您在控制項中繪製的個別項目、 子項目和資料行標頭。  
  
 若要啟用主控描繪控制項中，設定`OwnerDraw`屬性`true`。  
  
 若要繪製控制項中的每個項目，處理`DrawItem`事件。  
  
 若要繪製控制項中的每一個子項目或資料行的標頭時<xref:System.Windows.Forms.ListView.View%2A>屬性設定為<xref:System.Windows.Forms.View>，處理`DrawSubItem`和`DrawColumnHeader`事件。  
  
 如需詳細資訊，包括程式碼範例，請參閱下列參考主題︰  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=fullName>  
  
### <a name="treeview-control"></a>TreeView 控制項  
 <xref:System.Windows.Forms.TreeView>控制項可讓您在控制項中繪製個別節點。  
  
 若要繪製只會顯示在每個節點的文字，設定`DrawMode`屬性<xref:System.Windows.Forms.TreeViewDrawMode>及處理`DrawNode`繪製文字的事件。  
  
 若要繪製的每個節點的所有項目，設定`DrawMode`屬性<xref:System.Windows.Forms.TreeViewDrawMode>及處理`DrawNode`事件，以繪製任何所需項目，例如文字、 圖示的核取方塊，加號和減號，以及連接節點的線條。  
  
 如需詳細資訊，包括程式碼範例，請參閱下列參考主題︰  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=fullName>  
  
### <a name="datagridview-control"></a>DataGridView 控制項  
 <xref:System.Windows.Forms.DataGridView>控制項可讓您在控制項中繪製個別儲存格和資料列。  
  
 若要繪製的個別資料格，處理`CellPainting`事件。  
  
 若要繪製的資料列的項目或個別資料列，處理一或兩個`RowPrePaint`和`RowPostPaint`事件。 `RowPrePaint`事件發生之前的資料列中的儲存格繪製，而`RowPostPaint`繪製儲存格之後，就會發生事件。 您可以處理這兩個事件和`CellPainting`事件，以分別繪製資料列背景、 個別的儲存格和資料列的前景，或者您可以提供特定的自訂，您需要這些資訊並使用預設顯示的資料列的其他項目。  
  
 如需詳細資訊，包括程式碼範例，請參閱下列主題︰  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [How to︰ 自訂 Windows Form DataGridView 控制項中的儲存格的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [How to︰ 自訂 Windows Form DataGridView 控制項中的資料列的外觀](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip 控制項  
 <xref:System.Windows.Forms.ToolStrip>和衍生的控制項可讓您自訂其外觀的任何層面。  
  
 若要提供的自訂呈現<xref:System.Windows.Forms.ToolStrip>控制項，設定`Renderer`屬性<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.ToolStripManager>， <xref:System.Windows.Forms.ToolStripPanel>，或<xref:System.Windows.Forms.ToolStripContentPanel>至`ToolStripRenderer`物件，並處理一或多個所提供的許多繪圖事件`ToolStripRenderer`類別。 或者，設定`Renderer`您自己的類別執行個體的屬性衍生自`ToolStripRenderer`， <xref:System.Windows.Forms.ToolStripProfessionalRenderer>，或<xref:System.Windows.Forms.ToolStripSystemRenderer>所實作或覆寫特定`On` *EventName*方法。  
  
 如需詳細資訊，包括程式碼範例，請參閱下列主題︰  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [如何︰ 建立和設定 Windows Form 中 ToolStrip 控制項自訂產生器](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [How to︰ 自訂繪製 ToolStrip 控制項](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)