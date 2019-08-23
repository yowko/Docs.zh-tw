---
title: Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠處理
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
ms.openlocfilehash: 97b8c8c3e418586bbc0053c358a2924484115a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969135"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠處理

下表說明使用者可以如何透過鍵盤和滑鼠<xref:System.Windows.Forms.DataGridView>與控制項互動。  
  
> [!NOTE]
> 若要自訂鍵盤行為, 您可以處理標準鍵盤事件<xref:System.Windows.Forms.Control.KeyDown>, 例如。 不過在編輯模式中, 主控編輯控制項會接收鍵盤輸入, 而且<xref:System.Windows.Forms.DataGridView>控制項不會發生鍵盤事件。 若要處理編輯控制項事件, 請將您的處理常式附加至<xref:System.Windows.Forms.DataGridView.EditingControlShowing>事件處理常式中的編輯控制項。 或者, 您也可以藉由覆<xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A>寫和<xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>方法, 在子類別中自訂鍵盤行為。  
  
## <a name="default-keyboard-handling"></a>預設鍵盤處理  
  
### <a name="basic-navigation-and-entry-keys"></a>基本導覽和專案索引鍵  
  
|按鍵或按鍵組合|描述|  
|----------------------------|-----------------|  
|向下鍵|將焦點移至目前儲存格正下方的資料格。 如果焦點是在最後一個資料列中, 則不會執行任何操作。|  
|向左鍵|將焦點移到資料列中的上一個儲存格。 如果焦點是在資料列的第一個資料格中, 則不會執行任何操作。|  
|向右鍵|將焦點移到資料列中的下一個儲存格。 如果焦點是在資料列的最後一個資料格中, 則不會執行任何操作。|  
|向上鍵|將焦點移至目前儲存格正上方的資料格。 如果焦點是在第一個資料列中, 則不會執行任何操作。|  
|首頁|將焦點移至目前資料列中的第一個資料格。|  
|END|將焦點移至目前資料列中的最後一個資料格。|  
|PAGE DOWN|將控制項向下滾動到完全顯示的資料列數目。 將焦點移至最後一個完整顯示的資料列, 而不變更資料行。|  
|PAGE UP|以完整顯示的資料列數目向上滾動控制項。 將焦點移至第一個顯示的資料列, 而不變更資料行。|  
|TAB|如果屬性值為, `false`則會將焦點移至目前資料列中的下一個儲存格。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 如果焦點已經在資料列的最後一個資料格中, 則會將焦點移至下一個資料列中的第一個資料格。 如果焦點是在控制項的最後一個資料格中, 則會將焦點移至父容器的定位順序中的下一個控制項。<br /><br /> 如果屬性值為, `true`則會將焦點移至父容器的定位順序中的下一個控制項。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A>|  
|SHIFT+TAB|如果屬性值為, `false`則會將焦點移至目前資料列中的上一個儲存格。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 如果焦點已經在資料列的第一個資料格中, 則會將焦點移至前一個資料列中的最後一個資料格。 如果焦點是在控制項中的第一個資料格, 則會將焦點移至父容器的定位順序中的上一個控制項。<br /><br /> 如果屬性值為, `true`則會將焦點移至父容器之定位順序的上一個控制項。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A>|  
|CTRL+TAB|如果屬性值為, `false`則會將焦點移至父容器的定位順序中的下一個控制項。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A><br /><br /> 如果屬性值為, `true`則會將焦點移至目前資料列中的下一個儲存格。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 如果焦點已經在資料列的最後一個資料格中, 則會將焦點移至下一個資料列中的第一個資料格。 如果焦點是在控制項的最後一個資料格中, 則會將焦點移至父容器的定位順序中的下一個控制項。|  
|CTRL+SHIFT+TAB|如果屬性值為, `false`則會將焦點移至父容器之定位順序的上一個控制項。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A><br /><br /> 如果屬性值為, `true`則會將焦點移至目前資料列中的上一個儲存格。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 如果焦點已經在資料列的第一個資料格中, 則會將焦點移至前一個資料列中的最後一個資料格。 如果焦點是在控制項中的第一個資料格, 則會將焦點移至父容器的定位順序中的上一個控制項。|  
|CTRL + 箭號|將焦點移至箭號方向的最左邊儲存格。|  
|CTRL + HOME|將焦點移至控制項中的第一個資料格。|  
|CTRL + END|將焦點移至控制項中的最後一個儲存格。|  
|CTRL + PAGE DOWN/UP|與 PAGE DOWN 或 PAGE UP 相同。|  
|F2|如果<xref:System.Windows.Forms.DataGridView.EditMode%2A>屬性值為<xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2>或<xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>, 則將目前儲存格置於資料格編輯模式。|
|F3|如果<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>屬性值為<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>, 則排序目前的資料行。 這與按一下目前的資料行標頭相同。 從 .NET Framework 4.7.2 開始提供。 若要啟用這項功能, 應用程式必須以 .NET Framework 4.7.2 或更新版本為目標, 或使用 AppCoNtext 參數明確加入宣告協助工具改善。|  
|F4|如果目前儲存格是<xref:System.Windows.Forms.DataGridViewComboBoxCell>, 則會將儲存格放入編輯模式, 並顯示下拉式清單。|  
|ALT + 向上/向下鍵|如果目前儲存格是<xref:System.Windows.Forms.DataGridViewComboBoxCell>, 則會將儲存格放入編輯模式, 並顯示下拉式清單。|  
|空格鍵|如果目前儲存格是<xref:System.Windows.Forms.DataGridViewButtonCell>、 <xref:System.Windows.Forms.DataGridViewLinkCell>或<xref:System.Windows.Forms.DataGridViewCheckBoxCell>, 則會引發<xref:System.Windows.Forms.DataGridView.CellClick>和<xref:System.Windows.Forms.DataGridView.CellContentClick>事件。 如果目前儲存格為<xref:System.Windows.Forms.DataGridViewButtonCell>, 也請按下按鈕。 如果目前儲存格為<xref:System.Windows.Forms.DataGridViewCheckBoxCell>, 也會變更檢查狀態。|  
|ENTER|認可對目前儲存格和資料列所做的任何變更, 並將焦點移至目前儲存格正下方的資料格。 如果焦點是在最後一個資料列中, 則會認可任何變更, 而不移動焦點。|  
|ESC|如果控制項處於編輯模式, 則會取消編輯。 如果控制項不是在編輯模式中, 則會在控制項系結至支援編輯或虛擬模式的資料來源已使用資料列層級認可範圍來執行時, 還原對目前資料列所做的任何變更。|  
|倒退鍵|在編輯儲存格時, 刪除插入點之前的字元。|  
|Delete|在編輯儲存格時, 刪除插入點之後的字元。|  
|CTRL+ENTER|認可對目前資料格所做的任何變更, 而不移動焦點。 如果控制項系結至支援編輯或虛擬模式的資料來源已實作為資料列層級的認可範圍, 也會認可對目前資料列所做的任何變更。|  
|CTRL+0|如果可以<xref:System.DBNull.Value?displayProperty=nameWithType>編輯資料格, 則在目前儲存格中輸入一個值。 根據預設, 資料<xref:System.DBNull>格值的顯示值是目前儲存格生效的<xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>屬性<xref:System.Windows.Forms.DataGridViewCellStyle>值。|  
  
### <a name="selection-keys"></a>選取索引鍵

 如果屬性設定為`false` , 且<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, 則使用導覽鍵來變更目前的儲存格, 會將選取範圍變更為新的資料格。 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> SHIFT、CTRL 和 ALT 鍵不會影響此行為。  
  
 如果設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> 或<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, 則會發生相同的行為, 但新增了下列專案。 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
  
|按鍵或按鍵組合|描述|  
|----------------------------|-----------------|  
|SHIFT + 空格鍵|選取完整的資料列或資料行 (與按一下資料列或資料行標頭相同)。|  
|導覽鍵 (方向鍵、PAGE UP/DOWN、HOME、END)|如果選取了完整的資料列或資料行, 將目前的資料格變更為新的資料列或資料行, 就會將選取範圍移至完整的新資料列或資料行 (視選取模式而定)。|  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設定為`false` , 而且<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, 則使用鍵盤將目前儲存格變更為新的資料列或資料行, 就會將選取範圍移至完整的新資料列或資料行。 SHIFT、CTRL 和 ALT 鍵不會影響此行為。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設定為`true`, 則不會變更導覽行為, 但是按 SHIFT (包括 CTRL + SHIFT) 時使用鍵盤流覽會修改多儲存格選取範圍。 開始導覽之前, 控制項會將目前儲存格標示為錨定儲存格。 當您按下 SHIFT 鍵時流覽時, 選取範圍會包含錨點儲存格與目前儲存格之間的所有資料格。 如果控制項中的其他資料格已選取, 則會維持選取狀態, 但如果鍵盤導覽暫時將它們放在錨定儲存格和目前儲存格之間, 則可能會變成未選取。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設定為`true` , 且<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, 則錨定儲存格和目前儲存格的行為相同, 但是只會選取或取消選取完整的資料列或資料行。  
  
## <a name="default-mouse-handling"></a>預設的滑鼠處理
  
### <a name="basic-mouse-handling"></a>基本滑鼠處理
  
> [!NOTE]
> 按一下具有滑鼠左鍵的資料格, 一律會變更目前的儲存格。 按一下具有滑鼠右鍵的資料格時, 就會開啟快捷方式功能表 (如果有的話)。  
  
|滑鼠動作|說明|  
|------------------|-----------------|  
|滑鼠左鍵向下鍵|將已按下的資料格變成目前儲存格<xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> , 並引發事件。|  
|按下滑鼠左鍵|引發 <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> 事件。|  
|按滑鼠左鍵按一下|<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>引發和事件<xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType>|  
|滑鼠左鍵向下鍵, 並在資料行標頭儲存格上拖曳|如果屬性為`true`, 則移動資料行, 使其可以放入新的位置。 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>|  
  
### <a name="mouse-selection"></a>滑鼠選取

 中間滑鼠按鍵或滑鼠滾輪沒有相關聯的選取行為。  
  
 如果屬性設定為`false` , 且<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>屬性設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, 則會發生下列行為。 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
  
|滑鼠動作|說明|  
|------------------|-----------------|  
|按一下滑鼠左鍵|只有在使用者按一下資料格時, 才選取目前的儲存格。 如果使用者按一下資料列或資料行標頭, 則不會有任何選取行為。|  
|按一下滑鼠右鍵|顯示快捷方式功能表 (如果有的話)。|  
  
 當設定為<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>時, 就會發生相同的行為, 但根據選取模式, 按一下資料列或資料行標頭將會選取完整的資料列或資料行, 並將目前的資料格設定為數據列或資料行中的第一個資料格。  
  
 如果<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, 按一下資料列或資料行中的任何資料格, 將會選取完整的資料列或資料行。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設定為`true`, 則按下 CTRL 或 SHIFT 鍵時, 按一下資料格將會修改多個資料格的選取範圍。  
  
 當您按下 CTRL 鍵時, 資料格會變更其選取狀態, 而所有其他儲存格都會保留其目前的選取狀態。  
  
 當您按下 SHIFT 鍵同時按一下儲存格或一系列資料格時, 選取範圍會包含目前儲存格與位於目前儲存格位置的錨點儲存格之間的所有儲存格, 然後再按一下。 當您按一下並拖曳指標到多個資料格時, 錨點儲存格就是在拖曳作業開始時按一下的儲存格。 按 SHIFT 鍵時, 後續按一下會變更目前的儲存格, 而不是錨點儲存格。 如果控制項中的其他資料格已選取, 則會維持選取狀態, 但如果滑鼠導覽暫時將它們放在錨定儲存格和目前儲存格之間, 則可能會變成未選取。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設定為`true` , 而且<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, 則按下 SHIFT 時, 按一下資料列或資料行標頭 (視選取模式而定), 會修改現有的完整資料列或資料行選取範圍 (如果有的話)選取範圍存在。 否則, 它會清除選取專案, 並開始新的完整資料列或資料行選取專案。 不過, 按下 CTRL 鍵時, 按一下資料列或資料行標頭, 將會從目前的選取範圍加入或移除按一下的資料列或資料行, 而不需要修改目前的選取專案。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>設定為`true` , 且<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>設定為<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>或<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, 則按下 SHIFT 或 CTRL 鍵時, 按一下資料格的行為方式相同, 不同之處在于只會影響完整的資料列和資料行。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView 控制項](datagridview-control-windows-forms.md)
