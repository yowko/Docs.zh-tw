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
ms.openlocfilehash: b9e55eac1c72cd3deec21754373da4364a7cfed2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646453"
---
# <a name="data-templating-overview"></a>資料範本化概觀
WPF 資料範本化模型對於資料呈現方式的定義，具有相當大的彈性。 WPF 控制項的內建功能支援自訂資料呈現方式。 本主題首先演示如何定義,<xref:System.Windows.DataTemplate>然後介紹其他數據範本化功能,例如基於自定義邏輯選擇範本和支援顯示分層資料。

<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Prerequisites
 本主題著重資料範本化功能，而不是資料繫結概念簡介。 如需基本資料繫結概念的資訊，請參閱[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。

 <xref:System.Windows.DataTemplate>是關於數據的表示,是 WPF 樣式和範本模型提供的眾多功能之一。 有關 WPF 樣式和範本模型的介紹(例如<xref:System.Windows.Style>如何使用 在控制項上設置屬性),請參閱[「樣式」和「範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)」主題。

 此外,瞭解 這一點本質上`Resources`是 使物件(<xref:System.Windows.Style><xref:System.Windows.DataTemplate>如和 ) 可重用的原因,這一點很重要。 如需詳細資訊，請參閱 [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。

<a name="DataTemplating_Basic"></a>
## <a name="data-templating-basics"></a>資料範本化基本概念

 為了演示為什麼<xref:System.Windows.DataTemplate>很重要,讓我們演練一個數據綁定示例。 這個選項, 我們有結合到物件清單<xref:System.Windows.Controls.ListBox>。`Task` 每個 `Task` 物件各有一個 `TaskName` (字串)、`Description` (字串)、`Priority` (整數)，和一個 `TaskType`型別的屬性，該型別是含有值 `Home` 和 `Work` 的 `Enum`。

 [!code-xaml[DataTemplatingIntro_snip#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]
[!code-xaml[DataTemplatingIntro_snip#UI1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]
[!code-xaml[DataTemplatingIntro_snip#UI2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]

<a name="without_a_datatemplate"></a>
### <a name="without-a-datatemplate"></a>沒有 DataTemplate
 如果沒有<xref:System.Windows.DataTemplate>,我們<xref:System.Windows.Controls.ListBox>目前 如下所示:

 ![資料樣本化範例螢幕擷取](./media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")

 發生的情況是,在沒有任何具體說明的情況下,<xref:System.Windows.Controls.ListBox>預設情況下在嘗試在集合中`ToString`顯示 物件時調用。 因此,`Task`如果物件重`ToString`寫 該方法,<xref:System.Windows.Controls.ListBox>則顯示 基礎集合中每個源物件的字串表示形式。

 例如，如果 `Task` 類別以此方式覆寫 `ToString` 方法，而其中 `name` 是 `TaskName`屬性的欄位︰

 [!code-csharp[DataTemplatingIntro_snip#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]

 然後以下的名稱<xref:System.Windows.Controls.ListBox>:

 ![資料樣本化範例螢幕擷取](./media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")

 不過，這是有限制的，而且缺乏彈性。 此外,如果要結合 XML 資料,將無法覆`ToString`寫 。

<a name="defining_simple_datatemplate"></a>
### <a name="defining-a-simple-datatemplate"></a>定義簡單的 DataTemplate
 解決方案是定義<xref:System.Windows.DataTemplate>。 一種方法是將的屬性<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A><xref:System.Windows.Controls.ListBox>設定為<xref:System.Windows.DataTemplate>。 在<xref:System.Windows.DataTemplate>中 指定的內容將成為數據物件的可視結構。 以下內容<xref:System.Windows.DataTemplate>相當簡單。 我們指示每個專案在 中顯示為<xref:System.Windows.Controls.TextBlock>三<xref:System.Windows.Controls.StackPanel>個元素。 每個<xref:System.Windows.Controls.TextBlock>元素都綁定`Task`到 類的屬性。

 [!code-xaml[DataTemplatingIntro_snip#Inline](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]

 本主題中範例的基礎數據是CLR物件的集合。 如果要綁定到 XML 數據,基本概念是相同的,但語法差異很小。 例如,`Path=TaskName`而不是設定為<xref:System.Windows.Data.Binding.XPath%2A>`@TaskName`(`TaskName`如果是 XML 節點的屬性)

 現在,<xref:System.Windows.Controls.ListBox>我們如下所示:

 ![資料樣本化範例螢幕擷取](./media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")

<a name="defining_datatemplate_as_a_resource"></a>
### <a name="creating-the-datatemplate-as-a-resource"></a>將 DataTemplate 建立為資源
 在上面的示例中,我們定義了<xref:System.Windows.DataTemplate>內聯。 更常見的是將它定義於資源區段中以成為可重複使用的物件，如下列範例所述：

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#AsResource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 現在您可以使用 `myTaskTemplate` 做為資源，如下列範例所示︰

 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]

 因為`myTaskTemplate`是一個資源,現在您可以在具有<xref:System.Windows.DataTemplate>採用類型的屬性的其他控制項上使用它。 如上所示,對於<xref:System.Windows.Controls.ItemsControl>物件(如<xref:System.Windows.Controls.ListBox>,<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>它是 屬性 )。 對於<xref:System.Windows.Controls.ContentControl>物件,它是屬性<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>。

<a name="Styling_DataType"></a>
### <a name="the-datatype-property"></a>DataType 屬性
 類<xref:System.Windows.DataTemplate>的屬性<xref:System.Windows.DataTemplate.DataType%2A><xref:System.Windows.Style.TargetType%2A><xref:System.Windows.Style>與 類的屬性非常相似。 因此,您可以執行以下操作`x:Key`,<xref:System.Windows.DataTemplate>而不是為中例中為 指定 。

 [!code-xaml[DataTemplatingIntro_snip#DataType](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]

 這將<xref:System.Windows.DataTemplate>自動應用於所有`Task`物件。 請注意，在此情況下，`x:Key` 是隱含設定的。 因此,如果為此賦值<xref:System.Windows.DataTemplate>`x:Key`,則重寫隱`x:Key`式 值,並且不會<xref:System.Windows.DataTemplate>自動應用 。

 如果要將<xref:System.Windows.Controls.ContentControl>綁定`Task`到<xref:System.Windows.Controls.ContentControl>物件集合, 則<xref:System.Windows.DataTemplate>不會自動使用上述 內容。 這是因為,對的綁定<xref:System.Windows.Controls.ContentControl>需要更多資訊來區分是綁定到整個集合還是單個物件。 如果正在<xref:System.Windows.Controls.ContentControl>追蹤<xref:System.Windows.Controls.ItemsControl>型態的選擇,則可以<xref:System.Windows.Data.Binding.Path%2A><xref:System.Windows.Controls.ContentControl>將綁定的屬性設置為""`/`以指示您對當前項感興趣。 如需範例，請參閱[繫結至集合並根據選取項目顯示資訊](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)。 否則,您必須透過設定<xref:System.Windows.DataTemplate><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>屬性顯示式指定 。

 當您<xref:System.Windows.DataTemplate.DataType%2A>具有不同類型的資料物件時<xref:System.Windows.Data.CompositeCollection>, 該屬性特別有用。 如需範例，請參閱[實作 CompositeCollection](how-to-implement-a-compositecollection.md)。

<a name="adding_more_to_datatemplate"></a>
## <a name="adding-more-to-the-datatemplate"></a>加入更多內容至 DataTemplate
 目前資料是以所需的資訊出現，不過還有很大的改進空間。 讓我們透過添加、<xref:System.Windows.Controls.Border>和<xref:System.Windows.Controls.Grid>一些<xref:System.Windows.Controls.TextBlock>描述顯示的資料來改進簡報。

 [!code-xaml[DataTemplatingIntro#AddingMore](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 以下螢幕截圖顯示此變更<xref:System.Windows.Controls.ListBox><xref:System.Windows.DataTemplate>的 :

 ![資料樣本化範例螢幕擷取](./media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")

 我們可以在<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A><xref:System.Windows.HorizontalAlignment.Stretch><xref:System.Windows.Controls.ListBox>上 設置為,以確保項目的寬度佔用整個空間:

 [!code-xaml[DataTemplatingIntro_snip#Stretch](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]

 屬性<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>設定為<xref:System.Windows.HorizontalAlignment.Stretch>,<xref:System.Windows.Controls.ListBox>現在所表示:

 ![資料樣本化範例螢幕擷取](./media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")

<a name="DataTrigger_to_Apply_Property_Values"></a>
### <a name="use-datatriggers-to-apply-property-values"></a>使用 DataTriggers 套用屬性值
 目前的展示方式並無法分辨出 `Task` 是家務還是公司的工作。 前面提過，`Task` 物件有一個型別為 `TaskType` 的 `TaskType` 屬性，這是具有 `Home` 和 `Work` 這兩個值的列舉。

 <xref:System.Windows.DataTrigger>在下面的範例中,<xref:System.Windows.Controls.Border.BorderBrush%2A>`border``Yellow``TaskType`如果屬性`TaskType.Home`為 ,則設定所命名的元素的 。

 [!code-xaml[DataTemplatingIntro#DT](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]
[!code-xaml[DataTemplatingIntro#DataTrigger](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]
[!code-xaml[DataTemplatingIntro#AddingMore2](~/samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]

 現在應用程式看起來就像下面這樣。 家務會用黃色框線框住，而公司工作則有水藍色框線框住：

 ![資料樣本化範例螢幕擷取](./media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")

 在此範例中,<xref:System.Windows.DataTrigger><xref:System.Windows.Setter>使用設定屬性值。 觸發器類還具有<xref:System.Windows.TriggerBase.EnterActions%2A><xref:System.Windows.TriggerBase.ExitActions%2A>和 屬性,允許您啟動一組操作,如動畫。 此外,還有一個<xref:System.Windows.MultiDataTrigger>類允許您基於多個數據綁定屬性值應用更改。

 實作相同效果的另一種方法是<xref:System.Windows.Controls.Border.BorderBrush%2A>將 屬性綁定到`TaskType`屬性, 並使用值`TaskType`轉換器根據值返回顏色。 使用轉換器建立上述效果，就效能上來說會快些。 此外，建立自己的轉換器能提供更多的彈性，因為您可以提供自己的邏輯。 最後，要選擇使用哪種方式，取決於個別情況和您的偏好而定。 有關如何寫入轉換器的資訊,請參考<xref:System.Windows.Data.IValueConverter>。

<a name="what_belongs_in_datatemplate"></a>
### <a name="what-belongs-in-a-datatemplate"></a>哪些內容屬於 DataTemplate 的範圍

在前面的示例中,我們將觸發器放在<xref:System.Windows.DataTemplate>使用<xref:System.Windows.DataTemplate.Triggers%2A?displayProperty=nameWithType>屬性中。 觸發器<xref:System.Windows.Setter>的設定的元素<xref:System.Windows.Controls.Border>( 元素)中的屬性的<xref:System.Windows.DataTemplate>值。 但是`Setters`,如果所關注的屬性<xref:System.Windows.DataTemplate>不是 當前元素的屬性,<xref:System.Windows.Style>則<xref:System.Windows.Controls.ListBoxItem>使用 用於類的屬性設置屬性可能更合適(如果綁定的控制<xref:System.Windows.Controls.ListBox>項是 。 例如,如果希望在<xref:System.Windows.Trigger>滑鼠指向項時為項<xref:System.Windows.UIElement.Opacity%2A>的值設置動畫,則<xref:System.Windows.Controls.ListBoxItem>可以在樣式中定義觸發器。 如需範例，請參閱[樣式設定和範本化範例的簡介](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

 通常,請記住,<xref:System.Windows.DataTemplate>正在應用於每個生成<xref:System.Windows.Controls.ListBoxItem>的 (有關它的實際應用方式和位置的詳細資訊,請<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>參閱 頁面)。 您<xref:System.Windows.DataTemplate>只關心數據物件的表示和外觀。 在大多數情況下,列表示的所有其他方面(如項目選擇時的外觀或<xref:System.Windows.Controls.ListBox>佈局項的方式)不屬於<xref:System.Windows.DataTemplate>的定義。 如需範例，請參閱 [ItemsControl 的樣式設定和範本化](#DataTemplating_ItemsControl)一節。

<a name="Styling_StyleSelection"></a>
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>根據資料物件的屬性選擇 DataTemplate
 在 [DataType 屬性](#Styling_DataType)一節中提到過，您可以為不同的資料物件定義不同的資料範本。 當您具有<xref:System.Windows.Data.CompositeCollection>不同類型的專案或集合時,這一點特別有用。 在「[使用資料觸發器應用屬性值」](#DataTrigger_to_Apply_Property_Values)部分中,我們顯示,如果您擁有相同類型的資料物件的集合,則可以<xref:System.Windows.DataTemplate>創建, 然後使用觸發器根據每個資料物件的屬性值應用更改。 不過，觸發程序雖然可以讓您套用屬性值或啟動動畫，但無法提供重新建構資料物件結構的彈性。 某些方案可能需要為相同類型但具有不同屬性<xref:System.Windows.DataTemplate>的數據物件創建不同的數據物件。

 例如，當 `Task` 物件有一個 `Priority` 值為 `1` 時，您可能會想讓它看起來完全不同，以便提醒自己。 在這種情況下,您會建立用於顯示高<xref:System.Windows.DataTemplate>優先順序`Task`的物件 。 讓我們將以下內容<xref:System.Windows.DataTemplate>新增到資源部分:

 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]

此示例使用[DataTemplate.Resources](xref:System.Windows.FrameworkTemplate.Resources%2A)屬性。 該節中定義的資源由中的<xref:System.Windows.DataTemplate>元素共用。

 要<xref:System.Windows.DataTemplate>提供邏輯以根據資料`Priority`物件的值選擇要使用的,請創建和重寫方法<xref:System.Windows.Controls.DataTemplateSelector><xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>的子類。 在下面的範例中,<xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>該方法提供邏輯,以便`Priority`根據 屬性的值返回相應的範本。 要返回的範本位於包絡<xref:System.Windows.Window>元素的資源中找到。

 [!code-csharp[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]

 然後，就可以宣告`TaskListDataTemplateSelector` 為資源：

 [!code-xaml[DataTemplatingIntro_snip#R1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]
[!code-xaml[DataTemplatingIntro_snip#DTS](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]
[!code-xaml[DataTemplatingIntro_snip#R2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]

 要使用範本選擇器資源,請將其分配給<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>的屬性。 <xref:System.Windows.Controls.ListBox> 呼叫<xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>基礎集合中每個`TaskListDataTemplateSelector`項目的 該呼叫會將資料物件當做項目參數傳遞。 然後<xref:System.Windows.DataTemplate>,該方法返回的 將應用於該數據物件。

 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]

 在樣本選擇器就位後,<xref:System.Windows.Controls.ListBox>現在如下所示:

 ![資料樣本化範例螢幕擷取](./media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")

這個範例的討論到此結束。 如需完整範例，請參閱[資料範本化範例簡介](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/DataTemplatingIntro)。

<a name="DataTemplating_ItemsControl"></a>
## <a name="styling-and-templating-an-itemscontrol"></a>ItemsControl 的樣式設定和範本化
 即使<xref:System.Windows.Controls.ItemsControl>不是可以使用<xref:System.Windows.DataTemplate>的唯一控件類型,但將綁定<xref:System.Windows.Controls.ItemsControl>到集合是很常見的方案。 在[DataTemplate 部分的「屬於什麼」部分中](#what_belongs_in_datatemplate),我們<xref:System.Windows.DataTemplate>討論了您的定義應只與數據的表示有關。 為了知道何時不適合使用<xref:System.Windows.DataTemplate><xref:System.Windows.Controls.ItemsControl>。 下列範例是設計來說明每個屬性的功能。 此示例<xref:System.Windows.Controls.ItemsControl>中的 綁定到與上`Tasks`一個 示例中相同的集合。 為方便示範，這個範例中的樣式和範本都是內嵌宣告的。

 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]

 下圖是範例呈現的畫面：

 ![ItemsControl 範例螢幕擷取畫面](./media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")

 請注意,可以使用<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>而不是<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>使用 。 請參閱上一節中的範例。 同樣, 可以使用的選項<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>,<xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>而不是使用 。

 此處未顯示的兩<xref:System.Windows.Controls.ItemsControl>個與樣式相關的屬性是<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A><xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>與 。

<a name="DataTemplating_HeirarchicalDataTemplate"></a>
## <a name="support-for-hierarchical-data"></a>支援階層式資料
 到目前為止，我們只討論了如何繫結和顯示單一集合。 有時候集合之中可能還有其他集合。 類<xref:System.Windows.HierarchicalDataTemplate>設計為用於顯示此類數據<xref:System.Windows.Controls.HeaderedItemsControl>的類型。 在下列範例中，`ListLeagueList` 是 `League` 物件的清單。 每個 `League` 物件都有一個 `Name` 和一組 `Division` 物件集合。 每一個 `Division` 都有一個 `Name` 和 `Team` 物件的集合，並且每一個 `Team` 物件都有一個 `Name`。

 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](~/samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]

 該範例顯示,使用<xref:System.Windows.HierarchicalDataTemplate>時可以輕鬆地顯示包含其他清單的清單數據。 以下是範例的螢幕擷取畫面。

 ![階層資料範本範例螢幕擷取](./media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")

## <a name="see-also"></a>另請參閱

- [資料繫結](../advanced/optimizing-performance-data-binding.md)
- [尋找資料樣本產生的元素](how-to-find-datatemplate-generated-elements.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [GridView 資料行標頭樣式和範本概觀](../controls/gridview-column-header-styles-and-templates-overview.md)
