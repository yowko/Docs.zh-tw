---
title: "設定樣式和範本 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "觸發程序"
  - "參考的樣式"
  - "事件觸發程序"
  - "必要條件的樣式"
  - "宣告的樣式"
  - "樣式、 概觀"
  - "擴充的樣式"
  - "觸發程序的樣式"
  - "事件觸發程序的樣式"
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# 設定樣式和範本
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]設定樣式和範本參考的功能 （樣式、 範本、 觸發程序，以及分鏡腳本） 可讓開發人員和設計工具來建立美觀的效果，並建立一致的外觀，其產品的套件。 雖然開發人員和/或設計工具來自訂廣泛為基礎的應用程式的應用程式的外觀和強式設定樣式和範本模型才能允許維護和分享以內和之間的應用程式的外觀。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供該模型。  
  
 另一項功能的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]樣式模型就是區隔展示和邏輯。 這表示只會使用設計工具可以運作的應用程式外觀[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]在同時使用 C# 或 Visual Basic 開發人員在程式設計邏輯。  
  
 本概觀著重於應用程式的設定樣式和範本方面並不討論任何資料繫結概念。 如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 此外，務必了解是什麼讓樣式和範本可重複使用的資源。 如需資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
   
  
<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>設定樣式和範本化範例  
 本概觀中所使用的程式碼範例根據簡單的相片範例，如下圖所示︰  
  
 ![樣式的 ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 這個簡單的相片範例使用設定樣式和範本來建立美觀的使用者經驗。 此範例有兩個<xref:System.Windows.Controls.TextBlock>項目和<xref:System.Windows.Controls.ListBox>控制項繫結至映像清單。 如需完整的範例，請參閱[樣式和範本化範例簡介](http://go.microsoft.com/fwlink/?LinkID=160010)。  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>樣式的基本概念  
 您可以將<xref:System.Windows.Style>做為套用至一個以上的項目屬性值的便利方式。 例如，請考慮下列<xref:System.Windows.Controls.TextBlock>項目和其預設外觀︰  
  
 [!code-xml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![設定樣式範例螢幕擷取畫面](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")  
  
 您可以變更預設外觀設定的屬性，例如<xref:System.Windows.Controls.Control.FontSize%2A>和<xref:System.Windows.Controls.Control.FontFamily%2A>，每個<xref:System.Windows.Controls.TextBlock>直接項目。 不過，如果您想要您<xref:System.Windows.Controls.TextBlock>項目共用某些屬性，您可以建立<xref:System.Windows.Style>中`Resources`區段您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，如下所示︰  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 當您設定<xref:System.Windows.Style.TargetType%2A>樣式的<xref:System.Windows.Controls.TextBlock>型別，該樣式會套用至所有<xref:System.Windows.Controls.TextBlock>  視窗中的項目。  
  
 現在<xref:System.Windows.Controls.TextBlock>項目會出現，如下所示︰  
  
 ![設定樣式範例螢幕擷取畫面](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>擴充樣式  
 通常您會想您兩個<xref:System.Windows.Controls.TextBlock>項目共用某些屬性值，例如<xref:System.Windows.Controls.Control.FontFamily%2A>和置中對齊<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>，但您也想 「 我的圖片 」 來取得其他的屬性的文字。 您可以執行，藉由建立新的樣式為基礎的第一個樣式，如下所示︰  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 請注意，先前的樣式會指定`x:Key`。 若要套用樣式，您將<xref:System.Windows.FrameworkElement.Style%2A>屬性您<xref:System.Windows.Controls.TextBlock>至`x:Key`值，如下所示︰  
  
 [!code-xml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 這<xref:System.Windows.Controls.TextBlock>樣式現在擁有<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>值<xref:System.Windows.HorizontalAlignment>、 <xref:System.Windows.Controls.TextBlock.FontFamily%2A>值`Comic Sans MS`、 <xref:System.Windows.Controls.TextBlock.FontSize%2A> 26 的值和<xref:System.Windows.Controls.TextBlock.Foreground%2A>值設為<xref:System.Windows.Media.LinearGradientBrush>範例所示。 請注意，它會覆寫<xref:System.Windows.Controls.Control.FontSize%2A>基底的樣式值。 如果有多個<xref:System.Windows.Setter>中設定相同屬性<xref:System.Windows.Style>、 <xref:System.Windows.Setter>也就是宣告最後一個擁有優先權。  
  
 下圖顯示什麼<xref:System.Windows.Controls.TextBlock>項目看起來像︰  
  
 ![樣式的 Textblock](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 這`TitleText`樣式擴充為所建立的樣式<xref:System.Windows.Controls.TextBlock>型別。 您也可以擴充以有`x:Key`使用`x:Key`值。 如需範例，請參閱提供的範例<xref:System.Windows.Style.BasedOn%2A>屬性。  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType 屬性和 X:key 屬性之間的關係  
 第一個範例所示，設定<xref:System.Windows.Style.TargetType%2A>屬性`TextBlock`而不指派樣式`x:Key`會將樣式套用至所有<xref:System.Windows.Controls.TextBlock>項目。 在此情況下，`x:Key`隱含地設定為`{x:Type TextBlock}`。 這表示，如果您明確設定`x:Key`以外的任何值`{x:Type TextBlock}`、<xref:System.Windows.Style>不會套用至所有<xref:System.Windows.Controls.TextBlock>項目自動。 相反地，您必須套用的樣式 (使用`x:Key`值) 到<xref:System.Windows.Controls.TextBlock>項目明確。 如果您的風格的資源區段中，您沒有設定<xref:System.Windows.Style.TargetType%2A>屬性，您的風格，則您必須提供`x:Key`。  
  
 除了提供的預設值`x:Key`、 <xref:System.Windows.Style.TargetType%2A>屬性會指定 set 存取子屬性套用至型別。 如果您未指定<xref:System.Windows.Style.TargetType%2A>，您必須限定名稱中的屬性您<xref:System.Windows.Setter>物件的類別名稱，可以使用語法`Property="ClassName.Property"`。 例如，不要設定`Property="FontSize"`，您必須設定<xref:System.Windows.Setter.Property%2A>至`"TextBlock.FontSize"`或`"Control.FontSize"`。  
  
 也請注意，許多[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項所組成的其他組合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項。 如果您建立適用於所有類型的控制項的樣式，您可能會收到非預期的結果。 例如，如果您建立目標的樣式<xref:System.Windows.Controls.TextBlock>輸入<xref:System.Windows.Window>，樣式會套用至所有<xref:System.Windows.Controls.TextBlock>控制項在視窗中，即使<xref:System.Windows.Controls.TextBlock>屬於另一個控制項，例如<xref:System.Windows.Controls.ListBox>。  
  
### <a name="styles-and-resources"></a>樣式和資源  
 您可以使用衍生自任何項目樣式<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。 宣告樣式的最常見方式是做為中`Resources`一節中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，因為前一個範例所示。 樣式是資源，因為它們會遵循相同的範圍規則可套用至所有資源。在您宣告樣式會影響套用樣式的位置。 例如，如果您宣告您的應用程式定義的根項目中的樣式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案中，樣式可以隨處使用應用程式中。 如果您建立導覽應用程式中的應用程式的其中一個宣告樣式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，樣式可以用僅在於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案。 如需範圍規則的資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 此外，您可以在此找到更多資訊樣式和中的資源[共用資源和佈景主題](#styling_themes)稍後在本概觀中。  
  
### <a name="setting-styles-programmatically"></a>以程式設計方式設定樣式  
 若要以程式設計的方式指派具名的樣式的項目，套用樣式資源集合，並將它指派給項目的<xref:System.Windows.FrameworkElement.Style%2A>屬性。 請注意，資源集合中的項目都屬於型別<xref:System.Object>。 因此，您必須轉換為要擷取的樣式<xref:System.Windows.Style>之前指派到<xref:System.Windows.FrameworkElement.Style%2A>屬性。 例如，若要將定義`TitleText`樣式上<xref:System.Windows.Controls.TextBlock>名為`textblock1`，執行下列動作︰  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 請注意，一旦已套用的樣式，它已密封且無法變更。 如果您想要動態變更已套用的樣式，您必須建立新的樣式，來取代現有的交易。 如需詳細資訊，請參閱<xref:System.Windows.Style.IsSealed%2A>屬性。  
  
 您可以建立選擇將根據自訂邏輯套用樣式的物件。 如需範例，請參閱提供的範例<xref:System.Windows.Controls.StyleSelector>類別。  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>繫結，動態資源和事件處理常式  
 請注意，您可以使用`Setter.Value`屬性來指定[繫結標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)或[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。 如需詳細資訊，請參閱提供的範例<xref:System.Windows.Setter.Value%2A?displayProperty=fullName>屬性。  
  
 到目前為止，本概觀僅討論使用可設定屬性值的 setter。 您也可以指定樣式中的事件處理常式。 如需詳細資訊，請參閱<xref:System.Windows.EventSetter>。  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>資料範本  
 在此範例應用程式中，沒有<xref:System.Windows.Controls.ListBox>控制項繫結至相片的清單︰  
  
 [!code-xml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 這<xref:System.Windows.Controls.ListBox>目前看起來如下︰  
  
 ![套用範本之前的 ListBox](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 大部分控制項都有某些類型的內容，以及該內容通常是來自您要繫結的資料。 在此範例中，資料是相片的清單。 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，您使用<xref:System.Windows.DataTemplate>來定義資料的視覺化表示。 基本上，什麼您放入<xref:System.Windows.DataTemplate>決定資料在呈現的應用程式的外觀。  
  
 在我們的範例應用程式，每個自訂`Photo`物件具有`Source`類型的字串，指定影像的檔案路徑的屬性。 目前，相片物件顯示為檔案路徑。  
  
 會顯示為影像的相片，您會建立<xref:System.Windows.DataTemplate>做為資源︰  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 請注意，<xref:System.Windows.DataTemplate.DataType%2A>屬性是非常類似於<xref:System.Windows.Style.TargetType%2A>屬性<xref:System.Windows.Style>。 如果您<xref:System.Windows.DataTemplate>是在資源區段中，當您指定<xref:System.Windows.DataTemplate.DataType%2A>屬性的型別並不會將它指派`x:Key`、 <xref:System.Windows.DataTemplate>出現該類型時套用。 您永遠可以選擇来指派<xref:System.Windows.DataTemplate>與`x:Key`然後將它做為設定`StaticResource`屬性採用<xref:System.Windows.DataTemplate>型別，例如<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性或<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性。  
  
 基本上， <xref:System.Windows.DataTemplate>在上述範例中定義的就會`Photo`物件，它應該會顯示為<xref:System.Windows.Controls.Image>內<xref:System.Windows.Controls.Border>。 與這個<xref:System.Windows.DataTemplate>，我們的應用程式現在看起來像這樣︰  
  
 ![相片影像](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 資料範本化模型提供其他功能。 例如，如果您要顯示包含使用其他集合的集合資料<xref:System.Windows.Controls.HeaderedItemsControl>輸入如<xref:System.Windows.Controls.Menu>或<xref:System.Windows.Controls.TreeView>，沒有<xref:System.Windows.HierarchicalDataTemplate>。 另一個資料範本化功能是<xref:System.Windows.Controls.DataTemplateSelector>，可讓您選擇<xref:System.Windows.DataTemplate>使用根據自訂邏輯。 如需詳細資訊，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)，它會提供不同的資料範本化功能的更深入討論。  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>控制項範本  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、 <xref:System.Windows.Controls.ControlTemplate>控制項的定義控制項的外觀。 您可以藉由定義新變更的結構和控制項的外觀<xref:System.Windows.Controls.ControlTemplate>控制項。 在許多情況下，這樣您足夠的彈性，您不需要撰寫您自己的自訂控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>觸發程序  
 觸發程序設定的屬性，或啟動的動作，例如動畫，或在屬性值變更時引發事件時。 <xref:System.Windows.Style>， <xref:System.Windows.Controls.ControlTemplate>，和<xref:System.Windows.DataTemplate>都`Triggers`包含觸發程序的一組屬性。 有各種類型的觸發程序。  
  
### <a name="property-triggers"></a>屬性觸發程序  
 A<xref:System.Windows.Trigger>集 」 屬性值，或啟動屬性的值為基礎的動作稱為屬性觸發程序。  
  
 為了示範如何使用屬性觸發程序，您可以讓每個<xref:System.Windows.Controls.ListBoxItem>部分透明，除非已選取。 下列樣式設定<xref:System.Windows.UIElement.Opacity%2A>值<xref:System.Windows.Controls.ListBoxItem>到`0.5`。 當<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>屬性是`true`，不過<xref:System.Windows.UIElement.Opacity%2A>設為`1.0`:  
  
 [!code-xml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 這個範例會使用<xref:System.Windows.Trigger>設定屬性值，但請注意，<xref:System.Windows.Trigger>類別也有<xref:System.Windows.TriggerBase.EnterActions%2A>和<xref:System.Windows.TriggerBase.ExitActions%2A>啟用觸發程序來執行動作的屬性。  
  
 請注意， <xref:System.Windows.FrameworkElement.MaxHeight%2A>屬性<xref:System.Windows.Controls.ListBoxItem>設為`75`。 在下圖中，第三個項目會是選取的項目︰  
  
 ![樣式的 ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers 和分鏡腳本  
 觸發程序的另一種是<xref:System.Windows.EventTrigger>，以便啟動一組根據事件發生的動作。 例如，下列<xref:System.Windows.EventTrigger>物件指定當滑鼠指標進入<xref:System.Windows.Controls.ListBoxItem>、 <xref:System.Windows.FrameworkElement.MaxHeight%2A>屬性產生值的動畫`90`透過`0.2`第二段。 當滑鼠移開的項目時，屬性會傳回原始值經過一段`1`第二個。 請注意，它不需要指定<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>值<xref:System.Windows.ContentElement.MouseLeave>動畫。 這是因為動畫可以追蹤的原始值。  
  
 [!code-xml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 如需詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 在下圖中，滑鼠指向第三個項目︰  
  
 ![設定樣式範例螢幕擷取畫面](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers、 DataTriggers 和 MultiDataTriggers  
 除了<xref:System.Windows.Trigger>和<xref:System.Windows.EventTrigger>，還有其他類型的觸發程序。 <xref:System.Windows.MultiTrigger>可讓您設定多個條件為基礎的屬性值。 您使用<xref:System.Windows.DataTrigger>和<xref:System.Windows.MultiDataTrigger>若條件的屬性是資料繫結。  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>共用的資源和佈景主題  
 一般[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]應用程式可能有多個會套用在整個應用程式的使用者介面 (UI) 資源。 整體而言，這組資源也可視為應用程式的佈景主題。 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]使用提供支援封裝使用者介面 (UI) 資源為主題資源字典，其封裝為<xref:System.Windows.ResourceDictionary>類別。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]透過設定樣式和範本機制來定義佈景主題的[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]公開自訂視覺效果的任何項目。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]佈景主題資源會儲存在內嵌的資源字典。 這些資源字典必須內嵌在簽署的組件，而且可以是內嵌程式碼本身相同的組件或由並存組件中。 在 PresentationFramework.dll，其中包含組件的情況下[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]控制項、 佈景主題資源位於一系列的並存組件。  
  
 佈景主題會變成尋找搜尋項目樣式時的最後一個位置。 一般而言，搜尋會開始藉由查核項目樹狀目錄中搜尋適當的資源，則應用程式資源集合中尋找，最後查詢系統。 這可讓應用程式開發人員有機會重新定義樹狀目錄或應用程式層級的任何物件的樣式之前達到佈景主題。  
  
 您可以為個別的檔案，可讓您重複使用多個應用程式的主題定義資源字典。 您也可以定義多個提供相同類型的資源，但是具有不同值的資源字典，以建立可切換的主題。 重新定義這些樣式或其他應用程式層級的資源是外觀設定應用程式的建議的方法。  
  
 若要共用一組資源，包括樣式和範本，在各個應用程式，您可以建立[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，並定義<xref:System.Windows.ResourceDictionary>。 比方說，看看下圖顯示的部分， [ControlTemplates 範例樣式](http://go.microsoft.com/fwlink/?LinkID=160041):  
  
 ![控制項範本範例](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 如果您看一下[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例中的檔案，您會發現所有的檔案具有下列︰  
  
 [!code-xml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 它是共用`shared.xaml`，以定義<xref:System.Windows.ResourceDictionary> ，其中包含一組樣式和筆刷資源，可讓擁有一致的外觀範例中的控制項。  
  
 如需詳細資訊，請參閱[合併的資源字典](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)。  
  
 如果您要建立佈景主題為您自訂控制項，請參閱外部控制項程式庫的[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 WPF 中的 pack Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)   
 [如何︰ 尋找 ControlTemplate 產生的項目](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)   
 [尋找 DataTemplate 產生的項目](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)