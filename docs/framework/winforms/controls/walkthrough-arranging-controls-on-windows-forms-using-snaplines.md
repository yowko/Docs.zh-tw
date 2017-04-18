---
title: "逐步解說：使用對齊線排列 Windows Form 上的控制項 | Microsoft Docs"
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
  - "控制項 [Windows Form], 使用對齊線排列"
  - "SnapLine 類別, 逐步解說"
  - "對齊線, 排列 Windows Form 控制項"
  - "Windows Form 控制項, 排列"
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 逐步解說：使用對齊線排列 Windows Form 上的控制項
表單控制項的精確置放對許多應用程式而言非常重要。  Windows Form 設計工具能提供您許多配置工具以完成這項作業。  其中最重要的一項就是 <xref:System.Windows.Forms.Design.Behavior.SnapLine> 功能。  
  
 對齊線能精確顯示控制項與其他控制項對齊的位置。  它們也能顯示在控制項之間的建議邊界距離 \(由 Windows 使用者介面方針所指定\)。  如需詳細資訊，請參閱[使用者介面設計與開發](http://go.microsoft.com/FWLink/?LinkId=83878) \(英文\)。  
  
 對齊線讓對齊控制項變得很簡單，可以獲得乾淨俐落、專業的外觀與行為 \(外觀和操作\)。  
  
 逐步解說將說明的工作包括：  
  
-   建立 Windows Form 專案  
  
-   使用對齊線調整控制項間距並對齊控制項  
  
-   對齊至表單和容器邊界  
  
-   對齊至群組的控制項  
  
-   繪製外框大小以使用對齊線放置控制項  
  
-   從工具箱拖曳控制項時使用對齊線  
  
-   使用對齊線調整控制項大小  
  
-   讓標籤對齊至控制項的文字  
  
-   使用具有鍵盤瀏覽的對齊線  
  
-   對齊線和配置面板  
  
-   停用對齊線  
  
 當您完成時，將會對於對齊線功能所扮演的配置角色有所了解。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### 若要建立專案  
  
1.  建立稱為 "SnaplineExample" 的 Windows 架構應用程式專案。  如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  從 \[表單設計工具\] 中選取表單。  
  
## 使用對齊線調整控制項間距並對齊控制項  
 對齊線提供您精確而容易了解的方式，以對齊表單上的控制項。  當您將選取的一或多個控制項移近與另一個控制項或控制項集對齊的位置時，對齊線便會出現。  當您將此控制項移動至超出其他控制項時，選取範圍就會「貼齊」\(Snap\) 至建議的位置。  
  
#### 若要使用對齊線排列控制項  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  
  
2.  將 <xref:System.Windows.Forms.Button> 控制項移至表單的右下角。  請注意在 <xref:System.Windows.Forms.Button> 控制項接近表單底部和右框線時，所出現的對齊線。  這些對齊線會顯示控制項邊框和表單之間的建議距離。  
  
3.  在表單的框線周圍移動 <xref:System.Windows.Forms.Button> 控制項，並注意對齊線出現的地方。  當您完成時，請將 <xref:System.Windows.Forms.Button> 控制項移至表單的中心附近。  
  
4.  從 \[**工具箱**\] 將另一個 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  
  
5.  移動第二個 <xref:System.Windows.Forms.Button> 控制項，直到幾乎與第一個控制項對齊為止。  請注意出現在兩個按鈕之文字基線中的對齊線，並請注意您所移動的控制項，會貼齊至與另一個控制項相同層次的位置。  
  
6.  移動第二個 <xref:System.Windows.Forms.Button> 控制項，直到它的位置在第一個控制項的正上方為止。  請注意出現在兩個按鈕左邊緣和右邊緣的對齊線，並請注意您所移動的控制項，會貼齊至與另一個控制項完全對齊的位置。  
  
7.  選取其中一個 <xref:System.Windows.Forms.Button> 控制項，並將它移動至靠近另一個控制項，直到幾乎彼此接觸為止。  請注意出現在它們之間的對齊線。  這個距離就是在控制項框線之間的建議距離。  同時也請注意，您移動的控制項會貼齊至這個位置。  
  
8.  從 \[**工具箱**\] 將兩個 <xref:System.Windows.Forms.Panel> 控制項拖曳至表單。  
  
9. 移動其中一個 <xref:System.Windows.Forms.Panel> 控制項，直到幾乎與第一個控制項對齊為止。  請注意出現在兩個控制項的上方和下方邊緣的對齊線，並請注意您所移動的控制項，會貼齊至與另一個控制項完全對齊的位置。  
  
## 對齊至表單和容器邊界  
 對齊線能協助您以一致的方式，將控制項對齊至表單和容器的邊界。  
  
#### 若要將控制項對齊至表單和容器邊界  
  
1.  選取其中一個 <xref:System.Windows.Forms.Button> 控制項，並將它移至靠近表單的右框線，直到對齊線出現為止。  對齊線到右框線的距離是控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性值和表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值的總和。  
  
> [!NOTE]
>  如果表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性設定為 0,0,0,0，Windows Form 設計工具便會為表單指定 9,9,9,9 的 <xref:System.Windows.Forms.Control.Padding%2A> 值。  若要覆寫這項行為，請指派不同於 0,0,0,0 的值。  
  
1.  在 \[**屬性**\] 視窗中展開 <xref:System.Windows.Forms.Control.Margin%2A> 項目，並將 <xref:System.Windows.Forms.Padding.All%2A> 屬性設定為 0，藉此變更 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性值。  如需詳細資訊，請參閱[逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)。  
  
2.  將 <xref:System.Windows.Forms.Button> 控制項移至靠近表單的右框線，直到對齊線出現為止。  這個距離是由表單的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值所提供。  
  
3.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.GroupBox> 控制項拖曳至表單。  
  
4.  在 \[**屬性**\] 視窗中展開 <xref:System.Windows.Forms.Control.Padding%2A> 項目，並將 <xref:System.Windows.Forms.Padding.All%2A> 屬性設定為 10，藉此變更 <xref:System.Windows.Forms.GroupBox> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值。  
  
5.  將 <xref:System.Windows.Forms.Button> 控制項從 \[**工具箱**\] 拖曳至 <xref:System.Windows.Forms.GroupBox> 控制項。  
  
6.  將 <xref:System.Windows.Forms.Button> 控制項移至靠近 <xref:System.Windows.Forms.GroupBox> 控制項的右框線，直到對齊線出現為止。  在 <xref:System.Windows.Forms.GroupBox> 控制項內移動 <xref:System.Windows.Forms.Button> 控制項，直到對齊線出現為止。  
  
## 對齊至群組的控制項  
 您可以使用對齊線來對齊群組的控制項以及 <xref:System.Windows.Forms.GroupBox> 控制項內的控制項。  
  
#### 若要對齊至群組的控制項  
  
1.  選取表單上的兩個控制項。  移動選取的控制項，並注意出現在您選取的控制項和其他控制項之間的對齊線。  
  
2.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.GroupBox> 控制項拖曳至表單。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項從 \[**工具箱**\] 拖曳至 <xref:System.Windows.Forms.GroupBox> 控制項。  
  
4.  選取其中一個 <xref:System.Windows.Forms.Button> 控制項，並將其在 <xref:System.Windows.Forms.GroupBox> 控制項的周圍移動。  請注意出現在 <xref:System.Windows.Forms.GroupBox> 控制項邊緣的對齊線。  同時也請注意，出現在 <xref:System.Windows.Forms.Button> 控制項邊緣的對齊線，此控制項是包含在 <xref:System.Windows.Forms.GroupBox> 控制項中。  容器控制項子系的控制項也支援對齊線。  
  
## 繪製外框大小以使用對齊線放置控制項  
 對齊線能在您剛將控制項放置在表單上時，協助對齊控制項。  
  
#### 若要繪製外框大小以使用對齊線放置控制項  
  
1.  在 \[**工具箱**\] 中，請按 <xref:System.Windows.Forms.Button> 控制項圖示。  請勿拖曳至表單。  
  
2.  將滑鼠指標移至表單的設計工具介面上。  請注意：指標會變成十字形，並且附有 <xref:System.Windows.Forms.Button> 控制項圖示。  同時也請注意，為建議 <xref:System.Windows.Forms.Button> 控制項的對齊位置而出現的對齊線。  
  
3.  按住滑鼠按鈕。  
  
4.  在表單上四處拖曳滑鼠指標。  請注意已繪製外框，指示出控制項的位置與大小。  
  
5.  拖曳指標，直到對齊表單上的另一個控制項為止。  請注意，會出現對齊線以指示對齊。  
  
6.  放開滑鼠按鈕。  會按照外框所指示的位置與大小建立控制項。  
  
## 從工具箱拖曳控制項時使用對齊線  
 對齊線能在您將控制項從 \[**工具箱**\] 拖曳至表單時對齊控制項。  
  
#### 若要從工具箱拖曳控制項時使用對齊線  
  
1.  將 <xref:System.Windows.Forms.Button> 控制項從 \[**工具箱**\] 拖曳至表單，但不要放開滑鼠按鈕。  
  
2.  將滑鼠指標移至表單的設計工具介面上。  請注意，指標會變更，以指示建立新 <xref:System.Windows.Forms.Button> 控制項的位置。  
  
3.  在表單上四處拖曳滑鼠指標。  請注意出現的對齊線，這些對齊線是用來建議 <xref:System.Windows.Forms.Button> 控制項的對齊位置。  尋找與其他控制項對齊的位置。  
  
4.  放開滑鼠按鈕。  控制項會建立於對齊線所指示的位置。  
  
## 使用對齊線調整控制項大小  
 在您調整控制項大小時，對齊線能協助您對齊控制項。  
  
#### 若要使用對齊線調整控制項大小  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  
  
2.  藉由抓取其中一個角落縮放控點並加以拖曳，調整 <xref:System.Windows.Forms.Button> 控制項大小。  如需詳細資訊，請參閱 [如何：重新調整 Windows Form 上控制項的大小](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)。  
  
3.  拖曳縮放控點直到其中一個 <xref:System.Windows.Forms.Button> 控制項的邊框對齊另一個控制項。  請注意會出現對齊線。  同時也請注意，縮放控點會貼齊至對齊線所指示的位置。  
  
4.  在不同方向中調整 <xref:System.Windows.Forms.Button> 控制項的大小，並將縮放控點對齊至不同的控制項。  請注意，對齊線會以不同的方向出現以指示對齊。  
  
## 讓標籤對齊至控制項的文字  
 某些控制項提供對齊線，可將其他控制項對齊至顯示的文字。  
  
#### 若要讓標籤對齊至控制項的文字  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TextBox> 控制項拖曳至表單。  當您把 <xref:System.Windows.Forms.TextBox> 控制項放在表單上時，請按一下智慧標籤圖像 \(Glyph\)，並選取 \[**設定文字為 textBox1**\] 選項。  如需詳細資訊，請參閱[逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)。  
  
2.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Label> 控制項拖曳至表單。  
  
3.  將 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值變更為 `true`。  請注意，控制項的框線會加以調整，以符合顯示文字。  
  
4.  將 <xref:System.Windows.Forms.Label> 控制項移至 <xref:System.Windows.Forms.TextBox> 控制項的左邊，讓它對齊 <xref:System.Windows.Forms.TextBox> 控制項的下邊緣。  請注意出現在兩個控制項下邊緣的對齊線。  
  
5.  將 <xref:System.Windows.Forms.Label>控制項略微往上移動，直到 <xref:System.Windows.Forms.Label>文字與 <xref:System.Windows.Forms.TextBox> 文字對齊為止。  請注意會顯示不同樣式的對齊線，指示兩個控制項的文字欄位對齊的時機。  
  
## 使用具有鍵盤瀏覽的對齊線  
 當您使用鍵盤的方向鍵排列控制項時，對齊線可幫您對齊控制項。  
  
#### 若要使用具有鍵盤瀏覽的對齊線  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  將它放在表單的左上角。  
  
2.  按下 CTRL\+向下鍵。  請注意，控制項會往表單下方移動至第一個可使用的水平對齊位置。  
  
3.  按住 CTRL\+向下鍵，直到控制項到達表單下方為止。  請注意在往表單下方移動時，控制項佔有的位置。  
  
4.  按下 CTRL\+向右鍵。  請注意，控制項會在表單中移動至第一個可使用的垂直對齊位置。  
  
5.  按下 CTRL\+向右鍵，直到控制項到達表單的側邊為止。  請注意在表單上移動時，控制項佔有的位置。  
  
6.  使用方向鍵的組合，在表單上四處移動控制項。  請注意控制項佔有的位置，以及伴隨出現的對齊線。  
  
7.  按下 SHIFT\+任何方向鍵，以調整 <xref:System.Windows.Forms.Button> 控制項大小 \(以一個像素遞增\)。  
  
8.  按下 CTRL\+SHIFT\+任何方向鍵，以調整 <xref:System.Windows.Forms.Button> 控制項大小 \(以對齊線來遞增\)。  
  
## 對齊線和配置面板  
 配置面板內停用對齊線。  
  
#### 若要選擇性地停用對齊線  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳至表單。  
  
2.  在 \[**工具箱**\] 中，按兩下 <xref:System.Windows.Forms.Button> 控制項圖示。  請注意，新的按鈕控制項會出現在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的第一個儲存格中。  
  
3.  多做兩次按兩下 \[**工具箱**\] 中 <xref:System.Windows.Forms.Button> 控制項圖示的動作。  這會在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中保留一個空白的儲存格。  
  
4.  將 <xref:System.Windows.Forms.Button> 控制項從 \[**工具箱**\] 拖曳至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的空白儲存格。  請注意，不會出現對齊線。  
  
5.  從 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中拖曳出 <xref:System.Windows.Forms.Button> 控制項，並將它在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項周圍移動。  請注意，對齊線會再度出現。  
  
## 停用對齊線  
 依據預設會開啟對齊線。  您可以選擇性地停用對齊線，或者在設計環境中停用對齊線。  
  
#### 若要選擇性地停用對齊線  
  
-   當控制項在表單上四處移動時按下 ALT 鍵。  
  
     請注意，不會出現任何對齊線，且控制項也不會貼齊至任何可能的對齊位置。  
  
#### 若要在設計環境中停用對齊線  
  
1.  從 \[**工具箱**\] 功能表中開啟 \[**選項**\] 對話方塊。  開啟 \[Windows Form 設計工具\] 對話方塊。  如需詳細資訊，請參閱[General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8dd170af-72f0-4212-b04b-034ceee92834)。  
  
2.  請選取 \[**一般**\] 節點。  在 \[**配置模式**\] 區段中，將選取範圍從 \[**SnapLines**\] 變更為 \[**SnapToGrid**\]。  
  
3.  按一下 \[確定\] 以套用設定。  
  
4.  選取表單上的控制項，並將它移至其他控制項周圍。  請注意，不會出現對齊線。  
  
## 後續步驟  
 對齊線提供在表單上對齊控制項的易用工具。  建議另外再研究以下各項：  
  
-   嘗試在另一個 <xref:System.Windows.Forms.GroupBox> 控制項中巢狀套疊 <xref:System.Windows.Forms.GroupBox> 控制項。  在 <xref:System.Windows.Forms.GroupBox> 子控制項內放置一個 <xref:System.Windows.Forms.Button> 控制項，並在父 <xref:System.Windows.Forms.GroupBox> 控制項中放置另一個。  四處移動 <xref:System.Windows.Forms.Button> 控制項，查看對齊線跨越容器界限的方式。  
  
-   建立 <xref:System.Windows.Forms.TextBox> 控制項的資料行和 <xref:System.Windows.Forms.Label> 控制項的對應資料行。  將 <xref:System.Windows.Forms.Label> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值設定為 `true`。  使用對齊線移動 <xref:System.Windows.Forms.Label> 控制項，讓顯示的文字對齊 <xref:System.Windows.Forms.TextBox> 控制項中的文字。  
  
 如需 Windows 使用者介面設計的詳細資訊，請參閱*《Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers》*一書，Redmond, WA: Microsoft Press, 1999  \(USBN: 0\-7356\-0566\-1\)。  
  
## 請參閱  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>   
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)