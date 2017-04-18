---
title: "收集筆墨 | Microsoft Docs"
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
  - "收集數位筆墨"
  - "DefaultDrawingAttributes 屬性"
  - "數位筆墨, 收集"
  - "DrawingAttributes 屬性"
  - "筆墨, 收集"
  - "InkCanvas 項目"
  - "屬性, DefaultDrawingAttributes"
  - "屬性, DrawingAttributes"
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 收集筆墨
[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) 平台會收集數位筆墨，做為其中一部分的核心功能。  這個主題將討論 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 中的筆墨收集方法。  
  
## 必要條件  
 您必須先安裝 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] 和 [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]，才能使用下列範例。  也應該瞭解如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式。  如需開始使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的詳細資訊，請參閱 [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## 使用 InkCanvas 項目  
 <xref:System.Windows.Controls.InkCanvas> 項目會提供在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中收集筆墨最簡易的方法。  <xref:System.Windows.Controls.InkCanvas> 項目與 [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] 和較早版本中的 <xref:Microsoft.Ink.InkOverlay> 物件類似。  
  
 使用 <xref:System.Windows.Controls.InkCanvas> 項目以接收和顯示筆墨輸入。  您通常是使用手寫筆來輸入筆墨，這會與數位板互動而產生筆墨筆劃。  此外，滑鼠也用來代替手寫筆。  建立的筆劃表示為 <xref:System.Windows.Ink.Stroke> 物件，且可以應由程式設計和使用者輸入加以操作。  <xref:System.Windows.Controls.InkCanvas>可讓使用者選取、修改或刪除現有的 <xref:System.Windows.Ink.Stroke>。  
  
 透過使用 XAML，您可以設定筆墨集合，就像將 `InkCanvas` 項目加入至樹狀目錄一樣輕鬆。  下列範例會將 <xref:System.Windows.Controls.InkCanvas> 加入在 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] 中建立的預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 專案。  
  
 [!code-xml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 `InkCanvas` 項目也可以包含子項目，以便將筆墨附註加入至幾乎所有類型的 XAML 項目。  例如，如果要將筆墨功能加入至文字項目，只要將之設為 <xref:System.Windows.Controls.InkCanvas> 的子系即可。  
  
 [!code-xml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 使用筆墨支援產生影像的作法也一樣簡單。  
  
 [!code-xml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### InkCollection 模式  
 <xref:System.Windows.Controls.InkCanvas> 透過其 <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> 屬性提供對各種輸入模式的支援。  
  
### 操作筆墨  
 <xref:System.Windows.Controls.InkCanvas> 提供對許多筆墨編輯作業的支援。  例如，<xref:System.Windows.Controls.InkCanvas> 支援畫筆背面清除功能，且不需要額外的程式碼，即可將功能加入至項目中。  
  
#### Selection  
 設定選取模式就像將 <xref:System.Windows.Controls.InkCanvasEditingMode> 屬性設定為 **Select** 一樣簡單。  下列程式碼會根據 <xref:System.Windows.Forms.CheckBox> 的值設定編輯模式：  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### DrawingAttributes  
 使用 <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> 屬性變更筆墨筆劃的外觀。  例如，<xref:System.Windows.Ink.DrawingAttributes> 的 <xref:System.Windows.Ink.DrawingAttributes.Color%2A> 成員會設定所呈現之 <xref:System.Windows.Ink.Stroke> 的色彩。  下列範例會將選取之筆劃的色彩變更為紅色。  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### DefaultDrawingAttributes  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> 屬性會提供要在 <xref:System.Windows.Controls.InkCanvas> 中建立之筆劃的屬性 \(例如，高度、寬度和色彩\)。  變更 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> 之後，所有在未來輸入 <xref:System.Windows.Controls.InkCanvas> 的筆劃都會以新的屬性值呈現。  
  
 除了在程式碼後置檔案中修改 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> 之外，您也可以使用 XAML 語法來指定 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> 屬性。  下列 XAML 程式碼會示範如何設定 <xref:System.Windows.Ink.DrawingAttributes.Color%2A> 屬性。  若要使用這個程式碼，請在 Visual Studio 2005 中建立名為 "HelloInkCanvas" 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 新專案。  使用下列程式碼取代 Window1.xaml 檔案中的程式碼。  
  
 [!code-xml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 接下來，將下列按鈕事件處理常式加入至 Window1 類別內的程式碼後置檔案。  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 複製這個程式碼之後，請按下 Microsoft Visual Studio 2005 中的 **F5** 在偵錯工具中執行程式。  
  
 請注意 <xref:System.Windows.Controls.StackPanel> 在 <xref:System.Windows.Controls.InkCanvas> 頂端放置按鈕的方式。  如果您想在按鈕頂端加上筆墨，<xref:System.Windows.Controls.InkCanvas> 便會收集和呈現按鈕後面的筆墨。  這是因為按鈕和 <xref:System.Windows.Controls.InkCanvas> 屬於同層級，而與子系相反。  此外，按鈕會處於疊置順序中的較高位置，因此筆墨會在按鈕後面呈現。  
  
## 請參閱  
 <xref:System.Windows.Ink.DrawingAttributes>   
 <xref:System.Windows.InkCanvas.DefaultDrawingAttributes%2A>   
 <xref:System.Windows.Ink>