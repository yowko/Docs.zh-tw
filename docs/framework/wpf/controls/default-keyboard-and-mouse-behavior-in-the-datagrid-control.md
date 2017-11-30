---
title: "DataGrid 控制項中的預設鍵盤和滑鼠行為"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddbbab88a22a4350626a36f79236aab67da24a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>DataGrid 控制項中的預設鍵盤和滑鼠行為
本主題描述使用者可以互動<xref:System.Windows.Controls.DataGrid>使用鍵盤和滑鼠控制。  
  
 典型的互動<xref:System.Windows.Controls.DataGrid>包括瀏覽、 選取和編輯。 選取行為會受到<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>和<xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>屬性。 造成本主題中描述的行為的預設值是<xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType>和<xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>。 變更這些值可能會導致不同於所描述的行為。 編輯控制項時的儲存格位於編輯模式時，可能會覆寫的標準鍵盤行為<xref:System.Windows.Controls.DataGrid>。  
  
## <a name="default-keyboard-behavior"></a>預設鍵盤行為  
 下表列出的預設鍵盤行為<xref:System.Windows.Controls.DataGrid>。  
  
|按鍵或按鍵組合|描述|  
|----------------------------|-----------------|  
|向下鍵|將焦點移至目前的資料格正下方的儲存格。 如果焦點是在最後一個資料列中，向下鍵沒有任何作用。|  
|向上鍵|將焦點移至上方的目前儲存格。 如果焦點是在第一個資料列中，按向上鍵沒有任何作用。|  
|向左鍵|將焦點移至先前的資料格的資料列中。 如果焦點是第一個資料格中的資料列中，按向左鍵並無關聯。|  
|向右鍵|將焦點移至下一個儲存格的資料列中。 如果焦點位於資料列中最後一個資料格，按向右箭號並無關聯。|  
|首頁|將焦點移至目前的資料列中的第一個儲存格。|  
|END|將焦點移至目前的資料列中的最後一個儲存格。|  
|PAGE DOWN|若未分組的資料列，將控制項向下捲動充分顯示之資料列數目。 將焦點移至最後一個完整顯示的資料列中，而不需要變更資料行。<br /><br /> 如果資料列分組，將焦點移至的最後一個資料列<xref:System.Windows.Controls.DataGrid>而不需要變更資料行。|  
|PAGE UP|如果資料列不分組，控制單位向上捲動充分顯示之資料列數目。 將焦點移到第一個顯示的資料列，而不需要變更資料行。<br /><br /> 如果資料列分組，將焦點移至的第一個資料列<xref:System.Windows.Controls.DataGrid>而不需要變更資料行。|  
|TAB|將焦點移至目前資料列中的下一個儲存格。 如果焦點位於資料列的最後一個資料格，將焦點移到下一個資料列的第一個儲存格。 如果焦點在控制項中的最後一個資料格，將焦點移至定位順序的父容器中的下一個控制項。<br /><br /> 如果目前儲存格處於編輯模式，並且按下索引標籤的原因焦點移離目前的資料列，資料列所做的任何變更認可之前變更焦點。|  
|SHIFT+TAB|將焦點移到目前資料列的上一個儲存格。 如果焦點位於資料列的第一個資料格，將焦點移至前一個資料列中的最後一個儲存格。 如果焦點在控制項中第一個資料格中，將焦點移至上一個控制項的父容器的定位順序。<br /><br /> 如果目前儲存格處於編輯模式，並且按下索引標籤的原因焦點移離目前的資料列，資料列所做的任何變更認可之前變更焦點。|  
|CTRL+向下鍵|將焦點移至目前的資料行中的最後一個資料格。|  
|CTRL+向上鍵|將焦點移至目前的資料行中的第一個儲存格。|  
|CTRL+向右鍵|將焦點移至目前的資料列中的最後一個儲存格。|  
|CTRL+向左鍵|將焦點移至目前的資料列中的第一個儲存格。|  
|CTRL + HOME|將焦點移至控制項中的第一個資料格。|  
|CTRL + END|將焦點移至控制項中的最後一個資料格。|  
|CTRL+PAGE DOWN|與 PAGE DOWN 相同。|  
|CTRL+PAGE UP|PAGE UP 相同。|  
|F2|如果<xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType>屬性是`false`和<xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType>屬性是`false`針對目前的資料行，放入目前的儲存格的儲存格的編輯模式。|  
|ENTER|認可目前儲存格和資料列的任何變更，並將焦點移至目前的資料格正下方的儲存格。 如果焦點是在最後一個資料列中，認可所有變更，而不移動焦點。|  
|ESC|如果控制項處於編輯模式，取消編輯，並還原控制項中所做的任何變更。 如果基礎資料來源實作<xref:System.ComponentModel.IEditableObject>，第二次按下 esc 鍵取消編輯模式，整個資料列。|  
|退格鍵|編輯儲存格時，則刪除游標前的字元。|  
|DELETE|刪除游標後的字元，當編輯儲存格。|  
|CTRL+ENTER|認可目前儲存格的任何變更，而不移動焦點。|  
|CTRL+A|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>設<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，會選取所有資料列中的<xref:System.Windows.Controls.DataGrid>。|  
  
## <a name="selection-keys"></a>選取按鍵  
 如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>屬性設定為<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、 導覽行為不會變更，但以鍵盤巡覽時按住 shift 鍵 （包括 CTRL + SHIFT） 會修改多個資料列選取項目。 導覽開始前，控制會將目前的資料列標示為錨定資料列中。 當您巡覽時按住 shift 鍵時，則選取範圍包含錨定的資料列和目前資料列之間的所有資料列。  
  
 下列選取按鍵修改多重資料列選取項目。  
  
-   SHIFT+向下鍵  
  
-   SHIFT+向上鍵  
  
-   SHIFT+PAGE DOWN  
  
-   SHIFT+PAGE UP  
  
-   CTRL+SHIFT+向下鍵  
  
-   CTRL+SHIFT+向上鍵  
  
-   CTRL + SHIFT + HOME  
  
-   CTRL + SHIFT + END  
  
## <a name="default-mouse-behavior"></a>預設滑鼠行為。  
 下表列出的預設滑鼠行為<xref:System.Windows.Controls.DataGrid>。  
  
|滑鼠動作|說明|  
|------------------|-----------------|  
|按一下未選取的資料列|目前的資料列，並按下儲存格的目前儲存格，可按的資料列。|  
|按一下目前的資料格|目前的儲存格置於編輯模式。|  
|拖曳資料行的標頭資料格|如果<xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType>屬性是`true`和<xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType>屬性是`true`針對目前的資料行，將資料行移動，讓它可以放入新的位置。|  
|拖曳資料行的標頭分隔符號|如果<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>屬性是`true`和<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>屬性是`true`目前的資料行中，調整大小之資料行。|  
|按兩下資料行行首分隔符號|如果<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>屬性是`true`和<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>屬性是`true`目前的資料行自動大小的資料行使用<xref:System.Windows.Controls.DataGridLength.Auto%2A>調整大小模式。|  
|按一下欄標頭資料格|如果<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType>屬性是`true`和<xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType>屬性是`true`目前的資料行來排序資料行。<br /><br /> 按一下已排序的資料行的標頭會回復該資料行的排序方向。<br /><br /> 按一下多個資料行標頭將多個資料欄來排序按下的順序時，請按 SHIFT 鍵。|  
|CTRL + 按一下的資料列|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>設<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，修改非連續的多重資料列選取。<br /><br /> 如果已選取的資料列，會取消選取資料列。|  
|SHIFT + 按一下的資料列|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>設<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，修改非連續的多重資料列選取範圍。|  
|按一下資料列群組標頭|展開或摺疊群組。|  
|按一下左上角的 [全選] 按鈕<xref:System.Windows.Controls.DataGrid>|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>設<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，會選取所有資料列中的<xref:System.Windows.Controls.DataGrid>。|  
  
## <a name="mouse-selection"></a>滑鼠選取範圍  
 如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>屬性設定為<xref:System.Windows.Controls.DataGridSelectionMode.Extended>，按一下資料列時按住 CTRL 或 shift 鍵，將會修改多資料列選取範圍。  
  
 當您按一下資料列時按住 ctrl 鍵時，資料列會變更選取狀態，而其他所有資料列會保留其目前的選取狀態。 這樣做來選取非相鄰的資料列。  
  
 當您按住 shift 鍵同時按一下資料列時，選取範圍包含目前資料列與之前按一下目前的資料列的位置上的錨定資料列之間的所有資料列。 後續的點選，按住 shift 鍵同時變更目前的資料列，但不是錨定的資料列。 這樣做可以選取某個範圍的相鄰的資料列。  
  
 CTRL + shift 鍵可以結合以選取非相鄰的範圍內的相鄰的資料列。 若要這樣做，請選取第一個範圍，使用 SHIFT + 滑鼠左鍵如先前所述。 選取的資料列的第一個範圍後，使用 CTRL + 按一下以在下一個範圍中，選取第一個資料列，然後按一下下一個範圍中的最後一個資料列時按住 CTRL + SHIFT。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
