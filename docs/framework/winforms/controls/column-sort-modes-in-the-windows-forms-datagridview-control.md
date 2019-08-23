---
title: Windows Form DataGridView 控制項中的資料行排序模式
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d0d743ccae38d101eda5bb9780b33ae18dfb608a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918454"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料行排序模式
<xref:System.Windows.Forms.DataGridView>資料行有三種排序模式。 每個資料行的排序模式都是透過<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>資料行的屬性來指定, 這可設為下列<xref:System.Windows.Forms.DataGridViewColumnSortMode>其中一個列舉值。  
  
|`DataGridViewColumnSortMode` 值|描述|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|文字方塊資料行的預設值。 除非使用資料行標頭做為選取範圍, 否則按一下欄標題會<xref:System.Windows.Forms.DataGridView>自動依此欄排序, 並顯示表示排序次序的圖像。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|非 text box 資料行的預設值。 您可以用程式設計方式排序此資料行;不過, 它不適合用于排序, 因此不會保留任何空間給排序圖像。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|您可以用程式設計方式排序此資料行, 並保留空間給排序圖像。|  
  
 <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>如果資料行包含可以有意義排序的值, 您可能會想要變更預設值的排序模式。 例如, 如果您的資料庫資料行包含代表專案狀態的數位, 您可以藉由將 image 資料行系結至資料庫資料行, 將這些數字顯示為對應的圖示。 然後, 您可以在<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件的處理常式中, 將數值資料格的值變更為影像顯示值。 在此情況下, 將<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性設定<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>為, 可讓您的使用者排序資料行。 自動排序可讓您的使用者群組具有相同狀態的專案, 即使對應到數位的狀態沒有自然順序也一樣。 核取方塊資料行是另一個範例, 其中自動排序適用于將相同狀態的專案分組。  
  
 <xref:System.Windows.Forms.DataGridView> 不論<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>設定為何, 您都可以透過任何資料行或多個資料行中的值, 以程式設計方式排序。 當您想要提供您自己的使用者介面 (UI) 進行排序時, 或當您想要執行自訂排序時, 程式設計排序就很有用。 提供您自己的<xref:System.Windows.Forms.DataGridView>排序 UI 很有用, 例如, 當您設定選取模式來啟用資料行標頭選擇時。 在此情況下, 雖然資料行標頭無法用於排序, 但您仍希望標頭顯示適當的排序圖像, 因此您可以將<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性設定為。 <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>  
  
 設定為以程式設計方式排序模式的資料行不會自動顯示排序圖像。 對於這些資料行, 您必須藉由設定<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>屬性來自行顯示圖像。 如果您想要在自訂排序中有彈性, 這是必要的。 例如, 如果您<xref:System.Windows.Forms.DataGridView>依多個資料行排序, 您可能會想要顯示多個排序字元或沒有排序圖像。  
  
 雖然您可以<xref:System.Windows.Forms.DataGridView>依任何資料行以程式設計方式排序, 但某些欄 (例如按鈕資料行) 可能不會包含可有意義地排序的值。 對於這些資料行, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>的屬性<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>設定表示永遠不會用於排序, 因此不需要在排序圖像的標頭中保留空間。  
  
 當排序時, 您可以藉由檢查<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>和<xref:System.Windows.Forms.DataGridView.SortOrder%2A>屬性的值來判斷排序資料行和排序次序。 <xref:System.Windows.Forms.DataGridView> 在自訂排序作業之後, 這些值沒有意義。 如需自訂排序的詳細資訊, 請參閱本主題稍後的自訂排序一節。  
  
 當同時包含系結和未系結資料行的控制項進行排序時,無法自動維護未系結資料行中的值。<xref:System.Windows.Forms.DataGridView> 若要維護這些值<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> , 您必須將屬性設定為`true`並處理和<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件, 以<xref:System.Windows.Forms.DataGridView.CellValueNeeded>實作為虛擬模式。 如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)中執行虛擬模式。 不支援以系結模式的未系結資料行排序。  
  
## <a name="programmatic-sorting"></a>程式設計排序  
 您可以藉由<xref:System.Windows.Forms.DataGridView>呼叫其<xref:System.Windows.Forms.DataGridView.Sort%2A>方法, 以程式設計方式排序。  
  
 方法的`Sort(DataGridViewColumn,ListSortDirection)`多載會採用<xref:System.Windows.Forms.DataGridViewColumn>和列舉值做為參數。<xref:System.ComponentModel.ListSortDirection> <xref:System.Windows.Forms.DataGridView.Sort%2A> 當排序依據的資料行具有可有意義排序的值, 但您不想設定自動排序時, 這個多載就很有用。 當您呼叫此多載, 並<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>傳入屬性值為的<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>資料行時, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A>會<xref:System.Windows.Forms.DataGridView.SortOrder%2A>自動設定和屬性, 且適當的排序圖像會出現在資料行標頭中。  
  
> [!NOTE]
> 藉由`Sort(DataGridViewColumn,ListSortDirection)`設定屬性來將控制項系結至外部資料源時,方法多載無法用於未系結資料行。<xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.DataSource%2A> 此外, 當<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性為`true`時, 您可以只針對系結的資料行呼叫此多載。 若要判斷資料行是否為數據系結, 請<xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>檢查屬性值。 不支援以系結模式排序未系結的資料行。  
  
## <a name="custom-sorting"></a>自訂排序  
 您可以使用<xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.Sort%2A>方法的`Sort(IComparer)`多載或藉由處理<xref:System.Windows.Forms.DataGridView.SortCompare>事件來自訂。  
  
 方法多載會採用將<xref:System.Collections.IComparer>介面實作為參數之類別的實例。 `Sort(IComparer)` 當您想要提供自訂排序時, 這個多載非常有用;例如, 當資料行中的值沒有自然排序次序, 或自然排序次序不適當時。 在此情況下, 您不能使用自動排序, 但是您可能還是想要讓使用者按一下資料行標頭來排序。 如果您未使用資料行標頭來進行選取<xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> , 則可以在事件的處理常式中呼叫這個多載。  
  
> [!NOTE]
> 只有當控制項未系結到<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>外部資料源, 且屬性值為時, `false`方法多載才會運作。`Sort(IComparer)` <xref:System.Windows.Forms.DataGridView> 若要針對系結至外部資料源的資料行自訂排序, 您必須使用資料來源所提供的排序作業。 在虛擬模式中, 您必須為未系結的資料行提供自己的排序作業。  
  
 若要使用`Sort(IComparer)`方法多載, 您必須建立自己的類別來<xref:System.Collections.IComparer>執行介面。 此介面<xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>需要您的類別來執行方法, <xref:System.Windows.Forms.DataGridView>在呼叫`Sort(IComparer)`方法多<xref:System.Windows.Forms.DataGridViewRow>載時, 會將物件當做輸入傳遞。 有了這項功能, 您就可以根據任何資料行中的值來計算正確的資料列排序。  
  
 方法多載不會<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>設定和<xref:System.Windows.Forms.DataGridView.SortOrder%2A> <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>屬性, 因此您必須一律設定屬性來顯示排序圖像。 `Sort(IComparer)`  
  
 除了方法多載以外, 您還可以藉由執行<xref:System.Windows.Forms.DataGridView.SortCompare>事件的處理常式來提供自訂排序。 `Sort(IComparer)` 當使用者按一下已設定自動排序的資料行標頭, 或當您呼叫`Sort(DataGridViewColumn,ListSortDirection)` <xref:System.Windows.Forms.DataGridView.Sort%2A>方法的多載時, 就會發生這個事件。 此事件會針對控制項中的每一對資料列進行, 讓您能夠計算其正確的順序。  
  
> [!NOTE]
> 當屬性已設定或<xref:System.Windows.Forms.DataGridView.SortCompare> `true`屬性值為時, 就不會發生此事件。 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> <xref:System.Windows.Forms.DataGridView.DataSource%2A>  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中排序資料](sorting-data-in-the-windows-forms-datagridview-control.md)
- [如何：設定 Windows Forms DataGridView 控制項中的資料行排序模式](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [如何：在 Windows Forms DataGridView 控制項中自訂排序](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
