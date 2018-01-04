---
title: "樣式設定和範本化"
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
- triggers [WPF]
- styles [WPF], referencing
- event triggers [WPF]
- styles [WPF], prerequisites
- styles [WPF], declaring
- styles [WPF], overview
- styles [WPF], extending
- styles [WPF], triggers
- styles [WPF], event triggers
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c33739d0e753146ffdc8b825d88c6ca7ba63fa1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="styling-and-templating"></a>樣式設定和範本化
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 樣式設定和範本化係指一套功能 (樣式、範本、觸發程序及分鏡腳本)，可讓開發人員和設計人員創造引人注目的效果，並為其產品建立一致的外觀。 雖然開發人員和 (或) 設計人員可以依個別應用程式廣泛地自訂外觀，但強大的樣式設定和範本化模型仍有其必要性，這可允許在應用程式內或應用程式之間維護及共用外觀。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 便有提供該模型。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 樣式設定模型的另一項功能是將呈現與邏輯區分開來。 這意謂著設計人員可以在開發人員使用 C# 或 Visual Basic 來處理程式設計邏輯的同時，僅使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來處理應用程式的外觀。  
  
 本概觀將焦點放在應用程式的樣式設定和範本化方面，而不討論任何資料繫結概念。 如需有關資料繫結的資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 此外，了解資源相當重要，資源可讓您重複使用樣式和範本。 如需有關資源的詳細資訊，請參閱 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 
  
<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>樣式設定和範本化範例  
 本概觀中使用的程式碼範例是根據下圖中所示的簡單相片範例：  
  
 ![已設定樣式的 ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 這個簡單的相片範例使用樣式設定和範本化，來創造引人注目的使用者體驗。 這個範例有兩個<xref:System.Windows.Controls.TextBlock>項目和<xref:System.Windows.Controls.ListBox>控制項繫結至映像清單。 如需完整範例，請參閱[樣式設定和範本化範例簡介 (英文)](http://go.microsoft.com/fwlink/?LinkID=160010)。  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>樣式基本概念  
 您可以將<xref:System.Windows.Style>作為簡便方式，將一組屬性值套用至一個以上的項目。 例如，請考慮下列<xref:System.Windows.Controls.TextBlock>項目和其預設外觀：  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![樣式設定範例螢幕擷取畫面](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 您可以藉由設定屬性，例如變更的預設外觀<xref:System.Windows.Controls.Control.FontSize%2A>和<xref:System.Windows.Controls.Control.FontFamily%2A>，每個<xref:System.Windows.Controls.TextBlock>直接項目。 不過，如果您想要您<xref:System.Windows.Controls.TextBlock>項目共用某些屬性，您可以建立<xref:System.Windows.Style>中`Resources`區段您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，如下所示：  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 當您將<xref:System.Windows.Style.TargetType%2A>樣式的<xref:System.Windows.Controls.TextBlock>型別，該樣式會套用到所有<xref:System.Windows.Controls.TextBlock>視窗中的項目。  
  
 現在<xref:System.Windows.Controls.TextBlock>項目會出現，如下所示：  
  
 ![樣式設定範例螢幕擷取畫面](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>延伸樣式  
 您也許想您兩個<xref:System.Windows.Controls.TextBlock>共用某些屬性值，例如項目<xref:System.Windows.Controls.Control.FontFamily%2A>和置中對齊<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>，但是您也想文字 「 我的圖片 」 有一些額外的屬性。 您可以建立一個以第一個樣式為基礎的新樣式來達到該目的，如以下所示：  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 請注意，前一個樣式已有指定的 `x:Key`。 若要套用樣式，您將<xref:System.Windows.FrameworkElement.Style%2A>屬性您<xref:System.Windows.Controls.TextBlock>至`x:Key`值，如下所示：  
  
 [!code-xaml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 這<xref:System.Windows.Controls.TextBlock>樣式現在具有<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>值<xref:System.Windows.HorizontalAlignment.Center>、<xref:System.Windows.Controls.TextBlock.FontFamily%2A>值`Comic Sans MS`、 <xref:System.Windows.Controls.TextBlock.FontSize%2A> 26 的值和<xref:System.Windows.Controls.TextBlock.Foreground%2A>值設定為<xref:System.Windows.Media.LinearGradientBrush>範例所示。 請注意，它會覆寫<xref:System.Windows.Controls.Control.FontSize%2A>的基底樣式值。 如果有一個以上<xref:System.Windows.Setter>中設定相同屬性<xref:System.Windows.Style>、<xref:System.Windows.Setter>也就是宣告最後會優先採用。  
  
 下列範例示範什麼<xref:System.Windows.Controls.TextBlock>項目現在看起來像：  
  
 ![已設定樣式的 TextBlock](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 這`TitleText`樣式擴充為所建立的樣式<xref:System.Windows.Controls.TextBlock>型別。 您也可以使用 `x:Key` 值來延伸具有 `x:Key` 的樣式。 如需範例，請參閱提供的範例<xref:System.Windows.Style.BasedOn%2A>屬性。  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType 屬性 (Property) 與 x:Key 屬性 (Attribute) 的關聯性  
 第一個範例所示，設定<xref:System.Windows.Style.TargetType%2A>屬性`TextBlock`未指派樣式情況下`x:Key`會將樣式套用至所有<xref:System.Windows.Controls.TextBlock>項目。 在此情況下，`x:Key` 會隱含地設定為 `{x:Type TextBlock}`。 這表示，如果您明確設定`x:Key`以外任何內容值`{x:Type TextBlock}`、<xref:System.Windows.Style>不會套用到所有<xref:System.Windows.Controls.TextBlock>項目自動。 相反地，您必須將樣式套用 (利用`x:Key`值) 到<xref:System.Windows.Controls.TextBlock>元素明確。 如果您的風格的資源區段中，您未設定<xref:System.Windows.Style.TargetType%2A>屬性上您的風格，則您必須提供`x:Key`。  
  
 除了提供的預設值`x:Key`、<xref:System.Windows.Style.TargetType%2A>屬性會指定要套用 setter 屬性的型別。 如果您未指定<xref:System.Windows.Style.TargetType%2A>，您必須使用限定名稱中的屬性您<xref:System.Windows.Setter>物件的類別名稱，可以使用語法`Property="ClassName.Property"`。 例如，而不是設定`Property="FontSize"`，您必須設定<xref:System.Windows.Setter.Property%2A>至`"TextBlock.FontSize"`或`"Control.FontSize"`。  
  
 另請注意，許多 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項都是由其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的組合所組成。 如果您建立一個套用到某個型別所有控制項的樣式，可能會獲得非預期的結果。 例如，如果您建立目標的樣式<xref:System.Windows.Controls.TextBlock>輸入<xref:System.Windows.Window>，樣式套用至所有<xref:System.Windows.Controls.TextBlock>控制項在視窗中，即使<xref:System.Windows.Controls.TextBlock>屬於另一個控制項，例如<xref:System.Windows.Controls.ListBox>。  
  
### <a name="styles-and-resources"></a>樣式和資源  
 您可以使用任何項目，衍生自樣式<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。 宣告樣式的最常見方式是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案的 `Resources` 區段中宣告成資源，如先前的範例所示。 由於樣式是資源，因此它們會遵守適用於所有資源的相同範圍限定規則；您宣告樣式的位置會影響可以套用樣式的位置。 例如，如果您是在應用程式定義 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案的根元素中宣告樣式，就可在應用程式中的任何地方使用該樣式。 如果您建立一個導覽應用程式並在應用程式的其中一個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中宣告樣式，則只能在該 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中使用該樣式。 如需有關資源範圍限定規則的詳細資訊，請參閱 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 此外，您也可以在本概觀稍後的[共用的資源和佈景主題](#styling_themes)中，找到有關樣式和資源的詳細資訊。  
  
### <a name="setting-styles-programmatically"></a>以程式設計方式設定樣式  
 若要以程式設計的方式指派具名的樣式的項目，從資源集合中取得的樣式，並將它指派至的項目<xref:System.Windows.FrameworkElement.Style%2A>屬性。 請注意，在資源集合中的項目屬於類型<xref:System.Object>。 因此，您必須轉換為要擷取的樣式<xref:System.Windows.Style>之前將它指派給<xref:System.Windows.FrameworkElement.Style%2A>屬性。 例如，若要設定在定義`TitleText`樣式上<xref:System.Windows.Controls.TextBlock>名為`textblock1`，執行下列動作：  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 請注意，套用樣式之後，系統就會將它密封而無法供您變更。 如果您想要動態變更已經套用的樣式，就必須建立新的樣式來取代現有的樣式。 如需詳細資訊，請參閱 <xref:System.Windows.Style.IsSealed%2A> 屬性 (Property)。  
  
 您可以建立一個物件來根據自訂邏輯選擇要套用的樣式。 如需範例，請參閱提供的範例<xref:System.Windows.Controls.StyleSelector>類別。  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>繫結、動態資源及事件處理常式  
 請注意，您可以使用 `Setter.Value` 屬性來指定 [Binding 標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)或 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。 如需詳細資訊，請參閱 < 為提供的範例<xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType>屬性。  
  
 到目前為止，本概觀僅討論使用 setter 來設定屬性值。 您也可以在樣式中指定事件處理常式。 如需詳細資訊，請參閱<xref:System.Windows.EventSetter>。  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>資料範本  
 在此範例應用程式中，沒有<xref:System.Windows.Controls.ListBox>控制項繫結至相片的清單：  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 這<xref:System.Windows.Controls.ListBox>目前看起來像下面這樣：  
  
 ![套用範本之前的 ListBox](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 大多數控制項都有某個型別的內容，而該內容通常來自您要繫結的資料。 在此範例中，該資料是相片清單。 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，您使用<xref:System.Windows.DataTemplate>來定義資料的視覺化表示法。 基本上，什麼您放入<xref:System.Windows.DataTemplate>決定資料在呈現的應用程式中的外觀。  
  
 在我們的範例應用程式中，每個自訂的 `Photo` 物件都有一個字串型別的 `Source` 屬性，用來指定影像的檔案路徑。 目前，相片物件是顯示成檔案路徑。  
  
 在您建立，相片才會顯示為映像中，<xref:System.Windows.DataTemplate>做為資源：  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 請注意，<xref:System.Windows.DataTemplate.DataType%2A>屬性是非常類似於<xref:System.Windows.Style.TargetType%2A>屬性<xref:System.Windows.Style>。 如果您<xref:System.Windows.DataTemplate>處於 [資源] 區段中，當您指定<xref:System.Windows.DataTemplate.DataType%2A>屬性的型別並不會將它指派`x:Key`、<xref:System.Windows.DataTemplate>出現該類型時套用。 您一律可以選擇来指派<xref:System.Windows.DataTemplate>與`x:Key`然後將它做為設定`StaticResource`屬性接受<xref:System.Windows.DataTemplate>類型，例如<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性或<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性。  
  
 基本上，<xref:System.Windows.DataTemplate>在上述範例中定義的就`Photo`物件，它應該會顯示為<xref:System.Windows.Controls.Image>內<xref:System.Windows.Controls.Border>。 與這個<xref:System.Windows.DataTemplate>，我們的應用程式現在看起來像這樣：  
  
 ![相片影像](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 資料範本化模型還提供其他功能。 例如，如果您要顯示包含使用其他集合的集合資料<xref:System.Windows.Controls.HeaderedItemsControl>輸入例如<xref:System.Windows.Controls.Menu>或<xref:System.Windows.Controls.TreeView>，沒有<xref:System.Windows.HierarchicalDataTemplate>。 另一個資料範本化功能是<xref:System.Windows.Controls.DataTemplateSelector>，可讓您選擇<xref:System.Windows.DataTemplate>使用根據自訂邏輯。 如需詳細資訊，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)，其中提供不同資料範本化功能的更深入探討。  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>控制項範本  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Controls.ControlTemplate>控制項的定義控制項的外觀。 您可以藉由定義 新變更的結構和控制項的外觀<xref:System.Windows.Controls.ControlTemplate>控制項。 在許多情況下，這會賦予您足夠的彈性，讓您不需要撰寫自己的自訂控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>觸發程序  
 觸發程序會在屬性值發生變更或在某個事件被引發時，設定屬性或啟動動作 (例如動畫)。 <xref:System.Windows.Style><xref:System.Windows.Controls.ControlTemplate>，和<xref:System.Windows.DataTemplate>都`Triggers`包含觸發程序的一組屬性。 有各種不同類型的觸發程序。  
  
### <a name="property-triggers"></a>屬性觸發程序  
 A<xref:System.Windows.Trigger>設定屬性值，或啟動屬性的值為基礎的動作稱為屬性觸發程序。  
  
 若要示範如何使用屬性觸發程序，您可以讓每個<xref:System.Windows.Controls.ListBoxItem>部分透明，除非選取它。 下列樣式設定<xref:System.Windows.UIElement.Opacity%2A>值<xref:System.Windows.Controls.ListBoxItem>至`0.5`。 當<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>屬性是`true`，不過<xref:System.Windows.UIElement.Opacity%2A>設`1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 這個範例會使用<xref:System.Windows.Trigger>設定屬性值，但請注意，<xref:System.Windows.Trigger>類別也有<xref:System.Windows.TriggerBase.EnterActions%2A>和<xref:System.Windows.TriggerBase.ExitActions%2A>啟用觸發程序來執行動作的屬性。  
  
 請注意，<xref:System.Windows.FrameworkElement.MaxHeight%2A>屬性<xref:System.Windows.Controls.ListBoxItem>設`75`。 在下圖中，第三個項目是已選取的項目：  
  
 ![已設定樣式的 ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTrigger 和分鏡腳本  
 觸發程序的另一種是<xref:System.Windows.EventTrigger>，以便啟動的一組根據事件發生的動作。 例如，下列<xref:System.Windows.EventTrigger>物件指定當滑鼠指標進入<xref:System.Windows.Controls.ListBoxItem>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>的值以動畫展示屬性`90`透過`0.2`第二個間隔。 當滑鼠指標從項目移開時，該屬性會在 `1` 秒的期間內恢復成原始值。 請注意如何不需要指定<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>值<xref:System.Windows.ContentElement.MouseLeave>動畫。 這是因為動畫能夠記錄原始值。  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 如需詳細資訊，請參閱[分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 在下圖中，滑鼠指標正指向第三個項目：  
  
 ![樣式設定範例螢幕擷取畫面](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTrigger、DataTrigger 及 MultiDataTrigger  
 除了<xref:System.Windows.Trigger>和<xref:System.Windows.EventTrigger>，有其他類型的觸發程序。 <xref:System.Windows.MultiTrigger>可讓您設定多個條件為基礎的屬性值。 您使用<xref:System.Windows.DataTrigger>和<xref:System.Windows.MultiDataTrigger>當條件的屬性是資料繫結。  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>共用的資源和佈景主題  
 典型的 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 應用程式可能會有多個透過應用程式套用的使用者介面 (UI) 資源。 這組資源集體可視為應用程式的佈景主題。 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]提供的支援封裝的使用者介面 (UI) 資源為主題所使用的資源字典會封裝為<xref:System.Windows.ResourceDictionary>類別。  
  
 定義 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 佈景主題時，是透過使用 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 所公開來自訂任何元素之視覺效果的樣式設定和範本化機制來定義。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 佈景主題資源儲存在內嵌資源字典中。 這些資源字典必須內嵌在已簽署的組件內，並且可內嵌在與程式碼本身相同的組件中，也可內嵌在並存的組件中。 以 PresentationFramework.dll (包含 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 控制項的組件) 為例，佈景主題資源是位於一系列並存的組件中。  
  
 當搜尋元素的樣式時，佈景主題會成為最後一個要查看的地方。 一般而言，搜尋會從元素樹狀目錄往上開始、搜尋適當的資源，然後查看應用程式資源集合，最後查詢系統。 這會為應用程式開發人員提供一個機會，可在到達佈景主題之前，先為樹狀目錄或應用程式層級的任何物件，重新定義樣式。  
  
 您可以將資源字典定義成個別的檔案，這可讓您跨多個應用程式重複使用佈景主題。 您也可以透過定義多個資源字典來提供類型相同但值不同的資源，以建立可切換的佈景主題。 重新定義這些樣式或其他應用程式層級的資源，是簡化應用程式的建議做法。  
  
 若要共用一組資源，包括樣式和範本，跨應用程式，您可以建立[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，並定義<xref:System.Windows.ResourceDictionary>。 例如，請看看下圖，當中顯示部分的[使用 ControlTemplates 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)：  
  
 ![控制項範本範例](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 如果您查看範例中的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案，您將會發現這些檔案都具有下列內容：  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 它是共用`shared.xaml`，而後者可定義<xref:System.Windows.ResourceDictionary>，其中包含一組樣式和筆刷資源，可讓具有一致的外觀範例中的控制項。  
  
 如需詳細資訊，請參閱[合併的資源字典](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)。  
  
 如果您要為自訂控制項建立佈景主題，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)的＜外部控制項程式庫＞一節。  
  
## <a name="see-also"></a>請參閱  
 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [操作說明：尋找 ControlTemplate 產生的元素](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [尋找 DataTemplate 產生的元素](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
