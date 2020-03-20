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
ms.openlocfilehash: 2ff0f134ea3174f7f034d47446aab782e2141916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186990"
---
# <a name="scrollviewer-overview"></a>ScrollViewer 概觀
使用者介面內的內容常常會大於電腦螢幕的顯示區域。 該<xref:System.Windows.Controls.ScrollViewer>控制項提供了一種在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中啟用內容滾動的便捷方法。 本主題介紹該<xref:System.Windows.Controls.ScrollViewer>元素，並提供幾個使用示例。  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>ScrollViewer 控制項  
 有兩個預定義元素在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中啟用滾動：<xref:System.Windows.Controls.Primitives.ScrollBar>和<xref:System.Windows.Controls.ScrollViewer>。 控制項<xref:System.Windows.Controls.ScrollViewer>封裝水準和垂直<xref:System.Windows.Controls.Primitives.ScrollBar>元素以及內容容器（如<xref:System.Windows.Controls.Panel>元素），以便在可捲動區域中顯示其他可見元素。 您必須生成自訂物件才能將<xref:System.Windows.Controls.Primitives.ScrollBar>元素用於內容滾動。 但是，您可以自行使用該<xref:System.Windows.Controls.ScrollViewer>元素，因為它是封裝<xref:System.Windows.Controls.Primitives.ScrollBar>功能的複合控制項。  
  
 該<xref:System.Windows.Controls.ScrollViewer>控制項同時回應滑鼠和鍵盤命令，並定義許多以預定增量滾動內容的方法。 可以使用 事件<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>檢測<xref:System.Windows.Controls.ScrollViewer>狀態中的更改。  
  
 只能<xref:System.Windows.Controls.ScrollViewer>有一個子級，通常是可以<xref:System.Windows.Controls.Panel>承載元素<xref:System.Windows.Controls.Panel.Children%2A>集合的元素。 屬性<xref:System.Windows.Controls.ContentPresenter.Content%2A>定義 的唯<xref:System.Windows.Controls.ScrollViewer>一子項。  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>物理與邏輯滾動  
 實體捲動可用來依預先決定的實體遞增值 (通常是以像素為單位宣告的值) 捲動內容。 邏輯捲動可用來捲動至邏輯樹狀結構中的下一個項目。 物理滾動是大多數<xref:System.Windows.Controls.Panel>元素的預設滾動行為。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 同時支援這兩種類型的捲動。  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo 介面  
 介面<xref:System.Windows.Controls.Primitives.IScrollInfo>表示<xref:System.Windows.Controls.ScrollViewer>或 派生控制項中的主捲動區域。 該介面定義滾動屬性和方法，這些屬性和方法可以由<xref:System.Windows.Controls.Panel>需要按邏輯單元滾動的元素實現，而不是物理增量。 將 的<xref:System.Windows.Controls.Primitives.IScrollInfo>實例強制轉換到<xref:System.Windows.Controls.Panel>派生的實例，然後使用其滾動方法提供了一種將滾動到子集合中的下一個邏輯單元的有用方法，而不是按圖元增量滾動。 預設情況下，<xref:System.Windows.Controls.ScrollViewer>控制項支援按物理單位滾動。  
  
 <xref:System.Windows.Controls.StackPanel>和<xref:System.Windows.Controls.VirtualizingStackPanel>實現<xref:System.Windows.Controls.Primitives.IScrollInfo>和本機支援邏輯滾動。 對於本機支援邏輯滾動的佈局控制項，您仍可以通過在 中包裝<xref:System.Windows.Controls.Panel>宿主元素<xref:System.Windows.Controls.ScrollViewer>並將<xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>屬性設置為`false`來實現物理滾動。  
  
 以下代碼示例演示如何<xref:System.Windows.Controls.Primitives.IScrollInfo>將 實例轉換為 ，<xref:System.Windows.Controls.StackPanel>並使用由介面定義的內容滾動方法 （<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>和<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>） 。  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>定義和使用 ScrollViewer 元素  
 下面的示例在包含某些<xref:System.Windows.Controls.ScrollViewer>文本和矩形的視窗中創建 。 <xref:System.Windows.Controls.Primitives.ScrollBar>元素僅在必要時才出現。 調整視窗大小時，由於 和<xref:System.Windows.Controls.Primitives.ScrollBar><xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A><xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>屬性的更新值，元素將顯示並消失。  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>設定 ScrollViewer 的樣式  
 與 Windows 演示文稿基礎中的所有控制項一<xref:System.Windows.Controls.ScrollViewer>樣，可以設置 樣式，以便更改控制項的預設呈現行為。 如需有關控制項樣式設定的其他資訊，請參閱[樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>文件分頁  
 就文件內容而言，捲動的替代方案是選擇一個支援分頁的文件容器。 <xref:System.Windows.Documents.FlowDocument>用於設計為託管在查看控制項中的文檔，例如<xref:System.Windows.Controls.FlowDocumentPageViewer>，支援跨多個頁面對內容進行分頁，從而防止需要滾動。 <xref:System.Windows.Controls.DocumentViewer>提供了用於查看<xref:System.Windows.Documents.FixedDocument>內容的解決方案，該解決方案使用傳統滾動在顯示區域之外顯示內容。  
  
 如需有關文件格式和呈現方式選項的其他資訊，請參閱 [WPF 中的文件](../advanced/documents-in-wpf.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [如何：創建滾動檢視器](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [WPF 中的文件](../advanced/documents-in-wpf.md)
- [ScrollBar 樣式和範本](scrollbar-styles-and-templates.md)
- [控制](../advanced/optimizing-performance-controls.md)
