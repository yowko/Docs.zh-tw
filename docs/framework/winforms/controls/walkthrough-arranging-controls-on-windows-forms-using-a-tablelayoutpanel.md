---
title: "逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項 | Microsoft Docs"
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
  - "控制項 [Windows Form], 使用 TableLayoutPanel 排列"
  - "TableLayoutPanel 控制項 [Windows Form], 逐步解說"
  - "Windows Form 控制項, 排列"
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# 逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項
某些應用程式需要具有配置的表單，此配置會在表單重新調整大小或內容大小變更時適當地排列表單。  當您需要動態的配置，且不希望在程式碼中明確處理 <xref:System.Windows.Forms.Control.Layout> 事件時，請考慮使用配置面板。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項和 <xref:System.Windows.Forms.TableLayoutPanel> 控制項會以容易了解的方式排列表單上的控制項。  兩者都提供自動而可設定的能力，可控制包含在其中的子控制項相對位置，且都提供在執行階段的動態配置功能，因此可以在父表單的維度變更時，調整子控制項的大小及位置。  配置面板可以用巢狀方式套疊在配置面板內，藉此提供複雜的使用者介面。  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> 會以特定的流量方向排列內容：水平或垂直。  其內容可以從某一資料列換行至下一個資料列，或從某一資料行換行至下一個資料行。  此外，也可裁剪該內容而不換行。  如需詳細資訊，請參閱[逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> 會排列方格中的內容，提供與 HTML \<table\> 項目類似的功能。  <xref:System.Windows.Forms.TableLayoutPanel> 控制項能讓您將控制項放置在格線配置中，而不需要精確地指定每個個別控制項的位置。  它的儲存格會在資料列和資料行中排列，且這些儲存格可以具有不同大小。  儲存格可以跨資料列和資料行合併。  儲存格能包含任何表單可以包含的內容，並在大部分的其他方面均像容器一般運作。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> 控制項也提供在執行階段時的按比例調整大小能力，所以您的配置可以在調整表單時順利地變更。  這會讓 <xref:System.Windows.Forms.TableLayoutPanel> 控制項非常適合類似資料輸入表單或當地語系化應用程式等用途。  如需詳細資訊，請參閱[Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/zh-tw/e193b4fc-912a-4917-b036-b76c7a6f58ab)和[Walkthrough: Creating a Localizable Windows Form](http://msdn.microsoft.com/zh-tw/c5240b6e-aaca-4286-9bae-778a416edb9c)。  
  
 一般說來，您不應該使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項做為整個配置的容器。  請使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項，為配置的組件提供按比例調整大小的功能。  
  
 逐步解說將說明的工作包括：  
  
-   建立 Windows Form 專案  
  
-   排列資料列和資料行中的控制項  
  
-   設定資料列和資料行屬性  
  
-   使用控制項擴展資料列和資料行  
  
-   溢位的自動處理  
  
-   按兩下工具箱中的控制項以插入該控制項  
  
-   繪製外框以插入控制項  
  
-   將現有的控制項重新指派至不同的父代  
  
 當您完成時，將會對這些重要的配置功能所扮演的角色有所了解。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### 若要建立專案  
  
1.  建立稱為 "TableLayoutPanelExample" 的 Windows 應用程式專案。  如需詳細資訊，請參閱[How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  從 \[**Windows Form 設計工具**\] 中選取表單。  
  
## 排列資料列和資料行中的控制項  
 <xref:System.Windows.Forms.TableLayoutPanel> 控制項能讓您輕鬆地將控制項排列成資料列和資料行。  
  
#### 若要使用 TableLayoutPanel 排列資料列和資料行中的控制項  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳至表單。  請注意，根據預設，<xref:System.Windows.Forms.TableLayoutPanel> 控制項具有四個儲存格。  
  
2.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Button> 控制項拖曳至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項，並將它放入其中一個儲存格。  請注意，在您選取的儲存格中會建立 <xref:System.Windows.Forms.Button> 控制項。  
  
3.  從 \[**工具箱**\] 再拖曳三個 <xref:System.Windows.Forms.Button> 控制項至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項，讓每個儲存格都包含一個按鈕。  
  
4.  抓取在兩個資料行之間的垂直縮放控點 \(Sizing Handle\)，然後將它移至左邊。  請注意，在第一個資料行中的 <xref:System.Windows.Forms.Button> 控制項會重新調整為較小的寬度，而第二個資料行中的 <xref:System.Windows.Forms.Button> 控制項大小則不會有所變更。  
  
5.  抓取在兩個資料行之間的垂直縮放控點，然後將它移至右邊。  請注意，在第一個資料行中的 <xref:System.Windows.Forms.Button> 控制項會回到原來的大小，而第二個資料行中的 <xref:System.Windows.Forms.Button> 控制項則會移至右邊。  
  
6.  向上和向下移動水平縮放控點，觀察在面板中對於控制項的作用。  
  
## 使用停駐和錨定在儲存格中放置控制項  
 <xref:System.Windows.Forms.TableLayoutPanel> 中子控制項的錨定行為，不同於在其他容器控制項中的錨定行為。  子控制項的停駐行為則和其他容器控制項的停駐行為一樣。  
  
#### 在儲存格內放置控制項  
  
1.  選取第一個 <xref:System.Windows.Forms.Button> 控制項。  將其 <xref:System.Windows.Forms.Control.Dock%2A> 屬性的值變更為 <xref:System.Windows.Forms.DockStyle>。  請注意，<xref:System.Windows.Forms.Button> 控制項會展開，以填滿儲存格。  
  
2.  選取其他 <xref:System.Windows.Forms.Button> 控制項的其中一個。  將其 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性的值變更為 <xref:System.Windows.Forms.AnchorStyles>。  請注意，它已經移動，所以右框線會接近儲存格的右框線。  在框線之間的距離是 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性和面板的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性的總和。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性值變更為 <xref:System.Windows.Forms.AnchorStyles> 和 <xref:System.Windows.Forms.AnchorStyles>。  請注意，控制項會調整大小為儲存格的寬度，同時會將 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 值納入考慮。  
  
4.  使用 <xref:System.Windows.Forms.AnchorStyles> 和 <xref:System.Windows.Forms.AnchorStyles> 樣式重複執行步驟 2 和 3。  
  
## 設定資料列和資料行屬性  
 您可以設定資料列和資料行的個別屬性，方法是使用 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> 和 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 集合。  
  
#### 若要設定資料列和資料行屬性  
  
1.  從 \[**Windows Form 設計工具**\] 中選取 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。  
  
2.  在 \[**屬性**\] 視窗中，按一下 \[**資料行**\] 項目旁邊的省略 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕，藉此開啟 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 集合。  
  
3.  選取第一個資料行，並將 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 屬性值變更為 <xref:System.Windows.Forms.SizeType>。  按一下 \[**確定**\] 接受變更。  請注意，第一個資料行的寬度會縮小，以符合 <xref:System.Windows.Forms.Button> 控制項。  同時也請注意，資料行的寬度是無法調整的。  
  
4.  在 \[**屬性**\] 視窗中，開啟 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 集合，並選取第一個資料行。  將其 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 屬性的值變更為 <xref:System.Windows.Forms.SizeType>。  按一下 \[**確定**\] 接受變更。  將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項調整為較大的寬度，並且請注意，第一個資料行的寬度會擴充。  將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項調整為較小的寬度，並且請注意，第一個資料行中的按鈕會調整大小以符合儲存格。  同時也請注意，資料行的寬度是可以調整的。  
  
5.  在 \[**屬性**\] 視窗中，開啟 <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> 集合，並選取所有列出的資料行。  將每個 <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> 屬性值都設定為 <xref:System.Windows.Forms.SizeType>。  按一下 \[**確定**\] 接受變更。  使用 <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> 集合重複執行。  
  
6.  抓取其中一個角落縮放控點，並調整 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的寬度和高度。  請注意，資料列和資料行會在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的大小變更時重新調整。  同時也請注意，資料列和資料行可以使用水平或垂直縮放控點調整大小。  
  
## 使用控制項擴展資料列和資料行  
 <xref:System.Windows.Forms.TableLayoutPanel> 控制項會在設計階段時加入數種新屬性至控制項。  這些屬性的其中兩個為 `RowSpan` 和 `ColumnSpan`。  您可以使用這些屬性，讓控制項擴展一個以上的資料列或資料行。  
  
#### 若要使用控制項擴展資料列和資料行  
  
1.  選取第一個資料列和第一個資料行中的 <xref:System.Windows.Forms.Button> 控制項。  
  
2.  在 \[**屬性**\] 視窗中，將 `ColumnSpan` 屬性的值變更為 2。  請注意，<xref:System.Windows.Forms.Button> 控制項會填滿第一個資料行和第二個資料行。  同時也請注意，已經加入額外的資料列以容納這項變更。  
  
3.  重複執行 `RowSpan` 屬性的步驟 2。  
  
## 按兩下工具箱中的控制項以插入該控制項  
 您可以按兩下 \[**工具箱**\] 中的控制項，藉此填入 <xref:System.Windows.Forms.TableLayoutPanel> 控制項。  
  
#### 若要按兩下工具箱中的控制項以插入該控制項  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳至表單。  
  
2.  在 \[**工具箱**\] 中，按兩下 <xref:System.Windows.Forms.Button> 控制項圖示。  請注意，新的按鈕控制項會出現在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的第一個儲存格中。  
  
3.  在 \[**工具箱**\] 中的數個控制項上按兩下。  請注意，新控制項會連續出現在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的未佔用儲存格中。  同時也請注意，如果沒有可以使用的開放儲存格，<xref:System.Windows.Forms.TableLayoutPanel> 控制項會擴充以容納新控制項。  
  
## 溢位的自動處理  
 當您將控制項插入至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項時，可能會用完新控制項的空白儲存格。  <xref:System.Windows.Forms.TableLayoutPanel> 控制項會自動處理這種狀況，方法是增加儲存格數目。  
  
#### 若要觀察溢位的自動處理  
  
1.  如果在 <xref:System.Windows.Forms.TableLayoutPanel> 控制項中仍有空白儲存格，繼續插入新的 <xref:System.Windows.Forms.Button> 控制項，直到 <xref:System.Windows.Forms.TableLayoutPanel> 控制項已滿。  
  
2.  一旦 <xref:System.Windows.Forms.TableLayoutPanel> 控制項已滿，請按兩下 \[**工具箱**\] 中的 <xref:System.Windows.Forms.Button> 圖示，以插入另一個 <xref:System.Windows.Forms.Button> 控制項。  請注意，<xref:System.Windows.Forms.TableLayoutPanel> 控制項會建立新儲存格，以容納新控制項。  再插入數個控制項，並觀察調整大小行為。  
  
3.  將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的 <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> 屬性值變更為 <xref:System.Windows.Forms.TableLayoutPanelGrowStyle>。  按兩下 \[**工具箱**\] 中的 <xref:System.Windows.Forms.Button> 圖示，以插入 <xref:System.Windows.Forms.Button> 控制項，直到 <xref:System.Windows.Forms.TableLayoutPanel> 控制項已滿。  在 \[**工具箱**\] 中，再次按兩下 <xref:System.Windows.Forms.Button> 圖示。  請注意，您會從 \[**Windows Form 設計工具**\] 接收到錯誤訊息，通知您無法建立其他的資料列和資料行。  
  
## 繪製外框以插入控制項  
 您可以插入控制項至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項，並在儲存格中繪製外框，藉此指定大小。  
  
#### 若要繪製外框以插入控制項  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項拖曳至表單。  
  
2.  在 \[**工具箱**\] 中，請按 <xref:System.Windows.Forms.Button> 控制項圖示。  請勿拖曳至表單。  
  
3.  將滑鼠指標移至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項上。  請注意：指標會變成十字形，並且附有 <xref:System.Windows.Forms.Button> 控制項圖示。  
  
4.  按住滑鼠按鈕。  
  
5.  拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.Button> 控制項的外框。  當您對於大小感到滿意時，請放開滑鼠按鍵。  請注意，<xref:System.Windows.Forms.Button> 控制項會建立在您繪製控制項外框的儲存格中。  
  
## 不允許在儲存格中使用多個控制項  
 <xref:System.Windows.Forms.TableLayoutPanel> 控制項在每個儲存格中只能包含一個子控制項。  
  
#### 若要示範不允許在儲存格中使用多個控制項  
  
-   從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Button> 控制項拖曳至 <xref:System.Windows.Forms.TableLayoutPanel> 控制項，並將它放入其中一個佔用的儲存格。  請注意，<xref:System.Windows.Forms.TableLayoutPanel> 控制項不允許您將 <xref:System.Windows.Forms.Button> 控制項放入佔用的儲存格。  
  
## 交換控制項  
 <xref:System.Windows.Forms.TableLayoutPanel> 控制項能讓您交換佔有兩個不同儲存格的控制項。  
  
#### 若要交換控制項  
  
-   從佔用的儲存格中拖曳其中一個 <xref:System.Windows.Forms.Button> 控制項，並將它放入另一個佔用的儲存格。  請注意，這兩個控制項會從一個儲存格移入另一個儲存格。  
  
## 後續步驟  
 您可使用配置面板和控制項的組合，完成複雜的配置。  建議另外再研究以下各項：  
  
-   嘗試將其中一個 <xref:System.Windows.Forms.Button> 控制項調整為較大的大小，並且注意此動作對於配置的作用。  
  
-   將多個控制項的選取範圍貼入 <xref:System.Windows.Forms.TableLayoutPanel> 控制項，並且注意控制項是如何插入的。  
  
-   配置面板可包含其他配置面板。  嘗試將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項放入現有的控制項。  
  
-   將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項停駐至父表單。  調整表單大小，並注意此動作對於配置的作用。  
  
## 請參閱  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. \(USBN: 0\-7356\-0566\-1\)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)   
 [Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/zh-tw/e193b4fc-912a-4917-b036-b76c7a6f58ab)   
 [Walkthrough: Creating a Localizable Windows Form](http://msdn.microsoft.com/zh-tw/c5240b6e-aaca-4286-9bae-778a416edb9c)   
 [TableLayoutPanel 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)   
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [如何：將控制項停駐在 Windows Form 上](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [如何：錨定 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)   
 [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)