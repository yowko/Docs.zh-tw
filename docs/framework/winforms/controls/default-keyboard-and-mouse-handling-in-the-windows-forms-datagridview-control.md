---
title: 預設鍵盤和滑鼠處理 Windows Form DataGridView 控制項中
ms.date: 02/13/2018
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
ms.openlocfilehash: b0ed468fe7d38fbeda90d5347338bce14059b730
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529564"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>預設鍵盤和滑鼠處理 Windows Form DataGridView 控制項中

下表描述使用者可以互動<xref:System.Windows.Forms.DataGridView>透過鍵盤和滑鼠控制。  
  
> [!NOTE]
>  若要自訂鍵盤行為，可以處理標準鍵盤事件這類<xref:System.Windows.Forms.Control.KeyDown>。 在編輯模式，不過，裝載的編輯控制項接收鍵盤輸入和鍵盤事件不會對<xref:System.Windows.Forms.DataGridView>控制項。 若要處理編輯的控制項事件，將您的處理常式附加至編輯控制項中<xref:System.Windows.Forms.DataGridView.EditingControlShowing>事件處理常式。 或者，您可以自訂鍵盤行為<xref:System.Windows.Forms.DataGridView>藉由覆寫子類別<xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A>和<xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>方法。  
  
## <a name="default-keyboard-handling"></a>預設鍵盤處理  
  
### <a name="basic-navigation-and-entry-keys"></a>基本瀏覽和項目索引鍵  
  
|按鍵或按鍵組合|描述|  
|----------------------------|-----------------|  
|向下鍵|將焦點移至目前的資料格正下方的儲存格。 如果焦點是在最後一個資料列中，沒有任何作用。|  
|向左鍵|將焦點移至先前的資料格的資料列中。 如果焦點是資料列中第一個資料格中，沒有任何作用。|  
|向右鍵|將焦點移至下一個儲存格的資料列中。 如果焦點是在資料列中最後一個資料格中，沒有任何作用。|  
|向上鍵|將焦點移至上方的目前儲存格。 如果焦點是在第一個資料列中，沒有任何作用。|  
|首頁|將焦點移至目前的資料列中的第一個儲存格。|  
|END|將焦點移至目前的資料列中的最後一個儲存格。|  
|PAGE DOWN|將控制項向下捲動充分顯示之資料列數目。 將焦點移至最後一個完整顯示的資料列中，而不需要變更資料行。|  
|PAGE UP|向上捲動控制項的充分顯示之資料列數。 將焦點移到第一個顯示的資料列，而不需要變更資料行。|  
|TAB|如果<xref:System.Windows.Forms.DataGridView.StandardTab%2A>屬性值是`false`，將焦點移至目前資料列中的下一個儲存格。 如果焦點位於資料列的最後一個資料格，將焦點移到下一個資料列的第一個儲存格。 如果焦點在控制項中的最後一個資料格，將焦點移至定位順序的父容器中的下一個控制項。<br /><br /> 如果<xref:System.Windows.Forms.DataGridView.StandardTab%2A>屬性值是`true`，將焦點移至定位順序的父容器中的下一個控制項。|  
|SHIFT+TAB|如果<xref:System.Windows.Forms.DataGridView.StandardTab%2A>屬性值是`false`，將焦點移到目前資料列的上一個儲存格。 如果焦點位於資料列的第一個資料格，將焦點移至前一個資料列中的最後一個儲存格。 如果焦點在控制項中第一個資料格中，將焦點移至上一個控制項的父容器的定位順序。<br /><br /> 如果<xref:System.Windows.Forms.DataGridView.StandardTab%2A>屬性值是`true`，將焦點移至定位順序的父容器中的上一個控制項。|  
|CTRL+TAB|如果<xref:System.Windows.Forms.DataGridView.StandardTab%2A>屬性值是`false`，將焦點移至定位順序的父容器中的下一個控制項。<br /><br /> 如果<xref:System.Windows.Forms.DataGridView.StandardTab%2A>屬性值是`true`，將焦點移至目前資料列中的下一個儲存格。 如果焦點位於資料列的最後一個資料格，將焦點移到下一個資料列的第一個儲存格。 如果焦點在控制項中的最後一個資料格，將焦點移至定位順序的父容器中的下一個控制項。|  
|CTRL+SHIFT+TAB|如果<xref:System.Windows.Forms.DataGridView.StandardTab%2A>屬性值是`false`，將焦點移至定位順序的父容器中的上一個控制項。<br /><br /> 如果<xref:System.Windows.Forms.DataGridView.StandardTab%2A>屬性值是`true`，將焦點移到目前資料列的上一個儲存格。 如果焦點位於資料列的第一個資料格，將焦點移至前一個資料列中的最後一個儲存格。 如果焦點在控制項中第一個資料格中，將焦點移至上一個控制項的父容器的定位順序。|  
|CTRL + 方向鍵|將焦點移至箭頭的方向遠的儲存格。|  
|CTRL + HOME|將焦點移至控制項中的第一個資料格。|  
|CTRL + END|將焦點移至控制項中的最後一個資料格。|  
|CTRL + PAGE DOWN/總|與 PAGE down 鍵或 PAGE UP 鍵相同。|  
|F2|如果目前儲存格進入儲存格的編輯模式<xref:System.Windows.Forms.DataGridView.EditMode%2A>屬性值是<xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2>或<xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>。|
|F3|如果排序目前的資料行<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>屬性值是<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>。 它是不同於按一下目前的資料行標頭。 自.NET Framework 4.7.2 可用。 若要啟用這項功能，應用程式必須以.NET Framework 4.7.2 或更新版本為目標，或明確選擇進入使用 AppContext 參數的協助工具增強功能。|  
|F4|如果目前儲存格是<xref:System.Windows.Forms.DataGridViewComboBoxCell>，將儲存格進入編輯模式，並顯示下拉式清單。|  
|ALT + 向上/向下鍵|如果目前儲存格是<xref:System.Windows.Forms.DataGridViewComboBoxCell>，將儲存格進入編輯模式，並顯示下拉式清單。|  
|空格鍵|如果目前儲存格是<xref:System.Windows.Forms.DataGridViewButtonCell>， <xref:System.Windows.Forms.DataGridViewLinkCell>，或<xref:System.Windows.Forms.DataGridViewCheckBoxCell>，引發<xref:System.Windows.Forms.DataGridView.CellClick>和<xref:System.Windows.Forms.DataGridView.CellContentClick>事件。 如果目前儲存格是<xref:System.Windows.Forms.DataGridViewButtonCell>，也按下按鈕。 如果目前儲存格是<xref:System.Windows.Forms.DataGridViewCheckBoxCell>，也會變更選取狀態。|  
|ENTER|認可目前儲存格和資料列的任何變更，並將焦點移至目前的資料格正下方的儲存格。 如果焦點是在最後一個資料列中，認可所有變更，而不移動焦點。|  
|ESC|如果控制項處於編輯模式，取消編輯。 如果控制項不是處於編輯模式下，還原此控制項是繫結至支援編輯資料來源，目前的資料列所做的任何變更，或已實作虛擬模式與資料列層級的認可範圍。|  
|退格鍵|編輯儲存格時，會刪除之前插入點的字元。|  
|DELETE|編輯儲存格時，請在插入點後刪除的字元。|  
|CTRL+ENTER|認可目前儲存格的任何變更，而不移動焦點。 也與已實作此控制項是繫結至資料來源支援編輯或虛擬模式在目前資料列的任何變更的認可資料列層級的認可範圍。|  
|CTRL+0|進入<xref:System.DBNull.Value?displayProperty=nameWithType>值到目前的儲存格，如果可以編輯儲存格。 根據預設，顯示值<xref:System.DBNull>資料格的值是值<xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>屬性<xref:System.Windows.Forms.DataGridViewCellStyle>作用中的目前儲存格。|  
  
### <a name="selection-keys"></a>選取按鍵

 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>屬性設定為`false`和<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>，使用瀏覽鍵來變更目前的儲存格變更為新的儲存格的選取項目。 SHIFT、 CTRL 和 ALT 鍵並不會影響這個行為。  
  
 如果<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>，就會發生相同問題但具有下列功能。  
  
|按鍵或按鍵組合|描述|  
|----------------------------|-----------------|  
|SHIFT + 空格鍵|選取整個資料列或資料行 （不同於按一下資料列或資料行的標頭）。|  
|瀏覽金鑰 （箭號，PAGE up/down，首頁，結束）|如果選取整個資料列或資料行，將目前的儲存格變更為新的資料列或資料行選擇移至全新的資料列或資料行 （取決於選取的模式）。|  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設`false`和<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>，變更為新的資料列或資料行的目前儲存格，使用鍵盤將選取範圍移至全新的資料列或資料行。 SHIFT、 CTRL 和 ALT 鍵並不會影響這個行為。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設`true`、 導覽行為不會變更，但以鍵盤巡覽時按住 shift 鍵 （包括 CTRL + SHIFT） 會修改多個儲存格選取範圍。 導覽開始前，控制會標記為錨定儲存格的目前儲存格。 當您巡覽時按住 shift 鍵時，則選取範圍包含錨定儲存格和目前的儲存格之間的所有資料格。 如果它們尚未選取，但它們可能會變成未選取的鍵盤巡覽方式暫時便會將這些錨定儲存格之間的目前儲存格，如果在控制項中的其他資料格將會維持選取狀態。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設`true`和<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、 錨定儲存格和目前的儲存格的行為相同，但是只有完整的資料列或資料行變成選取或取消選取。  
  
## <a name="default-mouse-handling"></a>預設滑鼠處理
  
### <a name="basic-mouse-handling"></a>基本的滑鼠處理
  
> [!NOTE]
>  一律滑鼠左的按鈕儲存格上按一下變更目前的儲存格。 其中一個可用時，滑鼠右按鈕儲存格上按一下開啟快顯功能表。  
  
|滑鼠動作|描述|  
|------------------|-----------------|  
|向左鍵|按下儲存格的目前儲存格，並引發<xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType>事件。|  
|左邊的滑鼠向上按鈕|引發 <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> 事件。|  
|按一下滑鼠左鍵|引發<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>和<xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType>事件|  
|向下滑鼠左的按鈕並拖曳資料行的標頭資料格|如果<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>屬性是`true`，將資料行移，讓它可以放入新的位置。|  
  
### <a name="mouse-selection"></a>滑鼠選取範圍

 沒有選取範圍的行為都與滑鼠中間鍵或滑鼠滾輪。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>屬性設定為`false`和<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>，會發生下列行為。  
  
|滑鼠動作|描述|  
|------------------|-----------------|  
|按一下滑鼠左鍵|如果使用者按一下資料格，請選取目前儲存格。 如果使用者按一下資料列或資料行的標頭沒有選取行為。|  
|按一下滑鼠右鍵|如果有的話，會顯示快顯功能表。|  
  
 相同的行為發生時<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>，不過，根據選取模式中，按一下資料列或資料行的標頭會選取整個資料列或資料行，設定中的資料列或資料行的第一個儲存格的目前儲存格。  
  
 如果<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>，按一下任何資料列或資料行中的儲存格將會選取整個資料列或資料行。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設`true`，按一下儲存格時按住 CTRL 或 shift 鍵，將會修改多個儲存格選取範圍。  
  
 當您按一下儲存格時按住 ctrl 鍵時，資料格會變更選取狀態，而所有其他資料格保留其目前的選取狀態。  
  
 當您按一下儲存格或一系列的資料格時按住 shift 鍵時，則選取範圍包含目前資料格位於第一次之前的目前儲存格位置錨定儲存格之間的所有資料格。 當您按一下並拖曳滑鼠指標，跨多個資料格時，錨定儲存格是在拖曳作業開始所點選的資料格。 後續的點選，按住 shift 鍵同時變更目前的儲存格，但不是錨定儲存格。 如果它們尚未選取，但它們可能會變成未選取如果滑鼠巡覽暫時便會將這些錨定儲存格之間的目前儲存格控制項中的其他資料格將會維持選取狀態。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設`true`和<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>，按住 shift 鍵同時按一下資料列或資料行標頭 （取決於選取的模式） 會修改現有的完整資料列或資料行的選取範圍，如果這類選取項目存在。 否則，它將會清除選取項目，新的完整資料列或資料行的選取範圍。 按一下資料列或資料行的標頭時按住 ctrl 鍵，不過，會加入或移除的按下後的資料列或資料行從目前的選取項目而不是修改目前的選取範圍。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設`true`和<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、 在按下 SHIFT 或 ctrl 鍵同時按一下儲存格的行為相同的方式，除非該只有完整的資料列和資料行會受到影響。  
  
## <a name="see-also"></a>另請參閱

<xref:System.Windows.Forms.DataGridView>  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
