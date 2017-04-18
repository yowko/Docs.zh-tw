---
title: "ToolStrip 控制項架構 | Microsoft Docs"
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
  - "ToolStrip 控制項 [Windows Forms], 架構"
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# ToolStrip 控制項架構
<xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.ToolStripItem> 類別提供具彈性、可擴充的系統以顯示工具列、狀態和功能表項目。  這些類別全部包含於 <xref:System.Windows.Forms> 命名空間之內，而且通常以 "ToolStrip" 前置字元 \(例如 <xref:System.Windows.Forms.ToolStripOverflow>\)或 "Strip" 後置字元 \(例如 <xref:System.Windows.Forms.MenuStrip>\) 來命名。  
  
## ToolStrip  
 下列主題將說明 <xref:System.Windows.Forms.ToolStrip> 和其所衍生的控制項。  
  
 <xref:System.Windows.Forms.ToolStrip> 是 <xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.StatusStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 的抽象基底類別。  下列物件模型將說明 <xref:System.Windows.Forms.ToolStrip> 繼承階層架構 \(Inheritance Hierarchy\)。  
  
 ![ToolStrip 物件模型](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.png "ToolStripObjectModel")  
ToolStrip 物件模型  
  
 您可以透過 <xref:System.Windows.Forms.ToolStrip.Items%2A> 集合存取 <xref:System.Windows.Forms.ToolStrip> 中的所有項目。  您可以透過 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> 集合存取 <xref:System.Windows.Forms.ToolStripDropDownItem> 中的所有項目。  在衍生自 <xref:System.Windows.Forms.ToolStrip> 的類別中，您也可以使用 <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> 屬性僅存取目前顯示的項目。  這些就是目前不在溢位功能表中的項目。  
  
 下列項目是專門設計來緊密搭配所有方向的 <xref:System.Windows.Forms.ToolStripSystemRenderer> 和 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 使用。  根據預設，它們在設計階段可供 <xref:System.Windows.Forms.ToolStrip> 控制項使用：  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> 是取代 <xref:System.Windows.Forms.MainMenu> 的最上層容器。  此容器還會提供按鍵處理和多重文件介面 \(MDI\) 功能。  功能上來說，即使 <xref:System.Windows.Forms.ToolStripDropDownItem> 和 <xref:System.Windows.Forms.ToolStripMenuItem> 是衍生自 <xref:System.Windows.Forms.ToolStripItem>，仍會與 <xref:System.Windows.Forms.MenuStrip> 搭配使用。  
  
 下列項目是專門設計來緊密搭配所有方向的 <xref:System.Windows.Forms.ToolStripSystemRenderer> 和 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 使用。  根據預設，它們在設計階段可供 <xref:System.Windows.Forms.MenuStrip> 控制項使用：  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> 用以取代 <xref:System.Windows.Forms.StatusBar> 控制項。  <xref:System.Windows.Forms.StatusStrip> 的特殊功能包括自訂資料表配置、表單縮放與移動底框，以及允許 <xref:System.Windows.Forms.ToolStripStatusLabel> 自動填滿可用空間的 `Spring` 屬性。  
  
 下列項目是專門設計來緊密搭配所有方向的 <xref:System.Windows.Forms.ToolStripSystemRenderer> 和 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 使用。  根據預設，它們在設計階段可供 <xref:System.Windows.Forms.StatusStrip> 控制項使用：  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> 會取代 <xref:System.Windows.Forms.ContextMenu>。  您可以使 <xref:System.Windows.Forms.ContextMenuStrip> 與任何控制項產生關聯，而且按一下滑鼠右鍵便會自動顯示內容功能表 \(或捷徑功能表\)。  您可以使用 <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> 方法，以程式設計的方式顯示 <xref:System.Windows.Forms.ContextMenuStrip>。  <xref:System.Windows.Forms.ContextMenuStrip> 支援可以取消的 <xref:System.Windows.Forms.ToolStripDropDown.Opening> 和 <xref:System.Windows.Forms.ToolStripDropDown.Closing> 事件，以處理動態擴展及按下多次的案例。  <xref:System.Windows.Forms.ContextMenuStrip> 支援影像、功能表項目核取狀態、文字、便捷鍵 \(Access Key\)、快速鍵和串聯功能表。  
  
 下列項目是專門設計來緊密搭配所有方向的 <xref:System.Windows.Forms.ToolStripSystemRenderer> 和 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 使用。  根據預設，它們在設計階段可供 <xref:System.Windows.Forms.ContextMenuStrip> 控制項使用：  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### ToolStrip 的一般功能  
 下列主題將說明 <xref:System.Windows.Forms.ToolStrip> 及衍生之控制項的一般功能和行為。  
  
#### 繪製  
 您可以使用數種方法在 <xref:System.Windows.Forms.ToolStrip> 控制項中自訂繪製。  如同使用其他 Windows Form 控制項，<xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.ToolStripItem> 皆具有可覆寫的 `OnPaint` 方法和 `Paint` 事件。  而就如同一般繪製，座標系統會相對於控制項的工作區，也就是說，控制項的左上角為 0, 0。  <xref:System.Windows.Forms.ToolStripItem> 的 `Paint` 事件和 `OnPaint` 方法的行為會與其他控制項繪製事件一樣。  
  
 <xref:System.Windows.Forms.ToolStrip> 控制項可以經由 <xref:System.Windows.Forms.ToolStripRenderer> 類別，針對項目和容器之呈現，提供更細微的存取方式。該類別具有可覆寫的方法，以繪製 <xref:System.Windows.Forms.ToolStrip> 的背景 \(Background\)、項目背景、項目影像、項目箭號、項目文字和邊框。  這些方法的事件引數會公開 \(Expose\) 數個屬性，例如，可視需要調整的矩形、色彩和文字格式。  
  
 若只要調整少數幾個繪製項目的方法，通常只需覆寫 <xref:System.Windows.Forms.ToolStripRenderer> 即可。  
  
 如果您正撰寫新的項目而且想要控制繪製的所有部分，則覆寫 `OnPaint` 方法。  您可以從 `OnPaint` 內使用來自 <xref:System.Windows.Forms.ToolStripRenderer> 的方法。  
  
 根據預設，<xref:System.Windows.Forms.ToolStrip> 為雙重緩衝 \(利用 <xref:System.Windows.Forms.ControlStyles> 設定\)。  
  
#### 父代設定  
 在 <xref:System.Windows.Forms.ToolStrip> 控制項中之容器擁有權和父代設定的概念遠較在其他 Windows Forms 容器控制項中複雜。  對支援動態案例 \(例如：溢位\)、跨多個 <xref:System.Windows.Forms.ToolStrip> 項目共用下拉式項目，以及支援從控制項產生 <xref:System.Windows.Forms.ContextMenuStrip> 而言，這是必要的。  
  
 下列清單將說明父代設定的相關成員，並說明其使用方式。  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> 會存取下拉式項目的來源項目。  這與 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> 類似，但不會傳回控制項，而是傳回 <xref:System.Windows.Forms.ToolStripItem>。  
  
-   當多個控制項共用同一個 <xref:System.Windows.Forms.ContextMenuStrip> 時，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> 會判斷哪一個控制項是 <xref:System.Windows.Forms.ContextMenuStrip> 的來源。  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> 是 <xref:System.Windows.Forms.ToolStripItem.Parent%2A> 屬性的唯讀存取子 \(Accessor\)。  父代與擁有人的不同在於，父代表示傳回之目前顯示項目的 <xref:System.Windows.Forms.ToolStrip>，該項目可能位在溢位區域中。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A> 將傳回其 Items 集合包含目前 <xref:System.Windows.Forms.ToolStripItem> 的 <xref:System.Windows.Forms.ToolStrip>。  這是參考在最上層 <xref:System.Windows.Forms.ToolStrip> 中之 <xref:System.Windows.Forms.ToolStrip.ImageList%2A> 或其他屬性的最好方法，而不需要撰寫處理溢位的特殊程式碼。  
  
#### 繼承控制項的行為  
 每當在繼承中使用下列控制項時，便會被鎖定：  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>，其包含在 <xref:System.Windows.Forms.ToolStripContainer> 的面板和個別的 <xref:System.Windows.Forms.ToolStripPanel> 控制項中。  
  
 例如，使用在先前清單中的一或多個控制項，建立新的 Windows Forms 應用程式。  將一或多個控制項的存取修飾詞 \(Modifier\) 設定為 `public` 或 `protected`，然後建置專案。  加入繼承自第一個表單的表單，然後選取繼承的控制項。  該控制項會顯示已鎖定，而行為方式如同其存取修飾詞為 `private`。  
  
#### 繼承的 ToolStripContainer 支援  
 <xref:System.Windows.Forms.ToolStripContainer> 控制項支援有限制的繼承案例，類似於下列範例：  
  
1.  建立新的 Windows Form 應用程式。  
  
2.  將 <xref:System.Windows.Forms.ToolStripContainer> 加入表單中。  
  
3.  將 <xref:System.Windows.Forms.ToolStripContainer> 的存取修飾詞設定為 `public` 或 `protected`。  
  
4.  將 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 控制項的任何組合加入至 <xref:System.Windows.Forms.ToolStripContainer> 的 <xref:System.Windows.Forms.ToolStripPanel> 區域。  
  
5.  建置專案。  
  
6.  加入繼承自第一個表單的表單。  
  
7.  在表單上選取繼承的 <xref:System.Windows.Forms.ToolStripContainer>。  
  
#### 子控制項所繼承的行為  
 在完成先前的步驟之後，便會發生下列繼承的行為：  
  
-   在設計工具中，該控制項會以繼承的圖示顯示。  
  
-   <xref:System.Windows.Forms.ToolStripPanel> 控制項會被鎖定，因此您無法選取或重新整理其內容。  
  
-   您可以將控制項加入至 <xref:System.Windows.Forms.ToolStripContentPanel>、移動控制項及產生 <xref:System.Windows.Forms.ToolStripContentPanel> 的子控制項。  
  
-   在建置該表單之後，便會保存您的變更。  
  
    > [!NOTE]
    >  從所有屬於 <xref:System.Windows.Forms.ToolStripContainer> 的 <xref:System.Windows.Forms.ToolStripPanel> 控制項中，移除存取修飾詞。  <xref:System.Windows.Forms.ToolStripContainer> 的存取修飾詞將管理整個控制項。  
  
#### 部分信任  
 部分信任下的 `ToolStrip` 限制，是為了避免不會因為不慎輸入了個人資訊，而導致未經授權的人員或服務使用這些資訊。  預防措施如下：  
  
-   `ToolStripDropDown` 控制項需要 <xref:System.Security.Permissions.UIPermissionWindow>，才能在 <xref:System.Windows.Forms.ToolStripControlHost> 中顯示項目。  這項需求同時適用於內建控制項 \(例如：<xref:System.Windows.Forms.ToolStripTextBox>、<xref:System.Windows.Forms.ToolStripComboBox> 和 <xref:System.Windows.Forms.ToolStripProgressBar>\) 及使用者建立的控制項。  如果未符合這項需求，便不會顯示這些項目。  不會擲回例外狀況。  
  
-   不允許將 <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> 屬性設定為 `false`，並且忽略可取消的 <xref:System.Windows.Forms.ToolStripDropDown.Closing> 事件參數。  如此將造成無法在不關閉下拉式項目的情況下，輸入一個以上的按鍵。  如果未符合這項需求，便不會顯示這些項目。  不會擲回例外狀況。  
  
-   如果發生在部分信任的內容中，而非在 <xref:System.Security.Permissions.UIPermissionWindow> 中，許多按鍵處理事件將不會被引發。  
  
-   當未授與 <xref:System.Security.Permissions.UIPermissionWindow> 時，將不會處理便捷鍵。  
  
#### 使用方式  
 下列使用模式與 <xref:System.Windows.Forms.ToolStrip> 配置、鍵盤互動和使用者行為具有關聯性：  
  
-   已加入 <xref:System.Windows.Forms.ToolStripPanel> 中  
  
     <xref:System.Windows.Forms.ToolStrip> 的位置可以在 <xref:System.Windows.Forms.ToolStripPanel> 中或跨 <xref:System.Windows.Forms.ToolStripPanel> 重新調整。  `Dock` 屬性會被忽略，而且如果 <xref:System.Windows.Forms.ToolStrip.Stretch%2A> 屬性為 `false`，<xref:System.Windows.Forms.ToolStrip> 的大小會隨著將項目加入至 <xref:System.Windows.Forms.ToolStripPanel> 而擴充。  一般而言，<xref:System.Windows.Forms.ToolStrip> 不會加入定位順序。  
  
-   停駐  
  
     <xref:System.Windows.Forms.ToolStrip> 會放置於固定位置之容器的其中一側，而且其大小會展開以涵蓋整個所停駐的邊緣。  一般而言，<xref:System.Windows.Forms.ToolStrip> 不會加入定位順序。  
  
-   絕對位置  
  
     <xref:System.Windows.Forms.ToolStrip> 與其他透過 <xref:System.Windows.Forms.Control.Location%2A> 屬性放置的控制項類似，具有固定的大小，而且通常會加入定位順序。  
  
#### 鍵盤互動  
  
##### 便捷鍵  
 結合或跟隨 ALT 鍵，便捷鍵是一種使用鍵盤來啟動控制項的方式。  <xref:System.Windows.Forms.ToolStrip> 同時支援明確和隱含便捷鍵。  明確定義會在字母前使用連字號 \(&\) 字元。  隱含定義會使用演算法，嘗試根據所指定之 `Text` 屬性中的字元順序，尋找相符的項目。  
  
##### 快速鍵  
 <xref:System.Windows.Forms.MenuStrip> 所使用的快速鍵是使用無特定順序之 <xref:System.Windows.Forms.Keys> 列舉型別 \(Enumeration\) 的組合進行定義。  您也可以使用 <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> 屬性，僅以文字顯示快速鍵 \(例如：顯示 "Del" 而不顯示 "Delete"\)。  
  
##### 巡覽  
 ALT 鍵會啟動 <xref:System.Windows.Forms.Form.MainMenuStrip%2A> 所指向的 <xref:System.Windows.Forms.MenuStrip>。  從這裡開始，可以使用 CTRL\+TAB 在 `ToolStripPanel` 中的 <xref:System.Windows.Forms.ToolStrip> 控制項之間進行巡覽。  TAB 鍵和數字鍵台上的方向鍵則可用於在 <xref:System.Windows.Forms.ToolStrip> 中的項目之間進行巡覽。  特殊的演算法可處理在溢位區域中的巡覽。  空格鍵則會選取 <xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripDropDownButton> 或 <xref:System.Windows.Forms.ToolStripSplitButton>。  
  
##### 焦點 \(Focus\) 和驗證  
 當透過 ALT 鍵啟動時，通常 <xref:System.Windows.Forms.MenuStrip> 或 <xref:System.Windows.Forms.ToolStrip> 不會取得焦點，也不會將焦點從目前具有焦點的控制項中移除。  如果 <xref:System.Windows.Forms.MenuStrip> 內或是 <xref:System.Windows.Forms.MenuStrip> 的下拉式清單內裝載了控制項，則該控制項會在使用者按下 TAB 鍵時取得焦點。  一般來說，當透過鍵盤啟動 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.Control.GotFocus>、<xref:System.Windows.Forms.Control.LostFocus>、<xref:System.Windows.Forms.Control.Enter> 和 <xref:System.Windows.Forms.Control.Leave> 事件時，可能不會引發這些事件。  在這些情況下，請改用 <xref:System.Windows.Forms.MenuStrip.MenuActivate> 和 <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> 事件。  
  
 根據預設，<xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> 為 `false`。  在表單上明確呼叫 <xref:System.Windows.Forms.ContainerControl.Validate%2A>，以執行驗證。  
  
#### Layout  
 您可以透過使用 <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> 屬性選擇 <xref:System.Windows.Forms.ToolStripLayoutStyle> 的其中一個成員，控制 <xref:System.Windows.Forms.ToolStrip> 配置。  
  
##### 堆疊配置  
 堆疊是指將項目彼此並排在 <xref:System.Windows.Forms.ToolStrip> 的兩端。  下列清單將說明堆疊配置。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle> 為預設值。  這項設定會讓 <xref:System.Windows.Forms.ToolStrip> 根據 <xref:System.Windows.Forms.ToolStrip.Orientation%2A> 屬性自動修改其配置，以處理拖曳和停駐案例。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle> 會以彼此垂直並排的方式呈現 <xref:System.Windows.Forms.ToolStrip> 項目。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle> 會以彼此水平並排的方式呈現 <xref:System.Windows.Forms.ToolStrip> 項目。  
  
##### 堆疊配置的其他功能  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 會決定項目對齊的 <xref:System.Windows.Forms.ToolStrip> 結尾。  
  
 當項目無法納入 <xref:System.Windows.Forms.ToolStrip> 時，會自動出現溢位按鈕。  <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> 屬性設定會決定項目固定出現在溢位區 \(需要時\)，或永不出現在溢位區。  
  
 在 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> 事件中，您可以檢查 <xref:System.Windows.Forms.ToolStripItem.Placement%2A> 屬性，以判斷項目是放置在主要 <xref:System.Windows.Forms.ToolStrip> 上、溢位 <xref:System.Windows.Forms.ToolStrip> 上，或目前完全未顯示。  某個項目未顯示的一般原因是因為該項目不適合主要 <xref:System.Windows.Forms.ToolStrip> 而且它的 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> 屬性設定為 <xref:System.Windows.Forms.ToolStripItemOverflow>。  
  
 將 <xref:System.Windows.Forms.ToolStrip> 放入 <xref:System.Windows.Forms.ToolStripPanel> 並將其 <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> 設為 <xref:System.Windows.Forms.ToolStripGripStyle>，就可以移動該項目。  
  
##### 其他配置選項  
 其他配置選項包括 <xref:System.Windows.Forms.ToolStripLayoutStyle> 和 <xref:System.Windows.Forms.ToolStripLayoutStyle>。  
  
##### 流程配置  
 <xref:System.Windows.Forms.ToolStripLayoutStyle> 配置是 <xref:System.Windows.Forms.ContextMenuStrip>、<xref:System.Windows.Forms.ToolStripDropDownMenu> 和 <xref:System.Windows.Forms.ToolStripOverflow> 的預設值。  它與 <xref:System.Windows.Forms.FlowLayoutPanel> 相似。  <xref:System.Windows.Forms.ToolStripLayoutStyle> 配置的功能如下：  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel> 的所有功能都會由 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> 屬性公開 \(Expose\)。  您必須將 <xref:System.Windows.Forms.LayoutSettings> 類別轉換 \(Cast\) 成 <xref:System.Windows.Forms.FlowLayoutSettings> 類別。  
  
-   您可以在程式碼中使用 <xref:System.Windows.Forms.ToolStripItem.Dock%2A> 和 <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> 屬性對齊資料列中的項目。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性會加以忽略。  
  
-   在 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> 事件中，您可以檢查 <xref:System.Windows.Forms.ToolStripItem.Placement%2A> 屬性，以判斷項目是放置在主要 <xref:System.Windows.Forms.ToolStrip> 上或無法容納。  
  
-   底框並不會呈現，因此無法移動 <xref:System.Windows.Forms.ToolStripPanel> 中 <xref:System.Windows.Forms.ToolStripLayoutStyle> 配置樣式的 <xref:System.Windows.Forms.ToolStrip>。  
  
-   <xref:System.Windows.Forms.ToolStrip> 溢位按鈕將不會呈現，而且 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> 會被忽略。  
  
##### 資料表配置  
 <xref:System.Windows.Forms.ToolStripLayoutStyle> 配置是 <xref:System.Windows.Forms.StatusStrip> 的預設值。  它與 <xref:System.Windows.Forms.TableLayoutPanel> 相似。  <xref:System.Windows.Forms.ToolStripLayoutStyle> 配置的功能如下：  
  
-   <xref:System.Windows.Forms.TableLayoutPanel> 的所有功能都會由 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> 屬性公開 \(Expose\)。  您必須將 <xref:System.Windows.Forms.LayoutSettings> 類別轉換 \(Cast\) 成 <xref:System.Windows.Forms.TableLayoutSettings> 類別。  
  
-   您可以在程式碼中使用 <xref:System.Windows.Forms.ToolStripItem.Dock%2A> 和 <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> 屬性對齊資料表儲存格中的項目。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性會加以忽略。  
  
-   在 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> 事件中，您可以檢查 <xref:System.Windows.Forms.ToolStripItem.Placement%2A> 屬性，以判斷項目是放置在主要 <xref:System.Windows.Forms.ToolStrip> 上或無法容納。  
  
-   由於不會呈現底框，因此無法移動在 <xref:System.Windows.Forms.ToolStripPanel> 中配置樣式為 <xref:System.Windows.Forms.ToolStripLayoutStyle> 的 <xref:System.Windows.Forms.ToolStrip>。  
  
-   <xref:System.Windows.Forms.ToolStrip> 溢位按鈕將不會呈現，而且 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> 會被忽略。  
  
## ToolStripItem  
 下列主題將說明 <xref:System.Windows.Forms.ToolStripItem> 和其所衍生的控制項。  
  
 <xref:System.Windows.Forms.ToolStripItem> 是放置在 <xref:System.Windows.Forms.ToolStrip> 中之所有項目的抽象基底類別。  下列物件模型將說明 <xref:System.Windows.Forms.ToolStripItem> 繼承階層架構 \(Inheritance Hierarchy\)。  
  
 ![ToolStripItem 物件模型](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.png "ToolStripItemObjectModel")  
ToolStripItem 物件模型  
  
 <xref:System.Windows.Forms.ToolStripItem> 類別可以直接繼承自 <xref:System.Windows.Forms.ToolStripItem>，或者透過 <xref:System.Windows.Forms.ToolStripControlHost> 或 <xref:System.Windows.Forms.ToolStripDropDownItem> 間接繼承自 <xref:System.Windows.Forms.ToolStripItem>。  
  
 <xref:System.Windows.Forms.ToolStripItem> 控制項必須包含在 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.StatusStrip> 或 <xref:System.Windows.Forms.ContextMenuStrip> 內，且無法直接加入至表單。  各種容器類別的設計是用來包含適當的 <xref:System.Windows.Forms.ToolStripItem> 控制項子集合。  
  
 下表列出了內建 <xref:System.Windows.Forms.ToolStripItem> 控制項以及可提供控制項最佳顯示效果的容器。  雖然任何 <xref:System.Windows.Forms.ToolStrip> 項目皆可裝載於所有 <xref:System.Windows.Forms.ToolStrip> 衍生容器中，但這些項目在以下容器中會有最佳的顯示效果：  
  
> [!NOTE]
>  設計工具箱中並不會出現 <xref:System.Windows.Forms.ToolStripDropDown>。  
  
|包含的項目|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|-----------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|是|否|否|否|是|  
|<xref:System.Windows.Forms.ToolStripComboBox>|是|是|是|否|是|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripLabel>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripSeparator>|是|是|是|否|是|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripTextBox>|是|是|是|否|是|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|否|是|是|否|否|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|否|否|否|是|否|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|是|否|否|是|否|  
|<xref:System.Windows.Forms.ToolStripControlHost>|是|是|否|是|是|  
  
### ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> 是 <xref:System.Windows.Forms.ToolStrip> 的按鈕項目。  您可以使用各種框線樣式來顯示它，而且可以使用它來表示和啟動操作狀態。  您也可以將它定義為預設便取得焦點。  
  
### ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel> 會在 <xref:System.Windows.Forms.ToolStrip> 控制項中提供標籤功能。  <xref:System.Windows.Forms.ToolStripLabel> 與 <xref:System.Windows.Forms.ToolStripButton> 類似，預設不會取得焦點，而且不會呈現為已按下或已反白。  
  
 <xref:System.Windows.Forms.ToolStripLabel> 如同裝載項目 \(Hosted Item\)，皆支援便捷鍵。  
  
 在 <xref:System.Windows.Forms.ToolStripLabel> 上使用 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 和 <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> 屬性，以支援 <xref:System.Windows.Forms.ToolStrip> 中的連結控制。  
  
### ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> 是 <xref:System.Windows.Forms.ToolStripLabel> 的一種版本，特別針對在 <xref:System.Windows.Forms.StatusStrip> 中使用而設計。  特殊功能包括 <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>、<xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A> 和 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>。  
  
### ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> 會根據方向在工具列或功能表中加入垂直線或水平線。  它可以組成項目群組或區別項目，如同功能表上的項目。  
  
 透過從下拉式清單中選擇，即可在設計階段加入 <xref:System.Windows.Forms.ToolStripSeparator>。  但是，您也可以透過在設計工具範本節點或 <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> 方法中輸入連字號 \(\-\)，自動建立 <xref:System.Windows.Forms.ToolStripSeparator>。  
  
### ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> 是 <xref:System.Windows.Forms.ToolStripComboBox>、<xref:System.Windows.Forms.ToolStripTextBox> 和 <xref:System.Windows.Forms.ToolStripProgressBar> 的抽象基底類別。  <xref:System.Windows.Forms.ToolStripControlHost> 可利用兩種方式裝載其他控制項 \(包括自訂控制項\)：  
  
-   建構具有衍生自 <xref:System.Windows.Forms.Control> 之類別的 <xref:System.Windows.Forms.ToolStripControlHost>。  若要完整存取裝載的控制項和屬性，您必須將 <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> 屬性轉換 \(Cast\) 回它代表的實際類別。  
  
-   擴充 <xref:System.Windows.Forms.ToolStripControlHost>，並且在所繼承類別的預設建構函式中，呼叫傳遞衍生自 <xref:System.Windows.Forms.Control> 之類別的基底類別建構函式。  這個選項可讓您包裝通用控制項的方法和屬性，以便於在 <xref:System.Windows.Forms.ToolStrip> 之中進行存取。  
  
### ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> 是為了要在 <xref:System.Windows.Forms.ToolStrip> 中裝載而最佳化的 <xref:System.Windows.Forms.ComboBox>。  裝載控制項之屬性和事件的子集會在 <xref:System.Windows.Forms.ToolStripComboBox> 層級公開，但是基礎 <xref:System.Windows.Forms.ComboBox> 控制項可透過 <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> 屬性完整存取。  
  
### ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> 是為了要在 <xref:System.Windows.Forms.ToolStrip> 中裝載而最佳化的 <xref:System.Windows.Forms.TextBox>。  裝載控制項之屬性和事件的子集會在 <xref:System.Windows.Forms.ToolStripTextBox> 層級公開，但是基礎 <xref:System.Windows.Forms.TextBox> 控制項可透過 <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> 屬性完整存取。  
  
### ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> 是為了要在 <xref:System.Windows.Forms.ToolStrip> 中裝載而最佳化的 <xref:System.Windows.Forms.ProgressBar>。  裝載控制項之屬性和事件的子集會在 <xref:System.Windows.Forms.ToolStripProgressBar> 層級公開，但是基礎 <xref:System.Windows.Forms.ProgressBar> 控制項可透過 <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> 屬性完整存取。  
  
### ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> 是 <xref:System.Windows.Forms.ToolStripMenuItem>、<xref:System.Windows.Forms.ToolStripDropDownButton> 和 <xref:System.Windows.Forms.ToolStripSplitButton> 的抽象基底類別，可以直接裝載項目或裝載在下拉式容器中的其他項目。  您可以將 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> 屬性設為 <xref:System.Windows.Forms.ToolStripDropDown> 以及設定 <xref:System.Windows.Forms.ToolStripDropDown> 的 <xref:System.Windows.Forms.ToolStrip.Items%2A> 屬性，藉此執行這項操作。  您可以直接透過 <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> 屬性，存取這些下拉式項目。  
  
### ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> 是一個 <xref:System.Windows.Forms.ToolStripDropDownItem>，其使用 <xref:System.Windows.Forms.ToolStripDropDownMenu> 和 <xref:System.Windows.Forms.ContextMenuStrip> 以處理功能表的特殊反白顯示、配置及資料行排列。  
  
### ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> 與 <xref:System.Windows.Forms.ToolStripButton> 類似，但使用者按下它時將會顯示下拉式區域。  設定 <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> 屬性即可隱藏或顯示下拉式箭頭。  <xref:System.Windows.Forms.ToolStripDropDownButton> 裝載 <xref:System.Windows.Forms.ToolStripOverflowButton>，以便顯示讓 <xref:System.Windows.Forms.ToolStrip> 溢位的項目。  
  
### ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> 結合按鈕和下拉式按鈕的功能。  
  
 使用 <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> 屬性，將所選擇之下拉式項目的 <xref:System.Windows.Forms.Control.Click> 事件與按鈕上所顯示的項目進行同步。  
  
### ToolStripItem 的一般功能  
 <xref:System.Windows.Forms.ToolStripItem> 提供下列一般功能和選項給繼承的控制項：  
  
-   核心事件  
  
-   影像處理  
  
-   對齊方式  
  
-   文字和影像的關聯性  
  
-   顯示樣式  
  
#### 核心事件  
 <xref:System.Windows.Forms.ToolStripItem> 控制項會接收自己的點選、滑鼠和繪製事件，並且也可以執行某些鍵盤前置處理。  
  
#### 影像處理  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>、<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>、<xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>、<xref:System.Windows.Forms.ToolStripItem.ImageKey%2A> 和 <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> 屬性與影像處理的各種層面有關。  您可以透過直接設定這些屬性，或者設定僅限執行階段執行的 <xref:System.Windows.Forms.ToolStrip.ImageList%2A> 屬性，使用 <xref:System.Windows.Forms.ToolStrip> 控制項中的影像。  
  
 影像縮放是由 <xref:System.Windows.Forms.ToolStrip> 和 <xref:System.Windows.Forms.ToolStripItem> 中的屬性互動所決定，如下所示：  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> 是最終影像的比例，由該影像的 <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> 設定和容器的 <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> 設定構成的組合所決定。  
  
    -   如果 <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> 為 `true` \(預設值\) 且 <xref:System.Windows.Forms.ToolStripItemImageScaling> 為 <xref:System.Windows.Forms.ToolStripItemImageScaling>，則不會發生任何的影像縮放，而且 <xref:System.Windows.Forms.ToolStrip> 大小會是最大項目的大小或是規定大小的最小值。  
  
    -   如果 <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> 為 `false` 且 <xref:System.Windows.Forms.ToolStripItemImageScaling> 為 <xref:System.Windows.Forms.ToolStripItemImageScaling>，則不會發生影像及 <xref:System.Windows.Forms.ToolStrip> 的縮放。  
  
#### 對齊方式  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性的值將決定 <xref:System.Windows.Forms.ToolStrip> 的結尾，亦即項目顯示的地方。  只有當 <xref:System.Windows.Forms.ToolStrip> 的配置樣式設定為其中一個堆疊溢位 \(Stack Overflow\) 值時，<xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性才會有作用。  
  
 這些項目會根據它們在 Items 集合中出現的順序，放置在 <xref:System.Windows.Forms.ToolStrip> 上。  若要以程式設計的方式變更項目的配置位置，請使用 <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> 方法來移動集合中的項目。  這個方法會移動項目，但不會複製項目。  
  
#### 文字和影像的關聯性  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> 屬性可定義影像的相對位置 \(相對於 <xref:System.Windows.Forms.ToolStripItem> 上的文字\)。  缺少影像、文字或兩者的項目會被視為特殊狀況，因此 <xref:System.Windows.Forms.ToolStripItem> 不會針對缺少的項目顯示空白位置。  
  
#### 顯示樣式  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 可以讓您設定項目之 Text 和 Image 屬性的值，以便只顯示您想要的內容。  這個功能通常只用於在不同內容中顯示同一個項目時，變更顯示樣式。  
  
## 附屬類別  
 提供其他各種功能的類別，包括：  
  
-   <xref:System.Windows.Forms.ToolStripManager> 支援整個應用程式的 <xref:System.Windows.Forms.ToolStrip> 相關工作，例如：合併、設定和產生器選項。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> 可以讓您輕鬆地將特定的樣式或主題套用至 <xref:System.Windows.Forms.ToolStrip>。  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 會根據可取代的色彩表 \(<xref:System.Windows.Forms.ProfessionalColorTable>\) 建立畫筆和筆刷。  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> 會將系統色彩和平面視覺化樣式套用至 <xref:System.Windows.Forms.ToolStrip> 應用程式。  
  
-   <xref:System.Windows.Forms.ToolStripContainer> 與 <xref:System.Windows.Forms.SplitContainer> 類似。  它使用四個停駐側邊面板 \(<xref:System.Windows.Forms.ToolStripPanel> 的執行個體 \(Instance\)\) 和一個中央面板 \(<xref:System.Windows.Forms.ToolStripContentPanel> 的執行個體\)，以建立一般的排列方式。  您無法移除側邊面板，但可以將它們隱藏起來。  但是您無法移除或隱藏中央面板。  您可以在側邊面板中排列一或多個 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip> 或 <xref:System.Windows.Forms.StatusStrip> 控制項，並使用中央面板放置其他控制項。  <xref:System.Windows.Forms.ToolStripContentPanel> 還提供在表單的主體中支援產生器的方法，以維持外觀一致。  <xref:System.Windows.Forms.ToolStripContainer> 不支援多重文件介面 \(MDI\)。  
  
-   <xref:System.Windows.Forms.ToolStripPanel> 提供移動與排列 <xref:System.Windows.Forms.ToolStrip> 控制項的空間。  如果選擇這種方式，您只可以使用一個面板，而且 <xref:System.Windows.Forms.ToolStripPanel> 可以在 MDI 案例中正常運作。  
  
## 請參閱  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)   
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [StatusStrip 控制項](../../../../docs/framework/winforms/controls/statusstrip-control.md)   
 [ContextMenuStrip 控制項](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)   
 [BindingNavigator 控制項](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)