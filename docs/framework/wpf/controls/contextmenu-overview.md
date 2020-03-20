---
title: ContextMenu 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: 4d2d8db0f614b5240705146dbe91432b96b46dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185906"
---
# <a name="contextmenu-overview"></a>ContextMenu 概觀
類<xref:System.Windows.Controls.ContextMenu>表示使用特定于<xref:System.Windows.Controls.Menu>上下文的 公開功能的元素。 通常，使用者[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]通過按右鍵<xref:System.Windows.Controls.ContextMenu>滑鼠按鍵來公開 中的。 本主題介紹該<xref:System.Windows.Controls.ContextMenu>元素，並提供如何在 和 代碼中使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]該元素的示例。  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a>ContextMenu 控制項  
 附加到<xref:System.Windows.Controls.ContextMenu>特定控制項。 該<xref:System.Windows.Controls.ContextMenu>元素使您能夠向使用者顯示指定與特定控制項關聯的命令或選項的項清單，例如<xref:System.Windows.Controls.Button>。 使用者以滑鼠右鍵按一下控制項，即可顯示功能表。 通常，按一下<xref:System.Windows.Controls.MenuItem>將打開子功能表或導致應用程式執行命令。  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a>建立 ContextMenu  
 以下示例演示如何使用子功能表創建<xref:System.Windows.Controls.ContextMenu>。 控制項<xref:System.Windows.Controls.ContextMenu>附加到按鈕控制項。  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a>將樣式套用至 ContextMenu  
 通過使用 控制項<xref:System.Windows.Style>，可以顯著更改 的外觀<xref:System.Windows.Controls.ContextMenu>和行為，而無需編寫自訂控制項。 除了設定視覺屬性之外，您也可以套用樣式至控制項的組件。 例如，可以使用 屬性更改控制項的各個部分的行為，也可以向 或 更改<xref:System.Windows.Controls.ContextMenu>的佈局添加部件。 以下示例顯示了向<xref:System.Windows.Controls.ContextMenu>控制項添加樣式的幾種方法。  
  
 第一個範例會定義稱為 `SimpleSysResources` 的樣式，它會顯示如何以您的樣式使用目前的系統設定。 該示例將指定<xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A>為<xref:System.Windows.Controls.Control.Background%2A>顏色和<xref:System.Windows.SystemColors.MenuTextBrushKey%2A><xref:System.Windows.Controls.Control.Foreground%2A>顏色<xref:System.Windows.Controls.ContextMenu>。  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 下面的示例使用 元素<xref:System.Windows.Trigger>更改 的外觀<xref:System.Windows.Controls.Menu>，以回應在 上引發的事件<xref:System.Windows.Controls.ContextMenu>。 當使用者將滑鼠移到功能表上時，<xref:System.Windows.Controls.ContextMenu>專案的外觀會發生變化。  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [ContextMenu](contextmenu.md)
- [ContextMenu 樣式和範本](contextmenu-styles-and-templates.md)
- [WPF 控制項陳列庫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
