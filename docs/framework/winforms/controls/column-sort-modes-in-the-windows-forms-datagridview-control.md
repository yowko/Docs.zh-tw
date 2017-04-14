---
title: "Windows Form DataGridView 控制項中的資料行排序模式 | Microsoft Docs"
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
  - "資料格, 排序模式"
  - "DataGridView 控制項 [Windows Form], 排序模式"
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Windows Form DataGridView 控制項中的資料行排序模式
<xref:System.Windows.Forms.DataGridView> 資料行具有三種排序模式。  每個資料行的排序模式都是透過資料行的 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性所指定的，此屬性可設定為下列其中一個 <xref:System.Windows.Forms.DataGridViewColumnSortMode> 列舉值。  
  
|`DataGridViewColumnSortMode` 值|描述|  
|------------------------------------|--------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|文字方塊資料行的預設值。  除非資料行行首是使用於選取，否則按一下資料行行首就會以此資料行自動排序 <xref:System.Windows.Forms.DataGridView>，並顯示出代表排序次序的圖像 \(Glyph\)。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|非文字方塊資料行的預設值。  能夠以程式設計方式來排序此資料行；然而，因為資料行並非專供排序使用，所以沒有為排序圖像保留任何空間。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|能夠以程式設計方式排序這個資料行，且保留排序圖像的空間。|  
  
 如果預設為 <xref:System.Windows.Forms.DataGridViewColumnSortMode> 的資料行包含可以有意義地排序的值，您可能會想變更該資料行的排序模式。  例如，如果資料庫資料行包含代表項目狀態的數字，就可藉由繫結影像資料行至資料庫資料行，將這些數目顯示為對應的圖示。  然後可以在 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> 事件的處理常式中，將儲存格數值變更為影像顯示值。  在這種情況下，將 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewColumnSortMode> 可讓使用者排序資料行。  自動排序可以讓使用者將具有相同狀態的項目分組，即使對應至數字的狀態沒有自然序列也是如此。  檢查方塊資料行是另一個範例，在此範例中自動排序對於將相同狀態的項目分組，是非常有用的。  
  
 不論 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 設定為何，都可以依照任何資料行或多個資料行中的值，以程式設計方式將 <xref:System.Windows.Forms.DataGridView> 排序。  當您想要提供個人的排序使用者介面 \(UI\)，或想要實作自訂排序時，程式設計排序會很有用。  例如，將 <xref:System.Windows.Forms.DataGridView> 選取模式設定為啟用資料行行首選取時，提供自己的排序 UI 會非常有用。  在這種情況中，雖然資料行行首無法用來排序，您仍然想讓行首顯示適當的排序圖像，所以可將 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性設定為 <xref:System.Windows.Forms.DataGridViewColumnSortMode>。  
  
 設定為程式設計排序模式的資料行，不會自動顯示排序圖像。  對於這些資料行，必須透過設定 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName> 屬性來顯示圖像。  如果希望自訂排序具有彈性，這就是必要的。  例如，如果依照多個資料行排序 <xref:System.Windows.Forms.DataGridView>，則您可能希望顯示多個排序圖像或不顯示排序圖像。  
  
 雖然可以藉由程式設計方式，依任何資料行排序 <xref:System.Windows.Forms.DataGridView>，但是某些資料行 \(例如按鈕資料行\) 可能不會包含能有意義進行排序的值。  對於這些資料行，<xref:System.Windows.Forms.DataGridViewColumnSortMode> 的 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性設定代表絕不會用於排序，因此不需要在排序圖像的標頭中保留空間。  
  
 排序 <xref:System.Windows.Forms.DataGridView> 時，可以透過檢查 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> 和 <xref:System.Windows.Forms.DataGridView.SortOrder%2A> 屬性的值，決定排序資料行和排序順序。  這些值在自訂排序作業之後並不具備意義。  如需自訂排序的詳細資訊，請參閱這個主題稍後的＜自訂排序＞章節。  
  
 對包含繫結與未繫結資料行的 <xref:System.Windows.Forms.DataGridView> 控制項進行排序時，不會自動維護在未繫結資料行中的值。  若要維護這些值，您必須藉由將 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true`，且處理 <xref:System.Windows.Forms.DataGridView.CellValueNeeded> 和 <xref:System.Windows.Forms.DataGridView.CellValuePushed> 事件來實作虛擬模式。  如需詳細資訊，請參閱 [如何：在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。  在繫結模式中依未繫結的資料行排序不受支援。  
  
## 程式設計排序  
 您可透過呼叫 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法，以程式設計方式來排序 <xref:System.Windows.Forms.DataGridView>。  
  
 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(DataGridViewColumn,ListSortDirection)` 多載會使用 <xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.ComponentModel.ListSortDirection> 列舉值做為參數。  在依照具有可以有意義排序之值的資料行進行排序時，若不想設定自動排序，這個多載會非常有用。  當您呼叫這個多載，並在具有 <xref:System.Windows.Forms.DataGridViewColumnSortMode?displayProperty=fullName> 的 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性值之資料行中傳遞時，便會自動設定 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> 和 <xref:System.Windows.Forms.DataGridView.SortOrder%2A> 屬性，且適當的排序圖像會顯示於資料行行首。  
  
> [!NOTE]
>  當 <xref:System.Windows.Forms.DataGridView> 控制項透過設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性而繫結至外部資料來源時，`Sort(DataGridViewColumn,ListSortDirection)` 方法多載對未繫結的資料行將無法運作。  此外，當 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性設定為 `true` 時，您可以只為繫結的資料行呼叫此多載。  若要決定資料行是否為資料繫結，請檢查 <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> 屬性值。  不支援在繫結模式中排序未繫結的資料行。  
  
## 自訂排序  
 您可藉由使用 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(IComparer)` 多載或處理 <xref:System.Windows.Forms.DataGridView.SortCompare> 事件來自訂 <xref:System.Windows.Forms.DataGridView>。  
  
 `Sort(IComparer)` 方法多載會使用實作 <xref:System.Collections.IComparer> 介面之類別的執行個體做為參數。  當您想要提供自訂排序 \(例如，當資料行中的值沒有自然排序次序時或當自然排序次序不適用時\)，這個多載會非常有用。  在這種情況下，您不能使用自動排序，但可能還是想要使用者依按一下資料行行首來排序。  若不使用資料行行首做為選取範圍，您可在 <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> 事件的處理常式中呼叫這個多載。  
  
> [!NOTE]
>  只有在 <xref:System.Windows.Forms.DataGridView> 控制項未繫結至外部資料來源，且 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性為 `false` 時，`Sort(IComparer)` 方法多載才能作用。  若要自訂繫結至外部資料來源之資料行的排序，必須使用由資料來源所提供的排序作業。  在虛擬模式中，您必須為未繫結的資料行自行提供排序作業。  
  
 若要使用 `Sort(IComparer)` 方法多載，您必須建立實作 <xref:System.Collections.IComparer> 介面的個人類別。  這個介面需要您的類別實作 <xref:System.Collections.IComparer.Compare%2A?displayProperty=fullName> 方法，在呼叫 `Sort(IComparer)` 方法多載時，<xref:System.Windows.Forms.DataGridView> 會將 <xref:System.Windows.Forms.DataGridViewRow> 物件當作輸入傳遞至此方法。  藉由這個方法，可以依據任何資料行中的值，計算正確的資料列順序。  
  
 `Sort(IComparer)` 方法多載不會設定 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> 和 <xref:System.Windows.Forms.DataGridView.SortOrder%2A> 屬性，所以一定要設定 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName> 屬性以顯示排序圖像。  
  
 您可以藉由實作 <xref:System.Windows.Forms.DataGridView.SortCompare> 事件的處理常式來提供自訂排序，做為 `Sort(IComparer)` 方法多載的替代方法。  當使用者按一下為自動排序設定的資料行行首，或當您呼叫 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的 `Sort(DataGridViewColumn,ListSortDirection)` 多載時，便會發生這個事件。  控制項中的每一對資料列都會發生該事件，讓您可以計算它們的正確順序。  
  
> [!NOTE]
>  當設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性或當 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性值為 `true` 時，就不會發生 <xref:System.Windows.Forms.DataGridView.SortCompare> 事件。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName>   
 [在 Windows Form DataGridView 控制項中排序資料](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)   
 [如何：設定 Windows Form DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)   
 [如何：自訂 Windows Form DataGridView 控制項的排序](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)