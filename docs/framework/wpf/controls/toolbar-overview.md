---
title: ToolBar 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: b5498b8b88c7403ffe51256a57544261de3ace08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186619"
---
# <a name="toolbar-overview"></a>ToolBar 概觀
<xref:System.Windows.Controls.ToolBar>控制項是一組命令或控制項的容器，這些命令或控制項通常與其功能相關。 通常<xref:System.Windows.Controls.ToolBar>包含調用命令的按鈕。  

<a name="ToolBarControl"></a>
## <a name="toolbar-control"></a>ToolBar 控制項  
 控制項<xref:System.Windows.Controls.ToolBar>將其名稱從類似條形的按鈕或其他控制項排列到單個行或列中。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar>控制項提供溢出機制，將任何不自然適合在大小約束<xref:System.Windows.Controls.ToolBar>中的項放入特殊溢位區域域。 此外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar>控制項通常與相關<xref:System.Windows.Controls.ToolBarTray>控制項一起使用，後者提供特殊的佈局行為，並支援使用者啟動的工具列大小調整和排列。  
  
<a name="Creating_ToolBars"></a>
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>指定 ToolBar 在 ToolBarTray 中的位置  
 使用<xref:System.Windows.Controls.ToolBar.Band%2A>和<xref:System.Windows.Controls.ToolBar.BandIndex%2A>屬性將<xref:System.Windows.Controls.ToolBar>放置在<xref:System.Windows.Controls.ToolBarTray>中。 <xref:System.Windows.Controls.ToolBar.Band%2A>指示 放置在其父<xref:System.Windows.Controls.ToolBar><xref:System.Windows.Controls.ToolBarTray>項 中的位置。 <xref:System.Windows.Controls.ToolBar.BandIndex%2A>指示 在其波段中放置<xref:System.Windows.Controls.ToolBar>的順序。 下面的示例演示如何使用此屬性將控制項放置在<xref:System.Windows.Controls.ToolBar>中。 <xref:System.Windows.Controls.ToolBarTray>  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>
## <a name="toolbars-with-overflow-items"></a>具有溢位項目的 ToolBar  
 控制項<xref:System.Windows.Controls.ToolBar>包含的專案數通常超過工具列大小。 發生這種情況時，<xref:System.Windows.Controls.ToolBar>將顯示溢出按鈕。 要查看溢出項，使用者按一下溢出按鈕，這些專案將顯示在 下面的快顯視窗中<xref:System.Windows.Controls.ToolBar>。 下圖顯示了具有溢出項<xref:System.Windows.Controls.ToolBar>的：  
  
 ![顯示具有溢出項的工具列的螢幕截圖。](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 通過將<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType>附加屬性<xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType><xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>設置為 或，可以指定工具列上的項何時放置在溢出面板上。 <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType> 下列範例指定工具列上的最後四個按鈕應該一律位於溢位面板上。  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 中的<xref:System.Windows.Controls.ToolBar>使用<xref:System.Windows.Controls.Primitives.ToolBarPanel>和<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>在其<xref:System.Windows.Controls.ControlTemplate>中 。  <xref:System.Windows.Controls.Primitives.ToolBarPanel>負責工具列上項的佈局。  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>負責不適合 的項的佈局<xref:System.Windows.Controls.ToolBar>。 有關 的 。 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ToolBar>  
  
 [工具列樣式和範本](toolbar-styles-and-templates.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [ToolBar 上的樣式控制項](how-to-style-controls-on-a-toolbar.md)
- [WPF 控制項陳列庫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
