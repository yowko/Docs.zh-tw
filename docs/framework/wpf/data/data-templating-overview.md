---
title: 資料範本化概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
ms.openlocfilehash: 9287656349f2a10619bfe76a36ee7855d3861cba
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376100"
---
# <a name="data-templating-overview"></a>資料範本化概觀
WPF 資料範本化模型對於資料呈現方式的定義，具有相當大的彈性。 WPF 控制項的內建功能支援自訂資料呈現方式。 本主題會先示範如何定義<xref:System.Windows.DataTemplate>，之後再介紹其他資料範本化功能，例如根據自訂邏輯和的支援階層式資料的顯示範本的選取項目。  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題著重資料範本化功能，而不是資料繫結概念簡介。 如需基本資料繫結概念的資訊，請參閱[資料繫結概觀](data-binding-overview.md)。  
  
 <xref:System.Windows.DataTemplate> 是有關資料的呈現方式也是 WPF 樣式和範本化模型所提供的眾多功能之一。 如需 WPF 樣式和範本化模型，例如，若要使用的如何<xref:System.Windows.Style>若要在控制項上設定屬性，請參閱[樣式和範本化](../controls/styling-and-templating.md)主題。  
  
 此外，請務必了解`Resources`，這基本上是什麼啟用物件，例如<xref:System.Windows.Style>和<xref:System.Windows.DataTemplate>為可重複使用。 如需詳細資訊，請參閱 [XAML 資源](../advanced/xaml-resources.md)。  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>資料範本化基本概念  
  
 為了示範為什麼<xref:System.Windows.DataTemplate>很重要，讓我們逐步解說資料繫結範例。 在此範例中，我們有<xref:System.Windows.Controls.ListBox>繫結到一份`Task`物件。 每個 `Task` 物件各有一個 `TaskName` (字串)、`Description` (字串)、`Priority` (整數)，和一個 `TaskType`型別的屬性，該型別是含有值 `Home` 和 `Work` 的 `Enum`。  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>沒有 DataTemplate  
 不含<xref:System.Windows.DataTemplate>、 我們<xref:System.Windows.Controls.ListBox>目前看起來會像這樣：  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 發生的事情是，而不需要任何特定的指示，請<xref:System.Windows.Controls.ListBox>預設會呼叫`ToString`嘗試顯示集合中的物件時。 因此，如果`Task`物件會覆寫`ToString`方法，則<xref:System.Windows.Controls.ListBox>顯示基礎集合中的每個來源物件的字串表示。  
  
 例如，如果 `Task` 類別以此方式覆寫 `ToString` 方法，而其中 `name` 是 `TaskName`屬性的欄位︰  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 則<xref:System.Windows.Controls.ListBox>看起來如下所示：  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 不過，這是有限制的，而且缺乏彈性。 此外，如果是繫結至 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料，將無法覆寫 `ToString`。  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>定義簡單的 DataTemplate  
 解決方法是定義<xref:System.Windows.DataTemplate>。 若要這麼做的一個方式為設定<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>的屬性<xref:System.Windows.Controls.ListBox>至<xref:System.Windows.DataTemplate>。 您在中指定您<xref:System.Windows.DataTemplate>會變成您的資料物件的視覺化結構。 下列<xref:System.Windows.DataTemplate>相當簡單。 我們提供的指示每個項目顯示為三<xref:System.Windows.Controls.TextBlock>內的項目<xref:System.Windows.Controls.StackPanel>。 每個<xref:System.Windows.Controls.TextBlock>元素所繫結的屬性，`Task`類別。  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 本主題中範例的基礎資料是 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件的集合。 如果是繫結至 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料，基本概念都相同，但有些微的語法差異。 比方說，而不需`Path=TaskName`，您會設定<xref:System.Windows.Data.Binding.XPath%2A>要`@TaskName`(如果`TaskName`屬性您[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]節點)。  
  
 現在我們<xref:System.Windows.Controls.ListBox>看起來如下所示：  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>將 DataTemplate 建立為資源  
 在上述範例中，我們定義<xref:System.Windows.DataTemplate>內嵌。 更常見的是將它定義於資源區段中以成為可重複使用的物件，如下列範例所述：  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 現在您可以使用 `myTaskTemplate` 做為資源，如下列範例所示︰  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 因為`myTaskTemplate`是一項資源，您現在可以使用它所採用的屬性其他控制項<xref:System.Windows.DataTemplate>型別。 為如上所示，針對<xref:System.Windows.Controls.ItemsControl>物件，例如<xref:System.Windows.Controls.ListBox>，它是<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性。 針對<xref:System.Windows.Controls.ContentControl>物件，它是<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性。  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>DataType 屬性  
 <xref:System.Windows.DataTemplate>類別具有<xref:System.Windows.DataTemplate.DataType%2A>屬性，非常類似於<xref:System.Windows.Style.TargetType%2A>屬性<xref:System.Windows.Style>類別。 因此，而不是指定`x:Key`針對<xref:System.Windows.DataTemplate>在上述範例中，您可以執行下列動作：  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 這<xref:System.Windows.DataTemplate>會自動套用到所有`Task`物件。 請注意，在此情況下，`x:Key` 是隱含設定的。 因此，如果您指派此<xref:System.Windows.DataTemplate>`x:Key`值，您會覆寫的隱含`x:Key`而<xref:System.Windows.DataTemplate>不會自動套用。  
  
 如果您要繫結<xref:System.Windows.Controls.ContentControl>集合`Task`物件，<xref:System.Windows.Controls.ContentControl>不會使用上述<xref:System.Windows.DataTemplate>自動。 這是因為在繫結<xref:System.Windows.Controls.ContentControl>需要區別是否想要繫結至整個集合或個別物件的詳細資訊。 如果您<xref:System.Windows.Controls.ContentControl>正在追蹤的選取項目<xref:System.Windows.Controls.ItemsControl>類型，您可以設定<xref:System.Windows.Data.Binding.Path%2A>屬性<xref:System.Windows.Controls.ContentControl>繫結至"`/`」 表示您感興趣的目前項目。 如需範例，請參閱[繫結至集合並根據選取項目顯示資訊](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)。 否則，您必須指定<xref:System.Windows.DataTemplate>明確地設定<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性。  
  
 <xref:System.Windows.DataTemplate.DataType%2A>屬性會特別有用，當您有<xref:System.Windows.Data.CompositeCollection>不同型別的資料物件。 如需範例，請參閱[實作 CompositeCollection](how-to-implement-a-compositecollection.md)。  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>加入更多內容至 DataTemplate  
 目前資料是以所需的資訊出現，不過還有很大的改進空間。 讓我們來改善在簡報上加上<xref:System.Windows.Controls.Border>，則<xref:System.Windows.Controls.Grid>，和一些<xref:System.Windows.Controls.TextBlock>描述所顯示的資料的項目。  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 下列螢幕擷取畫面示<xref:System.Windows.Controls.ListBox>以此方式修改<xref:System.Windows.DataTemplate>:  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 我們可以把<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>要<xref:System.Windows.HorizontalAlignment.Stretch>上<xref:System.Windows.Controls.ListBox>藉此確定項目的寬度會佔用整個空間：  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 具有<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>屬性設定為<xref:System.Windows.HorizontalAlignment.Stretch>，則<xref:System.Windows.Controls.ListBox>現在看起來會像這樣：  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>使用 DataTriggers 套用屬性值  
 目前的展示方式並無法分辨出 `Task` 是家務還是公司的工作。 前面提過，`Task` 物件有一個型別為 `TaskType` 的 `TaskType` 屬性，這是具有 `Home` 和 `Work` 這兩個值的列舉。  
  
 在下列範例中，<xref:System.Windows.DataTrigger>設定<xref:System.Windows.Controls.Border.BorderBrush%2A>名為的項目`border`要`Yellow`如果`TaskType`屬性是`TaskType.Home`。  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 現在應用程式看起來就像下面這樣。 家務會用黃色框線框住，而公司工作則有水藍色框線框住：  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 在此範例中<xref:System.Windows.DataTrigger>使用<xref:System.Windows.Setter>來設定屬性值。 觸發程序類別也具有<xref:System.Windows.TriggerBase.EnterActions%2A>和<xref:System.Windows.TriggerBase.ExitActions%2A>可讓您啟動一組動作，例如動畫的屬性。 此外，還有<xref:System.Windows.MultiDataTrigger>可讓您套用變更的類別，根據多個資料繫結屬性值。  
  
 達到相同的效果的替代方式是繫結<xref:System.Windows.Controls.Border.BorderBrush%2A>屬性，以`TaskType`屬性，然後使用傳回色彩值轉換器根據`TaskType`值。 使用轉換器建立上述效果，就效能上來說會快些。 此外，建立自己的轉換器能提供更多的彈性，因為您可以提供自己的邏輯。 最後，要選擇使用哪種方式，取決於個別情況和您的偏好而定。 如需有關如何撰寫轉換器的資訊，請參閱<xref:System.Windows.Data.IValueConverter>。  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>哪些內容屬於 DataTemplate 的範圍  

在上述範例中，我們放在觸發程序<xref:System.Windows.DataTemplate>使用<xref:System.Windows.DataTemplate>。<xref:System.Windows.DataTemplate.Triggers%2A> 屬性。 <xref:System.Windows.Setter>觸發程序的設定項目的屬性值 (<xref:System.Windows.Controls.Border>項目) 內<xref:System.Windows.DataTemplate>。 不過，如果屬性，您`Setters`關心的都不是位於目前的項目屬性<xref:System.Windows.DataTemplate>，可能更適合用來設定內容<xref:System.Windows.Style>，為<xref:System.Windows.Controls.ListBoxItem>類別 (如果您要繫結的控制項是<xref:System.Windows.Controls.ListBox>)。 比方說，如果您想要您<xref:System.Windows.Trigger>來建立動畫<xref:System.Windows.UIElement.Opacity%2A>值的項目時滑鼠指向某個項目，您會定義觸發程序內<xref:System.Windows.Controls.ListBoxItem>樣式。 如需範例，請參閱[樣式設定和範本化範例的簡介](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。
  
 一般情況下，請記住<xref:System.Windows.DataTemplate>套用至每個產生<xref:System.Windows.Controls.ListBoxItem>(更多方式和位置實際套用的詳細資訊，請參閱<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>頁面。)。 您<xref:System.Windows.DataTemplate>關心只在展示層和資料物件的外觀。 在大部分情況下，所有其他展示方面，例如哪些項目看起來像選取時或如何<xref:System.Windows.Controls.ListBox>奠定出的項目不屬於定義<xref:System.Windows.DataTemplate>。 如需範例，請參閱 [ItemsControl 的樣式設定和範本化](#DataTemplating_ItemsControl)一節。  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>根據資料物件的屬性選擇 DataTemplate  
 在 [DataType 屬性](#Styling_DataType)一節中提到過，您可以為不同的資料物件定義不同的資料範本。 這是特別有用，當您有<xref:System.Windows.Data.CompositeCollection>不同類型的不同類型的項目集合。 在 [使用 Datatrigger 套用屬性值](#DataTrigger_to_Apply_Property_Values)區段中，我們已示範，是否您擁有的相同類型的資料物件集合，您可以建立<xref:System.Windows.DataTemplate>，然後使用以套用變更的屬性值為基礎的觸發程序每個資料物件。 不過，觸發程序雖然可以讓您套用屬性值或啟動動畫，但無法提供重新建構資料物件結構的彈性。 某些情況下可能需要您建立不同<xref:System.Windows.DataTemplate>資料屬於相同的物件類型但有不同的屬性。  
  
 例如，當 `Task` 物件有一個 `Priority` 值為 `1` 時，您可能會想讓它看起來完全不同，以便提醒自己。 在此情況下，您建立<xref:System.Windows.DataTemplate>高優先顯示`Task`物件。 讓我們加入下列<xref:System.Windows.DataTemplate>的資源區段：  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 請注意此範例會使用<xref:System.Windows.DataTemplate>。<xref:System.Windows.FrameworkTemplate.Resources%2A> 屬性。 中所定義一節中的項目所共用的資源<xref:System.Windows.DataTemplate>。  
  
 若要提供邏輯以選擇哪些<xref:System.Windows.DataTemplate>使用根據`Priority`值的資料物件，建立的子類別<xref:System.Windows.Controls.DataTemplateSelector>，並覆寫<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>方法。 在下列範例中，<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>方法會提供邏輯，以傳回適當的值為基礎的範本`Priority`屬性。 要傳回範本的資源封套中找到<xref:System.Windows.Window>項目。  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 然後，就可以宣告`TaskListDataTemplateSelector` 為資源：  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 若要使用的範本選取器資源，將它指派給<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>屬性<xref:System.Windows.Controls.ListBox>。 <xref:System.Windows.Controls.ListBox>呼叫<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>方法`TaskListDataTemplateSelector`針對每個基礎集合中的項目。 該呼叫會將資料物件當做項目參數傳遞。 <xref:System.Windows.DataTemplate>時所傳回的方法適用於該資料物件。  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 使用範本中的選取器的位置，<xref:System.Windows.Controls.ListBox>現在會出現，如下所示：  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

這個範例的討論到此結束。 如需完整範例，請參閱[資料範本化範例簡介](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro)。

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>ItemsControl 的樣式設定和範本化  
 即使<xref:System.Windows.Controls.ItemsControl>不是唯一的控制項類型可供<xref:System.Windows.DataTemplate>使用，就很常見的案例來繫結<xref:System.Windows.Controls.ItemsControl>至集合。 在 [哪些內容屬於 datatemplate 的範圍](#what_belongs_in_datatemplate)一節中提到，定義您<xref:System.Windows.DataTemplate>應該只考量資料的呈現方式。 若要知道何時不適合使用<xref:System.Windows.DataTemplate>務必要了解所提供的不同樣式和範本屬性<xref:System.Windows.Controls.ItemsControl>。 下列範例是設計來說明每個屬性的功能。 <xref:System.Windows.Controls.ItemsControl>在此範例會繫結至相同`Tasks`集合，如先前範例所示。 為方便示範，這個範例中的樣式和範本都是內嵌宣告的。  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 下圖是範例呈現的畫面：  
  
 ![ItemsControl 範例螢幕擷取畫面](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 請注意，而不是使用<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>，您可以使用<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>。 請參閱上一節中的範例。 同樣地，而不是使用<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>，您可以選擇使用<xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>。  
  
 兩個其他樣式相關屬性的<xref:System.Windows.Controls.ItemsControl>，不會顯示如下<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>和<xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>。  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>支援階層式資料  
 到目前為止，我們只討論了如何繫結和顯示單一集合。 有時候集合之中可能還有其他集合。 <xref:System.Windows.HierarchicalDataTemplate>類別設計來搭配<xref:System.Windows.Controls.HeaderedItemsControl>来顯示這類資料類型。 在下列範例中，`ListLeagueList` 是 `League` 物件的清單。 每個 `League` 物件都有一個 `Name` 和一組 `Division` 物件集合。 每一個 `Division` 都有一個 `Name` 和 `Team` 物件的集合，並且每一個 `Team` 物件都有一個 `Name`。  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 此範例所示範的是，使用<xref:System.Windows.HierarchicalDataTemplate>，您可以輕鬆地顯示包含其他清單的清單資料。 以下是範例的螢幕擷取畫面。  
  
 ![HierarchicalDataTemplate 範例螢幕擷取畫面](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>另請參閱
- [資料繫結](../advanced/optimizing-performance-data-binding.md)
- [尋找 DataTemplate 產生的元素](how-to-find-datatemplate-generated-elements.md)
- [樣式設定和範本化](../controls/styling-and-templating.md)
- [資料繫結概觀](data-binding-overview.md)
- [GridView 資料行標頭樣式和範本概觀](../controls/gridview-column-header-styles-and-templates-overview.md)
