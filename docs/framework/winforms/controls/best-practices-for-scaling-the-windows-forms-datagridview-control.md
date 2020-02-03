---
title: 調整 DataGridView 控制項的最佳做法
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 63500a79def89510b4bc7a436abc4620a7265a79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744132"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>縮放 Windows Form DataGridView 控制項的最佳作法

<xref:System.Windows.Forms.DataGridView> 控制項的設計目的是要提供最大的擴充性。 如果您需要顯示大量資料，您應該遵循本主題中所述的指導方針，以避免耗用大量的記憶體，或降低使用者介面（UI）的回應性。 本主題討論下列問題：

- 有效率地使用儲存格樣式

- 有效率地使用快捷方式功能表

- 有效率地使用自動調整大小

- 有效率地使用選取的儲存格、資料列和資料行集合

- 使用共用資料列

- 防止資料列遭到取消共用

如果您有特殊的效能需求，您可以執行虛擬模式，並提供您自己的資料管理作業。 如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)。

## <a name="using-cell-styles-efficiently"></a>有效率地使用儲存格樣式

每個資料格、資料列和資料行都可以有自己的樣式資訊。 樣式資訊會儲存在 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件中。 建立許多個別 <xref:System.Windows.Forms.DataGridView> 專案的儲存格樣式物件可能沒有效率，特別是在處理大量資料時。 若要避免對效能造成影響，請使用下列指導方針：

- 避免設定個別 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewRow> 物件的儲存格樣式屬性。 這包括 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> 屬性所指定的資料列物件。 每個從資料列範本複製的新資料列，都會收到自己的範本儲存格樣式物件複本。 如需最大的擴充性，請在 <xref:System.Windows.Forms.DataGridView> 層級設定儲存格樣式屬性。 例如，設定 [<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>] 屬性，而不是 [<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>] 屬性。

- 如果某些資料格需要預設格式以外的格式設定，請在資料格、資料列或資料行的群組之間使用相同的 <xref:System.Windows.Forms.DataGridViewCellStyle> 實例。 請避免在個別資料格、資料列和資料行上直接設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 類型的屬性。 如需儲存格樣式共用的範例，請參閱[如何：設定 Windows Forms DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。 您也可以藉由處理 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件處理常式來個別設定儲存格樣式，以避免效能上的負面影響。 如需範例，請參閱[如何：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。

- 判斷儲存格的樣式時，請使用 [<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>] 屬性，而不是 [<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>] 屬性。 如果尚未使用屬性，則存取 <xref:System.Windows.Forms.DataGridViewCell.Style%2A> 屬性會建立 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別的新實例。 此外，如果從資料列、資料行或控制項繼承某些樣式，此物件可能不會包含資料格的完整樣式資訊。 如需有關儲存格樣式繼承的詳細資訊，請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。

## <a name="using-shortcut-menus-efficiently"></a>有效率地使用快捷方式功能表

每個資料格、資料列和資料行都可以有自己的快捷方式功能表。 <xref:System.Windows.Forms.DataGridView> 控制項中的快捷方式功能表是由 <xref:System.Windows.Forms.ContextMenuStrip> 控制項表示。 就像儲存格樣式物件一樣，為許多個別的 <xref:System.Windows.Forms.DataGridView> 元素建立快捷方式功能表會對效能產生負面影響。 若要避免這種負面影響，請使用下列指導方針：

- 避免建立個別資料格和資料列的快捷方式功能表。 這包括資料列範本，會在新的資料列加入至控制項時，連同其快捷方式功能表一起複製。 為了達到最大的擴充性，請只使用控制項的 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> 屬性來指定整個控制項的單一快捷方式功能表。

- 如果您需要多個資料列或資料格的多個快捷方式功能表，請處理 <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> 或 <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> 事件。 這些事件可讓您自行管理快捷方式功能表物件，讓您能夠調整效能。

## <a name="using-automatic-resizing-efficiently"></a>有效率地使用自動調整大小

資料列、資料行和標頭可以在資料格內容變更時自動調整大小，以便在不進行裁剪的情況下顯示整個儲存格的內容。 變更大小調整模式也可以調整資料列、資料行和標頭的大小。 若要判斷正確的大小，<xref:System.Windows.Forms.DataGridView> 控制項必須檢查其必須容納的每個資料格的值。 當使用大型資料集時，這項分析可能會對控制項的效能造成負面影響，因為會自動調整大小。 若要避免效能受到影響，請使用下列指導方針：

- 避免在具有大量資料列集的 <xref:System.Windows.Forms.DataGridView> 控制項上使用自動調整大小。 如果您使用自動調整大小，則只會根據顯示的資料列調整大小。 一併只使用虛擬模式中顯示的資料列。

  - 針對資料列和資料行，請使用 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>、<xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>和 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> 列舉的 `DisplayedCells` 或 `DisplayedCellsExceptHeaders` 欄位。

  - 若為數據列標頭，請使用 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> 列舉的 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders> 或 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader> 欄位。

- 如需最大的擴充性，請關閉自動調整大小，並使用程式設計調整大小

如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)。

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>有效率地使用選取的儲存格、資料列和資料行集合

<xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 集合無法有效率地進行大量選取。 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 和 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 集合也可能沒有效率，雖然較低的程度，因為資料列數比一般 <xref:System.Windows.Forms.DataGridView> 控制項中的資料格少許多，而且資料行比資料列少許多。 若要避免使用這些集合時的效能受到影響，請使用下列指導方針：

- 若要判斷是否已選取 <xref:System.Windows.Forms.DataGridView> 中的所有資料格，再存取 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 集合的內容，請檢查 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> 方法的傳回值。 不過要注意的是，這個方法可能會造成資料列成為不共用的。 如需詳細資訊，請參閱下一節。

- 請避免使用 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType> 的 <xref:System.Collections.ICollection.Count%2A> 屬性來判斷選取的儲存格數目。 請改用 <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType> 方法，並傳入 <xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType> 值。 同樣地，您可以使用 <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType> 方法來判斷選取的元素數目，而不是存取選取的資料列和資料行集合。

- 避免以資料格為基礎的選取模式。 相反地，請將 [<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>] 屬性設定為 [<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>] 或 [<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>]。

## <a name="using-shared-rows"></a>使用共用資料列

透過共用資料列在 <xref:System.Windows.Forms.DataGridView> 控制中達到有效率的記憶體使用。 資料列會藉由共用 <xref:System.Windows.Forms.DataGridViewRow> 類別的實例，盡可能共用其外觀和行為的相關資訊。

共用資料列實例會節省記憶體，而資料列很容易就會變成不共用。 例如，每當使用者直接與儲存格互動時，其資料列就會變成非共用。 因為這無法避免，所以本主題中的指導方針只有在處理非常大量的資料時才有用，而且只有在每次執行程式時，使用者才會與資料的相對較小部分互動。

如果資料格包含值，則不能在未系結的 <xref:System.Windows.Forms.DataGridView> 控制項中共用該資料列。 當 <xref:System.Windows.Forms.DataGridView> 控制項系結到外部資料源時，或當您執行虛擬模式並提供您自己的資料來源時，儲存格的值會儲存在控制項外部，而不是資料格物件中，允許共用資料列。

只有在資料列的狀態和包含儲存格的資料行狀態之間，才可以共用資料列物件。 如果您變更資料格的狀態，使其無法再從其資料列和資料行的狀態推算出來，就無法共用該資料列。

例如，在下列任何情況下，都無法共用資料列：

- 資料列包含不在所選資料行中的單一選取儲存格。

- 資料列包含其 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> 或 <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> 屬性集的資料格。

- 資料列包含已設定 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> 屬性的 <xref:System.Windows.Forms.DataGridViewComboBoxCell>。

在 [系結模式] 或 [虛擬模式] 中，您可以藉由處理 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> 和 <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> 事件來提供個別資料格的工具提示和快捷方式功能表。

每當資料列新增至 <xref:System.Windows.Forms.DataGridViewRowCollection>時，<xref:System.Windows.Forms.DataGridView> 控制項都會自動嘗試使用共用資料列。 請使用下列指導方針來確保資料列是共用的：

- 請避免呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> 方法的 `Add(Object[])` 多載，以及 <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> 集合之 <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> 方法的 `Insert(Object[])` 多載。 這些多載會自動建立非共用的資料列。

- 請確定在下列情況中，可以共用 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> 屬性中指定的資料列：

  - 呼叫 `Add()` 或 `Add(Int32)` <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> 方法的多載，或 <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> 集合之 <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> 方法的 `Insert(Int32,Int32)` 多載時。

  - 增加 <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType> 屬性的值時。

  - 設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType> 屬性時。

- 呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> 集合的 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>和 <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> 方法時，請確定 `indexSource` 參數所表示的資料列可以共用。

- 呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> 方法的 `Add(DataGridViewRow)` 多載、<xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> 方法、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> 方法的 `Insert(Int32,DataGridViewRow)` 多載，以及 <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> 集合的 <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType> 方法時，請確定指定的一或多個資料列可以共用。

若要判斷資料列是否為共用的，請使用 <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> 方法來抓取資料列物件，然後檢查物件的 <xref:System.Windows.Forms.DataGridViewBand.Index%2A> 屬性。 共用資料列的 <xref:System.Windows.Forms.DataGridViewBand.Index%2A> 屬性值一律為-1。

## <a name="preventing-rows-from-becoming-unshared"></a>防止資料列遭到取消共用

共用資料列可能會因程式碼或使用者動作而變成取消共用。 若要避免對效能造成影響，您應該避免造成資料列被取消共用。 在應用程式開發期間，您可以處理 <xref:System.Windows.Forms.DataGridView.RowUnshared> 事件，以判斷資料列何時會取消共用。 這在調試資料列共用問題時很有用。

若要防止資料列變成非共用，請使用下列指導方針：

- 避免為 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合編制索引，或使用 `foreach` 迴圈逐一查看。 您通常不需要直接存取資料列。 在資料列上操作的 <xref:System.Windows.Forms.DataGridView> 方法會接受資料列索引引數，而不是資料列實例。 此外，資料列相關事件的處理常式會接收具有資料列屬性的事件引數物件，您可以用來運算元據列，而不會導致它們變成非共用。

- 如果您需要存取資料列物件，請使用 <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> 方法，並傳入資料列的實際索引。 不過，請注意，修改透過這個方法抓取的共用資料列物件，將會修改共用此物件的所有資料列。 不過，新記錄的資料列不會與其他資料列共用，因此當您修改任何其他資料列時，它不會受到影響。 另請注意，共用資料列所代表的不同資料列可能會有不同的快捷方式功能表。 若要從共用的資料列實例中取出正確的快捷方式功能表，請使用 <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> 方法，並傳入資料列的實際索引。 如果您改為存取共用資料列的 <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> 屬性，它會使用-1 的共用資料列索引，而且不會抓取正確的快捷方式功能表。

- 避免編制 <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType> 集合的索引。 直接存取資料格會使其父資料列變成非共用，並具現化新的 <xref:System.Windows.Forms.DataGridViewRow>。 資料格相關事件的處理常式會接收具有資料格屬性的事件引數物件，可讓您用來運算元據格，而不會造成資料列被取消共用。 您也可以使用 <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> 屬性來抓取目前儲存格的資料列和資料行索引，而不需要直接存取儲存格。

- 避免以資料格為基礎的選取模式。 這些模式會使資料列變成非共用。 相反地，請將 [<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>] 屬性設定為 [<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>] 或 [<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>]。

- 請勿處理 <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType> 事件。 這些事件會使資料列變成非共用。 此外，請勿呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType> 方法，這會引發這些事件。

- 當 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> 屬性值為 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>、<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或 <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>時，請勿存取 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType> 集合。 這會導致所有選取的資料列變成非共用。

- 請勿呼叫 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType> 方法。 這個方法可能會使資料列變成非共用。

- 當 <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect><xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> 屬性值時，請勿呼叫 <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType> 方法。 這會導致所有資料列變成非共用。

- 當資料行中的對應屬性設定為 `true`時，請勿將資料格的 <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> 或 <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> 屬性設定為 [`false`]。 這會導致所有資料列變成非共用。

- 請勿存取 <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType> 屬性。 這會導致所有資料列變成非共用。

- 請勿呼叫 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(IComparer)` 多載。 使用自訂比較子進行排序會使所有資料列變成非共用。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [操作說明：設定 Windows Forms DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)
