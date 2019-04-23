---
title: 樣式設定和範本化
ms.date: 03/30/2017
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
ms.openlocfilehash: 3fae4993a13b02ad998668f644a80ba7c07196fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132287"
---
# <a name="styling-and-templating"></a>樣式設定和範本化
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 樣式設定和範本化係指一套功能 (樣式、範本、觸發程序及分鏡腳本)，可讓開發人員和設計人員創造引人注目的效果，並為其產品建立一致的外觀。 雖然開發人員和 (或) 設計人員可以依個別應用程式廣泛地自訂外觀，但強大的樣式設定和範本化模型仍有其必要性，這可允許在應用程式內或應用程式之間維護及共用外觀。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 便有提供該模型。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 樣式設定模型的另一項功能是將呈現與邏輯區分開來。 這意謂著設計人員可以在開發人員使用 C# 或 Visual Basic 來處理程式設計邏輯的同時，僅使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來處理應用程式的外觀。  
  
 本概觀將焦點放在應用程式的樣式設定和範本化方面，而不討論任何資料繫結概念。 如需有關資料繫結的資訊，請參閱[資料繫結概觀](../data/data-binding-overview.md)。  
  
 此外，了解資源相當重要，資源可讓您重複使用樣式和範本。 如需有關資源的詳細資訊，請參閱 [XAML 資源](../advanced/xaml-resources.md)。

<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>樣式設定和範本化範例  
 本概觀中使用的程式碼範例是根據下圖中所示的簡單相片範例：  
  
 ![已設定樣式的 ListView](./media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 這個簡單的相片範例使用樣式設定和範本化，來創造引人注目的使用者體驗。 此範例有兩個<xref:System.Windows.Controls.TextBlock>項目和<xref:System.Windows.Controls.ListBox>控制項繫結至映像的清單。 如需完整範例，請參閱[樣式設定和範本化範例簡介 (英文)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>樣式基本概念  
 您可以將<xref:System.Windows.Style>作為便利的方式來將一組屬性值套用至一個以上的項目。 例如，請考慮下列<xref:System.Windows.Controls.TextBlock>項目和其預設外觀：  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![樣式設定範例螢幕擷取畫面](./media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 您可以藉由設定屬性，例如變更預設外觀<xref:System.Windows.Controls.Control.FontSize%2A>並<xref:System.Windows.Controls.Control.FontFamily%2A>，在每個<xref:System.Windows.Controls.TextBlock>直接項目。 不過，如果您想要您<xref:System.Windows.Controls.TextBlock>元素共用某些屬性，您可以建立<xref:System.Windows.Style>中`Resources`一節您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，如下所示：  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 當您設定<xref:System.Windows.Style.TargetType%2A>您要的樣式<xref:System.Windows.Controls.TextBlock>型別，樣式會套用到所有<xref:System.Windows.Controls.TextBlock> 視窗中的項目。  
  
 現在<xref:System.Windows.Controls.TextBlock>項目會出現，如下所示：  
  
 ![樣式設定範例螢幕擷取畫面](./media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>延伸樣式  
 或許您想要兩個<xref:System.Windows.Controls.TextBlock>元素共用某些屬性值，例如<xref:System.Windows.Controls.Control.FontFamily%2A>和置中對齊<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>，但您也想要有一些其他屬性的"My Pictures"文字。 您可以建立一個以第一個樣式為基礎的新樣式來達到該目的，如以下所示：  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 請注意，前一個樣式已有指定的 `x:Key`。 若要套用樣式，您設定<xref:System.Windows.FrameworkElement.Style%2A>屬性上的您<xref:System.Windows.Controls.TextBlock>到`x:Key`值，如下所示：  
  
 [!code-xaml[StylingIntroSnippet#UIText](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 這<xref:System.Windows.Controls.TextBlock>樣式現在已<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>的值<xref:System.Windows.HorizontalAlignment.Center>，則<xref:System.Windows.Controls.TextBlock.FontFamily%2A>的值`Comic Sans MS`、<xref:System.Windows.Controls.TextBlock.FontSize%2A>值為 26，和<xref:System.Windows.Controls.TextBlock.Foreground%2A>值設定為<xref:System.Windows.Media.LinearGradientBrush>範例所示。 請注意，它會覆寫<xref:System.Windows.Controls.Control.FontSize%2A>的基底的樣式值。 如果有一個以上<xref:System.Windows.Setter>中設定相同的屬性<xref:System.Windows.Style>，則<xref:System.Windows.Setter>也就是宣告最後一個會優先採用。  
  
 下圖顯示什麼<xref:System.Windows.Controls.TextBlock>元素現在看起來像：  
  
 ![已設定樣式的 TextBlock](./media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 這`TitleText`樣式會擴充已建立的樣式<xref:System.Windows.Controls.TextBlock>型別。 您也可以使用 `x:Key` 值來延伸具有 `x:Key` 的樣式。 如需範例，請參閱針對提供的範例<xref:System.Windows.Style.BasedOn%2A>屬性。  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType 屬性 (Property) 與 x:Key 屬性 (Attribute) 的關聯性  
 第一個範例所示，設定<xref:System.Windows.Style.TargetType%2A>屬性，以`TextBlock`而不為樣式指派`x:Key`會導致將樣式套用至所有<xref:System.Windows.Controls.TextBlock>項目。 在此情況下，`x:Key` 會隱含地設定為 `{x:Type TextBlock}`。 這表示，如果您明確設定`x:Key`以外的其他值的任何項目`{x:Type TextBlock}`，則<xref:System.Windows.Style>不會套用到所有<xref:System.Windows.Controls.TextBlock>項目自動。 相反地，您必須套用的樣式 (使用`x:Key`值) 到<xref:System.Windows.Controls.TextBlock>項目明確。 如果您的樣式是資源區段中，您未設定<xref:System.Windows.Style.TargetType%2A>屬性，您的樣式，則您必須提供`x:Key`。  
  
 除了提供的預設值`x:Key`，則<xref:System.Windows.Style.TargetType%2A>屬性會指定要套用 setter 屬性的型別。 如果您未指定<xref:System.Windows.Style.TargetType%2A>，您必須限定名稱的屬性，在您<xref:System.Windows.Setter>使用語法的類別名稱的物件`Property="ClassName.Property"`。 比方說，而不是設定`Property="FontSize"`，您必須設定<xref:System.Windows.Setter.Property%2A>要`"TextBlock.FontSize"`或`"Control.FontSize"`。  
  
 另請注意，許多 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項都是由其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的組合所組成。 如果您建立一個套用到某個型別所有控制項的樣式，可能會獲得非預期的結果。 比方說，如果您建立目標的樣式<xref:System.Windows.Controls.TextBlock>中輸入<xref:System.Windows.Window>，樣式會套用到所有<xref:System.Windows.Controls.TextBlock>控制項，在視窗中，即使<xref:System.Windows.Controls.TextBlock>屬於另一個控制項，例如<xref:System.Windows.Controls.ListBox>。  
  
### <a name="styles-and-resources"></a>樣式和資源  
 您可以使用衍生自任何項目上的樣式<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。 宣告樣式的最常見方式是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案的 `Resources` 區段中宣告成資源，如先前的範例所示。 由於樣式是資源，因此它們會遵守適用於所有資源的相同範圍限定規則；您宣告樣式的位置會影響可以套用樣式的位置。 例如，如果您是在應用程式定義 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案的根元素中宣告樣式，就可在應用程式中的任何地方使用該樣式。 如果您建立一個導覽應用程式並在應用程式的其中一個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中宣告樣式，則只能在該 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中使用該樣式。 如需有關資源範圍限定規則的詳細資訊，請參閱 [XAML 資源](../advanced/xaml-resources.md)。  
  
 此外，您也可以在本概觀稍後的[共用的資源和佈景主題](#styling_themes)中，找到有關樣式和資源的詳細資訊。  
  
### <a name="setting-styles-programmatically"></a>以程式設計方式設定樣式  
 若要以程式設計方式將具名的樣式指派給項目，獲取的資源集合中的樣式，並將它指派給元素的<xref:System.Windows.FrameworkElement.Style%2A>屬性。 請注意，資源集合中的項目都屬於型別<xref:System.Object>。 因此，您必須轉換為要擷取的樣式<xref:System.Windows.Style>之前將它指派給<xref:System.Windows.FrameworkElement.Style%2A>屬性。 例如，若要設定已定義`TitleText`上設定樣式<xref:System.Windows.Controls.TextBlock>名為`textblock1`，執行下列動作：  
  
 [!code-csharp[StylingIntroSample_snippet#Code](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 請注意，套用樣式之後，系統就會將它密封而無法供您變更。 如果您想要動態變更已經套用的樣式，就必須建立新的樣式來取代現有的樣式。 如需詳細資訊，請參閱 <xref:System.Windows.Style.IsSealed%2A> 屬性 (Property)。  
  
 您可以建立一個物件來根據自訂邏輯選擇要套用的樣式。 如需範例，請參閱針對提供的範例<xref:System.Windows.Controls.StyleSelector>類別。  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>繫結、動態資源及事件處理常式  
 請注意，您可以使用 `Setter.Value` 屬性來指定 [Binding 標記延伸](../advanced/binding-markup-extension.md)或 [DynamicResource 標記延伸](../advanced/dynamicresource-markup-extension.md)。 如需詳細資訊，請參閱提供的範例<xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType>屬性。  
  
 到目前為止，本概觀僅討論使用 setter 來設定屬性值。 您也可以在樣式中指定事件處理常式。 如需詳細資訊，請參閱<xref:System.Windows.EventSetter>。  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>資料範本  
 在此範例應用程式中，沒有<xref:System.Windows.Controls.ListBox>繫結至相片清單的控制項：  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 這<xref:System.Windows.Controls.ListBox>目前看起來如下所示：  
  
 ![套用範本之前的 ListBox](./media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 大多數控制項都有某個型別的內容，而該內容通常來自您要繫結的資料。 在此範例中，該資料是相片清單。 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，您使用<xref:System.Windows.DataTemplate>來定義資料的視覺表示法。 基本上，什麼您放入<xref:System.Windows.DataTemplate>決定資料在轉譯的應用程式中的外觀。  
  
 在我們的範例應用程式中，每個自訂的 `Photo` 物件都有一個字串型別的 `Source` 屬性，用來指定影像的檔案路徑。 目前，相片物件是顯示成檔案路徑。  
  
 在您建立文件，相片才會顯示為映像，<xref:System.Windows.DataTemplate>做為資源：  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 請注意，<xref:System.Windows.DataTemplate.DataType%2A>屬性是非常類似於<xref:System.Windows.Style.TargetType%2A>屬性<xref:System.Windows.Style>。 如果您<xref:System.Windows.DataTemplate>位於 [資源] 區段中，當您指定<xref:System.Windows.DataTemplate.DataType%2A>屬性的型別並不會將它指派`x:Key`，則<xref:System.Windows.DataTemplate>該型別出現時套用。 您一律可以選擇来指派<xref:System.Windows.DataTemplate>具有`x:Key`，然後將它設為`StaticResource`屬性採用<xref:System.Windows.DataTemplate>類型，例如<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性或<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性。  
  
 基本上，<xref:System.Windows.DataTemplate>在上述範例中定義了每當有`Photo`物件，它應該會顯示為<xref:System.Windows.Controls.Image>內<xref:System.Windows.Controls.Border>。 與這個<xref:System.Windows.DataTemplate>，我們的應用程式現在看起來像這樣：  
  
 ![相片影像](./media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 資料範本化模型還提供其他功能。 例如，如果您要顯示包含使用其他集合的集合資料<xref:System.Windows.Controls.HeaderedItemsControl>輸入，例如<xref:System.Windows.Controls.Menu>或<xref:System.Windows.Controls.TreeView>，沒有<xref:System.Windows.HierarchicalDataTemplate>。 另一個資料範本化功能是<xref:System.Windows.Controls.DataTemplateSelector>，這可讓您選擇<xref:System.Windows.DataTemplate>使用根據自訂邏輯。 如需詳細資訊，請參閱[資料範本化概觀](../data/data-templating-overview.md)，其中提供不同資料範本化功能的更深入探討。  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>控制項範本  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，則<xref:System.Windows.Controls.ControlTemplate>控制項的定義控制項的外觀。 您可以藉由定義新變更的結構和控制項的外觀<xref:System.Windows.Controls.ControlTemplate>控制項。 在許多情況下，這會賦予您足夠的彈性，讓您不需要撰寫自己的自訂控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>觸發程序  
 觸發程序會在屬性值發生變更或在某個事件被引發時，設定屬性或啟動動作 (例如動畫)。 <xref:System.Windows.Style><xref:System.Windows.Controls.ControlTemplate>，並<xref:System.Windows.DataTemplate>都有`Triggers`可以包含一組觸發程序的屬性。 有各種不同類型的觸發程序。  
  
### <a name="property-triggers"></a>屬性觸發程序  
 A<xref:System.Windows.Trigger>設定屬性值，或啟動屬性的值為基礎的動作稱為屬性觸發程序。  
  
 為了示範如何使用屬性觸發程序，您可以讓每個<xref:System.Windows.Controls.ListBoxItem>部分透明，除非已選取。 下列樣式集<xref:System.Windows.UIElement.Opacity%2A>的值<xref:System.Windows.Controls.ListBoxItem>至`0.5`。 當<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>屬性是`true`，不過<xref:System.Windows.UIElement.Opacity%2A>設定為`1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 這個範例會使用<xref:System.Windows.Trigger>若要設定的屬性值，但請注意<xref:System.Windows.Trigger>類別也有<xref:System.Windows.TriggerBase.EnterActions%2A>和<xref:System.Windows.TriggerBase.ExitActions%2A>啟用觸發程序執行動作的屬性。  
  
 請注意，<xref:System.Windows.FrameworkElement.MaxHeight%2A>的屬性<xref:System.Windows.Controls.ListBoxItem>設定為`75`。 在下圖中，第三個項目是已選取的項目：  
  
 ![已設定樣式的 ListView](./media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTrigger 和分鏡腳本  
 觸發程序的另一種是<xref:System.Windows.EventTrigger>，這會啟動一組發生的事件為基礎的動作。 例如，下列<xref:System.Windows.EventTrigger>物件指定當滑鼠指標進入<xref:System.Windows.Controls.ListBoxItem>，則<xref:System.Windows.FrameworkElement.MaxHeight%2A>屬性以動畫顯示的值`90`透過`0.2`第二段。 當滑鼠指標從項目移開時，該屬性會在 `1` 秒的期間內恢復成原始值。 請注意如何不需要指定<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>值<xref:System.Windows.ContentElement.MouseLeave>動畫。 這是因為動畫能夠記錄原始值。  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 如需詳細資訊，請參閱[分鏡腳本概觀](../graphics-multimedia/storyboards-overview.md)。  
  
 在下圖中，滑鼠指標正指向第三個項目：  
  
 ![樣式設定範例螢幕擷取畫面](./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTrigger、DataTrigger 及 MultiDataTrigger  
 除了<xref:System.Windows.Trigger>和<xref:System.Windows.EventTrigger>，還有其他類型的觸發程序。 <xref:System.Windows.MultiTrigger> 可讓您設定多個條件為基礎的屬性值。 您使用<xref:System.Windows.DataTrigger>和<xref:System.Windows.MultiDataTrigger>若條件的屬性是資料繫結。  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>共用的資源和佈景主題  
 典型的 Windows Presentation Foundation (WPF) 應用程式可能會有多個套用整個應用程式的使用者介面 (UI) 資源。 這組資源集體可視為應用程式的佈景主題。 Windows Presentation Foundation (WPF) 提供的支援封裝使用者介面 (UI) 資源做為主題藉由使用資源字典，其會封裝為<xref:System.Windows.ResourceDictionary>類別。  
  
 Windows Presentation Foundation (WPF) 佈景主題定義使用的樣式和範本化機制，Windows Presentation Foundation (WPF) 會公開用於自訂的視覺效果的任何項目。  
  
 Windows Presentation Foundation (WPF) 佈景主題資源會儲存在內嵌的資源字典。 這些資源字典必須內嵌在已簽署的組件內，並且可內嵌在與程式碼本身相同的組件中，也可內嵌在並存的組件中。 在 PresentationFramework.dll 中，其中包含 Windows Presentation Foundation (WPF) 控制項的組件的情況下佈景主題資源是一系列並排顯示組件中。  
  
 當搜尋元素的樣式時，佈景主題會成為最後一個要查看的地方。 一般而言，搜尋會從元素樹狀目錄往上開始、搜尋適當的資源，然後查看應用程式資源集合，最後查詢系統。 這會為應用程式開發人員提供一個機會，可在到達佈景主題之前，先為樹狀目錄或應用程式層級的任何物件，重新定義樣式。  
  
 您可以將資源字典定義成個別的檔案，這可讓您跨多個應用程式重複使用佈景主題。 您也可以透過定義多個資源字典來提供類型相同但值不同的資源，以建立可切換的佈景主題。 重新定義這些樣式或其他應用程式層級的資源，是簡化應用程式的建議做法。  
  
 若要共用一組資源，包括樣式和範本，跨應用程式，您可以建立[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，並定義<xref:System.Windows.ResourceDictionary>。 例如，請看看下圖，當中顯示部分的[使用 ControlTemplates 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)：

![控制項範本範例](./media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 如果您查看範例中的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案，您將會發現這些檔案都具有下列內容：  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 它是共用`shared.xaml`，其定義<xref:System.Windows.ResourceDictionary>，其中包含一組樣式和筆刷資源，可讓擁有一致的外觀範例中的控制項。  
  
 如需詳細資訊，請參閱[合併的資源字典](../advanced/merged-resource-dictionaries.md)。  
  
 如果您要為自訂控制項建立佈景主題，請參閱[控制項撰寫概觀](control-authoring-overview.md)的＜外部控制項程式庫＞一節。  
  
## <a name="see-also"></a>另請參閱

- [WPF 中的 Pack URI](../app-development/pack-uris-in-wpf.md)
- [如何：尋找 ControlTemplate 產生的項目](how-to-find-controltemplate-generated-elements.md)
- [尋找 DataTemplate 產生的元素](../data/how-to-find-datatemplate-generated-elements.md)
