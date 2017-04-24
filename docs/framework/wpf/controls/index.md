---
title: "控制項 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: 3c9baa45741cbc21e1d22ad6a126d7c3d94370cb
ms.lasthandoff: 04/08/2017

---
# <a name="controls"></a>控制項
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 隨附許多幾乎在每個 Windows 應用程式中都使用的常見 UI 元件，例如              <xref:System.Windows.Controls.Button>、              <xref:System.Windows.Controls.Label>、              <xref:System.Windows.Controls.TextBox>、              <xref:System.Windows.Controls.Menu> 及              <xref:System.Windows.Controls.ListBox>。 在過去，這些物件是稱為控制項。 雖然              [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK 繼續使用「控制項」一詞來泛指任何在應用程式中代表可見物件的類別，但請務必注意，一個類別並不需要從              <xref:System.Windows.Controls.Control> 類別繼承，即可顯示出來。 從              <xref:System.Windows.Controls.Control> 類別繼承的類別會包含              <xref:System.Windows.Controls.ControlTemplate>，可讓控制項的取用者不須建立新的子類別，即可完全變更控制項的外觀。  本主題討論控制項 (同時包括從              <xref:System.Windows.Controls.Control> 類別繼承及不從該類別繼承的控制項) 在              [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的常見使用方式。  
  
<<<<<<< HEAD
 
=======
   
>>>>>>> 3f8246b... fix build errors
  
<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>建立控制項的執行個體  
 您可以藉由使用                  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 或程式碼，將控制項新增到應用程式。  下列範例示範如何建立一個要求使用者輸入其名字和姓氏的簡單應用程式。  此範例會以                  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 建立六個控制項：兩個標籤、兩個文字方塊，以及兩個按鈕。 您可以用類似的方式建立所有控制項。  
  
 [!code-xml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 下列範例會以程式碼建立相同的應用程式。 為求簡潔，此範例中不包含建立                  <xref:System.Windows.Controls.Grid> (                  `grid1`)。                   `grid1` 的資料行和資料列定義與上述                  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例中顯示的相同。  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>變更控制項的外觀  
 變更控制項的外觀以符合您應用程式的外觀及操作，是很常見的做法。 您可以根據想要達成的目的，執行下列其中一項操作來變更控制項的外觀：  
  
-   變更控制項的屬性值。  
  
-   為控制項建立                          <xref:System.Windows.Style>。  
  
-   為控制項建立新的                          <xref:System.Windows.Controls.ControlTemplate>。  
  
### <a name="changing-a-controls-property-value"></a>變更控制項的屬性值  
 許多控制項都有可讓您變更控制項顯示方式的屬性，例如                          <xref:System.Windows.Controls.Button> 的                           <xref:System.Windows.Controls.Control.Background%2A>。 您可以在                          [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和程式碼中都設定值屬性。 下列範例會以                          [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 設定                          <xref:System.Windows.Controls.Button> 上的                          <xref:System.Windows.Controls.Control.Background%2A>、                          <xref:System.Windows.Controls.Control.FontSize%2A> 及                          <xref:System.Windows.Controls.Control.FontWeight%2A> 屬性。  
  
 [!code-xml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 下列範例會以程式碼設定相同的屬性。  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>為控制項建立樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您透過建立                          <xref:System.Windows.Style> 來大批指定控制項的外觀，而不需在應用程式中的每個執行個體上設定屬性。                           下列範例                          會建立一個套用到應用程式中每個                          <xref:System.Windows.Controls.Button> 的                          <xref:System.Windows.Style>。                          <xref:System.Windows.Style> 定義通常是以                          [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 在                          <xref:System.Windows.ResourceDictionary> (例如                          <xref:System.Windows.FrameworkElement> 的                           <xref:System.Windows.FrameworkElement.Resources%2A> 屬性) 中定義。  
  
 [!code-xml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 您也可以透過指派樣式索引鍵並在控制項的                          `Style` 屬性中指定該索引鍵，將樣式只套用到某些特定型別的控制項。  如需有關樣式的詳細資訊，請參閱                          [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
### <a name="creating-a-controltemplate"></a>建立 ControlTemplate  
                          &lt;xref:System.Windows.Style&gt; 可讓您一次在多個控制項上設定屬性，但有時您想要對                          &lt;xref:System.Windows.Controls.Control&gt; 外觀進行的自訂可能會超出建立                          &lt;xref:System.Windows.Style&gt; 所能達到的效果。 從                          <xref:System.Windows.Controls.Control> 類別繼承的類別會具有                          <xref:System.Windows.Controls.ControlTemplate>，可用來定義                          <xref:System.Windows.Controls.Control> 的結構和外觀。                          &lt;xref:System.Windows.Controls.Control&gt; 的                          &lt;xref:System.Windows.Controls.Control.Template%2A&gt; 屬性是公用屬性，因此您可以為                          &lt;xref:System.Windows.Controls.Control&gt; 提供一個與其預設值不同的                          &lt;xref:System.Windows.Controls.ControlTemplate&gt;。 您通常會為                          <xref:System.Windows.Controls.Control> 指定一個新的                          <xref:System.Windows.Controls.ControlTemplate>，而不從控制項繼承，來自訂                          <xref:System.Windows.Controls.Control> 的外觀。  
  
 請思考一下非常常見的控制項                          <xref:System.Windows.Controls.Button>。                           &lt;xref:System.Windows.Controls.Button&gt; 的主要行為是讓應用程式能夠在使用者按一下它時採取某個動作。                           [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的                          <xref:System.Windows.Controls.Button> 預設會顯示為凸起的矩形。  開發應用程式時，您可能會想要利用                          <xref:System.Windows.Controls.Button> 的行為 (亦即透過處理按鈕的點選事件)，但您對按鈕外觀進行的變更可能超出變更按鈕屬性所能達到的效果。  在此情況下，您可以建立一個新的                          <xref:System.Windows.Controls.ControlTemplate>。  
  
 下列範例會為                          <xref:System.Windows.Controls.Button> 建立一個                          <xref:System.Windows.Controls.ControlTemplate>。                           &lt;xref:System.Windows.Controls.ControlTemplate&gt; 會建立一個具有圓角和漸層背景的                          &lt;xref:System.Windows.Controls.Button&gt;。                           &lt;xref:System.Windows.Controls.ControlTemplate&gt; 包含一個                          &lt;xref:System.Windows.Controls.Border&gt;，其中其                          &lt;xref:System.Windows.Controls.Border.Background%2A&gt; 是含有兩個                          &lt;xref:System.Windows.Media.GradientStop&gt; 物件的                          &lt;xref:System.Windows.Media.LinearGradientBrush&gt;。  第一個                          <xref:System.Windows.Media.GradientStop> 會使用資料繫結將                          <xref:System.Windows.Media.GradientStop> 的                          <xref:System.Windows.Media.GradientStop.Color%2A> 屬性繫結至按鈕背景的色彩。  當您設定                          <xref:System.Windows.Controls.Button> 的                          <xref:System.Windows.Controls.Control.Background%2A> 屬性時，該值的色彩將會用來作為第一個                          <xref:System.Windows.Media.GradientStop>。 如需有關資料繫結的詳細資訊，請參閱                          [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。 此範例也會建立一個                          <xref:System.Windows.Trigger>，可在                          <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> 為                          `true` 時，變更                          <xref:System.Windows.Controls.Button> 的外觀。  
  
 [!code-xml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>                               &lt;xref:System.Windows.Controls.Button&gt; 的                              &lt;xref:System.Windows.Controls.Control.Background%2A&gt; 屬性必須設定為                              &lt;xref:System.Windows.Media.SolidColorBrush&gt;，此範例才能正確運作。  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>訂閱事件  
 您可以使用                  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 或程式碼來訂閱控制項的事件，但只能在程式碼中處理事件。  下列範例示範如何訂閱                  <xref:System.Windows.Controls.Button> 的                  `Click` 事件。  
  
 [!code-xml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 下列範例會處理                  <xref:System.Windows.Controls.Button> 的                  `Click` 事件。  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>控制項中的多格式內容  
 大多數會從                  <xref:System.Windows.Controls.Control> 類別繼承的類別都能夠包含多格式內容。 例如，                  <xref:System.Windows.Controls.Label> 便可以包含任何物件，像是字串、                  <xref:System.Windows.Controls.Image> 或                  <xref:System.Windows.Controls.Panel>。  下列類別會提供對多格式內容的支援，並可作為                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中大多數控制項的基底類別。  
  
-   <xref:System.Windows.Controls.ContentControl> -- 從此類別繼承的一些類別範例包括                          <xref:System.Windows.Controls.Label>、                          <xref:System.Windows.Controls.Button> 及                          <xref:System.Windows.Controls.ToolTip>。  
  
-   <xref:System.Windows.Controls.ItemsControl> -- 從此類別繼承的一些類別範例包括                          <xref:System.Windows.Controls.ListBox>、                          <xref:System.Windows.Controls.Menu> 及                          <xref:System.Windows.Controls.Primitives.StatusBar>。  
  
-   <xref:System.Windows.Controls.HeaderedContentControl> -- 從此類別繼承的一些類別範例包括                          <xref:System.Windows.Controls.TabItem>、                          <xref:System.Windows.Controls.GroupBox> 及                          <xref:System.Windows.Controls.Expander>。  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl> -- 從此類別繼承的一些類別範例包括                          <xref:System.Windows.Controls.MenuItem>、                          <xref:System.Windows.Controls.TreeViewItem> 及                          <xref:System.Windows.Controls.ToolBar>。  
  
-  
  
 如需有關這些基底類別的詳細資訊，請參閱                  [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)。  
  
## <a name="see-also"></a>另請參閱  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [按分類區隔控制項](../../../../docs/framework/wpf/controls/controls-by-category.md)   
 [控制項程式庫](../../../../docs/framework/wpf/controls/control-library.md)   
 [資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [輸入](../../../../docs/framework/wpf/advanced/input-wpf.md)   
 [啟用命令](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)   
 [逐步解說：建立自訂動畫按鈕](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)
