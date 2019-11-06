---
title: ScrollViewer 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 993f3c861cbead88df3503eb01f18e5d1f69e2d8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458430"
---
# <a name="scrollviewer-overview"></a>ScrollViewer 概觀
使用者介面內的內容常常會大於電腦螢幕的顯示區域。 <xref:System.Windows.Controls.ScrollViewer> 控制項提供便利的方式來啟用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中的內容滾動。 本主題將介紹 <xref:System.Windows.Controls.ScrollViewer> 元素，並提供數個使用範例。  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>ScrollViewer 控制項  
 有兩個預先定義的元素可讓您在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中進行滾動： <xref:System.Windows.Controls.Primitives.ScrollBar> 和 <xref:System.Windows.Controls.ScrollViewer>。 <xref:System.Windows.Controls.ScrollViewer> 控制項會封裝水準和垂直 <xref:System.Windows.Controls.Primitives.ScrollBar> 元素和內容容器（例如 <xref:System.Windows.Controls.Panel> 元素），以便在可捲動區域中顯示其他可見的元素。 您必須建立自訂物件，才能使用 <xref:System.Windows.Controls.Primitives.ScrollBar> 元素進行內容滾動。 不過，您可以單獨使用 <xref:System.Windows.Controls.ScrollViewer> 元素，因為它是封裝 <xref:System.Windows.Controls.Primitives.ScrollBar> 功能的複合控制項。  
  
 <xref:System.Windows.Controls.ScrollViewer> 控制項會同時回應滑鼠和鍵盤命令，並定義許多用來以預先決定的增量來滾動內容的方法。 您可以使用 <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> 事件來偵測 <xref:System.Windows.Controls.ScrollViewer> 狀態的變更。  
  
 <xref:System.Windows.Controls.ScrollViewer> 只能有一個子系，通常是可以裝載 <xref:System.Windows.Controls.Panel.Children%2A> 元素集合的 <xref:System.Windows.Controls.Panel> 專案。 <xref:System.Windows.Controls.ContentPresenter.Content%2A> 屬性會定義 <xref:System.Windows.Controls.ScrollViewer>的唯一子系。  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>實體與邏輯滾動  
 實體捲動可用來依預先決定的實體遞增值 (通常是以像素為單位宣告的值) 捲動內容。 邏輯捲動可用來捲動至邏輯樹狀結構中的下一個項目。 實體滾動是大部分 <xref:System.Windows.Controls.Panel> 元素的預設捲軸行為。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 同時支援這兩種類型的捲動。  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo 介面  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> 介面代表 <xref:System.Windows.Controls.ScrollViewer> 或衍生控制項內的主要捲動區域。 介面會定義滾動屬性和方法，而這些專案可以由需要依邏輯單元（而不是實體增量）進行滾動的 <xref:System.Windows.Controls.Panel> 元素來執行。 將 <xref:System.Windows.Controls.Primitives.IScrollInfo> 的實例轉型為衍生的 <xref:System.Windows.Controls.Panel>，然後使用其滾動方法，可讓您在子集合中的下一個邏輯單元中滾動，而不是以圖元增量的方式。 根據預設，<xref:System.Windows.Controls.ScrollViewer> 控制項支援依實體單位來滾動。  
  
 <xref:System.Windows.Controls.StackPanel> 和 <xref:System.Windows.Controls.VirtualizingStackPanel> 都會執行 <xref:System.Windows.Controls.Primitives.IScrollInfo> 並原生支援邏輯滾動。 對於原生支援邏輯滾動的版面配置控制項，您仍然可以藉由將主機 <xref:System.Windows.Controls.Panel> 專案包裝在 <xref:System.Windows.Controls.ScrollViewer> 中，並將 <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> 屬性設定為 `false`來達到實際滾動。  
  
 下列程式碼範例示範如何將 <xref:System.Windows.Controls.Primitives.IScrollInfo> 的實例轉換成 <xref:System.Windows.Controls.StackPanel>，並使用介面所定義的內容滾動方法（<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> 和 <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>）。  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>定義和使用 ScrollViewer 元素  
 下列範例會在包含一些文字和矩形的視窗中建立 <xref:System.Windows.Controls.ScrollViewer>。 只有在必要時才會顯示 <xref:System.Windows.Controls.Primitives.ScrollBar> 元素。 當您調整視窗的大小時，<xref:System.Windows.Controls.Primitives.ScrollBar> 元素會出現並消失，因為 <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> 和 <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> 屬性的更新值。  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>設定 ScrollViewer 的樣式  
 就像 Windows Presentation Foundation 中的所有控制項一樣，<xref:System.Windows.Controls.ScrollViewer> 可以進行樣式，以變更控制項的預設呈現行為。 如需有關控制項樣式設定的其他資訊，請參閱[樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>文件分頁  
 就文件內容而言，捲動的替代方案是選擇一個支援分頁的文件容器。 <xref:System.Windows.Documents.FlowDocument> 適用于設計為裝載于視圖控制項內的檔，例如 <xref:System.Windows.Controls.FlowDocumentPageViewer>，支援跨多個頁面分頁內容，而不需要進行滾動。 <xref:System.Windows.Controls.DocumentViewer> 提供用來觀看 <xref:System.Windows.Documents.FixedDocument> 內容的解決方案，其使用傳統的滾動來顯示顯示區域範圍外的內容。  
  
 如需有關文件格式和呈現方式選項的其他資訊，請參閱 [WPF 中的文件](../advanced/documents-in-wpf.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [如何：建立捲軸檢視器](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [WPF 中的文件](../advanced/documents-in-wpf.md)
- [ScrollBar 樣式和範本](scrollbar-styles-and-templates.md)
- [控制項](../advanced/optimizing-performance-controls.md)
