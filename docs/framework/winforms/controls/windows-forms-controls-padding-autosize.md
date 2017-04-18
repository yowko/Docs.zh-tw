---
title: "逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Form 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Margin.Bottom"
  - "Margin.Left"
  - "Margin.Top"
  - "Margin.All"
  - "Margin.Right"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "AutoSize 屬性, 逐步解說"
  - "版面配置 [Windows Form], 邊界和邊框距離"
  - "Margin 屬性 [Windows Form], 逐步解說"
  - "Padding 屬性 [Windows Form], 逐步解說"
  - "逐步解說 [Windows Form], 配置"
  - "Windows Form, 配置"
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# 逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Form 控制項
表單控制項的精確置放對許多應用程式而言非常重要。  \[**Windows Form 設計工具**\] 能提供您許多配置工具以完成這項作業。  三個最重要的工具是 <xref:System.Windows.Forms.Control.Margin%2A>、<xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性，在所有 Windows Form 控制項上都有這些屬性。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> 屬性會定義控制項周圍的空間，讓其他控制項與該控制項的邊框保持特定的距離。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> 屬性會定義控制項內部的空間，讓控制項的內容 \(例如，<xref:System.Windows.Forms.Control.Text%2A> 屬性的值\) 與控制項的框線保持指定的距離。  
  
 下列圖例顯示控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。  
  
 ![Windows Form 控制項的邊框距離和邊界](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS\_WinFormPadMargin")  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性會告訴控制項自動調整大小，以符合控制項的內容。  該控制項不會調整至小於原始 <xref:System.Windows.Forms.Control.Size%2A> 屬性的值，且會考慮 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值。  
  
 逐步解說將說明的工作包括：  
  
-   建立 Windows Form 專案  
  
-   設定控制項的邊界  
  
-   設定控制項的邊框距離  
  
-   自動調整控制項大小  
  
 當您完成時，將會對這些重要的配置功能所扮演的角色有所了解。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   擁有足夠的使用權限，可以在安裝 Visual Studio 的電腦上建立並執行 Windows Form 應用程式專案。  
  
## 建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### 若要建立專案  
  
1.  建立名為 `LayoutExample` 的 \[**Windows 應用程式**\] 專案。  如需詳細資訊，請參閱[How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  從 \[**Windows Form 設計工具**\] 中選取表單。  
  
## 設定控制項的邊界  
 您可以使用 <xref:System.Windows.Forms.Control.Margin%2A> 屬性，設定控制項之間的預設距離。  當您將控制項移至夠靠近另一個控制項時，會看見顯示兩個控制項之邊界的對齊線。  您移動的控制項將會貼齊至邊界所定義的距離。  
  
#### 若要使用 Margin 屬性排列表單上的控制項  
  
1.  從 \[**工具箱**\] 將兩個 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  
  
2.  選取其中一個 <xref:System.Windows.Forms.Button> 控制項，並將它移動至靠近另一個控制項，直到幾乎彼此接觸為止。  
  
     觀察出現在它們之間的對齊線。  這個距離是兩個控制項之 <xref:System.Windows.Forms.Control.Margin%2A> 值的總和。  您所移動的控制項會貼齊至這個距離。  如需詳細資訊，請參閱[逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。  
  
3.  在 \[**屬性**\] 視窗中展開 <xref:System.Windows.Forms.Control.Margin%2A> 項目，並將 <xref:System.Windows.Forms.Padding.All%2A> 屬性設定為 20，藉此變更其中一個控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。  
  
4.  選取其中一個 <xref:System.Windows.Forms.Button> 控制項，並將它移至靠近另一個控制項。  
  
     定義邊界值總和的對齊線比較長，且該控制項會貼齊至離其他控制項較遠的距離。  
  
5.  在 \[**屬性**\] 視窗中展開 <xref:System.Windows.Forms.Control.Margin%2A> 項目，並將 <xref:System.Windows.Forms.Padding.Top%2A> 屬性設定為 5，藉此變更選取控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。  
  
6.  移動其他控制項下方的選取控制項，並且觀察對齊線會較短。  將選取的控制項移動至其他控制項的左邊，然後觀察對齊線會保留在步驟 4 中所觀察到的值。  
  
7.  您可以將 <xref:System.Windows.Forms.Control.Margin%2A> 屬性的每一個方面 \(<xref:System.Windows.Forms.Padding.Left%2A>、<xref:System.Windows.Forms.Padding.Top%2A>、<xref:System.Windows.Forms.Padding.Right%2A>、<xref:System.Windows.Forms.Padding.Bottom%2A>\) 設定為不同的值，或者您可以使用 <xref:System.Windows.Forms.Padding.All%2A> 屬性將它們全部設定成相同的值。  
  
## 設定控制項的邊框距離  
 若要達到應用程式所需要的精準配置，您的控制項通常會包含子控制項。  當您想要指定子控制項邊框與父控制項邊框之間的相距時，請一起使用父控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性和子控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。  <xref:System.Windows.Forms.Control.Padding%2A> 屬性也用來控制控制項的內容與邊框之間的相距 \(例如，<xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性\)。  
  
#### 若要使用邊框距離排列表單上的控制項  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  
  
2.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值變更為 `true`。  
  
3.  在 \[**屬性**\] 視窗中展開 <xref:System.Windows.Forms.Control.Padding%2A> 項目，並將 <xref:System.Windows.Forms.Padding.All%2A> 屬性設定為 5，藉此變更 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。  
  
     控制項會展開以提供空間給新的邊框距離。  
  
4.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.GroupBox> 控制項拖曳至表單。  將 <xref:System.Windows.Forms.Button> 控制項從 \[**工具箱**\] 拖曳至 <xref:System.Windows.Forms.GroupBox> 控制項。  放置 <xref:System.Windows.Forms.Button> 控制項，讓控制項與 <xref:System.Windows.Forms.GroupBox> 控制項的右下角一起清除。  
  
     觀察當 <xref:System.Windows.Forms.Button> 控制項接近 <xref:System.Windows.Forms.GroupBox> 控制項的下方和右邊緣時，所出現的對齊線。  這些對齊線會對應至 <xref:System.Windows.Forms.Button> 的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。  
  
5.  在 \[**屬性**\] 視窗中展開 <xref:System.Windows.Forms.Control.Padding%2A> 項目，並將 <xref:System.Windows.Forms.Padding.All%2A> 屬性設定為 20，藉此變更 <xref:System.Windows.Forms.GroupBox> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。  
  
6.  選取 <xref:System.Windows.Forms.GroupBox> 控制項中的 <xref:System.Windows.Forms.Button> 控制項，並將它往 <xref:System.Windows.Forms.GroupBox> 的中心方向移動。  
  
     對齊線會顯示為大於 <xref:System.Windows.Forms.GroupBox> 控制項邊框的距離。  這個距離是 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性和 <xref:System.Windows.Forms.GroupBox> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性的總和。  
  
## 自動調整控制項大小  
 在一些應用程式中，控制項在執行階段的大小與在設計階段的大小不相同。  例如，<xref:System.Windows.Forms.Button> 控制項的文字，可能是來自資料庫，而文字的長度將不會預先知道。  
  
 當 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性設定為 `true` 時，控制項會自行調整大小，以符合內容。  如需詳細資訊，請參閱 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。  
  
#### 若要使用 AutoSize 屬性排列表單上的控制項  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  
  
2.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值變更為 `true`。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性變更為 "This button has a long string for its Text property."。  
  
     當您認可變更時，<xref:System.Windows.Forms.Button> 控制項會自行調整大小，以符合新文字內容。  
  
4.  從 \[**工具箱**\] 將另一個 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  
  
5.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性變更為 "This button has a long string for its Text property."。  
  
     當您認可變更時，<xref:System.Windows.Forms.Button> 控制項不會自行調整大小，而控制項的右邊緣會裁剪文字。  
  
6.  在 \[**屬性**\] 視窗中展開 <xref:System.Windows.Forms.Control.Padding%2A> 項目，並將 <xref:System.Windows.Forms.Padding.All%2A> 屬性設定為 5，藉此變更 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。  
  
     控制項內部的文字會在所有四個方向上進行裁剪。  
  
7.  將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性變更為 `true`。  
  
     <xref:System.Windows.Forms.Button> 控制項會調整大小以包含整個字串。  此外，已經在文字周圍加入邊框距離，這會造成 <xref:System.Windows.Forms.Button> 控制項往所有四個方向展開。  
  
8.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  將它放置在表單右下角的附近。  
  
9. 將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值變更為 `true`。  
  
10. 將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設定為 <xref:System.Windows.Forms.AnchorStyles> 和 <xref:System.Windows.Forms.AnchorStyles>。  
  
11. 將 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性變更為 "This button has a long string for its Text property."。  
  
     當您認可變更時，<xref:System.Windows.Forms.Button> 控制項會自行向左邊調整大小。  通常，自動調整大小會增加與 <xref:System.Windows.Forms.Control.Anchor%2A> 屬性設定相反方向的控制項大小。  
  
## AutoSize 和 AutoSizeMode 屬性  
 某些控制項支援 `AutoSizeMode` 屬性，此屬性會提供比控制項的自動調整大小行為還要詳細的控制項。  
  
#### 若要使用 AutoSizeMode 屬性  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.Panel> 控制項拖曳至表單。  
  
2.  將 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.AutoSize%2A> 屬性值設定為 `true`。  
  
3.  將 <xref:System.Windows.Forms.Button> 控制項從 \[**工具箱**\] 拖曳至 <xref:System.Windows.Forms.Panel> 控制項。  
  
4.  將 <xref:System.Windows.Forms.Button> 控制項放置在 <xref:System.Windows.Forms.Panel> 控制項的右下角附近。  
  
5.  選取 <xref:System.Windows.Forms.Panel> 控制項並抓取右下角的縮放控點 \(Sizing Handle\)。  將 <xref:System.Windows.Forms.Panel> 控制項的大小調整為較大或較小。  
  
    > [!NOTE]
    >  您可以自由調整 <xref:System.Windows.Forms.Panel> 控制項的大小，但是不能讓它小於 <xref:System.Windows.Forms.Button> 控制項右下角的位置。  這個行為是由 `AutoSizeMode` 屬性的預設值所指定，即是 <xref:System.Windows.Forms.AutoSizeMode>。  
  
6.  將 <xref:System.Windows.Forms.Panel> 控制項的 `AutoSizeMode` 屬性值設定為 <xref:System.Windows.Forms.AutoSizeMode>。  
  
     <xref:System.Windows.Forms.Panel> 控制項會調整大小以圍繞 <xref:System.Windows.Forms.Button> 控制項。  您無法調整 <xref:System.Windows.Forms.Panel> 控制項大小。  
  
7.  將 <xref:System.Windows.Forms.Button> 控制項往 <xref:System.Windows.Forms.Panel> 控制項的左上角拖曳。  
  
     <xref:System.Windows.Forms.Panel> 控制項會調整大小至 <xref:System.Windows.Forms.Button> 控制項的新位置。  
  
## 後續步驟  
 在 Windows Form 應用程式中有排列控制項的許多其他配置功能。  您可能會想嘗試某些組合：  
  
-   使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項建置表單。  如需詳細資訊，請參閱[逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。  嘗試變更 <xref:System.Windows.Forms.TableLayoutPanel> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值，以及在子控制項上的 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。  
  
-   使用 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項嘗試相同的實驗。  如需詳細資訊，請參閱[逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)。  
  
-   使用 <xref:System.Windows.Forms.Panel> 控制項中的停駐子控制項做實驗。  <xref:System.Windows.Forms.Control.Padding%2A> 屬性是 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> 屬性的較通用版本，您可以將子控制項放置在 <xref:System.Windows.Forms.Panel> 控制項中，並將子控制項的 <xref:System.Windows.Forms.Control.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle>，藉此自我滿足。  將 <xref:System.Windows.Forms.Panel> 控制項的 <xref:System.Windows.Forms.Control.Padding%2A> 屬性設定為各種值，並注意其效果。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.AutoSize%2A>   
 <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>   
 <xref:System.Windows.Forms.Control.Margin%2A>   
 <xref:System.Windows.Forms.Control.Padding%2A>   
 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)