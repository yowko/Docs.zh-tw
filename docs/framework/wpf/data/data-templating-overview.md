---
title: "資料範本化概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料繫結、 範本"
  - "資料繫結範本"
  - "資料範本"
  - "資料範本"
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 資料範本化概觀
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料範本化模型會將您提供更多的彈性來定義資料的呈現方式。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項具有內建功能來支援自訂資料的呈現。 本主題會先示範如何定義<xref:System.Windows.DataTemplate> ，則會介紹其他資料範本化功能，例如選取的範本為基礎的自訂邏輯以及支援的階層式資料的顯示。  
  
   
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題著重資料範本化功能，而不是資料繫結概念簡介。 如需基本資料繫結的概念資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 <xref:System.Windows.DataTemplate>是有關資料的呈現方式，而且是其中一個所提供的許多功能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]設定樣式和範本的模型。 本文將介紹的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]設定樣式和範本的模型，例如，如何使用<xref:System.Windows.Style>若要在控制項上設定屬性，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)主題。  
  
 此外，請務必了解`Resources`，這基本上是什麼啟用物件，例如<xref:System.Windows.Style>和<xref:System.Windows.DataTemplate>為可重複使用。 如需資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>資料範本化基本概念  
   
  
 為了示範為什麼<xref:System.Windows.DataTemplate>很重要，現在就來逐一查看資料繫結範例。 在此範例中，我們<xref:System.Windows.Controls.ListBox> ，繫結至一份`Task`物件。 每個`Task`物件具有`TaskName`（字串）， `Description` （字串）、 `Priority` (int)，和型別的屬性`TaskType`，也就是`Enum`值`Home`和`Work`。  
  
 [!code-xml[DataTemplatingIntro_snip#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xml[DataTemplatingIntro_snip#UI1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xml[DataTemplatingIntro_snip#UI2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>沒有 DataTemplate  
 不含<xref:System.Windows.DataTemplate>，我們<xref:System.Windows.Controls.ListBox>目前看起來像這樣︰  
  
 ![資料範本化範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 發生什麼事是，而不需要任何特定的指示，請<xref:System.Windows.Controls.ListBox>預設呼叫`ToString`時想要顯示集合中的物件。 因此，如果`Task`物件會覆寫`ToString`方法，然後在<xref:System.Windows.Controls.ListBox>顯示基礎集合中的每個來源物件的字串表示。  
  
 例如，如果`Task`類別覆寫`ToString`方法如此一來，其中`name`欄位`TaskName`屬性︰  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 然後在<xref:System.Windows.Controls.ListBox>看起來如下︰  
  
 ![資料範本化範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 不過，這限制和彈性。 此外，如果您要繫結[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料，您將無法覆寫`ToString`。  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>定義簡單的 DataTemplate  
 解決方法是定義<xref:System.Windows.DataTemplate>。 若要設定的方法之一是<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性<xref:System.Windows.Controls.ListBox>至<xref:System.Windows.DataTemplate>。 您指定在您<xref:System.Windows.DataTemplate>會變成您的資料物件的視覺化結構。 下列<xref:System.Windows.DataTemplate>相當簡單。 會為每個項目顯示為三個指示<xref:System.Windows.Controls.TextBlock>中的項目<xref:System.Windows.Controls.StackPanel>。 每個<xref:System.Windows.Controls.TextBlock>元素所繫結之屬性的`Task`類別。  
  
 [!code-xml[DataTemplatingIntro_snip#Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 本主題中的範例為基礎的資料是一系列[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]物件。 如果您要繫結[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料，基本概念都相同，但有些微的語法差異。 比方說，而不需`Path=TaskName`，您會設定<xref:System.Windows.Data.Binding.XPath%2A>至`@TaskName`(如果`TaskName`屬性您[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]節點)。  
  
 現在我們<xref:System.Windows.Controls.ListBox>看起來如下︰  
  
 ![資料範本化範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>為資源建立 DataTemplate  
 在上述範例中，我們定義<xref:System.Windows.DataTemplate>內嵌。 它是較常見的資源區段中定義，它可以是可重複使用的物件，如下列範例所示︰  
  
 [!code-xml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xml[DataTemplatingIntro_snip#AsResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 現在您可以使用`myTaskTemplate`做為資源，如下列範例所示︰  
  
 [!code-xml[DataTemplatingIntro_snip#MyTaskTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 因為`myTaskTemplate`是資源，您現在可以使用它所採用的屬性其他控制項<xref:System.Windows.DataTemplate>型別。 為如上所示，如<xref:System.Windows.Controls.ItemsControl>物件，例如<xref:System.Windows.Controls.ListBox>，它是<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性。 如<xref:System.Windows.Controls.ContentControl>物件，它是<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性。  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>資料類型屬性  
 <xref:System.Windows.DataTemplate>類別具有<xref:System.Windows.DataTemplate.DataType%2A>屬性，非常類似於<xref:System.Windows.Style.TargetType%2A>屬性<xref:System.Windows.Style>類別。 因此，而不是指定`x:Key`的<xref:System.Windows.DataTemplate>在上述範例中，您可以執行下列︰  
  
 [!code-xml[DataTemplatingIntro_snip#DataType](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 這<xref:System.Windows.DataTemplate>取得自動套用至所有`Task`物件。 請注意，在此情況下`x:Key`隱含地設定。 因此，如果您指派這個<xref:System.Windows.DataTemplate> `x:Key`值覆寫隱含`x:Key`和<xref:System.Windows.DataTemplate>不會自動套用。  
  
 如果您要繫結<xref:System.Windows.Controls.ContentControl>集合的`Task`物件， <xref:System.Windows.Controls.ContentControl>不會使用上述<xref:System.Windows.DataTemplate>自動。 這是因為繫結的<xref:System.Windows.Controls.ContentControl>需要區別您是否想要繫結至整個集合或個別物件的詳細資訊。 如果您<xref:System.Windows.Controls.ContentControl>正在追蹤的選取項目<xref:System.Windows.Controls.ItemsControl>型別，您可以設定<xref:System.Windows.Data.Binding.Path%2A>屬性<xref:System.Windows.Controls.ContentControl>繫結至 「`/`」，表示您感興趣的目前項目。 如需範例，請參閱[繫結至集合並顯示選取範圍的資訊基礎](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)。 否則，您需要指定<xref:System.Windows.DataTemplate>明確地設定<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性。  
  
 <xref:System.Windows.DataTemplate.DataType%2A>屬性是特別有用，當您有<xref:System.Windows.Data.CompositeCollection>的不同類型的資料物件。 如需範例，請參閱[實作 CompositeCollection](../../../../docs/framework/wpf/data/how-to-implement-a-compositecollection.md)。  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>更加入 DataTemplate  
 目前的資料會出現的必要資訊，不過還有很大的改進空間。 讓我們在簡報上新增改善的<xref:System.Windows.Controls.Border>、<xref:System.Windows.Controls.Grid>，以及一些<xref:System.Windows.Controls.TextBlock>項目，描述所顯示的資料。  
  
 [!code-xml[DataTemplatingIntro#AddingMore](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 下列螢幕擷取畫面顯示<xref:System.Windows.Controls.ListBox>與這個修改過的<xref:System.Windows.DataTemplate>:  
  
 ![資料範本化範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 我們可以設定<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>至<xref:System.Windows.HorizontalAlignment>上<xref:System.Windows.Controls.ListBox>藉此確定項目的寬度會佔用整個空間︰  
  
 [!code-xml[DataTemplatingIntro_snip#Stretch](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 使用<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>屬性設定為<xref:System.Windows.HorizontalAlignment>、 <xref:System.Windows.Controls.ListBox>現在看起來像這樣︰  
  
 ![資料範本化範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>使用 DataTriggers 套用屬性值  
 目前的簡報不會告訴我們是否`Task`是主要的工作或公司的工作。 請記住，`Task`物件具有`TaskType`型別的屬性`TaskType`，這是列舉型別值`Home`和`Work`。  
  
 在下列範例中， <xref:System.Windows.DataTrigger>設定<xref:System.Windows.Controls.Border.BorderBrush%2A>名為項目的`border`至`Yellow`如果`TaskType`屬性是`TaskType.Home`。  
  
 [!code-xml[DataTemplatingIntro#DT](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xml[DataTemplatingIntro#DataTrigger](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 我們的應用程式現在看起來如下所示。 主要的工作會加上黃色框線，且 office 工作會出現一個藍色框線︰  
  
 ![資料範本化範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 在此範例中<xref:System.Windows.DataTrigger>使用<xref:System.Windows.Setter>可設定屬性值。 觸發程序類別也具有<xref:System.Windows.TriggerBase.EnterActions%2A>和<xref:System.Windows.TriggerBase.ExitActions%2A>可讓您開始的一組動作，例如動畫的屬性。 此外，還有<xref:System.Windows.MultiDataTrigger>可讓您將變更套用的類別，根據多個資料繫結屬性值。  
  
 達到相同效果的替代方式是將繫結<xref:System.Windows.Controls.Border.BorderBrush%2A>屬性`TaskType`屬性，並使用傳回的色彩值轉換器型`TaskType`值。 建立上述實際上是使用轉換程式是在效能方面較有效率的。 此外，建立您自己的轉換子提供更大的彈性因為您可以提供您自己的邏輯。 最後，您選擇哪一種技術會隨著您的案例和您的喜好設定而定。 如需有關如何撰寫轉換程式的資訊，請參閱<xref:System.Windows.Data.IValueConverter>。  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>什麼所屬 DataTemplate 中？  
 在上述範例中，我們放在觸發程序<xref:System.Windows.DataTemplate>使用<xref:System.Windows.DataTemplate>。<xref:System.Windows.DataTemplate.Triggers%2A>屬性。 <xref:System.Windows.Setter>的觸發程序設定的項目屬性的值 (<xref:System.Windows.Controls.Border>項目) 內<xref:System.Windows.DataTemplate>。 不過，如果屬性，您`Setters`關心不會在目前的項目屬性<xref:System.Windows.DataTemplate>，可能會更適合使用設定屬性<xref:System.Windows.Style>為<xref:System.Windows.Controls.ListBoxItem>類別 (如果您要繫結的控制項是<xref:System.Windows.Controls.ListBox>)。 例如，如果您想要您<xref:System.Windows.Trigger>動畫<xref:System.Windows.UIElement.Opacity%2A>值的項目時滑鼠指向某個項目，您會定義觸發程序內<xref:System.Windows.Controls.ListBoxItem>樣式。 如需範例，請參閱[樣式和範本化範例簡介](http://go.microsoft.com/fwlink/?LinkID=160010)。  
  
 一般情況下，請記住， <xref:System.Windows.DataTemplate>套用至所產生的每個<xref:System.Windows.Controls.ListBoxItem> (如需如何以及在何處實際套用的詳細資訊，請參閱<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>頁面。)。 您<xref:System.Windows.DataTemplate>關心只在展示層和資料物件的外觀。 在大部分情況下，所有其他層面的呈現方式，例如項目看起來像選取時或如何<xref:System.Windows.Controls.ListBox>奠定出的項目，定義中不屬於<xref:System.Windows.DataTemplate>。 如需範例，請參閱[設定樣式和範本 ItemsControl](#DataTemplating_ItemsControl)一節。  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>選擇 DataTemplate，根據資料物件的屬性  
 在[DataType 屬性](#Styling_DataType) 區段中，我們討論了您可以定義不同的資料物件的不同資料範本。 這是特別有用，就<xref:System.Windows.Data.CompositeCollection>不同類型的不同類型的項目集合。 在[套用屬性值的使用 DataTriggers](#DataTrigger_to_Apply_Property_Values)  區段中，我們已經示範，是否您擁有相同類型的資料物件的集合，您可以建立<xref:System.Windows.DataTemplate> ，然後使用以套用變更的每個資料物件的屬性值為基礎的觸發程序。 不過，觸發程序可讓您套用屬性值，或開始動畫，但無法提供您彈性地重新建構資料物件的結構。 某些情況下可能需要您建立不同<xref:System.Windows.DataTemplate>資料都屬於相同的物件類型，但有不同的屬性。  
  
 例如，當`Task`物件具有`Priority`值`1`，您可能想要給予它完全不同的外觀，做為您自己的警示。 在此情況下，您建立<xref:System.Windows.DataTemplate>高優先順序的顯示`Task`物件。 讓我們新增下列<xref:System.Windows.DataTemplate>資源一節︰  
  
 [!code-xml[DataTemplatingIntro_snip#ImportantTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 請注意此範例使用<xref:System.Windows.DataTemplate>。<xref:System.Windows.FrameworkTemplate.Resources%2A>屬性。 中所定義區段內的項目所共用的資源<xref:System.Windows.DataTemplate>。  
  
 要提供邏輯來選擇哪些<xref:System.Windows.DataTemplate>使用根據`Priority`值的資料物件，建立的子類別<xref:System.Windows.Controls.DataTemplateSelector>並覆寫<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>方法。 在下列範例中， <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>方法提供邏輯，以傳回適當的值為基礎的範本`Priority`屬性。 傳回範本的資源封套中找到<xref:System.Windows.Window>項目。  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 我們可以宣告`TaskListDataTemplateSelector`做為資源︰  
  
 [!code-xml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xml[DataTemplatingIntro_snip#DTS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 若要使用的範本選取器資源，將它指派給<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>屬性<xref:System.Windows.Controls.ListBox>。 <xref:System.Windows.Controls.ListBox>呼叫<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>方法`TaskListDataTemplateSelector`每個基礎集合中的項目。 呼叫會項目參數傳遞的資料物件。 <xref:System.Windows.DataTemplate>所傳回的方法適用於該資料物件。  
  
 [!code-xml[DataTemplatingIntro_snip#ItemTemplateSelector](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 使用範本中的選取器的位置， <xref:System.Windows.Controls.ListBox>現在會出現，如下所示︰  
  
 ![資料範本化範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  
  
 此範例的討論到此為止。 如需完整的範例，請參閱[資料範本化範例簡介](http://go.microsoft.com/fwlink/?LinkID=160009)。  
  
<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>設定樣式和範本的 ItemsControl  
 即使<xref:System.Windows.Controls.ItemsControl>不是唯一的控制項類型，您可以使用<xref:System.Windows.DataTemplate> ，是很常見的案例來繫結<xref:System.Windows.Controls.ItemsControl>至集合。 在[什麼屬於 DataTemplate](#what_belongs_in_datatemplate)一節我們將討論的定義您<xref:System.Windows.DataTemplate>應該只考量資料的呈現方式。 為了了解並不適合使用<xref:System.Windows.DataTemplate>請務必了解所提供的不同樣式和範本屬性<xref:System.Windows.Controls.ItemsControl>。 下列範例被設計來說明每個屬性的函式。 <xref:System.Windows.Controls.ItemsControl>在這個範例會繫結至相同`Tasks`集合，如先前範例所示。 示範用途、 樣式和範本，在此範例中的所有宣告為內嵌。  
  
 [!code-xml[DataTemplatingIntro_snip#ItemsControlProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 以下是範例的呈現時螢幕擷取畫面︰  
  
 ![ItemsControl 範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 請注意，而不是使用<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>，您可以使用<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>。 請參閱上一節的範例。 同樣地，而不是使用<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>，您可以使用<xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>。  
  
 兩個其他樣式相關屬性的<xref:System.Windows.Controls.ItemsControl> ，不會顯示下面是<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>和<xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>。  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>支援階層式資料  
 到目前為止我們只看過如何繫結至並顯示單一集合。 有時候，您必須包含其他集合的集合。 <xref:System.Windows.HierarchicalDataTemplate>類別主要用來搭配<xref:System.Windows.Controls.HeaderedItemsControl>来顯示這類資料類型。 在下列範例中，`ListLeagueList`是一份`League`物件。 每個`League`物件具有`Name`和集合`Division`物件。 每個`Division`有`Name`和集合`Team`物件，以及每個`Team`物件具有`Name`。  
  
 [!code-xml[HierarchicalDataTemplateSnippet#HDT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 此範例顯示使用<xref:System.Windows.HierarchicalDataTemplate>，就可以輕鬆顯示包含其他清單的清單資料。 以下是範例的螢幕擷取畫面。  
  
 ![HierarchicalDataTemplate 範例螢幕擷取畫面](../../../../docs/framework/wpf/data/media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [尋找 DataTemplate 產生的項目](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [GridView 資料行行首樣式和範本概觀](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)