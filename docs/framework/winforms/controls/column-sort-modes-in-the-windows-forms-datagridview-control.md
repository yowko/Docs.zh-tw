---
title: "Windows Form DataGridView 控制項中的資料行排序模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 088d9f1f76e88d8be838cbf7050601835eff216a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料行排序模式
<xref:System.Windows.Forms.DataGridView>資料行有三種排序模式。 每個資料行的排序模式透過指定<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>資料行，可以設定為下列其中一種屬性<xref:System.Windows.Forms.DataGridViewColumnSortMode>列舉值。  
  
|`DataGridViewColumnSortMode` 值|描述|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|文字資料行的預設值。 按一下資料行標頭會自動排序資料行標頭來選取項目，除非<xref:System.Windows.Forms.DataGridView>依據此資料行，並顯示圖像，表示排序順序。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|非文字方塊的資料行的預設值。 您可以排序此資料行，以程式設計的方式;不過，它不是適合進行排序，因此會不保留任何空間排序圖像。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|您可以透過程式設計的方式，來排序此資料行，並保留空間排序圖像。|  
  
 您可能想要變更預設值為資料行的排序模式<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>如果它包含可以有意義地排序的值。 例如，如果您有包含數字，代表項目狀態的資料庫資料行，您可以顯示這些數字為對應的圖示的影像資料行繫結至資料庫資料行。 您可以再將變更的數值資料格值的處理常式中的影像顯示值<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件。 在此情況下，設定<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>要讓使用者排序資料行。 自動排序，可讓您的使用者群組項目具有相同的狀態，即使對應的數字的狀態不會有自然的順序。 核取方塊資料行是另一個範例可用於群組的相同狀態的項目自動排序。  
  
 您可以排序<xref:System.Windows.Forms.DataGridView>以程式設計方式或多個資料行，不論中任何資料行的值<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>設定。 當您想要提供您自己的使用者介面 (UI) 進行排序，或當您想要實作自訂排序，程式設計排序非常有用。 提供您自己的排序 UI 非常有用，例如，當您將<xref:System.Windows.Forms.DataGridView>選取模式，以啟用資料行的標頭選取範圍。 在此情況下，無法使用資料行標頭來排序，但是您仍然想要顯示適當的排序圖像，因此您會在設定的標頭<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>。  
  
 設定為以程式設計方式排序模式資料行不會自動顯示排序圖像。 這些資料行，您必須顯示圖像自行設定<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>屬性。 這是必要，如果您想自訂排序的彈性。 例如，如果您排序<xref:System.Windows.Forms.DataGridView>多個資料行，您可能想要顯示多個排序圖像 （glyph） 或未排序圖像。  
  
 雖然您可以透過程式設計方式來排序<xref:System.Windows.Forms.DataGridView>任何資料行，某些資料行，例如按鈕資料行，可能不包含可以有意義地排序的值。 這些資料行，<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性設定為<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>指出，它會永遠不會用於排序，因此不需要保留排序圖像標頭中的空間。  
  
 當<xref:System.Windows.Forms.DataGridView>是已排序，您可以檢查以判斷排序資料行和排序次序的值<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>和<xref:System.Windows.Forms.DataGridView.SortOrder%2A>屬性。 這些值不是自訂排序作業之後有意義。 如需自訂排序的詳細資訊，請參閱本主題稍後的自訂排序的一節。  
  
 當<xref:System.Windows.Forms.DataGridView>控制項包含繫結和繫結資料行排序，無法自動維護未繫結的資料行的值。 為了維護這些值，您必須實作虛擬模式，藉由設定<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性`true`和處理<xref:System.Windows.Forms.DataGridView.CellValueNeeded>和<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件。 如需詳細資訊，請參閱[How to： 在 Windows Form DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。 不支援的繫結模式的未繫結資料行排序。  
  
## <a name="programmatic-sorting"></a>程式設計排序  
 您可以排序<xref:System.Windows.Forms.DataGridView>以程式設計的方式是藉由呼叫其<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。  
  
 `Sort(DataGridViewColumn,ListSortDirection)`多載<xref:System.Windows.Forms.DataGridView.Sort%2A>方法會採用<xref:System.Windows.Forms.DataGridViewColumn>和<xref:System.ComponentModel.ListSortDirection>做為參數的列舉值。 這個多載時，可以有意義地加以排序，但不是想設定自動排序值的資料行排序。 當您呼叫這個多載，並傳入的資料行<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性值為<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>、<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>和<xref:System.Windows.Forms.DataGridView.SortOrder%2A>屬性會自動設定和資料行標題中顯示適當的排序圖像。  
  
> [!NOTE]
>  當<xref:System.Windows.Forms.DataGridView>控制項繫結至外部資料來源藉由設定<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性，`Sort(DataGridViewColumn,ListSortDirection)`方法多載不適用於未繫結的資料行。 此外，當<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性是`true`，您可以呼叫這個多載僅適用於繫結資料行。 若要判斷資料行是否為資料繫結，請檢查<xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>屬性值。 不支援排序繫結模式中的未繫結資料行。  
  
## <a name="custom-sorting"></a>自訂排序  
 您可以自訂<xref:System.Windows.Forms.DataGridView>使用`Sort(IComparer)`多載<xref:System.Windows.Forms.DataGridView.Sort%2A>方法或透過處理<xref:System.Windows.Forms.DataGridView.SortCompare>事件。  
  
 `Sort(IComparer)`方法多載會實作的類別的執行個體<xref:System.Collections.IComparer>做為參數的介面。 這個多載時，您想要提供自訂排序。例如，當資料行中的值沒有自然排序次序，或當自然排序次序不適當。 在此情況下，您不能使用自動排序，但您仍可能會想讓使用者按一下資料行標頭來排序。 您可以在處理常式中呼叫這個多載<xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick>事件，如果您選擇不使用資料行標頭。  
  
> [!NOTE]
>  `Sort(IComparer)`方法多載的運作時，才<xref:System.Windows.Forms.DataGridView>控制項未繫結至外部資料來源和<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性值是`false`。 若要自訂的繫結至外部資料來源的資料行排序，您必須使用資料來源所提供的排序作業。 在虛擬模式中，您必須提供您自己未繫結的資料行的排序作業。  
  
 若要使用`Sort(IComparer)`方法多載時，您必須建立您自己的類別可實作<xref:System.Collections.IComparer>介面。 這個介面需要您的類別來實作<xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>方法，要<xref:System.Windows.Forms.DataGridView>傳遞<xref:System.Windows.Forms.DataGridViewRow>物件做為輸入時`Sort(IComparer)`呼叫的方法多載。 與這個項目，您可以計算任何資料行中的值為基礎的正確的資料列排序。  
  
 `Sort(IComparer)`方法多載不會設定<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>和<xref:System.Windows.Forms.DataGridView.SortOrder%2A>屬性，因此您必須永遠設定<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>屬性來顯示排序圖像。  
  
 做為替代`Sort(IComparer)`方法多載時，您可以提供藉由實作的處理常式自訂排序<xref:System.Windows.Forms.DataGridView.SortCompare>事件。 當使用者按一下資料行設定為自動排序，或當您呼叫的標頭，就會發生此事件`Sort(DataGridViewColumn,ListSortDirection)`多載<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。 事件發生的每個組中的控制項，讓您可以計算其正確順序的資料列。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare>不會發生事件時<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性設定或當<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性值是`true`。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>  
 [在 Windows Forms DataGridView 控制項中排序資料](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [操作說明：設定 Windows Forms DataGridView 控制項中的資料行排序模式](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 [操作說明：自訂 Windows Forms DataGridView 控制項中的排序](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
