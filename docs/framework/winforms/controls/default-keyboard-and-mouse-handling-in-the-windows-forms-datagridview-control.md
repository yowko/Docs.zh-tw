---
title: "Windows Form DataGridView 控制項中的預設鍵盤和滑鼠處理 | Microsoft Docs"
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
  - "資料格, 滑鼠處理"
  - "DataGridView 控制項 [Windows Form], 鍵盤處理"
  - "DataGridView 控制項 [Windows Form], 滑鼠處理"
  - "DataGridView 控制項 [Windows Form], 巡覽鍵"
  - "鍵盤, DataGridView 控制項中的預設處理"
  - "滑鼠, DataGridView 控制項中的預設處理"
  - "巡覽鍵, DataGridView 控制項"
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Windows Form DataGridView 控制項中的預設鍵盤和滑鼠處理
下表描述使用者如何透過鍵盤和滑鼠與 <xref:System.Windows.Forms.DataGridView> 控制項互動。  
  
> [!NOTE]
>  若要自訂鍵盤行為，您可以處理標準鍵盤事件 \(例如：<xref:System.Windows.Forms.Control.KeyDown>\)。  但是，在編輯模式中，裝載的編輯控制項會接收鍵盤輸入，而且 <xref:System.Windows.Forms.DataGridView> 控制項不會發生鍵盤事件。  若要處理編輯控制項事件，請將您的處理常式附加至 <xref:System.Windows.Forms.DataGridView.EditingControlShowing> 事件處理常式中的編輯控制項。  或者，您可以透過覆寫 <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> 和 <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> 方法，以自訂 <xref:System.Windows.Forms.DataGridView> 子類別中的鍵盤行為。  
  
## 預設鍵盤處理  
  
### 基本的巡覽按鍵和輸入按鍵  
  
|按鍵或組合鍵|描述|  
|------------|--------|  
|向下鍵|移動焦點至緊接在目前儲存格下方的儲存格。  如果焦點已在最後一筆資料列，將不會有任何作用。|  
|向左鍵|移動焦點至資料列中的前一個儲存格。  如果焦點已在資料列中的第一個儲存格，將不會有任何作用。|  
|向右鍵|移動焦點至資料列中的下一個儲存格。  如果焦點已在資料列中的最後一個儲存格，將不會有任何作用。|  
|向上鍵|移動焦點至緊接在目前儲存格上方的儲存格。  如果焦點已在第一筆資料列，將不會有任何作用。|  
|HOME|移動焦點至目前資料列中的第一個儲存格。|  
|END|移動焦點至目前資料列中的最後一個儲存格。|  
|PAGE DOWN|以目前完整顯示的資料列數目為一個單位，將控制項向下捲動。  移動焦點至最後一個完整顯示的資料列，且不會變更資料行。|  
|PAGE UP|以目前完整顯示的資料列數目為一個單位，將控制項向上捲動。   移動焦點至第一個顯示的資料列，且不會變更資料行。|  
|TAB|如果 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 屬性值為 `false`，TAB 鍵會將焦點移動到目前資料列中的下一個儲存格。  如果焦點已在資料列中的最後一個儲存格，則會將焦點移動至下一筆資料列的第一個儲存格。  如果焦點已在控制項中的最後一個儲存格，則依照父容器的定位順序，將焦點移動到下一個控制項。<br /><br /> 如果 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 屬性值為 `true`，則那麼會以父容器的定位順序，將焦點移動到下一個控制項。|  
|SHIFT\+TAB|如果 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 屬性值為 `false`，則移動焦點至目前資料列中的前一個儲存格。  如果焦點已在資料列中的第一個儲存格，則移動焦點至前一個資料列的最後一個儲存格。  如果焦點已在控制項中的第一個儲存格，則依照父容器的定位順序，將焦點移動至前一個控制項。<br /><br /> 如果 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 屬性值為 `true`，則依照父容器的定位順序移動焦點至前一個控制項。|  
|CTRL\+TAB|如果 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 屬性值為 `false`，則那麼會以父容器的定位順序，將焦點移動到下一個控制項。<br /><br /> 如果 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 屬性值為 `true`，TAB 鍵會將焦點移動到目前資料列中的下一個儲存格。  如果焦點已在資料列中的最後一個儲存格，則會將焦點移動至下一筆資料列的第一個儲存格。  如果焦點已在控制項中的最後一個儲存格，則依照父容器的定位順序，將焦點移動到下一個控制項。|  
|CTRL\+SHIFT\+TAB|如果 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 屬性值為 `false`，則依照父容器的定位順序移動焦點至前一個控制項。<br /><br /> 如果 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> 屬性值為 `true`，則移動焦點至目前資料列中的前一個儲存格。  如果焦點已在資料列中的第一個儲存格，則移動焦點至前一個資料列的最後一個儲存格。  如果焦點已在控制項中的第一個儲存格，則依照父容器的定位順序，將焦點移動至前一個控制項。|  
|CTRL\+ARROW|依箭號方向移動焦點至最遠的儲存格。|  
|CTRL\+HOME|移動焦點至控制項中的第一個儲存格。|  
|CTRL\+END|移動焦點至控制項中的最後一個儲存格。|  
|CTRL\+PAGE DOWN\/UP|與 PAGE DOWN 或 PAGE UP 的作用相同。|  
|F2|如果 <xref:System.Windows.Forms.DataGridView.EditMode%2A> 屬性值為 <xref:System.Windows.Forms.DataGridViewEditMode> 或 <xref:System.Windows.Forms.DataGridViewEditMode>，可以讓目前儲存格進入儲存格編輯模式。|  
|F4|如果目前儲存格是 <xref:System.Windows.Forms.DataGridViewComboBoxCell>，可以讓目前儲存格進入儲存格編輯模式並且顯示下拉式清單。|  
|ALT\+ 向上\/向下鍵|如果目前儲存格是 <xref:System.Windows.Forms.DataGridViewComboBoxCell>，可以讓目前儲存格進入儲存格編輯模式並且顯示下拉式清單。|  
|空格鍵|如果目前儲存格是 <xref:System.Windows.Forms.DataGridViewButtonCell>、<xref:System.Windows.Forms.DataGridViewLinkCell> 或 <xref:System.Windows.Forms.DataGridViewCheckBoxCell>，將會引發 <xref:System.Windows.Forms.DataGridView.CellClick> 和 <xref:System.Windows.Forms.DataGridView.CellContentClick> 事件。  如果目前儲存格是 <xref:System.Windows.Forms.DataGridViewButtonCell>，將同時也會按下按鈕。  如果目前儲存格是 <xref:System.Windows.Forms.DataGridViewCheckBoxCell>，將同時也會變更核取狀態。|  
|ENTER|認可目前儲存格和資料列的變更，並且移動焦點至緊接在目前儲存格下方的儲存格。  如果焦點已在最後一個資料列，將會認可所有變更，但不移動焦點。|  
|ESC|如果控制項處於編輯模式，將會取消編輯。  如果控制項不在編輯模式中，則若控制項已繫結至支援編輯的資料來源，或者虛擬模式已使用資料列層級的認可範圍進行實作的話，請還原已對目前資料列進行的任何變更。|  
|退格鍵|會於編輯儲存格時，刪除插入點前的字元。|  
|DELETE|在編輯儲存格時，刪除插入點後的字元。|  
|CTRL\+ENTER|認可目前儲存格的所有變更，但不移動焦點。  如果控制項已繫結至支援編輯的資料來源，或者虛擬模式已使用資料列層級的認可範圍，請同時認可對目前資料列的任何變更。|  
|CTRL\+0|如果可以編輯目前的儲存格，會在儲存格內輸入 <xref:System.DBNull.Value?displayProperty=fullName> 值。  根據預設，<xref:System.DBNull> 儲存格值的顯示值，其實就是目前儲存格之 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 屬性值。|  
  
### 選取鍵  
 如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 屬性設為 `false` 且 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性設為 <xref:System.Windows.Forms.DataGridViewSelectionMode>，則使用巡覽鍵變更目前儲存格時，選取範圍會同時變更為新儲存格。  SHIFT、CTRL 和 ALT 鍵將無法影響此一行為。  
  
 如果 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 設為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode>，則會發生以上相同的行為，但是會附帶下列項目。  
  
|按鍵或組合鍵|描述|  
|------------|--------|  
|SHIFT\+ 空格鍵|選取整個資料列或資料行 \(等同於按一下資料列行首或資料行行首\)。|  
|巡覽鍵 \(方向鍵、PAGE UP\/DOWN、HOME、END\)|如果整個資料列或資料行已選取，則變更目前儲存格為新資料列或新資料行時，選取範圍會同時變更為整個新資料列或新資料行 \(須視選取模式而定\)。|  
  
 如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 設為 `false` 且 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 設為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode>，則使用鍵盤將目前儲存格變更為新資料列或新資料行時，選取範圍會同時變更為整個新資料列或新資料行。  SHIFT、CTRL 和 ALT 鍵將無法影響此一行為。  
  
 如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 設為 `true`，巡覽行為將維持不變，但是當按下 SHIFT 鍵 \(包括 CTRL\+SHIFT 鍵\) 時使用鍵盤巡覽，將會修改多重儲存格的選取範圍。  在開始巡覽之前，控制項會將目前儲存格標示為錨定 \(Anchor\) 儲存格。  在按下 SHIFT 鍵時同時巡覽，選取範圍會包含所有在錨定儲存格和目前儲存格之間的儲存格。  控制項中之前已選取的其餘儲存格將會維持已選取狀態，但是如果鍵盤巡覽將這些儲存格暫時置於錨定儲存格和目前儲存格之間，則它們可能會改為未選取狀態。  
  
 如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 設為 `true` 且 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 設為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode>，錨定儲存格和目前儲存格兩者的行為相同，這時只有整個資料列或整個資料行會改為已選取或未選取。  
  
## 預設滑鼠處理  
  
### 基本的滑鼠處理  
  
> [!NOTE]
>  以滑鼠左鍵按一下儲存格時，一律會變更目前的儲存格。  以滑鼠右鍵按一下儲存格時，會開啟捷徑功能表 \(如果有的話\)。  
  
|滑鼠動作|描述|  
|----------|--------|  
|按下滑鼠左鍵|使按下的儲存格成為目前的儲存格，並且引發 <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=fullName> 事件。|  
|鬆開滑鼠左鍵|引發 <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=fullName> 事件。|  
|按一下滑鼠左鍵|引發 <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> 和 <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=fullName> 事件|  
|在資料行標題儲存格上按下滑鼠左鍵並拖曳|如果 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=fullName> 屬性為 `true`，可以移動資料行以置入新位置。|  
  
### 滑鼠選取  
 滑鼠中間鍵或滑鼠滾輪都無法進行選取的動作。  
  
 如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 屬性設為 `false` 且 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 屬性設為 <xref:System.Windows.Forms.DataGridViewSelectionMode>，則會發生以下行為：  
  
|滑鼠動作|描述|  
|----------|--------|  
|按一下滑鼠左鍵|使用者按一下儲存格，只會選取目前的儲存格。  如果是按一下資料列行首或資料行行首，則不會有選取行為。|  
|按一下滑鼠右鍵|顯示捷徑功能表 \(如果有的話\)。|  
  
 當 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 設為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode> 時也會產生相同的行為，但不同的是會根據當時的選取模式，於按一下資料列行首或資料行行首時選取整個資料列或資料行，並且將目前儲存格設為資料列或資料行的第一個儲存格。  
  
 如果 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 設為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode>，只要按一下資料列或資料行中的任何儲存格即可選取整個資料列或資料行。  
  
 如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 設為 `true`，在按住 CTRL 或 SHIFT 鍵時同時按一下儲存格，將會修改多重儲存格的選取範圍。  
  
 如果在按住 CTRL 鍵時按一下儲存格，該儲存格的選取狀態將會變更，而其他所有儲存格則是保留原來的選取狀態。  
  
 如果在按住 SHIFT 鍵時同時按一下某個儲存格或連續好幾個儲存格，選取範圍會包括所有介於目前儲存格和錨定儲存格 \(位於第一次點選之前的目前儲存格位置\) 之間的儲存格。  當您按一下儲存格並拖曳指標橫跨多個儲存格時，錨定儲存格則是拖曳作業開始時所點選的儲存格。  接著按住 SHIFT 鍵且同時再按一下儲存格，則變更的是目前的儲存格，而非錨定儲存格。  控制項中之前已選取的其餘儲存格將會維持已選取狀態，但是如果滑鼠巡覽將這些儲存格暫時置於錨定儲存格和目前儲存格之間，則它們有可能改為未選取狀態。  
  
 如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 設為 `true` 且 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 設為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode>，按住 SHIFT 鍵再按一下資料列行首或資料行行首 \(視選取模式而定\)，將會修改目前整個資料列或資料行的選取範圍 \(如果有該選取範圍\)。  否則，它會清除選取範圍而且新的選取範圍將以整個資料列或資料行為基本單位。  不過，在按住 CTRL 鍵時同時按一下資料列行首或資料行行首，則將會從目前的選取範圍加入或移除所按的資料列或資料行，而不是修改目前的選取範圍。  
  
 如果 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 設為 `true` 且 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 設為 <xref:System.Windows.Forms.DataGridViewSelectionMode> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode>，在按住 SHIFT 或 CTRL 鍵時同時按一下儲存格，將會產生相同的行為，其中唯一的不同之處是其影響的對象為整個資料列以及整個資料行。  
  
## 請參閱  
 <xref:System.Windows.Forms.DataGridView>   
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)