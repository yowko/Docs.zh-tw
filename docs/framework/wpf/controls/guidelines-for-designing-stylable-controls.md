---
title: "設計可設定樣式控制項的方針 | Microsoft Docs"
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
  - "控制項, 樣式設計"
  - "控制項的樣式設計"
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 設計可設定樣式控制項的方針
本文件摘要說明在設計控制項時，若希望能很容易地設定控制項的樣式並且可做成樣板，要考量的一套最佳做法。  我們是在處理內建 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項集的佈景主題控制項樣式時，歷經許多的嘗試和錯誤，最後得出這一套最佳做法。  我們學到，成功的樣式設定不僅取決於樣式本身，還要有良好的物件模型設計。  本文件的目標對象是控制項的作者，不是樣式的作者。  
  
   
  
<a name="Terminology"></a>   
## 用語  
 「設計樣式和樣板化」是指一套技巧，可以讓控制項的作者將控制項的視覺外觀處理委派給控制項的樣式和樣板。  這一套技巧包括：  
  
-   樣式 \(包括屬性 setter、觸發程序和腳本\)。  
  
-   資源。  
  
-   控制項樣板。  
  
-   資料範本。  
  
 如需設計樣式和樣板化的簡介，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## 在開始之前：了解您的控制項  
 在您閱讀這些方針之前，最重要的是了解您的控制項，並且定義它們的常見用途。  設計樣式會帶出一堆通常難以駕馭的可能性。  預定要廣泛使用 \(由許多開發人員使用於許多應用程式中\) 的控制項面臨的挑戰是，樣式可能會產生深遠的控制項視覺外觀變更。  事實上，經過樣式設計的控制項甚至可能和作者原本想要的完全不同。  因為樣式設計有如此無限大的彈性，您可以利用常見用途的概念來規劃樣式。  
  
 為了要了解您的控制項常見用法，最好想想控制項的價值所在。  您的控制項帶給表格什麼其他控制項所沒有的？  常見用法不是指特定的視覺外觀，而是指控制項的使用哲學及對其用法的一套合理期望。  了解這個，讓您可以針對常見情況，做出關於控制項的撰寫模式和由樣式定義之行為的假設。  以 <xref:System.Windows.Controls.ComboBox> 為例，了解常見用法無法告訴您特定 <xref:System.Windows.Controls.ComboBox> 是否有圓角，但會告訴您 <xref:System.Windows.Controls.ComboBox>可能需要快顯視窗以及某種開啟它的切換機制。  
  
<a name="General_Guidelines"></a>   
## 一般方針  
  
-   **不要嚴格強制執行樣板合約**： 控制項的樣板合約可能由項目、命令、繫結、觸發程序 \(Trigger\)，甚至屬性設定 \(控制項運作正常所需要或期望的\) 組成。  
  
    -   盡量將合約最小化。  
  
    -   在設計時要有心理準備，也就是說在設計階段 \(即使用設計工具時\) 的控制項樣板常常會處於未完成狀態。  由於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 沒有提供「撰寫中」狀態的基礎架構，因此建置控制項時您可能要有控制項處於這類狀態的心理準備。  
  
    -   當樣板合約的任何一方面沒有做到時，不要擲回例外狀況。  遵循這些方針，如果面板中的子系太多或太少，都不應該擲回例外狀況。  
  
-   **把周邊功能因素計入樣板 Helper 項目**： 每個控制項都應該專注於其核心功能和真正價值所在，並按照控制項的常見用途定義。  為達這個目的，請在樣板中使用撰寫和 Helper 項目，以展示周邊行為和視覺化效果 \(也就是與控制項核心功能無關的行為和視覺化效果\)。  Helper 項目分成三類：  
  
    -   **獨立** 的 Helper 型別是在樣板中「匿名」使用的公用、可重複使用的控制項或基本型別，而所謂匿名意指這個 Helper 項目和已設定樣式的控制項都不知道彼此的存在。  就技術上而言，任何項目都可以是匿名型別，但是在這個情境中，獨立一詞是指封裝了特殊功能 \(以實現目標案例\) 的型別。  
  
    -   **以型別為基礎** 的 Helper 項目是封裝了特殊功能的新型別。  這些項目的功能設計範圍，通常比通用控制項或基本型別要窄。  和獨立 Helper 項目不同的是，以型別為基礎的 Helper 項目知道它們所處的使用內容，而且通常必須與其所屬樣板的控制項共用資料。  
  
    -   **具名** 的 Helper 項目是控制項可以利用名稱在樣板內找到的通用控制項或基本型別。這些項目在樣板中具有已知的名稱，使控制項能夠找到它們，並且用程式設計的方式與其互動。  在任何樣板中，一個名稱只能對應至一個項目。  
  
     下表列出今日的控制項樣式可以採用的 Helper 項目 \(此表未列出所有項目\)：  
  
    |項目|型別|使用|  
    |--------|--------|--------|  
    |<xref:System.Windows.Controls.ContentPresenter>|以型別為基礎|<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.CheckBox>、<xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame> 等等 \(所有 <xref:System.Windows.Controls.ContentControl> 型別\)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|以型別為基礎|<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.Menu> 等等 \(所有 <xref:System.Windows.Controls.ItemsControl> 型別\)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|具名|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|獨立|<xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.ToolBar>、<xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.ToolTip> 等等|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|具名|<xref:System.Windows.Controls.Slider>、<xref:System.Windows.Controls.Primitives.ScrollBar> 等等|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|具名|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|獨立|<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ComboBox>、<xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.Frame> 等等|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|獨立|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|具名|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|以型別為基礎|<xref:System.Windows.Controls.Slider>|  
  
-   **在 Helper 項目上將使用者需要指定的繫結或屬性設定減至最少**：  Helper 項目經常需要特定的繫結或屬性設定，才能在控制項樣板中正常運作。  Helper 項目和樣板化的控制項應該盡可能建立這些設定。  在設定屬性或建立繫結時，應特別小心不要覆寫使用者設定的值。  具體的最佳做法如下：  
  
    -   具名 Helper 項目應該由父代 \(Parent\) 識別，且父代應該在 Helper 項目上建立所有需要的設定。  
  
    -   以型別為基礎的 Helper 項目應該直接在自己身上建立所有需要的設定。  若要這麼做，Helper 項目可能需要查詢它所處的使用資訊內容，包括它的 `TemplatedParent` \(要使用它的樣板控制項型別\)。  例如，當在 <xref:System.Windows.Controls.ContentControl> 衍生型別 \(Derived Type\) 中使用時，<xref:System.Windows.Controls.ContentPresenter> 會自動將其 `TemplatedParent` 的 `Content` 屬性繫結至其 <xref:System.Windows.Controls.ContentPresenter.Content%2A> 屬性。  
  
    -   獨立的 Helper 項目則無法以這種方式最佳化，因為在定義上 Helper 項目和父代都不知道彼此的存在。  
  
-   **使用 Name 屬性標示樣板內的項目**：  如果控制項需要在其樣式中尋找某個項目並以程式設計的方式加以存取，應該使用 `Name` 屬性和 `FindName` 開發架構來達成這個目的。  找不到項目時，控制項不應該擲回例外狀況，而是要安靜而正常地停用需要該項目的功能。  
  
-   **在樣式中使用最佳做法來表達控制項狀態和行為**： 下列依序列出在樣式中表達控制項狀態變更和行為的最佳做法。  您應該使用清單中第一個符合您案例的做法。  
  
    1.  屬性繫結。  範例：<xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=fullName> 和 <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=fullName> 之間的繫結。  
  
    2.  觸發的屬性變更或屬性動畫。  範例：<xref:System.Windows.Controls.Button> 的停留 \(Hover\) 狀態。  
  
    3.  命令。  範例：<xref:System.Windows.Controls.Primitives.ScrollBar> 中的 <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand> \/ <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand>。  
  
    4.  獨立的 Helper 項目。  範例：<xref:System.Windows.Controls.TabControl> 中的 <xref:System.Windows.Controls.Primitives.TabPanel>。  
  
    5.  以型別為基礎的 Helper 型別。  範例：<xref:System.Windows.Controls.Button> 中的 <xref:System.Windows.Controls.ContentPresenter>、<xref:System.Windows.Controls.Slider> 中的 <xref:System.Windows.Controls.Primitives.TickBar>。  
  
    6.  具名的 Helper 項目。  範例：<xref:System.Windows.Controls.ComboBox> 中的 <xref:System.Windows.Controls.TextBox>。  
  
    7.  來自具名 Helper 型別的反昇 \(Bubbled\) 事件。  如果您接聽來自樣式項目的反昇事件，應該要求產生該事件的項目必須能夠受到唯一識別。  範例：<xref:System.Windows.Controls.ToolBar> 中的 <xref:System.Windows.Controls.Primitives.Thumb>。  
  
    8.  自訂的 `OnRender` 行為。  範例：<xref:System.Windows.Controls.Button> 中的 <xref:Microsoft.Windows.Themes.ButtonChrome>。  
  
-   **謹慎使用樣式觸發程序 \(相對於樣板觸發程序\)**：  要用以影響樣板中之項目屬性的觸發程序，必須宣告在樣板中。  除非您確知變更樣板也會終結觸發程序，否則就可以在樣式中宣告會影響控制項上之屬性的觸發程序 \(沒有 `TargetName`\)。  
  
-   **與現有的樣式模式一致**： 許多時候解決問題的方法不只一種。  要知道現有的控制項樣式模式，並盡量與之一致。  這對於從同一基底類別衍生出來的控制項來說尤其重要 \(如 <xref:System.Windows.Controls.ContentControl>、<xref:System.Windows.Controls.ItemsControl>、<xref:System.Windows.Controls.Primitives.RangeBase> 等等\)。  
  
-   **公開屬性以提供常用的自訂案例，而不需重製樣板**：  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 不支援可外掛\/可自訂的組件，因此控制項使用者只剩下兩種自訂方法可用：直接設定屬性或者用樣式設定屬性。  知道這一點後，就可以針對十分常用、高優先權的自訂案例公開少數屬性，而不需重製樣板。  以下是適合啟用自訂案例的時間與方法之最佳做法：  
  
    -   如為十分常用的自訂，則應該在控制項上公開為屬性，並由樣板使用。  
  
    -   如為較不常用 \(但非極少用\) 的自訂，則應該公開附加屬性，並由樣板使用。  
  
    -   如為已知但極少用的自訂，則重製樣板是可以接受的。  
  
<a name="Theme_Considerations"></a>   
## 佈景主題考量  
  
-   **所有佈景主題的佈景主題樣式都應該盡量保有一致的屬性語意，但不必強制保證**：  您的控制項的文件中應該要有份文件來描述控制項的屬性語意 \(Semantics\)，也就是屬性對控制項的「意義」。  例如，<xref:System.Windows.Controls.ComboBox> 控制項應該在 <xref:System.Windows.Controls.ComboBox>中定義 <xref:System.Windows.Controls.Control.Background%2A> 屬性的意義。  不論什麼佈景主題，控制項的預設樣式都應該盡量遵循在這份文件中定義的語意。  另一方面，控制項使用者則應該知道屬性語意可能因佈景主題不同而改變。  在某些情況下，可能因為特定佈景主題的視覺物件限制，而無法表達某個屬性   \(例如，Classic 佈景主題就沒有單一邊界可以讓 `Thickness` 針對許多控制項來套用\)。  
  
-   **所有佈景主題的佈景主題樣式不需要都有一致的觸發程序語意**：  控制項樣式透過觸發程序或動畫公開的行為可能依佈景主題而異。  控制項使用者應該知道，不同佈景主題的控制項不一定會採用相同機制來達成特定行為。  例如，一個佈景主題可能用動畫來表達停留 \(Hover\) 行為，而另一個佈景主題則用觸發程序來表達同樣的行為。  這可能造成自訂控制項上保留的行為不一致   \(例如，如果控制項的停留 \(Hover\) 狀態是以觸發程序表達，變更背景 \(Background\) 屬性並不會影響控制項的停留狀態。  但是，如果停留狀態是以動畫實作，變更背景就會中斷動畫，進而中斷狀態轉換作業，而且無法恢復\)。  
  
-   **所有佈景主題的佈景主題樣式不需要都有一致的「配置」語意**：  例如，預設樣式不必保證控制項會在所有佈景主題中佔據同樣的大小，或保證控制項在所有佈景主題中都有相同的內容邊界 \/ 邊框。  
  
## 請參閱  
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)