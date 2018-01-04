---
title: "ContextMenu 概觀"
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
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0776e7960aa76a76422d01180af5fd6a089bc98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-overview"></a>ContextMenu 概觀
<xref:System.Windows.Controls.ContextMenu>類別代表使用特定內容公開功能的項目<xref:System.Windows.Controls.Menu>。 一般而言，使用者會公開<xref:System.Windows.Controls.ContextMenu>中[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]以滑鼠右鍵按一下滑鼠按鈕。 本主題將介紹<xref:System.Windows.Controls.ContextMenu>項目，並提供如何使用中的範例[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]和程式碼。  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>ContextMenu 控制項  
 A<xref:System.Windows.Controls.ContextMenu>附加至特定的控制項。 <xref:System.Windows.Controls.ContextMenu>元素可讓您向使用者呈現的項目，指定命令或相關聯選項與特定控制項，例如，清單<xref:System.Windows.Controls.Button>。 使用者以滑鼠右鍵按一下控制項，即可顯示功能表。 一般而言，按一下<xref:System.Windows.Controls.MenuItem>開啟子功能表，或是造成應用程式來執行命令。  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>建立 ContextMenu  
 下列範例顯示如何建立<xref:System.Windows.Controls.ContextMenu>具有子功能表。 <xref:System.Windows.Controls.ContextMenu>控制項附加至按鈕控制項。  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>將樣式套用至 ContextMenu  
 使用控制項<xref:System.Windows.Style>，您可以大幅變更外觀和行為<xref:System.Windows.Controls.ContextMenu>而不需要撰寫自訂控制項。 除了設定視覺屬性之外，您也可以套用樣式至控制項的組件。 例如，您可以變更的組件控制項的行為，藉由使用屬性，或您可以將組件，加入或變更的配置<xref:System.Windows.Controls.ContextMenu>。 下列範例示範幾種方式可以加入樣式以<xref:System.Windows.Controls.ContextMenu>控制項。  
  
 第一個範例會定義稱為 `SimpleSysResources` 的樣式，它會顯示如何以您的樣式使用目前的系統設定。 此範例將指派<xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A>為<xref:System.Windows.Controls.Control.Background%2A>色彩和<xref:System.Windows.SystemColors.MenuTextBrushKey%2A>為<xref:System.Windows.Controls.Control.Foreground%2A>色彩<xref:System.Windows.Controls.ContextMenu>。  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 下列範例會使用<xref:System.Windows.Trigger>項目，變更的外觀<xref:System.Windows.Controls.Menu>以回應所引發的事件<xref:System.Windows.Controls.ContextMenu>。 當使用者將滑鼠移功能表的外觀<xref:System.Windows.Controls.ContextMenu>變更的項目。  
  
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [ContextMenu 樣式和範本](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [WPF 控制項陳列庫範例](http://go.microsoft.com/fwlink/?LinkID=160053)
