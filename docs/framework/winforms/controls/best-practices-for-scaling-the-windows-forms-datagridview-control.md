---
title: 縮放 Windows Form DataGridView 控制項的最佳作法
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 65afd73c166332f08003c3b3bfcc70e488d0373a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663545"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>縮放 Windows Form DataGridView 控制項的最佳作法

<xref:System.Windows.Forms.DataGridView>控制項的設計是可提供最大的延展性。 如果您要顯示大量的資料，您應該遵循本主題，以避免消耗大量的記憶體，或降低回應能力的使用者介面 (UI) 中所述的指導方針。 本主題將討論下列問題：

- 有效率地使用的儲存格樣式

- 有效率地使用快顯功能表

- 使用有效率的方式自動的調整大小

- 有效率地使用選取的資料格、 資料列和資料行集合

- 使用共用的資料列

- 防止資料列變成非共用

如果您有特殊效能需求，您可以實作虛擬模式，並提供您自己的資料管理作業。 如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)。

## <a name="using-cell-styles-efficiently"></a>有效率地使用的儲存格樣式

每個資料格、 資料列和資料行可以有它自己的樣式資訊。 樣式資訊會儲存在<xref:System.Windows.Forms.DataGridViewCellStyle>物件。 建立針對許多個別儲存格樣式物件<xref:System.Windows.Forms.DataGridView>項目可以是效率不佳，尤其是使用大量的資料。 若要避免對效能產生影響，請使用下列指導方針：

- 請避免設定個別的儲存格樣式屬性<xref:System.Windows.Forms.DataGridViewCell>或<xref:System.Windows.Forms.DataGridViewRow>物件。 這包括所指定的資料列物件<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>屬性。 每個新的資料列作為複製來源資料列範本，將會收到它自己的範本的儲存格樣式物件的複本。 最大延展性，設定儲存格樣式屬性，在<xref:System.Windows.Forms.DataGridView>層級。 例如，設定<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>屬性而非<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>屬性。

- 如果某些資料格需要格式而非預設的格式設定，請使用相同<xref:System.Windows.Forms.DataGridViewCellStyle>跨越的資料格、 資料列或資料行群組的執行個體。 請避免直接設定屬性的型別<xref:System.Windows.Forms.DataGridViewCellStyle>個別儲存格、 資料列和資料行上。 如需的儲存格樣式共用的範例，請參閱[How to:設定 Windows Form DataGridView 控制項的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。 您也可以藉由處理個別設定儲存格樣式時避免對效能帶來負面影響<xref:System.Windows.Forms.DataGridView.CellFormatting>事件處理常式。 如需範例，請參閱[如何：自訂 Windows Form DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。

- 在決定的儲存格樣式，請使用<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>屬性而非<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>屬性。 存取<xref:System.Windows.Forms.DataGridViewCell.Style%2A>屬性建立的新執行個體<xref:System.Windows.Forms.DataGridViewCellStyle>類別已經尚未使用的屬性。 此外，如果某些樣式繼承自資料列、 資料行或控制這個物件可能並未包含儲存格的完整樣式資訊。 如需有關儲存格樣式繼承的詳細資訊，請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。

## <a name="using-shortcut-menus-efficiently"></a>有效率地使用快顯功能表

每個資料格、 資料列和資料行可以有它自己的快顯功能表。 中的快顯功能表<xref:System.Windows.Forms.DataGridView>控制項由<xref:System.Windows.Forms.ContextMenuStrip>控制項。 如同儲存格樣式的物件，建立快顯功能表針對許多個別<xref:System.Windows.Forms.DataGridView>項目將會對效能產生負面影響。 若要避免這種效能損失，請使用下列指導方針：

- 請避免建立個別儲存格和資料列的捷徑功能表。 這包括資料列範本，當新的資料列加入至控制項時，會將其捷徑功能表以及複製。 最大的擴充性，使用只有控制項的<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>屬性可指定整個控制項的單一快顯功能表。

- 如果您需要多個快顯功能表的多個資料列或資料格時，處理<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>或<xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>事件。 這些事件可讓您管理的快顯功能表物件自己，可讓您調整效能。

## <a name="using-automatic-resizing-efficiently"></a>使用有效率的方式自動的調整大小

資料列、 資料行和標頭可以是自動調整為資料格的內容變更，讓整個儲存格的內容會顯示未遭裁剪。 變更縮放模式也可以調整資料列、 資料行和標頭。 若要判斷正確的大小，<xref:System.Windows.Forms.DataGridView>控制項必須檢查它必須配合每個儲存格的值。 當使用大型資料集，這項分析可以效能產生負面影響的控制項時自動調整大小，就會發生。 若要避免效能的負面影響，請使用下列指導方針：

- 請避免使用自動調整大小上<xref:System.Windows.Forms.DataGridView>大型的資料列集的控制項。 如果您使用自動調整大小，只根據顯示的資料列的調整大小。 在虛擬模式中也使用只顯示的資料列。

  - 資料列和資料行，請使用`DisplayedCells`或是`DisplayedCellsExceptHeaders`欄位<xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>， <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>，和<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>列舉型別。

  - 用於資料列行首<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders>或是<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader>欄位<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>列舉型別。

- 最大延展性，關閉自動調整大小，並使用以程式設計方式調整大小。

如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)。

## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>有效率地使用選取的資料格、 列和資料行集合

<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>大型的選取項目後的集合不會有效率地執行。 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>並<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>集合也可以是效率不佳，雖然是以壓縮的程度會因為有許多資料列少於在典型的資料格<xref:System.Windows.Forms.DataGridView>控制和資料列比許多較少的資料行。 若要使用這些集合時，請避免效能的負面影響，請使用下列指導方針：

- 若要判斷是否中的所有儲存格<xref:System.Windows.Forms.DataGridView>存取的內容之前已選取<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>集合中，檢查傳回值的<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>方法。 不過，要注意的是，這個方法可能會導致變成非共用的資料列。 如需詳細資訊，請參閱下一章節。

- 請避免使用<xref:System.Collections.ICollection.Count%2A>屬性<xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType>來決定選取之資料格數目。 請改用<xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType>方法並傳入<xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType>值。 同樣地，使用<xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType>和<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType>方法來判斷選取的項目，而不是存取選取的資料列和資料行集合的數目。

- 避免資料格為基礎的選取模式。 相反地，設定<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>屬性，以<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>。

## <a name="using-shared-rows"></a>使用共用資料列

有效率的記憶體使用量，就能<xref:System.Windows.Forms.DataGridView>透過共用的資料列的控制。 資料列會共用其外觀和行為的相關最多資訊，盡可能共用的執行個體<xref:System.Windows.Forms.DataGridViewRow>類別。

共用資料列執行個體節省記憶體，而資料列很容易變得不共用。 例如，每當使用者互動直接與儲存格時，其資料列會變成不共用。 這並無法避免，因為本主題中的指導方針只在使用非常大量的資料時，才，並且唯有在使用者互動相對較小的部分資料的每次執行程式時很有用。

無法共用一個資料列中包含解除繫結<xref:System.Windows.Forms.DataGridView>控制如果它的儲存格的任何包含的值。 當<xref:System.Windows.Forms.DataGridView>控制項所繫結至外部資料來源，或控制項之外，而不是資料格物件，可讓要共用的資料列中，當您實作虛擬模式，並提供您自己的資料來源，會儲存資料格的值。

如果可以判斷其所有儲存格的狀態，從資料列狀態和資料行包含儲存格的狀態，可共用的資料列物件。 如果您變更儲存格的狀態，使它不再推算其資料列和資料行的狀態，無法共用的資料列。

比方說，資料列不共用任何下列情況：

- 資料列都包含單一的所選儲存格不在所選資料行中。

- 資料列包含資料格與它<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>或<xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A>屬性集。

- 資料列都包含<xref:System.Windows.Forms.DataGridViewComboBoxCell>具有其<xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A>屬性集。

在繫結的模式或虛擬模式中，您可以提供工具提示和捷徑功能表個別資料格的處理<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>和<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>事件。

<xref:System.Windows.Forms.DataGridView>控制項將會自動嘗試使用共用的資料列，每當資料列會加入<xref:System.Windows.Forms.DataGridViewRowCollection>。 若要確認資料列共用，使用下列指導方針：

- 避免呼叫`Add(Object[])`多載<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>方法並`Insert(Object[])`多載<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>方法<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>集合。 這些多載會自動建立非共用的資料列。

- 請確認在指定的資料列<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>可共用屬性，在下列情況：

  - 呼叫時`Add()`或是`Add(Int32)`的多載<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>方法或`Insert(Int32,Int32)`多載<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>方法<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>集合。

  - 增加的值時<xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType>屬性。

  - 設定時<xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>屬性。

- 請確認所指定的資料列`indexSource`呼叫時，就可以共用參數<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>， <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>， <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>，並<xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A>方法<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>集合。

- 確定建議的指定資料列或資料列可以共用時呼叫`Add(DataGridViewRow)`多載<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>方法，<xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A>方法，`Insert(Int32,DataGridViewRow)`多載<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>方法，而<xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A>方法<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>集合。

若要判斷是否為共用資料列，請使用<xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>方法來擷取資料列物件，並接著檢查物件的<xref:System.Windows.Forms.DataGridViewBand.Index%2A>屬性。 共用的資料列一定<xref:System.Windows.Forms.DataGridViewBand.Index%2A>屬性值為-1。

## <a name="preventing-rows-from-becoming-unshared"></a>防止資料列變成非共用

共用的資料列可能會取消共用程式碼或使用者動作的結果。 若要避免對效能產生影響，您應該避免造成變成非共用的資料列。 應用程式在開發期間，您可以處理<xref:System.Windows.Forms.DataGridView.RowUnshared>事件，以判斷當資料列變為非共用。 當資料列共用問題進行偵錯時，這非常有用。

若要防止資料列變成非共用，請使用下列指導方針：

- 避免索引編製<xref:System.Windows.Forms.DataGridView.Rows%2A>集合或逐一查看與`foreach`迴圈。 您會通常不需要直接存取的資料列。 <xref:System.Windows.Forms.DataGridView> 對資料列的方法會採用資料列索引引數，而不是資料列執行個體。 此外，資料列相關的事件處理常式會收到事件引數物件包含可供您管理的資料列，而不會造成它們變成非共用的資料列屬性。

- 如果您需要存取資料列的物件，使用<xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>方法並傳入資料列的實際的索引。 不過請注意，修改共用的資料列物件，擷取透過這個方法會修改共用此物件的所有資料列。 新記錄的資料列不會與共用其他資料列，不過，因此它不會影響當您修改任何其他資料列。 也請注意，共用的資料列代表不同的資料列可能會有不同的快顯功能表。 若要從共用的資料列執行個體中擷取正確的快顯功能表，請使用<xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A>方法並傳入資料列的實際的索引。 如果您在存取共用的資料列<xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A>屬性相反地，它會使用共用資料列索引，-1，並將不會擷取正確的快顯功能表。

- 避免索引<xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType>集合。 直接存取的資料格，則會導致它變成非共用，具現化新的父資料列<xref:System.Windows.Forms.DataGridViewRow>。 儲存格相關的事件處理常式會接收事件引數物件包含可用來操作儲存格，而不會造成資料列變為非共用的資料格屬性。 您也可以使用<xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A>屬性來擷取目前的儲存格的資料列和資料行索引，而不需要直接存取的資料格。

- 避免資料格為基礎的選取模式。 這些模式會導致變成非共用的資料列。 相反地，設定<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>屬性，以<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>。

- 不會處理<xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType>或<xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType>事件。 這些事件會導致變成非共用的資料列。 此外，請勿呼叫<xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType>引發這些事件的方法。

- 不會存取<xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType>集合時<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>屬性值是<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>， <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>， <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>，或<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>。 這會導致變成非共用所有選取的資料列。

- 請勿呼叫<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType>方法。 這個方法可能會導致變成非共用的資料列。

- 請勿呼叫<xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType>方法時<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>屬性值是<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>。 這會導致變成非共用的所有資料列。

- 未設定<xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A>或是<xref:System.Windows.Forms.DataGridViewCell.Selected%2A>屬性之資料格`false`當其資料行中對應的屬性設定為`true`。 這會導致變成非共用的所有資料列。

- 不會存取<xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType>屬性。 這會導致變成非共用的所有資料列。

- 請勿呼叫`Sort(IComparer)`多載<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。 使用自訂比較子進行排序時，會導致變成非共用的所有資料列。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView 控制項中的效能微調](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [如何：為 Windows Form DataGridView 控制項中的預設儲存格樣式](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)
