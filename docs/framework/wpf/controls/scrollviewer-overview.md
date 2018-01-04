---
title: "ScrollViewer 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d060e0b511f17a68edb013ae7241e1accbc7dcf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="scrollviewer-overview"></a>ScrollViewer 概觀
使用者介面內的內容常常會大於電腦螢幕的顯示區域。 <xref:System.Windows.Controls.ScrollViewer>控制項提供便利的方式，若要啟用的內容中捲動[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式。 本主題將介紹<xref:System.Windows.Controls.ScrollViewer>項目，並提供數種使用方式範例。  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>ScrollViewer 控制項  
 有兩個預先定義的項目啟用捲動功能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式：<xref:System.Windows.Controls.Primitives.ScrollBar>和<xref:System.Windows.Controls.ScrollViewer>。 <xref:System.Windows.Controls.ScrollViewer>控制項封裝水平和垂直<xref:System.Windows.Controls.Primitives.ScrollBar>項目和內容的容器 (例如<xref:System.Windows.Controls.Panel>元素) 以顯示其他可見元素的可捲動區域中。 您必須建立自訂物件，才能使用<xref:System.Windows.Controls.Primitives.ScrollBar>內容捲動的項目。 不過，您可以使用<xref:System.Windows.Controls.ScrollViewer>單獨使用的項目，因為它是複合控制項封裝<xref:System.Windows.Controls.Primitives.ScrollBar>功能。  
  
 <xref:System.Windows.Controls.ScrollViewer>控制回應滑鼠和鍵盤命令，並定義許多方法，用來捲動預先決定的增量的內容。 您可以使用<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>事件來偵測變更<xref:System.Windows.Controls.ScrollViewer>狀態。  
  
 A<xref:System.Windows.Controls.ScrollViewer>通常只能有一個子系，<xref:System.Windows.Controls.Panel>項目，可裝載<xref:System.Windows.Controls.Panel.Children%2A>項目的集合。 <xref:System.Windows.Controls.ContentPresenter.Content%2A>屬性定義的唯一子系<xref:System.Windows.Controls.ScrollViewer>。  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>實體捲動與邏輯捲動的比較  
 實體捲動可用來依預先決定的實體遞增值 (通常是以像素為單位宣告的值) 捲動內容。 邏輯捲動可用來捲動至邏輯樹狀結構中的下一個項目。 實體捲動是預設的捲動行為，適用於大部分<xref:System.Windows.Controls.Panel>項目。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 同時支援這兩種類型的捲動。  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo 介面  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>介面代表主要捲動區域內<xref:System.Windows.Controls.ScrollViewer>或衍生的控制項。 介面會定義捲動屬性和方法，可由實作<xref:System.Windows.Controls.Panel>需要捲動邏輯單元，而非實體的遞增值的項目。 轉型的執行個體<xref:System.Windows.Controls.Primitives.IScrollInfo>來衍生<xref:System.Windows.Controls.Panel>，然後使用它的捲動方法提供實用的方式，捲動至下一個邏輯單元中子集合，而不是像素。 根據預設，<xref:System.Windows.Controls.ScrollViewer>控制項支援捲動實體單位。  
  
 <xref:System.Windows.Controls.StackPanel>和<xref:System.Windows.Controls.VirtualizingStackPanel>兩者實作<xref:System.Windows.Controls.Primitives.IScrollInfo>和原生方式支援邏輯捲動。 針對版面配置控制項的原生支援邏輯捲動，您仍然可以達到包裝主機的實體捲動<xref:System.Windows.Controls.Panel>中的項目<xref:System.Windows.Controls.ScrollViewer>和設定<xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>屬性`false`。  
  
 下列程式碼範例示範如何轉型的執行個體<xref:System.Windows.Controls.Primitives.IScrollInfo>至<xref:System.Windows.Controls.StackPanel>並使用內容捲動方法 (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>和<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) 介面所定義。  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>定義和使用 ScrollViewer 元素  
 下列範例會建立<xref:System.Windows.Controls.ScrollViewer>視窗，其中包含一些文字和矩形中。 <xref:System.Windows.Controls.Primitives.ScrollBar>元素會顯示只有當他們有必要。 當您調整視窗<xref:System.Windows.Controls.Primitives.ScrollBar>項目出現，而且會消失，因為已更新的值，所以<xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A>和<xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>屬性。  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>設定 ScrollViewer 的樣式  
 要在 Windows Presentation Foundation 中，所有控制項<xref:System.Windows.Controls.ScrollViewer>可以套用樣式，以變更控制項的預設轉譯行為。 如需有關控制項樣式設定的其他資訊，請參閱[樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>文件分頁  
 就文件內容而言，捲動的替代方案是選擇一個支援分頁的文件容器。 <xref:System.Windows.Documents.FlowDocument>適用於文件，專為將服務裝載在檢視控制項，例如<xref:System.Windows.Controls.FlowDocumentPageViewer>，跨多個頁面，這樣就不需要捲動支援分頁的內容。 <xref:System.Windows.Controls.DocumentViewer>提供的檢視解決方案<xref:System.Windows.Documents.FixedDocument>使用傳統捲動顯示內容以外的領域的顯示區域的內容。  
  
 如需有關文件格式和呈現方式選項的其他資訊，請參閱 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [建立捲動檢視器](http://msdn.microsoft.com/en-us/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [ScrollBar 樣式和範本](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)  
 [控制項](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
