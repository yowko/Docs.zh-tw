---
title: Windows Form DataGridView 控制項中的資料行排序模式
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: 935251c783bbe74903cee6afd5e14eed4483d69d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717852"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料行排序模式
<xref:System.Windows.Forms.DataGridView> 資料行有三種排序模式。 透過所指定的每個資料行的排序模式<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>資料行，可以設定為下列其中一種屬性<xref:System.Windows.Forms.DataGridViewColumnSortMode>列舉值。  
  
|`DataGridViewColumnSortMode` 值|描述|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|文字方塊資料行的預設值。 除非資料行標頭用於選項，按一下資料行標頭會自動排序<xref:System.Windows.Forms.DataGridView>依據此資料行，並顯示圖像 （glyph），表示排序順序。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|非文字方塊的資料行的預設值。 您可以排序此資料行，以程式設計的方式;不過，它並不適用於排序，因此會不保留任何空間，用於排序圖像。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|您可以透過程式設計的方式，排序這個資料行和排序圖像 （glyph） 保留的空間。|  
  
 您可能想要變更預設的資料行的排序模式<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>如果它包含可以有意義地排序的值。 比方說，如果您有包含數字，代表項目狀態的資料庫資料行時，您可以顯示這些數字為對應的圖示的影像資料行繫結至資料庫資料行。 您可以變更數字的資料格的值到映像中的處理常式的顯示值<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件。 在此情況下，設定<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性設<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>會讓使用者排序資料行。 自動排序，可讓您的使用者群組項目具有相同的狀態，即使對應的數字的狀態並沒有自然的順序。 核取方塊資料行是另一個範例是用於群組的相同狀態的項目自動排序。  
  
 您可以排序<xref:System.Windows.Forms.DataGridView>多個資料行，不論在任何資料行中選取的值，以程式設計方式<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>設定。 當您想要提供您自己的使用者介面 (UI) 進行排序，或當您想要實作自訂排序，以程式設計方式排序非常有用。 提供排序的 UI 是非常有用，例如，當您將設定<xref:System.Windows.Forms.DataGridView>選取模式，以啟用資料行的標頭選取範圍。 在此情況下，雖然資料行標頭不能用於排序，但是您仍想標頭來顯示適當的排序圖像，因此您會設定<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性設<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>。  
  
 設定為以程式設計方式排序模式資料行不會自動顯示排序圖像。 針對這些資料行中，您必須顯示圖像 （glyph） 自行設定<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>屬性。 這是必要，如果您想自訂排序的彈性。 例如，如果您排序<xref:System.Windows.Forms.DataGridView>多個資料行，您可能想要顯示多個排序圖像 （glyph） 或未排序圖像 （glyph）。  
  
 雖然您可以以程式設計的方式排序<xref:System.Windows.Forms.DataGridView>依任何資料行，某些資料行，例如按鈕資料行，可能不會包含可以有意義地排序的值。 針對這些資料行中，<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性設定<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>表示，它將永遠不會用於排序，因此不需要排序圖像 （glyph） 的標頭中保留的空間。  
  
 當<xref:System.Windows.Forms.DataGridView>是已排序，您可以決定排序資料行和排序次序所檢查的值<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>和<xref:System.Windows.Forms.DataGridView.SortOrder%2A>屬性。 這些值不是自訂的排序作業之後有意義。 如需有關自訂排序的詳細資訊，請參閱本主題稍後的自訂排序 」 一節。  
  
 當<xref:System.Windows.Forms.DataGridView>控制項包含繫結和解除繫結的資料行已排序且未繫結的資料行的值不能自動維護。 為了維護這些值，您必須實作虛擬模式，藉由設定<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性，以`true`和處理<xref:System.Windows.Forms.DataGridView.CellValueNeeded>和<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件。 如需詳細資訊，請參閱[如何：實作虛擬模式中的 Windows Form DataGridView 控制項](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。 不支援未繫結中繫結模式的資料行排序。  
  
## <a name="programmatic-sorting"></a>程式設計排序  
 您可以排序<xref:System.Windows.Forms.DataGridView>程式設計的方式是藉由呼叫其<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。  
  
 `Sort(DataGridViewColumn,ListSortDirection)`多載<xref:System.Windows.Forms.DataGridView.Sort%2A>方法會採用<xref:System.Windows.Forms.DataGridViewColumn>和<xref:System.ComponentModel.ListSortDirection>做為參數的列舉值。 值，可以有意義地排序，但不是想設定自動排序的資料行排序時，這個多載會很有用。 當您呼叫這個多載，並傳入的資料行<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性值<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>，則<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>和<xref:System.Windows.Forms.DataGridView.SortOrder%2A>屬性會自動設定，並適當排序圖像 （glyph） 出現在資料行標頭。  
  
> [!NOTE]
>  當<xref:System.Windows.Forms.DataGridView>控制項繫結至外部資料來源藉由設定<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性，`Sort(DataGridViewColumn,ListSortDirection)`方法多載不適用於未繫結的資料行。 此外，當<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性是`true`，您可以呼叫這個多載只對繫結的資料行。 若要判斷資料行是否為資料繫結，請檢查<xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>屬性值。 不支援排序繫結模式中的未繫結資料行。  
  
## <a name="custom-sorting"></a>自訂排序  
 您可以自訂<xref:System.Windows.Forms.DataGridView>利用`Sort(IComparer)`多載<xref:System.Windows.Forms.DataGridView.Sort%2A>方法或透過處理<xref:System.Windows.Forms.DataGridView.SortCompare>事件。  
  
 `Sort(IComparer)`方法多載會採用實作類別的執行個體<xref:System.Collections.IComparer>做為參數的介面。 這個多載會很有用，當您想要提供自訂排序;例如，當資料行的值沒有自然排序次序，或當自然排序次序不適當。 在此情況下，您無法使用自動排序，但您仍可以使用者按一下資料行標頭來排序。 您可以在處理常式中呼叫這個多載<xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick>事件，如果您選擇不使用資料行標頭。  
  
> [!NOTE]
>  `Sort(IComparer)`方法多載的運作時，才<xref:System.Windows.Forms.DataGridView>控制項未繫結至外部資料來源並<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性值是`false`。 若要自訂的繫結至外部資料來源的資料行排序，您必須使用資料來源所提供的排序作業。 在虛擬模式中，您必須提供您自己未繫結的資料行的排序作業。  
  
 若要使用`Sort(IComparer)`方法多載，您必須建立您自己的類別可實作<xref:System.Collections.IComparer>介面。 此介面需要您的類別來實作<xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>方法，要<xref:System.Windows.Forms.DataGridView>通過<xref:System.Windows.Forms.DataGridViewRow>物件做為輸入時`Sort(IComparer)`方法多載會呼叫。 以此方式，您可以計算任何資料行的值為基礎的正確的資料列排序。  
  
 `Sort(IComparer)`方法多載不會設定<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>並<xref:System.Windows.Forms.DataGridView.SortOrder%2A>屬性，因此您必須一律設定<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>顯示排序圖像 （glyph） 的屬性。  
  
 做為替代`Sort(IComparer)`方法多載，您可以藉由實作的處理常式自訂排序<xref:System.Windows.Forms.DataGridView.SortCompare>事件。 當使用者按一下 設定用於自動排序，或當您呼叫的資料行的標頭，就會發生此事件`Sort(DataGridViewColumn,ListSortDirection)`多載<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。 事件發生的每個組的控制項，讓您可以計算其正確的順序中的資料列。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare>不會發生事件時<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性設定或當<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性值是`true`。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中排序資料](sorting-data-in-the-windows-forms-datagridview-control.md)
- [如何：設定 Windows Form DataGridView 控制項中的資料行排序模式](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [如何：自訂 Windows Form DataGridView 控制項中排序](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
