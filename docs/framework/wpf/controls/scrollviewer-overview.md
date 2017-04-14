---
title: "ScrollViewer 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "控制項, ScrollViewer"
  - "ScrollViewer 控制項, 關於 ScrollViewer 控制項"
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# ScrollViewer 概觀
使用者介面中的內容通常會大於電腦螢幕的顯示區域。  <xref:System.Windows.Controls.ScrollViewer> 控制項提供便利的方式，讓您可以捲動 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中的內容。  本主題將介紹 <xref:System.Windows.Controls.ScrollViewer> 項目並且提供多個使用範例。  
  
 此主題包括下列章節：  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [ScrollViewer 控制項](#what_is_a_scrollviewer_element)  
  
-   [實體與邏輯捲動的比較](#scrollviewer_physical_vs_logical)  
  
-   [定義和使用 ScrollViewer 項目](#scrollviewer_markup_syntax_and_sample)  
  
-   [設定 ScrollViewer 的樣式](#scrollviewer_styling_scrollviewer)  
  
-   [分頁文件](#scrollviewer_scroll_vs_paginate)  
  
-   [Related Topics](#seeAlsoToggle)  
  
<a name="what_is_a_scrollviewer_element"></a>   
## ScrollViewer 控制項  
 有含兩個預先定義的項目，可以讓您在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中捲動：<xref:System.Windows.Controls.Primitives.ScrollBar> 和 <xref:System.Windows.Controls.ScrollViewer>。  <xref:System.Windows.Controls.ScrollViewer> 控制項會封裝水平與垂直的 <xref:System.Windows.Controls.Primitives.ScrollBar> 項目和內容容器 \(例如，<xref:System.Windows.Controls.Panel> 項目\)，才能在可捲動區域中顯示其他可見的項目。  您必須建置自訂物件，才能使用 <xref:System.Windows.Controls.Primitives.ScrollBar> 項目來捲動內容。  但是，您可以使用 <xref:System.Windows.Controls.ScrollViewer> 項目本身，因為此項目是會封裝 <xref:System.Windows.Controls.Primitives.ScrollBar> 功能的複合控制項。  
  
 <xref:System.Windows.Controls.ScrollViewer> 控制項會同時回應滑鼠和鍵盤命令，並定義許多方法，使用預先決定的遞增量來捲動內容。  您可以使用 <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> 事件來偵測 <xref:System.Windows.Controls.ScrollViewer> 狀態中的變更。  
  
 <xref:System.Windows.Controls.ScrollViewer> 只能有一個子系，通常是 <xref:System.Windows.Controls.Panel> 項目，此項目可裝載項目的 <xref:System.Windows.Controls.Panel.Children%2A> 集合。  <xref:System.Windows.Controls.ContentPresenter.Content%2A> 屬性會定義 <xref:System.Windows.Controls.ScrollViewer> 的唯一子系。  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## 實體與邏輯捲動的比較  
 實體捲動會以預先決定之實體遞增量捲動內容，通常是以像素宣告的值。  邏輯捲動用於捲動邏輯樹狀目錄中的下一個項目。  實體捲動對大多數 <xref:System.Windows.Controls.Panel> 項目而言是預設的捲動行為。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援兩種類型的捲動。  
  
#### IScrollInfo 介面  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> 介面表示 <xref:System.Windows.Controls.ScrollViewer> 中的主要捲動區域或衍生控制項。  介面會定義捲動可由 <xref:System.Windows.Controls.Panel> 實作的屬性和方法，這些屬性和方法必須以邏輯單位捲動，而不是以實體遞增量捲動。  將 <xref:System.Windows.Controls.Primitives.IScrollInfo> 的執行個體轉換為衍生的 <xref:System.Windows.Controls.Panel>，然後使用其捲動方法，提供捲動至子系集合中下一個邏輯單位的有用方法，而不是以像素遞增量進行捲動。  根據預設，<xref:System.Windows.Controls.ScrollViewer> 控制項支援以實體單位進行捲動。  
  
 <xref:System.Windows.Controls.StackPanel> 和 <xref:System.Windows.Controls.VirtualizingStackPanel> 同時實作 <xref:System.Windows.Controls.Primitives.IScrollInfo> 而且原本就會支援邏輯捲動。  對於原本就支援邏輯捲動的版面配置控制項，您仍然可以透過包裝 <xref:System.Windows.Controls.ScrollViewer> 中的主 <xref:System.Windows.Controls.Panel> 項目，並將 <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> 屬性設定為 `false`。  
  
 下列程式碼範例會示範如何將 <xref:System.Windows.Controls.Primitives.IScrollInfo> 的執行個體轉換為 <xref:System.Windows.Controls.StackPanel>，以及使用介面定義的內容捲動方法 \(<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> 和 <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>\)。  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## 定義和使用 ScrollViewer 項目  
 下列範例會在視窗中建立含有某些文字和一個矩形的 <xref:System.Windows.Controls.ScrollViewer>。  <xref:System.Windows.Controls.Primitives.ScrollBar> 項目只會在必要時才顯示。  當您重新調整視窗大小時，因為 <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> 更新值和 <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> 屬性的緣故，<xref:System.Windows.Controls.Primitives.ScrollBar> 項目會出現然後消失。  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## 設定 ScrollViewer 的樣式  
 和 Windows Presentation Foundation 中所有控制項一樣，可設定 <xref:System.Windows.Controls.ScrollViewer> 的樣式，來變更控制項的預設呈現行為。  如需控制項樣式設定的額外資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## 分頁文件  
 就文件內容而言，另一個捲動的方法是選擇支援分頁的文件容器。  <xref:System.Windows.Documents.FlowDocument> 是針對設計裝載於檢視控制項 \(例如 <xref:System.Windows.Controls.FlowDocumentPageViewer>\) 內的文件，而檢視控制項支援跨多個頁面來編頁內容，以避免捲動。  <xref:System.Windows.Controls.DocumentViewer> 提供方案來檢視 <xref:System.Windows.Documents.FixedDocument> 內容，這種方案使用傳統捲動來顯示不在顯示區範圍內的內容。  
  
 如需文件格式和展示選項的額外資訊，請參閱 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)。  
  
## 請參閱  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.Primitives.ScrollBar>   
 <xref:System.Windows.Controls.Primitives.IScrollInfo>   
 [Create a Scroll Viewer](http://msdn.microsoft.com/zh-tw/c8e46af7-b417-441b-aa30-791cbdbd43ef)   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [ScrollBar 樣式和範本](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)   
 [控制項](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)