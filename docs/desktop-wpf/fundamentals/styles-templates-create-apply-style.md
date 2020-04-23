---
title: 為控制項建立樣式
description: 瞭解如何在 Windows 演示文稿基礎和 .NET Core 中創建和引用控制項樣式。
author: thraka
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2956dbf93a1d34feca31d3ab10536f5089010189
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "82071266"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>為 WPF 中的控制項建立樣式

使用 Windows 簡報簡報 (WPF),您可以使用自己的可重用樣式自訂現有控制項的外觀。 樣式可以全域應用於你的應用、視窗和頁面,也可以直接應用於控件。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>建立樣式

可以將<xref:System.Windows.Style>a 視為將一組屬性值應用於一個或多個元素的便捷方法。 <xref:System.Windows.FrameworkElement>可以在派生自<xref:System.Windows.FrameworkContentElement>或<xref:System.Windows.Window>或 或的任何元素上使用<xref:System.Windows.Controls.Button>樣式。

聲明樣式的最常見方法是作為 XAML`Resources`檔中 部分中的資源。 因為樣式是資源,因此它們遵循適用於所有資源的相同範圍規則。 簡單地說,聲明樣式會影響樣式的應用位置。 例如,如果在應用定義 XAML 檔的根元素中聲明樣式,則可以在應用中的任意位置使用該樣式。

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

如果在應用的 XAML 檔中聲明樣式,則該樣式只能在該 XAML 檔中使用。 如需有關資源範圍限定規則的詳細資訊，請參閱 [XAML 資源](xaml-resources-define.md)。

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

樣式由`<Setter>`子元素組成,這些子元素在樣式應用的元素上設置屬性。 在上面的示例中,請注意樣式設置為應用於`TextBlock`通過屬性的類型`TargetType`。 <xref:System.Windows.Controls.Control.FontSize%2A>樣式設定`15`為與<xref:System.Windows.Controls.Control.FontWeight%2A>。 `ExtraBold` 為每個屬性`<Setter>`新增樣式變更的 。

## <a name="apply-a-style-implicitly"></a>隱式應用樣式

A<xref:System.Windows.Style>是一種將一組屬性值應用於多個元素的便捷方法。 例如,請考慮以下<xref:System.Windows.Controls.TextBlock>元素及其在視窗中的默認外觀。

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![樣式範例螢幕擷取](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

可以通過直接在<xref:System.Windows.Controls.Control.FontSize%2A><xref:System.Windows.Controls.Control.FontFamily%2A><xref:System.Windows.Controls.TextBlock>每個 元素上設置屬性(如和 ,)來更改預設外觀。 但是,如果您希望<xref:System.Windows.Controls.TextBlock>元素共用某些屬性,則可以在 XAML 檔<xref:System.Windows.Style>`Resources`部分中創建 a,如下所示。

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

將<xref:System.Windows.Style.TargetType%2A>樣式設定<xref:System.Windows.Controls.TextBlock>為 類型並`x:Key`省略 屬性時,該樣式將應用於範圍為<xref:System.Windows.Controls.TextBlock>樣式的所有 元素,該元素通常是 XAML 檔本身。

現在元素<xref:System.Windows.Controls.TextBlock>如下所示。

![樣式範例螢幕擷取](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>明確應用樣式

如果向樣式添加`x:Key`具有值的屬性,則該樣式將不再隱式應用<xref:System.Windows.Style.TargetType%2A>於 的所有元素。 只有顯式引用樣式的元素才會應用樣式。

下面是上一節中的樣式,但使用`x:Key`屬性聲明。

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

要應用樣式,請使用<xref:System.Windows.FrameworkElement.Style%2A>[StaticResource 標記擴展](../../framework/wpf/advanced/staticresource-markup-extension.md)將元素`x:Key`上的屬性設置為值,如下所示。

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

請注意,第一<xref:System.Windows.Controls.TextBlock>個元素的樣式應用於它,而第二個 TextBlock 元素保持不變。 上一節的隱式樣式已更改為聲明`x:Key`屬性的樣式,這意味著受該樣式影響的唯一元素是直接引用該樣式的元素。

![樣式範例螢幕擷取](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "建立樣式-顯示式文字塊")

一旦顯式或隱式應用樣式,它就會密封,並且無法更改。 如果要更改已應用的樣式,請創建新樣式以替換現有樣式。 如需詳細資訊，請參閱 <xref:System.Windows.Style.IsSealed%2A> 屬性 (Property)。

您可以建立一個物件來根據自訂邏輯選擇要套用的樣式。 例如,請參閱為<xref:System.Windows.Controls.StyleSelector>類提供的範例。

## <a name="apply-a-style-programmatically"></a>以程式設計方式套用樣式

要以程式設計方式將命名樣式配置給元素,請從資源集合中取得樣式並將其分配給元素的屬性<xref:System.Windows.FrameworkElement.Style%2A>。 資源集合的項目類型<xref:System.Object>為 。 因此,在將其分配給屬性之前,必須將檢索<xref:System.Windows.Style?displayProperty=fullName>的樣式轉換為`Style`。 例如,以下代碼設置對定義的樣式`TextBlock``textblock1``TitleText`命名的樣式。

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>擴充樣式

您可能希望兩個<xref:System.Windows.Controls.TextBlock>元素分享一些屬性值,<xref:System.Windows.Controls.Control.FontFamily%2A>例如與中<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>位 。 但是,您還希望文本 **「我的圖片」** 具有一些其他屬性。 可以通過創建基於第一種樣式的新樣式來執行此操作,如下所示。

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

此`TextBlock`樣式現在居中,使用`Comic Sans MS`大小`26`為 的 字體,前景顏色設置<xref:System.Windows.Media.LinearGradientBrush>為示例中 所示。 請注意,它覆蓋基本樣式<xref:System.Windows.Controls.Control.FontSize%2A>的值。 如果有多個<xref:System.Windows.Setter>指向 中的同<xref:System.Windows.Style>一 屬性,則最後聲明`Setter`的將優先。

下面顯示了<xref:System.Windows.Controls.TextBlock>元素現在的外觀:

![已設定樣式的 TextBlock](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

此`TitleText`樣式延伸為<xref:System.Windows.Controls.TextBlock>類型建立的樣式,該樣式參考`BasedOn="{StaticResource {x:Type TextBlock}}"`於 。 還可以通過使用`x:Key`的樣式擴展`x:Key`具有 的樣式。 例如,如果有一個樣式命名`Header1`,並且要擴展該樣式,則可以使用`BasedOn="{StaticResource Header1}"`。

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>目標類型屬性與 x:鍵屬性的關係

如<xref:System.Windows.Style.TargetType%2A>前所示`TextBlock`, 在不分配樣式的情況下將屬性設置`x:Key`為 , 會導致將樣<xref:System.Windows.Controls.TextBlock>式應用於所有 元素。 在此情況下，`x:Key` 會隱含地設定為 `{x:Type TextBlock}`。 `x:Key`這意味著,如果顯式將值設置為`{x:Type TextBlock}`以外的任何內容,<xref:System.Windows.Style>則不會自動應用於`TextBlock`所有 元素。 相反,必須顯式將樣式(通過使用`x:Key`值)應用於`TextBlock`元素。 如果樣式位於資源部分,並且未在樣式上設置`TargetType`屬性,則必須設置`x:Key`該 屬性。

除了為`x:Key`提供預設值外`TargetType`, 屬性還指定 setter 屬性應用於的類型。 如果不指定,`TargetType`則必須使用<xref:System.Windows.Setter>`Property="ClassName.Property"`語法 限定物件中的屬性與類名稱。 例如`Property="FontSize"`,必須設定為<xref:System.Windows.Setter.Property%2A>`"TextBlock.FontSize"`或`"Control.FontSize"`,而不是設定 。

另請注意,許多 WPF 控件由其他 WPF 控件的組合組成。 如果您建立一個套用到某個型別所有控制項的樣式，可能會獲得非預期的結果。 例如,如果建立以<xref:System.Windows.Controls.TextBlock>中的類型<xref:System.Windows.Window>為目標的樣式,則該樣式將應用於視窗中的所有`TextBlock`控制項,即使是`TextBlock`另一個控制項的一<xref:System.Windows.Controls.ListBox>部分(如 。

## <a name="see-also"></a>另請參閱

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [XAML 資源概述](xaml-resources-define.md)
- [XAML 概述(WPF & .NET 核心)](xaml.md)
