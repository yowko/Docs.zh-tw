---
title: ToolBar 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 460d4420d5faf849a8d05a94e0170aea384f69b4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452691"
---
# <a name="toolbar-overview"></a>ToolBar 概觀
<xref:System.Windows.Controls.ToolBar> 控制項是一組命令或控制項的容器，它們通常都是在其功能中相關。 <xref:System.Windows.Controls.ToolBar> 通常包含可叫用命令的按鈕。  

<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar 控制項  
 <xref:System.Windows.Controls.ToolBar> 控制項將其名稱從類似橫條圖的按鈕或其他控制項的相片順序，改為單一資料列或資料行。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> 控制項提供溢位機制，其會將無法在大小限制的 <xref:System.Windows.Controls.ToolBar> 中自然符合的任何專案放入特殊的溢位區域中。 此外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> 控制項通常會與相關的 <xref:System.Windows.Controls.ToolBarTray> 控制項搭配使用，這會提供特殊的版面配置行為，並支援使用者起始的大小調整和排列工具列。  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>指定 ToolBar 在 ToolBarTray 中的位置  
 使用 [<xref:System.Windows.Controls.ToolBar.Band%2A>] 和 [<xref:System.Windows.Controls.ToolBar.BandIndex%2A> 屬性]，將 <xref:System.Windows.Controls.ToolBar> 放置在 <xref:System.Windows.Controls.ToolBarTray>中。 <xref:System.Windows.Controls.ToolBar.Band%2A> 表示 <xref:System.Windows.Controls.ToolBar> 放在其父 <xref:System.Windows.Controls.ToolBarTray>中的位置。 <xref:System.Windows.Controls.ToolBar.BandIndex%2A> 表示 <xref:System.Windows.Controls.ToolBar> 放在其寬線中的順序。 下列範例顯示如何使用這個屬性，將 <xref:System.Windows.Controls.ToolBar> 控制項放在 <xref:System.Windows.Controls.ToolBarTray>內。  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>具有溢位項目的 ToolBar  
 通常 <xref:System.Windows.Controls.ToolBar> 控制項所包含的專案數超過工具列大小所能容納的數量。 當發生這種情況時，<xref:System.Windows.Controls.ToolBar> 會顯示溢位按鈕。 若要查看溢位專案，使用者可以按一下 [溢位] 按鈕，專案就會顯示在 <xref:System.Windows.Controls.ToolBar>底下的快顯視窗中。 下圖顯示具有溢位專案的 <xref:System.Windows.Controls.ToolBar>：  
  
 ![顯示具有溢位專案之工具列的螢幕擷取畫面。](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 您可以藉由將 [<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType>] 附加屬性設定為 [<xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>]、[<xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>] 或 [<xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>]，指定將工具列上的專案放在溢位面板上的時機。 下列範例指定工具列上的最後四個按鈕應該一律位於溢位面板上。  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar> 在其 <xref:System.Windows.Controls.ControlTemplate>中使用 <xref:System.Windows.Controls.Primitives.ToolBarPanel> 和 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>。  <xref:System.Windows.Controls.Primitives.ToolBarPanel> 會負責工具列上專案的版面配置。  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> 會負責 <xref:System.Windows.Controls.ToolBar>不符合的專案配置。 如需 <xref:System.Windows.Controls.ToolBar>的 <xref:System.Windows.Controls.ControlTemplate> 範例，請參閱  
  
 [ToolBar 樣式和範本](toolbar-styles-and-templates.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [ToolBar 上的樣式控制項](how-to-style-controls-on-a-toolbar.md)
- [WPF 控制項陳列庫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
