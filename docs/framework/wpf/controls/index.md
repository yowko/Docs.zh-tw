---
title: 控制項
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66c6cc58423a2af8d0fd6de93b8884918888fb48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="controls"></a>控制項
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]隨附許多常見的 UI 元件中幾乎每個 Windows 應用程式，例如使用<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.TextBox>， <xref:System.Windows.Controls.Menu>，和<xref:System.Windows.Controls.ListBox>。 在過去，這些物件是稱為控制項。 而[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]SDK 仍持續鬆散表示任何類別，表示應用程式中，可見的物件時，用於 「 控制項 」 一詞是很重要的一點類別不需要繼承自<xref:System.Windows.Controls.Control>類別具有可見的目前狀態。 類別繼承自<xref:System.Windows.Controls.Control>類別包含<xref:System.Windows.Controls.ControlTemplate>，可讓取用者的控制項來徹底變更控制項的外觀，而不需要建立新的子類別。  本主題討論如何控制項 (不要繼承自兩個那些<xref:System.Windows.Controls.Control>類別和未) 中常用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>建立控制項的執行個體  
 您可以將控制項加入應用程式使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或程式碼。  下列範例示範如何建立一個要求使用者輸入其名字和姓氏的簡單應用程式。  這個範例會建立六個控制項： 兩個標籤，兩個文字方塊和兩個按鈕，在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 您可以用類似的方式建立所有控制項。  
  
 [!code-xaml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 下列範例會以程式碼建立相同的應用程式。 為求簡潔，建立<xref:System.Windows.Controls.Grid>， `grid1`，排除範例。 `grid1`具有相同的資料行和資料列定義，如先前所示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例。  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>變更控制項的外觀  
 變更控制項的外觀以符合您應用程式的外觀及操作，是很常見的做法。 您可以根據想要達成的目的，執行下列其中一項操作來變更控制項的外觀：  
  
-   變更控制項的屬性值。  
  
-   建立<xref:System.Windows.Style>控制項。  
  
-   建立新<xref:System.Windows.Controls.ControlTemplate>控制項。  
  
### <a name="changing-a-controls-property-value"></a>變更控制項的屬性值  
 許多控制項都有屬性可讓您變更控制項的顯示方式，例如<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>。 您可以設定的值屬性中都[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和程式碼。 下列範例會設定<xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.FontSize%2A>，和<xref:System.Windows.Controls.Control.FontWeight%2A>屬性<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xaml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 下列範例會以程式碼設定相同的屬性。  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>為控制項建立樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可讓您全面，指定控制項的外觀，而不是在應用程式，每個執行個體上設定屬性，藉由建立<xref:System.Windows.Style>。 下列範例會建立<xref:System.Windows.Style>套用至每個<xref:System.Windows.Controls.Button>應用程式中。 <xref:System.Windows.Style>定義通常定義在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中<xref:System.Windows.ResourceDictionary>，例如<xref:System.Windows.FrameworkElement.Resources%2A>屬性<xref:System.Windows.FrameworkElement>。  
  
 [!code-xaml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 您也可以套用至只有某些特定類型的控制項的樣式，將索引鍵指派的樣式，並指定該索引鍵中的`Style`控制項的屬性。  如需有關樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
### <a name="creating-a-controltemplate"></a>建立 ControlTemplate  
 A<xref:System.Windows.Style>可讓您一次設定多個控制項上的屬性，但有時您可能想要自訂的外觀<xref:System.Windows.Controls.Control>超出您可以透過建立執行<xref:System.Windows.Style>。 類別繼承自<xref:System.Windows.Controls.Control>類別有<xref:System.Windows.Controls.ControlTemplate>，其定義的結構和外觀<xref:System.Windows.Controls.Control>。 <xref:System.Windows.Controls.Control.Template%2A>屬性<xref:System.Windows.Controls.Control>是公用的因此您可以提供<xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> ，為其預設值不同。 通常您可以指定新<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Control>而不是繼承自控制項自訂外觀<xref:System.Windows.Controls.Control>。  
  
 請考慮很常見的控制項， <xref:System.Windows.Controls.Button>。  主要行為<xref:System.Windows.Controls.Button>是要讓應用程式採取某些動作，當使用者按一下它。  根據預設，<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]顯示為引發的矩形。  在開發應用程式時，您可能想要利用的行為<xref:System.Windows.Controls.Button>-也就是藉由處理按鈕的按一下事件--但是您可能會變更超出您可以進行變更按鈕的屬性按鈕的外觀。  在此情況下，您可以建立新<xref:System.Windows.Controls.ControlTemplate>。  
  
 下列範例會建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.Button>。  <xref:System.Windows.Controls.ControlTemplate>建立<xref:System.Windows.Controls.Button>圓的角和漸層背景。  <xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.Border>其<xref:System.Windows.Controls.Border.Background%2A>是<xref:System.Windows.Media.LinearGradientBrush>具有兩個<xref:System.Windows.Media.GradientStop>物件。  第一個<xref:System.Windows.Media.GradientStop>使用資料繫結來繫結<xref:System.Windows.Media.GradientStop.Color%2A>屬性<xref:System.Windows.Media.GradientStop>按鈕的背景色彩。  當您將<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.Button>，該值的色彩，會使用第一個作為<xref:System.Windows.Media.GradientStop>。 如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。 此範例也會建立<xref:System.Windows.Trigger>變更的外觀<xref:System.Windows.Controls.Button>時<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>是`true`。  
  
 [!code-xaml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.Button>必須設為<xref:System.Windows.Media.SolidColorBrush>例如才能正常運作。  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>訂閱事件  
 您可以使用控制項的事件訂閱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]或程式碼，但您只能處理程式碼中的事件。  下列範例示範如何訂閱`Click`事件<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 下列範例會處理`Click`事件<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>控制項中的多格式內容  
 大部分的類別繼承自<xref:System.Windows.Controls.Control>類別有容量足以包含豐富的內容。 例如，<xref:System.Windows.Controls.Label>可以包含任何物件，例如字串， <xref:System.Windows.Controls.Image>，或<xref:System.Windows.Controls.Panel>。  下列類別支援豐富的內容，並做為基底類別中的控制項的大部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
-   <xref:System.Windows.Controls.ContentControl>-繼承自這個類別的類別部分範例包括<xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.Button>，和<xref:System.Windows.Controls.ToolTip>。  
  
-   <xref:System.Windows.Controls.ItemsControl>-繼承自這個類別的類別部分範例包括<xref:System.Windows.Controls.ListBox>， <xref:System.Windows.Controls.Menu>，和<xref:System.Windows.Controls.Primitives.StatusBar>。  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>-繼承自這個類別的類別部分範例包括<xref:System.Windows.Controls.TabItem>， <xref:System.Windows.Controls.GroupBox>，和<xref:System.Windows.Controls.Expander>。  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>-繼承自這個類別的類別部分範例包括<xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.TreeViewItem>，和<xref:System.Windows.Controls.ToolBar>。  
  
-  
  
 如需有關這些基底類別的詳細資訊，請參閱[WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)。  
  
## <a name="see-also"></a>請參閱  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [依分類列出控制項](../../../../docs/framework/wpf/controls/controls-by-category.md)  
 [控制項程式庫](../../../../docs/framework/wpf/controls/control-library.md)  
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [輸入](../../../../docs/framework/wpf/advanced/input-wpf.md)  
 [啟用命令](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)  
 [逐步解說：建立自訂動畫按鈕](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)  
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)
