---
title: 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 5abafe1edfdbac1966a98d5eef28265e6504c868
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154410"
---
# <a name="controls"></a>控制項
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 隨附許多中幾乎所有 Windows 應用程式，例如使用的常見 UI 元件<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.TextBox>， <xref:System.Windows.Controls.Menu>，和<xref:System.Windows.Controls.ListBox>。 在過去，這些物件是稱為控制項。 雖然[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]SDK 繼續使用 「 控制項 」 一詞來泛指任何類別，代表可見物件在應用程式，請務必注意，類別不需要繼承自<xref:System.Windows.Controls.Control>類別，以顯示出來。 繼承自類別<xref:System.Windows.Controls.Control>類別包含<xref:System.Windows.Controls.ControlTemplate>，可讓控制項的取用者，即可完全變更控制項的外觀，而不需要建立新的子類別。  本主題討論如何控制項 (不要繼承自兩個那些<xref:System.Windows.Controls.Control>類別和非執行) 中常用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>建立控制項的執行個體  
 您可以將控制項加入應用程式使用其中一種[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或程式碼。  下列範例示範如何建立一個要求使用者輸入其名字和姓氏的簡單應用程式。  這個範例會建立六個控制項： 兩個標籤、 兩個文字方塊中，以及兩個按鈕，在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 您可以用類似的方式建立所有控制項。  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 下列範例會以程式碼建立相同的應用程式。 為求簡潔，建立<xref:System.Windows.Controls.Grid>， `grid1`，已排除的範例。 `grid1` 先前所示，有相同的資料行和資料列定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例。  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>變更控制項的外觀  
 變更控制項的外觀以符合您應用程式的外觀及操作，是很常見的做法。 您可以根據想要達成的目的，執行下列其中一項操作來變更控制項的外觀：  
  
-   變更控制項的屬性值。  
  
-   建立<xref:System.Windows.Style>控制項。  
  
-   建立新<xref:System.Windows.Controls.ControlTemplate>控制項。  
  
### <a name="changing-a-controls-property-value"></a>變更控制項的屬性值  
 許多控制項都有屬性，可讓您變更控制項的顯示方式，例如<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>。 您可以設定的值屬性中同時[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和程式碼。 下列範例會設定<xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.FontSize%2A>，並<xref:System.Windows.Controls.Control.FontWeight%2A>上的屬性<xref:System.Windows.Controls.Button>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 下列範例會以程式碼設定相同的屬性。  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>為控制項建立樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 讓您能夠全面，指定控制項的外觀，而不是在應用程式，每個執行個體上設定屬性，藉由建立<xref:System.Windows.Style>。 下列範例會建立<xref:System.Windows.Style>套用至每個<xref:System.Windows.Controls.Button>應用程式中。 <xref:System.Windows.Style> 定義通常定義於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中<xref:System.Windows.ResourceDictionary>，例如<xref:System.Windows.FrameworkElement.Resources%2A>屬性<xref:System.Windows.FrameworkElement>。  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 您也可以套用到只有某些特定類型的控制項樣式，將索引鍵指派樣式，並指定該金鑰在`Style`您控制項的屬性。  如需有關樣式的詳細資訊，請參閱 <<c0> [ 設定樣式和範本](styling-and-templating.md)。  
  
### <a name="creating-a-controltemplate"></a>建立 ControlTemplate  
 A<xref:System.Windows.Style>可讓您在多個控制項上設定屬性，一次，但有時您可能想要自訂的外觀<xref:System.Windows.Controls.Control>超出您可以藉由建立達到<xref:System.Windows.Style>。 繼承自類別<xref:System.Windows.Controls.Control>類別具有<xref:System.Windows.Controls.ControlTemplate>，其定義的結構和外觀<xref:System.Windows.Controls.Control>。 <xref:System.Windows.Controls.Control.Template%2A>的屬性<xref:System.Windows.Controls.Control>是公用的因此您可以提供給<xref:System.Windows.Controls.Control><xref:System.Windows.Controls.ControlTemplate>與其預設值不同。 通常您可以指定新<xref:System.Windows.Controls.ControlTemplate>for<xref:System.Windows.Controls.Control>而不是繼承自控制項自訂外觀<xref:System.Windows.Controls.Control>。  
  
 請考慮非常常見的控制項， <xref:System.Windows.Controls.Button>。  主要行為<xref:System.Windows.Controls.Button>是要讓應用程式以採取某些動作，當使用者按一下它。  根據預設，<xref:System.Windows.Controls.Button>在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]會顯示為凸起的矩形。  在開發應用程式時，您可能想要利用的行為<xref:System.Windows.Controls.Button>-也就是透過處理按鈕的點選事件，但您可能會變更超出您能達到的變更按鈕的屬性按鈕的外觀。  在此情況下，您可以建立新<xref:System.Windows.Controls.ControlTemplate>。  
  
 下列範例會建立<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.Button>。  <xref:System.Windows.Controls.ControlTemplate>建立<xref:System.Windows.Controls.Button>具有圓的角和漸層背景。  <xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.Border>其<xref:System.Windows.Controls.Border.Background%2A>是<xref:System.Windows.Media.LinearGradientBrush>具有兩個<xref:System.Windows.Media.GradientStop>物件。  第一個<xref:System.Windows.Media.GradientStop>使用資料繫結來繫結<xref:System.Windows.Media.GradientStop.Color%2A>屬性<xref:System.Windows.Media.GradientStop>按鈕的背景色彩。  當您設定<xref:System.Windows.Controls.Control.Background%2A>的屬性<xref:System.Windows.Controls.Button>，將使用該值的色彩，與第一個<xref:System.Windows.Media.GradientStop>。 如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../data/data-binding-overview.md)。 此範例也會建立<xref:System.Windows.Trigger>變更的外觀<xref:System.Windows.Controls.Button>當<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>是`true`。  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A>的屬性<xref:System.Windows.Controls.Button>必須設為<xref:System.Windows.Media.SolidColorBrush>範例中，才能正常運作。  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>訂閱事件  
 您可以使用其中一種訂閱控制項事件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]或程式碼，但您只能處理程式碼中的事件。  下列範例示範如何訂閱`Click`事件的<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 下列範例會處理`Click`事件的<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>控制項中的多格式內容  
 大部分的類別繼承自<xref:System.Windows.Controls.Control>類別都能夠包含多格式內容。 例如，<xref:System.Windows.Controls.Label>可以包含任何物件，例如字串， <xref:System.Windows.Controls.Image>，或<xref:System.Windows.Controls.Panel>。  下列類別支援豐富的內容並做為基底類別中的控制項中的大多數[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
-   <xref:System.Windows.Controls.ContentControl>，繼承自這個類別的類別部分範例如下<xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.Button>，和<xref:System.Windows.Controls.ToolTip>。  
  
-   <xref:System.Windows.Controls.ItemsControl>，繼承自這個類別的類別部分範例如下<xref:System.Windows.Controls.ListBox>， <xref:System.Windows.Controls.Menu>，和<xref:System.Windows.Controls.Primitives.StatusBar>。  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>，繼承自這個類別的類別部分範例如下<xref:System.Windows.Controls.TabItem>， <xref:System.Windows.Controls.GroupBox>，和<xref:System.Windows.Controls.Expander>。  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>，繼承自這個類別的類別部分範例如下<xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.TreeViewItem>，和<xref:System.Windows.Controls.ToolBar>。  

 如需有關這些基底類別的詳細資訊，請參閱 < [WPF 內容模型](wpf-content-model.md)。  
  
## <a name="see-also"></a>另請參閱

- [樣式設定和範本化](styling-and-templating.md)
- [依分類列出控制項](controls-by-category.md)
- [控制項程式庫](control-library.md)
- [資料範本化概觀](../data/data-templating-overview.md)
- [資料繫結概觀](../data/data-binding-overview.md)
- [輸入](../advanced/input-wpf.md)
- [啟用命令](../advanced/how-to-enable-a-command.md)
- [逐步解說：建立自訂動畫的按鈕](walkthroughs-create-a-custom-animated-button.md)
- [控制項自訂](control-customization.md)
