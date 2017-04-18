---
title: "縮放 Windows Form DataGridView 控制項的最佳作法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "最佳作法, DataGridView 控制項"
  - "資料格, 最佳作法"
  - "DataGridView 控制項 [Windows Form], 最佳作法"
  - "DataGridView 控制項 [Windows Form], 資料列共用"
  - "DataGridView 控制項 [Windows Form], 縮放比例"
  - "DataGridView 控制項 [Windows Form], 共用資料列"
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# 縮放 Windows Form DataGridView 控制項的最佳作法
<xref:System.Windows.Forms.DataGridView> 控制項的設計是為了要提供最佳的延展性 \(Scalability\)。  如果您需要顯示大量的資料，則應該遵循本主題中所提供的方針，以避免耗用大量的記憶體，或造成使用者介面 \(UI\) 的回應效能下滑。  這個主題討論了下列問題：  
  
-   有效使用儲存格樣式  
  
-   有效使用捷徑功能表  
  
-   有效使用自動調整大小  
  
-   有效使用選取的儲存格、資料列和資料行集合  
  
-   使用共用資料列  
  
-   避免資料列變成非共用  
  
 如果您有特殊的效能需求，則可以實作虛擬模式並提供您自己的資料管理作業。  如需詳細資訊，請參閱 [Windows Form DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)。  
  
## 有效使用儲存格樣式  
 每個儲存格、資料列和資料行都有自己的樣式資訊。  樣式資訊儲存於 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件當中。  為許多個別的 <xref:System.Windows.Forms.DataGridView> 項目建立儲存格樣式物件可能會很沒有效率，尤其是當您要使用大量資料的時候。  若要避免對效能產生影響，請使用以下的方針：  
  
-   避免為個別的 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewRow> 物件設定儲存格樣式屬性。  這包括了在 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> 屬性中指定的資料列物件。  每個從資料列範本複製 \(Clone\) 的新資料列都會收到自己的範本之儲存格樣式物件複本。  為了達到最佳的延展性，請在 <xref:System.Windows.Forms.DataGridView> 層級設定儲存格樣式屬性。  例如，設定 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> 屬性，而不要設定 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName> 屬性。  
  
-   如果有些儲存格所需的格式與預設格式不同，請在儲存格、資料列或資料行群組中使用相同的 <xref:System.Windows.Forms.DataGridViewCellStyle> 執行個體。  避免直接在個別儲存格、資料列和資料行的 <xref:System.Windows.Forms.DataGridViewCellStyle> 型別上設定屬性。  如需儲存格樣式共用的範例，請參閱 [如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)。  當您必須個別設定儲存格樣式時，也可以藉由處理 <xref:System.Windows.Forms.DataGridView.CellFormatting> 事件處理常式，來避免效能的損失。  如需範例，請參閱 [如何：自訂 Windows Form DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
-   當您要決定儲存格的樣式時，請使用 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=fullName> 屬性，而不要使用 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName> 屬性。  如果在 <xref:System.Windows.Forms.DataGridViewCell.Style%2A> 屬性尚未使用時對其進行存取，會建立 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別的新執行個體。  此外，如果有些儲存格樣式是從資料列、資料行或控制項中繼承而來，則這個物件中可能並未包含完整的儲存格樣式資訊。  如需儲存格樣式繼承的詳細資訊，請參閱 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
## 有效使用捷徑功能表  
 每個儲存格、資料列和資料行都有自己的捷徑功能表。  <xref:System.Windows.Forms.DataGridView> 控制項中的捷徑功能表會以 <xref:System.Windows.Forms.ContextMenuStrip> 控制項來表示。  就如同儲存格樣式物件一般，為許多個別的 <xref:System.Windows.Forms.DataGridView> 項目建立捷徑功能表將會對效能造成負面影響。  若要避免這種效能損失，請使用以下的方針：  
  
-   避免為個別儲存格和資料列建立捷徑功能表。  這包括了資料列範本，當新的資料列加入至控制項時，會將其捷徑功能表一併複製。  為了達到最佳的延展性，請只使用控制項的 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> 屬性為整個控制項指定單一的捷徑功能表。  
  
-   如果您必須為多個資料列或儲存格建立多個捷徑功能表，請處理 <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> or <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> 事件。  這些事件可以讓您自行管理捷徑功能表物件，允許您調整效能。  
  
## 有效使用自動調整大小  
 資料列、資料行和行首都可以在儲存格內容變更時自動調整大小，以顯示儲存格的完整內容而不致於發生裁剪。  變更調整大小模式同樣可以調整資料列、資料行和行首的大小。  為了判斷正確的大小，<xref:System.Windows.Forms.DataGridView> 控制項必須檢查其必須容納的每個儲存格的值。  當處理大量資料集時，如果發生自動調整大小，則這項分析可能會對控制項的效能造成負面影響。  若要避免效能損失，請使用以下的方針：  
  
-   避免在具有大量資料集的 <xref:System.Windows.Forms.DataGridView> 控制項上使用自動調整大小。  如果您必須使用自動調整大小，請只根據顯示的資料列調整大小。  在虛擬模式中也請只使用顯示的資料列。  
  
    -   在資料列和資料行上，請使用 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>、<xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode> 和 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> 列舉型別的 `DisplayedCells` 或 `DisplayedCellsExceptHeaders` 欄位。  
  
    -   在行首上，請使用 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> 列舉型別的 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> 或 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> 欄位。  
  
-   為了達到最佳的延展性，請關閉自動調整大小，並使用程式設計方式來調整大小。  
  
 如需詳細資訊，請參閱 [Windows Form DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
## 有效使用選取的儲存格、資料列和資料行集合  
 當選取範圍比較大時，<xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 集合並無法有效率地執行。  <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 和 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 集合也可能會變得沒有效率，但是情況會稍微緩和一點，因為在典型的 <xref:System.Windows.Forms.DataGridView> 控制項中，資料列要比儲存格少得多，而資料行又比資料列來得更少。  若要避免使用這些集合時的效能損失，請使用以下方針：  
  
-   若要在存取 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 集合的內容之前，判斷是否已選取 <xref:System.Windows.Forms.DataGridView> 中的所有儲存格，請檢查 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> 方法的傳回值。  然而，要注意這個方法可能會讓資料行變成非共用的。  如需詳細資訊，請參閱下一章節。  
  
-   避免使用 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=fullName> 的 <xref:System.Collections.ICollection.Count%2A> 屬性來判斷選取的儲存格數目。  請使用 <xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=fullName> 方法並傳入 <xref:System.Windows.Forms.DataGridViewElementStates?displayProperty=fullName> 值來代替。  同樣地，請使用 <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=fullName> 和 <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=fullName> 方法來判斷選取的項目數目，而不要存取選取的資料列和資料行集合。  
  
-   避免使用儲存格架構的選取模式。  將 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> 屬性設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> 來代替。  
  
## 使用共用資料列  
 在 <xref:System.Windows.Forms.DataGridView> 控制項中共用資料列可以達到記憶體的有效使用。  透過共用 <xref:System.Windows.Forms.DataGridViewRow> 類別的執行個體，資料列會盡可能共用其外觀和行為的資訊。  
  
 雖然共用資料列的執行個體可以節省記憶體，但是資料列很容易就會變成非共用的。  例如，每當使用者直接與一個儲存格互動時，該資料列就會變成非共用的。  因為這種情況無法避免，本主題的方針只有在您必須使用大量資料，而且每次程式執行時，使用者只會與相對少數的資料互動的情況下，才會顯得有用。  
  
 在未繫結的 <xref:System.Windows.Forms.DataGridView> 控制項中，如果資料列的任何一個儲存格包含值，該資料列就非共用的。  當 <xref:System.Windows.Forms.DataGridView> 控制項繫結至一個外部資料來源，或當您實作了虛擬模式並提供自己的資料來源時，儲存格的值會儲存在控制項之外，而不是在儲存格物件中，因此資料列就可以共用。  
  
 如果資料列物件其全部儲存格的狀態都可以從資料列狀態和包含儲存格的資料行狀態來判斷時，才可以將這個物件共用。  如果您變更了一個儲存格的狀態，使它無法再從資料列或資料行的狀態推算，該資料列就會變成非共用的。  
  
 例如，在下列任何一種情況下均無法共用資料列：  
  
-   資料列中包含了一個單一選取的儲存格，而且不屬於已選取的資料行。  
  
-   資料列中包含了一個儲存格，它的 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> 或 <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> 屬性已經被設定。  
  
-   資料列中包含了一個 <xref:System.Windows.Forms.DataGridViewComboBoxCell>，它的 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> 屬性已經被設定。  
  
 在繫結模式或虛擬模式中，您可以藉由處理 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> 和 <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> 事件，為個別的儲存格提供工具提示和捷徑功能表。  
  
 每當有資料列加入至 <xref:System.Windows.Forms.DataGridViewRowCollection> 時，<xref:System.Windows.Forms.DataGridView> 控制項將自動嘗試共用資料列。  請使用以下方針來確保資料列會共用：  
  
-   避免呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> 方法的 `Add(Object[])` 多載，以及 <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName> 集合之 <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> 方法的 `Insert(Object[])` 多載。  這些多載會自動建立未共用的資料列。  
  
-   請確認在 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName> 屬性中指定的資料列在下列情況下可以共用：  
  
    -   當呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> 方法的 `Add()` 或 `Add(Int32)` 多載，或 <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName> 集合之 <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> 方法的 `Insert(Int32,Int32)` 多載時。  
  
    -   當增加 <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=fullName> 屬性值時。  
  
    -   當設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName> 屬性時。  
  
-   確認當呼叫 <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName> 集合的 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A> 和 <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> 方法時，在 `indexSource` 參數中所指定的資料列可以共用。  
  
-   確認當呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> 方法的 `Add(DataGridViewRow)` 多載、<xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> 方法、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> 方法的 `Insert(Int32,DataGridViewRow)` 多載以及 <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName> 集合的 <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> 方法時，指定的資料列可以共用。  
  
 若要判斷資料列是否已共用，可使用 <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=fullName> 方法來擷取資料列物件，然後檢查物件的 <xref:System.Windows.Forms.DataGridViewBand.Index%2A> 屬性。  共用的資料列其 <xref:System.Windows.Forms.DataGridViewBand.Index%2A> 屬性值永遠為 –1。  
  
## 避免資料列變成非共用  
 由於程式碼或使用者的操作，共用的資料列可能會變成非共用的。  若要避免對效能產生影響，您應該避免讓資料列變成非共用的。  在應用程式開發期間，您可以處理 <xref:System.Windows.Forms.DataGridView.RowUnshared> 事件來判斷資料列何時變成非共用的。  這種做法在偵錯資料列共用問題時相當有用。  
  
 若要避免資料列變成非共用的，請使用以下的方針：  
  
-   避免將 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合進行索引，或使用 `foreach` 迴圈來逐一查看。  您通常不需要直接存取資料列。  在資料列上運作的 <xref:System.Windows.Forms.DataGridView> 方法會取得資料列索引引數，而不是資料列執行個體。  此外，資料列相關事件的處理常式會接收包含資料列屬性的事件引數物件，您可以利用此物件來操作資料列，而不至於造成資料列變成非共用的。  
  
-   如果您必須存取資料列物件，請使用 <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=fullName> 方法並傳入資料列的實質索引。  然而請注意，修改透過此方法所擷取的共用資料列物件，也將會修改共用此物件的所有資料列。  新資料錄的資料列由於尚未與其他資料列共用，當您修改其他資料列時並不會受到影響。  還要注意的是，共用資料列所代表的不同資料列，可能會有不同的捷徑功能表。  若要從共用資料列執行個體擷取正確的捷徑功能表，請使用 <xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> 方法並傳入資料列的實質索引。  如果您使用共用資料列的 <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> 屬性來代替，它將會使用共用資料列的索引 \-1，而不會擷取正確的捷徑功能表。  
  
-   避免將 <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=fullName> 集合進行索引。  直接存取儲存格會讓其上層資料列變成非共用的，並且會執行個體化一個新的 <xref:System.Windows.Forms.DataGridViewRow>。  儲存格相關事件的處理常式會接收包含儲存格屬性的事件引數物件，您可以利用此物件來操作儲存格，而不至於讓資料列變成非共用的。  您也可以使用 <xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> 屬性來擷取目前儲存格的資料列和資料行索引，而不必直接存取儲存格。  
  
-   避免使用儲存格架構的選取模式。  這些模式會使資料列變得非共用的。  將 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> 屬性設定為 <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> 來代替。  
  
-   不要處理 <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=fullName> 或 <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=fullName> 事件。  這些事件會使資料列變得非共用的。  同樣地，不要呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=fullName> 或 <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=fullName> 方法，它們會引發這些事件。  
  
-   當 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> 屬性值為 <xref:System.Windows.Forms.DataGridViewSelectionMode>、<xref:System.Windows.Forms.DataGridViewSelectionMode>、<xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode> 時，不要存取 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=fullName> 集合。  這樣會使所有選取的資料列都變成非共用。  
  
-   不要呼叫 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=fullName> 方法。  這個方法會使資料列變成非共用的。  
  
-   當 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> 屬性值為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 時，不要呼叫 <xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=fullName> 方法。  這樣會使所有的資料列都變成非共用的。  
  
-   當欄位中相對應的屬性設定為 `true` 時，不要將儲存格中的 <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> 或 <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> 屬性設定為 `false`。  這樣會使所有的資料列都變成非共用的。  
  
-   不要存取 <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=fullName> 屬性。  這樣會使所有的資料列都變成非共用的。  
  
-   不要呼叫 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(IComparer)` 多載。  使用自訂比較子 \(Comparer\) 排序會使所有資料列變成非共用的。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [Windows Form DataGridView 控制項中的效能微調](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [如何：設定 Windows Form DataGridView 控制項的預設儲存格樣式](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)   
 [Windows Form DataGridView 控制項中的調整大小選項](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)