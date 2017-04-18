---
title: "使用自動配置概觀 | Microsoft Docs"
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
  - "自動配置"
  - "配置, 自動"
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 使用自動配置概觀
本主題向開發人員介紹以可當地語系化的[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] 撰寫 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式的方針。  在過去，將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 當地語系化是一項非常費時的程序。  每當 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 需要顯示新的語言就必須逐一調整像素。  現在有了正確的設計和編碼標準，[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的建構就可以更簡單，進而減少當地語系化人員調整大小和位置的工作。  這種使應用程式的大小和位置更容易調整的撰寫方法稱為「自動配置」，可以使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式設計來達成。  
  
 本主題包含下列章節。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [使用自動配置的優點](#advantages_of_autolayout)  
  
-   [自動配置和控制項](#autolayout_controls)  
  
-   [自動配置和編碼標準](#autolayout_coding)  
  
-   [自動配置和格線](#autolay_grids)  
  
-   [使用 IsSharedSizeScope 屬性的自動配置和格線](#autolay_grids_issharedsizescope)  
  
-   [相關主題](#seeAlsoToggle)  
  
<a name="advantages_of_autolayout"></a>   
## 使用自動配置的優點  
 因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 展示系統強大且有彈性，所以可以在應用程式中針對不同語言的需求來配置項目。  下表指出部分自動配置的優點。  
  
-   在任何語言中，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 都能正常顯示。  
  
-   減少文字轉譯之後重新調整控制項位置和大小的需要。  
  
-   減少重新調整視窗大小的需要。  
  
-   在任何語言中，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 配置都能適當呈現。  
  
-   減少當地語系化的工作，幾乎只要翻譯字串就能完成。  
  
<a name="autolayout_controls"></a>   
## 自動配置和控制項  
 自動配置可以讓應用程式自動調整控制項的大小。  例如，控制項可以隨文字長度調整。  這項功能讓當地語系化人員可以翻譯字串，而不再需要調整控制項大小以符合翻譯後文字的大小。  下列範例會建立具有英文內容的按鈕。  
  
 [!code-xml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 在這個範例中，要變成西班牙文按鈕只需要變更文字。  例如：  
  
 [!code-xml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 下圖顯示程式碼範例的輸出。  
  
 ![按鈕相同，但文字的語言不同](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
可自動調整大小的按鈕  
  
<a name="autolayout_coding"></a>   
## 自動配置和編碼標準  
 使用自動配置方法需要一組編碼、設計標準及規則，才能產生可完全當地語系化的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  下列方針會協助自動配置編碼。  
  
|編碼標準|描述|  
|----------|--------|  
|請勿使用絕對位置。|-   請勿使用 <xref:System.Windows.Controls.Canvas>，因為它會設定項目的絕對位置。<br />-   使用 <xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.StackPanel> 及 <xref:System.Windows.Controls.Grid> 來放置控制項。<br />-   如需各類面板的討論，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。|  
|請勿對視窗設定固定大小。|-   使用 <xref:System.Windows.Window.SizeToContent%2A>。<br />-   例如：<br /><br /> [!code-xml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]|  
|加入 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。|<ul><li>將 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 加入至應用程式的根項目。</li><li>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一種便利的方式來支援水平、雙向和垂直的版面配置。  在展示架構中，<xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性可以用來定義配置。  行文方向模式有：<br /><br /> <ul><li><xref:System.Windows.FlowDirection> \(LrTb\) \- 適用於拉丁文、東亞文字等的水平版面配置。</li><li><xref:System.Windows.FlowDirection> \(RlTb\) \- 適用於阿拉伯文、希伯來文等的雙向版面配置。</li></ul></li></ul>|  
|使用複合字型而非實體字型 \(Physical Font\)。|<ul><li>使用複合字型，<xref:System.Windows.Controls.Control.FontFamily%2A> 屬性就不需要當地語系化。</li><li>開發人員可以使用下列其中一種字型或自行建立字型。<br /><br /> <ul><li>Global User Interface</li><li>Global San Serif</li><li>Global Serif</li></ul></li></ul>|  
|加入 xml:lang。|-   將 `xml:lang` 屬性加入至 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的根項目，例如代表英文應用程式的 `xml:lang="en-US"`。<br />-   因為複合字型是使用 `xml:lang` 決定要使用的字型，所以請設定這個屬性以支援多語系案例。|  
  
<a name="autolay_grids"></a>   
## 自動配置和格線  
 <xref:System.Windows.Controls.Grid> 項目對於自動配置相當有用，因為它可以讓開發人員放置項目。  <xref:System.Windows.Controls.Grid> 控制項可以在其子項目之間使用欄和列排列的方式分配可用空間。  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目可以橫跨多個儲存格，因此格線內還可以有格線。  格線相當有用，因為它們可以讓您建立並放置複雜的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  下列範例示範使用格線來放置部分按鈕和文字。  請注意，儲存格的高度和寬度是設為 <xref:System.Windows.GridUnitType>，因此包含影像按鈕的儲存格會隨影像調整大小。  
  
 [!code-xml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 下圖顯示上述程式碼產生的格線。  
  
 ![格線範例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob\_grid")  
Grid  
  
<a name="autolay_grids_issharedsizescope"></a>   
## 使用 IsSharedSizeScope 屬性的自動配置和格線  
 <xref:System.Windows.Controls.Grid> 項目在可當地語系化的應用程式中相當實用，可以建立隨內容大小調整的控制項。  但是，有時候您會想要讓控制項維持特定大小，不論內容有多大。  例如，如果您有 \[確定\]、\[取消\] 及 \[瀏覽\] 按鈕，可能就不希望按鈕隨內容調整大小。  在此情況下 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=fullName> 附加屬性相當實用，可在多個格線項目之間共用相同的大小。  下列範例示範如何在多個 <xref:System.Windows.Controls.Grid> 項目之間共用欄和列的大小資料。  
  
 [!code-xml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **注意**：如需完整程式碼範例，請參閱 [在格線之間共用調整大小屬性](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## 請參閱  
 [WPF 的全球化](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)   
 [使用自動配置建立按鈕](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)   
 [針對自動配置使用格線](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)