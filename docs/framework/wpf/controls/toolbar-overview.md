---
title: ToolBar 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 816ac0d81ddcaa461a842c0f69fe5ed5b21a32d1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868688"
---
# <a name="toolbar-overview"></a>ToolBar 概觀
<xref:System.Windows.Controls.ToolBar> 控制項是一組命令或其功能通常彼此相關的控制項的容器。 A<xref:System.Windows.Controls.ToolBar>通常包含會叫用命令的按鈕。  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar 控制項  
 <xref:System.Windows.Controls.ToolBar>控制項接受名稱，取自到單一資料列或資料行的按鈕或其他控制項的列類似的排列方式。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> 控制項提供一種溢位機制而放置容納不下自然大小限制的任何項目<xref:System.Windows.Controls.ToolBar>到特殊的溢位區域。 此外， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar>通常是使用控制項與相關<xref:System.Windows.Controls.ToolBarTray>提供特殊的版面配置行為，以及支援使用者起始調整大小和排列工具列的控制項。  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>指定 ToolBar 在 ToolBarTray 中的位置  
 使用<xref:System.Windows.Controls.ToolBar.Band%2A>並<xref:System.Windows.Controls.ToolBar.BandIndex%2A>屬性來定位<xref:System.Windows.Controls.ToolBar>在<xref:System.Windows.Controls.ToolBarTray>。 <xref:System.Windows.Controls.ToolBar.Band%2A> 表示在其中的位置<xref:System.Windows.Controls.ToolBar>放在其父系<xref:System.Windows.Controls.ToolBarTray>。 <xref:System.Windows.Controls.ToolBar.BandIndex%2A> 表示順序<xref:System.Windows.Controls.ToolBar>會放置在其群組列。 下列範例示範如何使用這個屬性來放置<xref:System.Windows.Controls.ToolBar>內的控制項<xref:System.Windows.Controls.ToolBarTray>。  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>具有溢位項目的 ToolBar  
 通常<xref:System.Windows.Controls.ToolBar>控制項包含超過工具列大小可以納入項目。 當發生這種情況時，<xref:System.Windows.Controls.ToolBar>顯示溢位按鈕。 若要查看溢位項目，使用者按一下溢位按鈕和下列快顯視窗中顯示的項目<xref:System.Windows.Controls.ToolBar>。 下圖顯示<xref:System.Windows.Controls.ToolBar>溢位項目。  
  
 ![溢位的工具列](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")  
具有溢位項目的工具列  
  
 您可以指定工具列上的項目放置到溢位面板藉由設定當<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType>附加屬性<xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>， <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>，或<xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>。 下列範例指定工具列上的最後四個按鈕應該一律位於溢位面板上。  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar>會使用<xref:System.Windows.Controls.Primitives.ToolBarPanel>並<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>在其<xref:System.Windows.Controls.ControlTemplate>。  <xref:System.Windows.Controls.Primitives.ToolBarPanel>負責版面配置 工具列上的項目。  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>負責無法容納項目的配置<xref:System.Windows.Controls.ToolBar>。 如需<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.ToolBar>，請參閱  
  
 [ToolBar 樣式和範本](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [ToolBar 上的樣式控制項](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [WPF 控制項陳列庫範例](https://go.microsoft.com/fwlink/?LinkID=160053)
