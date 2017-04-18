---
title: "DataGrid 控制項中的預設鍵盤和滑鼠行為 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataGrid [WPF], 鍵盤行為"
  - "DataGrid [WPF], 滑鼠行為"
  - "鍵盤行為 [WPF], DataGrid"
  - "滑鼠行為 [WPF], DataGrid"
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# DataGrid 控制項中的預設鍵盤和滑鼠行為
本主題在說明使用者如何透過鍵盤和滑鼠與 <xref:System.Windows.Controls.DataGrid> 控制項互動。  
  
 與 <xref:System.Windows.Controls.DataGrid> 的一般互動包括巡覽、選取和編輯。  選取行為受 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 和 <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> 屬性影響。  本主題描述的行為導致的預設值是<xref:System.Windows.Controls.DataGridSelectionMode?displayProperty=fullName>和<xref:System.Windows.Controls.DataGridSelectionUnit?displayProperty=fullName>.  變更這些值可能導致與所述行為不同的行為。  當儲存格處於編輯模式時，編輯控制項可能會覆寫 <xref:System.Windows.Controls.DataGrid> 的標準鍵盤行為。  
  
## 預設鍵盤行為  
 下表列出 <xref:System.Windows.Controls.DataGrid> 的預設鍵盤行為。  
  
|按鍵或組合鍵|描述|  
|------------|--------|  
|向下鍵|移動焦點至緊接在目前儲存格下方的儲存格。  如果焦點位在最後一個資料列中，向下鍵將不會有任何作用。|  
|向上鍵|移動焦點至緊接在目前儲存格上方的儲存格。  如果焦點位在第一個資料列中，向上鍵將不會有任何作用。|  
|向左鍵|移動焦點至資料列中的前一個儲存格。  如果焦點位在資料列的第一個儲存格中，按向左鍵將不會有任何作用。|  
|向右鍵|移動焦點至資料列中的下一個儲存格。  如果焦點位在資料列的最後一個儲存格中，按向右鍵將不會有任何作用。|  
|HOME|移動焦點至目前資料列中的第一個儲存格。|  
|END|移動焦點至目前資料列中的最後一個儲存格。|  
|PAGE DOWN|如果未群組列，以目前完整顯示的資料列數目為一個單位，將控制項向下捲動。  移動焦點至最後一個完整顯示的資料列，且不會變更資料行。<br /><br /> 如果群組列，可以將焦點移到 <xref:System.Windows.Controls.DataGrid> 中的最後一列而不變更欄位。|  
|PAGE UP|如果未群組列，以目前完整顯示的資料列數目為一個單位，將控制項向上捲動。  移動焦點至第一個顯示的資料列，且不會變更資料行。<br /><br /> 如果群組列，可以將焦點移到 <xref:System.Windows.Controls.DataGrid> 中的第一列而不變更欄位。|  
|TAB|移動焦點至目前資料列中的下一個儲存格。  如果焦點在資料列中的最後一個儲存格，則會將焦點移動至下一筆資料列的第一個儲存格。  如果焦點已在控制項中的最後一個儲存格，則依照父容器的定位順序，將焦點移動到下一個控制項。<br /><br /> 如果目前的儲存格處於編輯模式並按下 TAB 鍵，會導致焦點離開目前的列，對於該列所進行的任何變更會在焦點變更之前認可。|  
|SHIFT\+TAB|移動焦點至目前資料列中的上一個儲存格。  如果焦點已在資料列中的第一個儲存格，則移動焦點至前一個資料列的最後一個儲存格。  如果焦點已在控制項中的第一個儲存格，則依照父容器的定位順序，將焦點移動至前一個控制項。<br /><br /> 如果目前的儲存格處於編輯模式並按下 TAB 鍵，會導致焦點離開目前的列，對於該列所進行的任何變更會在焦點變更之前認可。|  
|CTRL\+ 向下鍵|移動焦點至目前資料行中的最後一個儲存格。|  
|CTRL\+ 向上鍵|移動焦點至目前資料行中的第一個儲存格。|  
|CTRL\+向右鍵|移動焦點至目前資料列中的最後一個儲存格。|  
|CTRL\+向左鍵|移動焦點至目前資料列中的第一個儲存格。|  
|CTRL\+HOME|移動焦點至控制項中的第一個儲存格。|  
|CTRL\+END|移動焦點至控制項中的最後一個儲存格。|  
|CTRL\+PAGE DOWN|同 PAGE DOWN。|  
|CTRL\+PAGE UP|同 PAGE UP。|  
|F2|如果 <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=fullName> 屬性為 `false` 且目前資料行的 <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=fullName> 屬性為 `false`，則目前儲存格會進入儲存格編輯模式。|  
|ENTER|認可目前儲存格和資料列的變更，並且移動焦點至緊接在目前儲存格下方的儲存格。  如果焦點已在最後一個資料列，將會認可所有變更，但不移動焦點。|  
|ESC|如果控制項處於編輯模式，則會取消編輯模式並還原在控制項內所做的任何變更。  如果基礎資料來源實作 <xref:System.ComponentModel.IEditableObject>，再次按 ESC 會取消整個資料列的編輯模式。|  
|退格鍵|會於編輯儲存格時，刪除游標前面的字元。|  
|DELETE|會於編輯儲存格時，刪除游標後面的字元。|  
|CTRL\+ENTER|認可目前儲存格的所有變更，但不移動焦點。|  
|CTRL\+A|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>設為<xref:System.Windows.Controls.DataGridSelectionMode>，請選取 <xref:System.Windows.Controls.DataGrid> 中的所有列。|  
  
## 選取鍵  
 如果 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 屬性設為 <xref:System.Windows.Controls.DataGridSelectionMode>，則巡覽行為將維持不變，但是當按下 SHIFT 鍵 \(包括 CTRL\+SHIFT 鍵\) 時使用鍵盤巡覽，將會更改包含多個資料列的選取範圍。  在開始巡覽之前，控制項會將目前資料列標記為錨定資料列。  按住 SHIFT 鍵同時巡覽，選取範圍會包含所有介於錨定資料列和目前資料列間的資料列。  
  
 下列選取鍵會更改包含多個資料列的選取範圍。  
  
-   SHIFT\+向下鍵  
  
-   SHIFT\+向上鍵  
  
-   SHIFT\+PAGE DOWN  
  
-   SHIFT\+PAGE UP  
  
-   CTRL\+SHIFT\+向下鍵  
  
-   CTRL\+SHIFT\+向上鍵  
  
-   CTRL\+SHIFT\+HOME  
  
-   CTRL\+SHIFT\+END  
  
## 預設滑鼠行為。  
 下表列出 <xref:System.Windows.Controls.DataGrid> 的預設滑鼠行為。  
  
|滑鼠動作|描述|  
|----------|--------|  
|按一下未選取的資料列|使按下的列成為目前的列，並且使按下的儲存格成為目前的儲存格。|  
|按一下目前的儲存格|將目前儲存格置於編輯模式下。|  
|拖曳資料行行首儲存格|如果目前資料行的 <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=fullName> 屬性為 `true` 且 <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=fullName> 屬性為 `true`，會移動資料行以便放在新位置。|  
|拖曳資料行行首分隔符號|如果目前資料行的 <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName> 屬性為 `true` 且 <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName> 屬性為 `true`，會調整資料行大小。|  
|按兩下欄標題分隔符號|如果<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName>屬性是`true`而目前欄位的<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName>屬性是`true`，使用<xref:System.Windows.Controls.DataGridLength.Auto%2A>調整大小模式自動調整欄位的大小。|  
|按一下資料行行首儲存格|如果目前資料行的 <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=fullName> 屬性為 `true` 且 <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=fullName> 屬性為 `true`，會排序資料行。<br /><br /> 按一下已排序的資料行，該資料行中的資料會還原成排序作業前的順序。<br /><br /> 按住 SHIFT 鍵並按一下多個資料行行首，這些資料行會依滑鼠按下的順序進行排序。|  
|按住 CTRL 鍵並按一下資料列|如果 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 設為 <xref:System.Windows.Controls.DataGridSelectionMode>，則會更改包含多個不連續資料列的選取範圍。<br /><br /> 如果資料列已選取，則會取消選取該資料列。|  
|按住 SHIFT 鍵並按一下資料列|如果 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 設為 <xref:System.Windows.Controls.DataGridSelectionMode>，則會更改包含多個連續資料列的選取範圍。|  
|按一下資料列群組標題|展開或摺疊群組。|  
|按一下 <xref:System.Windows.Controls.DataGrid> 左上角的 \[全選\] 按鈕|如果<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>設為<xref:System.Windows.Controls.DataGridSelectionMode>，請選取 <xref:System.Windows.Controls.DataGrid> 中的所有列。|  
  
## 滑鼠選取  
 如果 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> 設為 <xref:System.Windows.Controls.DataGridSelectionMode>，在按住 CTRL 或 SHIFT 鍵時按一下儲存格，將會更改包含多個資料列的選取範圍。  
  
 如果在按住 CTRL 鍵時按一下資料列，該資料列的選取狀態將會變更，而其他所有資料列則會保留原來的選取狀態。  請執行此操作以選取不相鄰的列。  
  
 如果在按住 SHIFT 鍵時按一下資料列，選取範圍會包括所有介於目前資料列和錨定資料列間的資料列，以及在按一下滑鼠前位於目前資料列位置的錨定資料列。  之後，再按住 SHIFT 鍵按一下儲存格，則變更的是目前資料列，而非錨定資料列。  請執行此操作以選取相鄰的列。  
  
 可以結合 CTRL \+ SHIFT 以選取非相鄰的相鄰列範圍。  若要這樣做，請使用 SHIFT\+按一下選取第一個範圍，如前所述。  選取第一個範圍的列之後，使用 CTRL \+ 按一下以選取下一個範圍中的第一列，然後按下一個範圍中的最後一列，同時按下 CTRL \+ SHIFT。  
  
## 請參閱  
 <xref:System.Windows.Controls.DataGrid>   
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>