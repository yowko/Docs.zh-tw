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
ms.openlocfilehash: 556ce7b42f13d7c5ba7fba36b09277cda9bcae5d
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400667"
---
# <a name="data-templating-overview"></a>資料範本化概觀
WPF 資料範本化模型對於資料呈現方式的定義，具有相當大的彈性。 WPF 控制項的內建功能支援自訂資料呈現方式。 本主題首先會示範如何定義<xref:System.Windows.DataTemplate> , 然後導入其他的資料範本化功能, 例如根據自訂邏輯選取範本, 以及顯示階層式資料的支援。  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題著重資料範本化功能，而不是資料繫結概念簡介。 如需基本資料繫結概念的資訊，請參閱[資料繫結概觀](data-binding-overview.md)。  
  
 <xref:System.Windows.DataTemplate>是關於資料的呈現方式, 而且是 WPF 樣式和範本化模型提供的眾多功能之一。 如需 WPF 樣式和範本化模型的簡介, 例如如何使用<xref:System.Windows.Style>設定控制項的屬性, 請參閱樣式設定[和範本化](../controls/styling-and-templating.md)主題。  
  
 此外, 請務必瞭解`Resources`, 這基本上是讓<xref:System.Windows.Style>和<xref:System.Windows.DataTemplate>等物件可重複使用的方式。 如需詳細資訊，請參閱 [XAML 資源](../advanced/xaml-resources.md)。  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>資料範本化基本概念  
  
 為了示範為什麼<xref:System.Windows.DataTemplate>很重要, 讓我們逐步解說資料系結範例。 在此範例中, 我們有<xref:System.Windows.Controls.ListBox>一個系結至物件清單的`Task` 。 每個 `Task` 物件各有一個 `TaskName` (字串)、`Description` (字串)、`Priority` (整數)，和一個 `TaskType`型別的屬性，該型別是含有值 `Home` 和 `Work` 的 `Enum`。  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>沒有 DataTemplate  
 如果沒有<xref:System.Windows.Controls.ListBox> , 我們目前看起來像這樣: <xref:System.Windows.DataTemplate>  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 發生的情況是, 沒有任何特定的指示, <xref:System.Windows.Controls.ListBox>預設會在`ToString`嘗試顯示集合中的物件時呼叫。 因此, 如果`Task`物件`ToString`覆寫方法, <xref:System.Windows.Controls.ListBox>則會顯示基礎集合中每個來源物件的字串表示。  
  
 例如，如果 `Task` 類別以此方式覆寫 `ToString` 方法，而其中 `name` 是 `TaskName`屬性的欄位︰  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 然後, <xref:System.Windows.Controls.ListBox>看起來如下所示:  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 不過，這是有限制的，而且缺乏彈性。 此外，如果是繫結至 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料，將無法覆寫 `ToString`。  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>定義簡單的 DataTemplate  
 解決方案是定義<xref:System.Windows.DataTemplate>。 其中一種方法是將的<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性<xref:System.Windows.Controls.ListBox>設定為<xref:System.Windows.DataTemplate>。 您在中<xref:System.Windows.DataTemplate>指定的內容會成為資料物件的視覺化結構。 以下<xref:System.Windows.DataTemplate>是相當簡單的。 我們會提供指示, 說明每個專案<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel>在中會顯示為三個元素。 每<xref:System.Windows.Controls.TextBlock>個元素都會系結至`Task`類別的屬性。  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 本主題中範例的基礎資料是 CLR 物件的集合。 如果是繫結至 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料，基本概念都相同，但有些微的語法差異。 例如, 您可以將設`Path=TaskName` <xref:System.Windows.Data.Binding.XPath%2A>為`@TaskName` (如果`TaskName`是[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]節點的屬性), 而不是 having。  
  
 現在我們<xref:System.Windows.Controls.ListBox>看起來如下所示:  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>將 DataTemplate 建立為資源  
 在上述範例中, 我們定義了<xref:System.Windows.DataTemplate>內嵌。 更常見的是將它定義於資源區段中以成為可重複使用的物件，如下列範例所述：  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 現在您可以使用 `myTaskTemplate` 做為資源，如下列範例所示︰  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 因為`myTaskTemplate`是一種資源, 所以您現在可以在具有屬性且<xref:System.Windows.DataTemplate>採用類型的其他控制項上使用它。 如上所示, 針對<xref:System.Windows.Controls.ItemsControl>物件 (例如<xref:System.Windows.Controls.ListBox>), 它是<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性。 對於<xref:System.Windows.Controls.ContentControl>物件, 它<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>是屬性。  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>DataType 屬性  
 類別的屬性與<xref:System.Windows.Style>類別的<xref:System.Windows.Style.TargetType%2A>屬性非常類似。 <xref:System.Windows.DataTemplate.DataType%2A> <xref:System.Windows.DataTemplate> 因此, 您可以執行下列`x:Key`動作, <xref:System.Windows.DataTemplate>而不是在上述範例中指定的:  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 這<xref:System.Windows.DataTemplate>會自動套用至所有`Task`物件。 請注意，在此情況下，`x:Key` 是隱含設定的。 因此, 如果您指派此<xref:System.Windows.DataTemplate> `x:Key`值給它, 就會覆<xref:System.Windows.DataTemplate>寫`x:Key`隱含的, 而且不會自動套用。  
  
 <xref:System.Windows.Controls.ContentControl>如果您要將系結至`Task`物件的集合, 則<xref:System.Windows.Controls.ContentControl>不會自動使用上述<xref:System.Windows.DataTemplate>的。 這是因為上<xref:System.Windows.Controls.ContentControl>的系結需要詳細資訊, 以區別您要系結至整個集合或個別物件。 如果您<xref:System.Windows.Controls.ContentControl>正在追蹤某個<xref:System.Windows.Controls.ItemsControl>類型的選取專案<xref:System.Windows.Data.Binding.Path%2A> , 您可以<xref:System.Windows.Controls.ContentControl>將系結的屬性設定為 "`/`", 以表示您對目前的專案有興趣。 如需範例，請參閱[繫結至集合並根據選取項目顯示資訊](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)。 否則, 您需要藉由<xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>設定屬性來明確指定。  
  
 當<xref:System.Windows.DataTemplate.DataType%2A> 您<xref:System.Windows.Data.CompositeCollection>有不同類型的資料物件時, 屬性特別有用。 如需範例，請參閱[實作 CompositeCollection](how-to-implement-a-compositecollection.md)。  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>加入更多內容至 DataTemplate  
 目前資料是以所需的資訊出現，不過還有很大的改進空間。 讓我們藉由新增<xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Grid>、和一些<xref:System.Windows.Controls.TextBlock>描述所顯示資料的專案, 來改善簡報。  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 下列螢幕擷取畫面顯示具有<xref:System.Windows.Controls.ListBox>此修改<xref:System.Windows.DataTemplate>的:  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 我們可以在<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>上將設<xref:System.Windows.HorizontalAlignment.Stretch>為,以確保專案的寬度佔用整個空間:<xref:System.Windows.Controls.ListBox>  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 當屬性設定為<xref:System.Windows.HorizontalAlignment.Stretch>時, <xref:System.Windows.Controls.ListBox>現在看起來像這樣: <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>使用 DataTriggers 套用屬性值  
 目前的展示方式並無法分辨出 `Task` 是家務還是公司的工作。 前面提過，`Task` 物件有一個型別為 `TaskType` 的 `TaskType` 屬性，這是具有 `Home` 和 `Work` 這兩個值的列舉。  
  
 在下列範例中, 如果<xref:System.Windows.DataTrigger> `Yellow` `TaskType.Home` <xref:System.Windows.Controls.Border.BorderBrush%2A> `border` 屬性`TaskType`為, 則會將名為的專案的設定為。  
  
 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 現在應用程式看起來就像下面這樣。 家務會用黃色框線框住，而公司工作則有水藍色框線框住：  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 在此範例中<xref:System.Windows.DataTrigger> , 會<xref:System.Windows.Setter>使用來設定屬性值。 觸發程式類別也具有<xref:System.Windows.TriggerBase.EnterActions%2A>和<xref:System.Windows.TriggerBase.ExitActions%2A>屬性, 可讓您啟動一組動作, 例如動畫。 此外, 還有一個<xref:System.Windows.MultiDataTrigger>類別, 可讓您根據多個資料系結屬性值來套用變更。  
  
 另一種達成相同效果的方法, 就是將<xref:System.Windows.Controls.Border.BorderBrush%2A>屬性系結`TaskType`至屬性, 並使用值轉換器來根據`TaskType`值傳回色彩。 使用轉換器建立上述效果，就效能上來說會快些。 此外，建立自己的轉換器能提供更多的彈性，因為您可以提供自己的邏輯。 最後，要選擇使用哪種方式，取決於個別情況和您的偏好而定。 如需如何撰寫轉換器的詳細資訊, 請<xref:System.Windows.Data.IValueConverter>參閱。  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>哪些內容屬於 DataTemplate 的範圍  

在上述範例中, 我們<xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate>使用將觸發程式放在中。<xref:System.Windows.DataTemplate.Triggers%2A> 屬性。 觸發<xref:System.Windows.Setter>程式的會設定中的專案<xref:System.Windows.Controls.Border> (專案<xref:System.Windows.DataTemplate>) 之屬性 (element) 的值。 不過, 如果`Setters`您所關心的屬性不是目前<xref:System.Windows.DataTemplate>內專案的屬性, 則可能比較適合使用<xref:System.Windows.Style> <xref:System.Windows.Controls.ListBoxItem>類別的來設定屬性 (如果您要系結的<xref:System.Windows.Controls.ListBox>控制項是)。 例如, 如果您想要在<xref:System.Windows.Trigger>滑鼠指向專案<xref:System.Windows.UIElement.Opacity%2A>時以動畫顯示專案的值, <xref:System.Windows.Controls.ListBoxItem>您可以在樣式內定義觸發程式。 如需範例，請參閱[樣式設定和範本化範例的簡介](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。
  
 一般來說, 請記住<xref:System.Windows.DataTemplate> , 會套用至每個產生<xref:System.Windows.Controls.ListBoxItem>的 (如需<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>實際套用方式和位置的詳細資訊, 請參閱頁面)。 您<xref:System.Windows.DataTemplate>只關心資料物件的呈現和外觀。 在大部分情況下, 簡報的所有其他層面 (例如, 當選取專案時, 或如何<xref:System.Windows.Controls.ListBox>設定項目時) 都不屬於的定義。 <xref:System.Windows.DataTemplate> 如需範例，請參閱 [ItemsControl 的樣式設定和範本化](#DataTemplating_ItemsControl)一節。  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>根據資料物件的屬性選擇 DataTemplate  
 在 [DataType 屬性](#Styling_DataType)一節中提到過，您可以為不同的資料物件定義不同的資料範本。 當您<xref:System.Windows.Data.CompositeCollection>的類型或集合具有不同類型的專案時, 這會特別有用。 在 [[使用 datatrigger 來套用屬性值](#DataTrigger_to_Apply_Property_Values)] 區段中, 我們顯示如果您有相同類型之資料物件的集合, 您可以建立<xref:System.Windows.DataTemplate> , 然後使用觸發程式, 根據每個資料物件的屬性值來套用變更。 不過，觸發程序雖然可以讓您套用屬性值或啟動動畫，但無法提供重新建構資料物件結構的彈性。 在某些情況下, 您可能需要為<xref:System.Windows.DataTemplate>相同類型但具有不同屬性的資料物件建立不同的。  
  
 例如，當 `Task` 物件有一個 `Priority` 值為 `1` 時，您可能會想讓它看起來完全不同，以便提醒自己。 在此情況下, 您會<xref:System.Windows.DataTemplate>建立以顯示高優先順序`Task`物件。 讓我們在 resources 區段<xref:System.Windows.DataTemplate>中新增下列內容:  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 請注意, <xref:System.Windows.DataTemplate>此範例會使用。<xref:System.Windows.FrameworkTemplate.Resources%2A> 屬性。 在該區段中定義的資源會由中<xref:System.Windows.DataTemplate>的元素共用。  
  
 若要提供邏輯以根據<xref:System.Windows.DataTemplate>資料物件的`Priority`值來選擇要使用哪一個<xref:System.Windows.Controls.DataTemplateSelector> , 請建立的子<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>類別, 並覆寫方法。 在下列範例中, <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>方法會根據`Priority`屬性的值, 提供傳回適當範本的邏輯。 要傳回的範本可在包裹<xref:System.Windows.Window>元素的資源中找到。  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 然後，就可以宣告`TaskListDataTemplateSelector` 為資源：  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 若要使用範本選取器資源, 請將它<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>指派給的<xref:System.Windows.Controls.ListBox>屬性。 會針對基礎<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>集合中的每個專案,呼叫的方法。<xref:System.Windows.Controls.ListBox> `TaskListDataTemplateSelector` 該呼叫會將資料物件當做項目參數傳遞。 然後<xref:System.Windows.DataTemplate> , 方法所傳回的會套用至該資料物件。  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 範本選取器備妥之後, <xref:System.Windows.Controls.ListBox>現在會顯示如下:  
  
 ![資料範本化範例螢幕擷取畫面](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  

這個範例的討論到此結束。 如需完整範例，請參閱[資料範本化範例簡介](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro)。

<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>ItemsControl 的樣式設定和範本化  
 雖然不<xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ItemsControl>是您可以搭配使用的唯一控制項類型, 但它是將系結至集合的一個很常見的案例。 <xref:System.Windows.Controls.ItemsControl> 在[DataTemplate](#what_belongs_in_datatemplate)一節中, 我們討論了的定義<xref:System.Windows.DataTemplate>應該只關心資料的呈現。 為了知道不適合使用的<xref:System.Windows.DataTemplate>時機, 請務必瞭解所提供<xref:System.Windows.Controls.ItemsControl>的不同樣式和範本屬性。 下列範例是設計來說明每個屬性的功能。 在此範例中, 會系結至`Tasks`與上一個範例相同的集合。 <xref:System.Windows.Controls.ItemsControl> 為方便示範，這個範例中的樣式和範本都是內嵌宣告的。  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 下圖是範例呈現的畫面：  
  
 ![ItemsControl 範例螢幕擷取畫面](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 請注意, 您可以<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>使用, 而不是使用。 請參閱上一節中的範例。 同樣地, 您可以選擇<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>使用, 而不是使用。  
  
 這裡未顯示的其他兩個與<xref:System.Windows.Controls.ItemsControl>樣式相關的屬性為<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>和<xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>。  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>支援階層式資料  
 到目前為止，我們只討論了如何繫結和顯示單一集合。 有時候集合之中可能還有其他集合。 類別是設計用來<xref:System.Windows.Controls.HeaderedItemsControl>搭配類型來顯示這類資料。 <xref:System.Windows.HierarchicalDataTemplate> 在下列範例中，`ListLeagueList` 是 `League` 物件的清單。 每個 `League` 物件都有一個 `Name` 和一組 `Division` 物件集合。 每一個 `Division` 都有一個 `Name` 和 `Team` 物件的集合，並且每一個 `Team` 物件都有一個 `Name`。  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 此範例顯示使用<xref:System.Windows.HierarchicalDataTemplate>, 您可以輕鬆地顯示包含其他清單的清單資料。 以下是範例的螢幕擷取畫面。  
  
 ![HierarchicalDataTemplate 範例螢幕擷取畫面](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>另請參閱

- [資料繫結](../advanced/optimizing-performance-data-binding.md)
- [尋找 DataTemplate 產生的元素](how-to-find-datatemplate-generated-elements.md)
- [樣式設定和範本化](../controls/styling-and-templating.md)
- [資料繫結概觀](data-binding-overview.md)
- [GridView 資料行標頭樣式和範本概觀](../controls/gridview-column-header-styles-and-templates-overview.md)
