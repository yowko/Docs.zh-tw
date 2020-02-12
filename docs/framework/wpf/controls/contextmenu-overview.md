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
ms.openlocfilehash: b973d47711632f4c0fe56f042545598272c79d2d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124360"
---
# <a name="contextmenu-overview"></a>ContextMenu 概觀
<xref:System.Windows.Controls.ContextMenu> 類別表示專案，此專案會使用內容特定的 <xref:System.Windows.Controls.Menu>來公開功能。 使用者通常會在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中公開 <xref:System.Windows.Controls.ContextMenu>，方法是以滑鼠右鍵按一下 [滑鼠] 按鈕。 本主題介紹 <xref:System.Windows.Controls.ContextMenu> 元素，並提供如何在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼中使用它的範例。  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>ContextMenu 控制項  
 <xref:System.Windows.Controls.ContextMenu> 會附加至特定的控制項。 [<xref:System.Windows.Controls.ContextMenu>] 專案可讓您向使用者顯示指定與特定控制項相關聯之命令或選項的專案清單，例如，<xref:System.Windows.Controls.Button>。 使用者以滑鼠右鍵按一下控制項，即可顯示功能表。 一般來說，按一下 <xref:System.Windows.Controls.MenuItem> 會開啟子功能表，或讓應用程式執行命令。  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>建立 ContextMenu  
 下列範例示範如何建立含有子功能表的 <xref:System.Windows.Controls.ContextMenu>。 <xref:System.Windows.Controls.ContextMenu> 控制項會附加至按鈕控制項。  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>將樣式套用至 ContextMenu  
 藉由使用控制項 <xref:System.Windows.Style>，您可以大幅變更 <xref:System.Windows.Controls.ContextMenu> 的外觀和行為，而不需要撰寫自訂控制項。 除了設定視覺屬性之外，您也可以套用樣式至控制項的組件。 例如，您可以使用屬性來變更控制項各部分的行為，也可以將元件加入或變更 <xref:System.Windows.Controls.ContextMenu>的版面配置。 下列範例示範數種將樣式加入 <xref:System.Windows.Controls.ContextMenu> 控制項的方式。  
  
 第一個範例會定義稱為 `SimpleSysResources` 的樣式，它會顯示如何以您的樣式使用目前的系統設定。 這個範例會將 <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> 指派為 <xref:System.Windows.Controls.Control.Background%2A> 色彩，並將 <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> 做為 <xref:System.Windows.Controls.ContextMenu>的 <xref:System.Windows.Controls.Control.Foreground%2A> 色彩。  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 下列範例會使用 <xref:System.Windows.Trigger> 元素來變更 <xref:System.Windows.Controls.Menu> 的外觀，以回應 <xref:System.Windows.Controls.ContextMenu>上引發的事件。 當使用者將滑鼠移至功能表上方時，<xref:System.Windows.Controls.ContextMenu> 專案的外觀就會變更。  
  
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
