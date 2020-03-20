---
title: 內容模型
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187398"
---
# <a name="wpf-content-model"></a>WPF 內容模型
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 是展示平台，提供許多以顯示不同類型內容為主要目的的控制項和類控制項類型。 為了判斷要使用哪一種控制項或從哪一種控制項衍生，您應該了解特定控制項顯示哪些物件的效果最佳。  
  
 本主題摘要說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項和類控制項類型所適用的內容模型。 內容模型描述控制項中可使用的內容。 本主題同時列出每一個內容模型的內容屬性。 內容屬性是一種用於儲存物件內容的屬性。  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a>包含任意內容的類別  
 某些控制項可以包含任何類型的物件，例如字串、<xref:System.DateTime>物件或<xref:System.Windows.UIElement>作為其他項的容器的物件。 例如，可以包含<xref:System.Windows.Controls.Button>圖像和某些文本;例如，可以包含圖像和某些文本。或<xref:System.Windows.Controls.CheckBox>可以包含 的值<xref:System.DateTime.Now%2A?displayProperty=nameWithType>。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 有四種可包含任意內容的類別。 下表列出了從 繼承的<xref:System.Windows.Controls.Control>類。  
  
|包含任意內容的類別|內容|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|單一任意物件。|  
|<xref:System.Windows.Controls.HeaderedContentControl>|標頭和單一項目，兩者都是任意物件。|  
|<xref:System.Windows.Controls.ItemsControl>|任意物件的集合。|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|標頭和項目集合，這些全部都是任意物件。|  
  
 繼承自這些類別的控制項可以包含相同類型的內容，並且以相同方式處理內容。 下圖顯示了每個內容模型中包含圖像和某些文本的控制項：  
  
 ![顯示四個不同控制項的螢幕截圖，每個內容模型一個。](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>包含單一任意物件的控制項  
 該<xref:System.Windows.Controls.ContentControl>類包含一段任意內容。 其內容屬性為<xref:System.Windows.Controls.ContentControl.Content%2A>。 以下控制項繼承<xref:System.Windows.Controls.ContentControl>並使用其內容模型：  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>下圖顯示了四個按鈕，其設置為字串、<xref:System.DateTime>物件、和<xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Panel> ， 包含 和<xref:System.Windows.Shapes.Ellipse>： <xref:System.Windows.Controls.TextBlock>  
  
 ![顯示四個不同內容類型的按鈕的螢幕截圖。](./media/wpf-content-model/control-content-model-buttons.png)  
  
 有關如何設置<xref:System.Windows.Controls.ContentControl.Content%2A>屬性的示例，請參閱<xref:System.Windows.Controls.ContentControl>。  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>包含標頭和單一任意物件的控制項  
 類<xref:System.Windows.Controls.HeaderedContentControl>繼承<xref:System.Windows.Controls.ContentControl>並顯示具有標頭的內容。 它繼承<xref:System.Windows.Controls.ContentControl.Content%2A>內容屬性 ， 和<xref:System.Windows.Controls.ContentControl>定義<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>類型<xref:System.Object>的屬性 ;因此，兩者都可以是任意物件。  
  
 以下控制項繼承<xref:System.Windows.Controls.HeaderedContentControl>並使用其內容模型：  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 下圖顯示了兩<xref:System.Windows.Controls.TabItem>個物件。 第一<xref:System.Windows.Controls.TabItem>個<xref:System.Windows.UIElement>物件為<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和<xref:System.Windows.Controls.ContentControl.Content%2A>。 <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>設置為<xref:System.Windows.Controls.StackPanel>包含 和<xref:System.Windows.Shapes.Ellipse>的 。 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.ContentControl.Content%2A>設置為<xref:System.Windows.Controls.StackPanel>包含 和<xref:System.Windows.Controls.TextBlock>的 。 <xref:System.Windows.Controls.Label> 第二<xref:System.Windows.Controls.TabItem>個在 和<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>中有<xref:System.Windows.Controls.TextBlock>一個<xref:System.Windows.Controls.ContentControl.Content%2A>字串。  
  
 ![在"標頭"屬性中使用不同類型的 TabControl。](./media/wpf-content-model/control-content-model-tab.png)  
  
 有關如何創建<xref:System.Windows.Controls.TabItem>物件的示例，請參閱<xref:System.Windows.Controls.HeaderedContentControl>。  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>包含任意物件集合的控制項  
 類<xref:System.Windows.Controls.ItemsControl>繼承 from<xref:System.Windows.Controls.Control>可以包含多個項，如字串、物件或其他元素。 其內容屬性為<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>和<xref:System.Windows.Controls.ItemsControl.Items%2A>。 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>通常用於使用資料收集填充 。 <xref:System.Windows.Controls.ItemsControl> 如果不想使用集合填充 ，<xref:System.Windows.Controls.ItemsControl>則可以使用 屬性<xref:System.Windows.Controls.ItemsControl.Items%2A>添加項。  
  
 以下控制項繼承<xref:System.Windows.Controls.ItemsControl>並使用其內容模型：  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 下圖顯示了包含這些類型的項<xref:System.Windows.Controls.ListBox>的 圖所示：  
  
- 字串。  
  
- <xref:System.DateTime> 物件。  
  
- <xref:System.Windows.UIElement>。  
  
- 包含<xref:System.Windows.Controls.Panel>和<xref:System.Windows.Shapes.Ellipse>的 A。 <xref:System.Windows.Controls.TextBlock>  
  
 ![顯示包含四種類型的內容的 ListBox 的螢幕截圖。](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>包含標頭和任意物件集合的控制項  
 類<xref:System.Windows.Controls.HeaderedItemsControl>繼承和<xref:System.Windows.Controls.ItemsControl>可以包含多個項，如字串、物件或其他元素以及標頭。 它繼承<xref:System.Windows.Controls.ItemsControl>內容屬性<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>和<xref:System.Windows.Controls.ItemsControl.Items%2A>，並定義可以是任意物件<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>的屬性。  
  
 以下控制項繼承<xref:System.Windows.Controls.HeaderedItemsControl>並使用其內容模型：  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>包含 UIElement 物件集合的類別  
 類<xref:System.Windows.Controls.Panel>位置並排列子<xref:System.Windows.UIElement>物件。 其內容屬性為<xref:System.Windows.Controls.Panel.Children%2A>。  
  
 以下類從<xref:System.Windows.Controls.Panel>類繼承並使用其內容模型：  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 如需詳細資訊，請參閱[面板概觀](panels-overview.md)。  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>影響 UIElement 外觀的類別  
 該<xref:System.Windows.Controls.Decorator>類對單個子項<xref:System.Windows.UIElement>或周圍應用視覺效果。 其內容屬性為<xref:System.Windows.Controls.Decorator.Child%2A>。 以下類繼承<xref:System.Windows.Controls.Decorator>並使用其內容模型：  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 下圖顯示了一個<xref:System.Windows.Controls.TextBox>（用）其周圍裝飾<xref:System.Windows.Controls.Border>的。  
  
 ![具有黑色框線的 TextBox](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
具有框線的 TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>提供 UIElement 相關視覺化回應的類別  
 類<xref:System.Windows.Documents.Adorner>向使用者提供可視提示。 例如，使用<xref:System.Windows.Documents.Adorner>將函數控制碼添加到元素或提供有關控制項的狀態資訊。 該<xref:System.Windows.Documents.Adorner>類提供了一個框架，以便您可以創建自己的修飾器。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 不會提供任何已實作的裝飾項。 如需詳細資訊，請參閱[裝飾項概觀](adorners-overview.md)。  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a>可讓使用者輸入文字的類別  
 WPF 提供三種可讓使用者輸入文字的主要控制項。 每一個控制項都會以不同方式顯示文字。 下表列出這三個文字相關控制項、它們顯示文字時的功能，以及其包含控制項文字的屬性。  
  
|控制|文字顯示為|內容屬性|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|純文字|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|格式化文字|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|隱藏文字 (字元會加上遮罩)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a>顯示文字的類別  
 有數種類別可用來顯示純文字或格式化文字。 您可以使用<xref:System.Windows.Controls.TextBlock>來顯示少量的文本。 如果要顯示大量文本，請使用 。 <xref:System.Windows.Controls.FlowDocumentReader> <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
  
 具有<xref:System.Windows.Controls.TextBlock>兩個內容屬性： <xref:System.Windows.Controls.TextBlock.Text%2A> <xref:System.Windows.Controls.TextBlock.Inlines%2A>和 。 當您要顯示使用一致格式的文本時，該<xref:System.Windows.Controls.TextBlock.Text%2A>屬性通常是最佳選擇。 如果計畫在整個文本中使用不同的格式，請使用 該<xref:System.Windows.Controls.TextBlock.Inlines%2A>屬性。 該<xref:System.Windows.Controls.TextBlock.Inlines%2A>屬性是<xref:System.Windows.Documents.Inline>物件的集合，它指定如何設置文本的格式。  
  
 下表列出了<xref:System.Windows.Controls.FlowDocumentReader>和<xref:System.Windows.Controls.FlowDocumentPageViewer><xref:System.Windows.Controls.FlowDocumentScrollViewer>類的內容屬性。  
  
|控制|內容屬性|內容屬性類型|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Document|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Document|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Document|<xref:System.Windows.Documents.FlowDocument>|  
  
 實現<xref:System.Windows.Documents.FlowDocument><xref:System.Windows.Documents.IDocumentPaginatorSource>介面;因此，所有三個類都可以以<xref:System.Windows.Documents.FlowDocument>作為內容。  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a>格式化文字的類別  
 <xref:System.Windows.Documents.TextElement>及其相關類允許您設置文本格式。 <xref:System.Windows.Documents.TextElement>物件在 和 中<xref:System.Windows.Controls.TextBlock>包含<xref:System.Windows.Documents.FlowDocument>和設置文本的格式。 物件的兩種主要類型<xref:System.Windows.Documents.TextElement>是<xref:System.Windows.Documents.Block>元素和<xref:System.Windows.Documents.Inline>元素。 元素<xref:System.Windows.Documents.Block>表示文字區塊，如段落或清單。 元素<xref:System.Windows.Documents.Inline>表示塊中文本的一部分。 許多<xref:System.Windows.Documents.Inline>類指定應用它們的文本的格式。 每個<xref:System.Windows.Documents.TextElement>都有自己的內容模型。 如需詳細資訊，請參閱 [TextElement 內容模型概觀](../advanced/textelement-content-model-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [進階](../advanced/index.md)
