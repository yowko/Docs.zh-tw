---
title: 建立控制項的樣式
description: 瞭解如何在 Windows Presentation Foundation 和 .NET Core 中建立和參考控制項樣式。
author: adegeo
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: de186cd6da83ffef8a5cd59df581e88b24bc474d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325786"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>在 WPF 中建立控制項的樣式

使用 Windows Presentation Foundation （WPF），您可以使用自己的可重複使用樣式，自訂現有控制項的外觀。 樣式可全域套用至您的應用程式、視窗和頁面，或直接套用到控制項。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>建立樣式

您可以將視為一 <xref:System.Windows.Style> 種方便的方式，將一組屬性值套用至一或多個元素。 您可以對任何衍生自或的專案 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> （例如或）使用樣式 <xref:System.Windows.Window> <xref:System.Windows.Controls.Button> 。

宣告樣式最常見的方式，就是當做 XAML 檔案中區段的資源 `Resources` 。 因為樣式是資源，所以它們會遵守適用于所有資源的相同範圍規則。 簡單地說，您在其中宣告樣式會影響可以套用樣式的位置。 例如，如果您在應用程式定義 XAML 檔案的根項目中宣告樣式，則樣式可以在應用程式中的任何位置使用。

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

如果您在其中一個應用程式的 XAML 檔案中宣告樣式，則樣式只能用在該 XAML 檔案中。 如需有關資源範圍限定規則的詳細資訊，請參閱 [XAML 資源](xaml-resources-define.md)。

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

樣式是由子項目所組成，這些專案會在套用 `<Setter>` 樣式的元素上設定屬性。 在上述範例中，請注意樣式已設定為 `TextBlock` 透過屬性套用至類型 `TargetType` 。 樣式會將設定 <xref:System.Windows.Controls.Control.FontSize%2A> 為 `15` ，並將設 <xref:System.Windows.Controls.Control.FontWeight%2A> 為 `ExtraBold` 。 `<Setter>`為每個屬性加入樣式變更的。

## <a name="apply-a-style-implicitly"></a>隱含套用樣式

<xref:System.Windows.Style>是將一組屬性值套用至多個元素的便利方式。 例如，請考慮下列 <xref:System.Windows.Controls.TextBlock> 元素及其在視窗中的預設面板。

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![樣式設定範例螢幕擷取畫面](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

您可以 <xref:System.Windows.Controls.Control.FontSize%2A> <xref:System.Windows.Controls.Control.FontFamily%2A> 在每個專案上設定屬性（例如和），以變更預設的外觀 <xref:System.Windows.Controls.TextBlock> 。 不過，如果您想要讓 <xref:System.Windows.Controls.TextBlock> 元素共用某些屬性，您可以 <xref:System.Windows.Style> 在 XAML 檔案的 `Resources` 區段中建立，如下所示。

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

當您將樣式的設定 <xref:System.Windows.Style.TargetType%2A> 為 <xref:System.Windows.Controls.TextBlock> 類型並省略 `x:Key` 屬性時，樣式會套用至範圍設定為樣式的所有 <xref:System.Windows.Controls.TextBlock> 元素，這通常是 XAML 檔案本身。

現在 <xref:System.Windows.Controls.TextBlock> 元素會顯示如下。

![樣式設定範例螢幕擷取畫面](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>明確套用樣式

如果您將 `x:Key` 具有值的屬性加入至樣式，則樣式不會再隱含地套用至的所有專案 <xref:System.Windows.Style.TargetType%2A> 。 只有明確參考樣式的元素才會套用樣式。

以下是上一節的樣式，但使用 `x:Key` 屬性宣告。

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

若要套用樣式，請 <xref:System.Windows.FrameworkElement.Style%2A> `x:Key` 使用[StaticResource 標記延伸](../../framework/wpf/advanced/staticresource-markup-extension.md)，將元素上的屬性設定為值，如下所示。

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

請注意，第一個專案 <xref:System.Windows.Controls.TextBlock> 已套用樣式，而第二個 TextBlock 元素保持不變。 上一節中的隱含樣式已變更為宣告屬性的樣式 `x:Key` ，亦即，受此樣式影響的專案是直接參考樣式的元素。

![樣式設定範例螢幕擷取畫面](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "建立-a 樣式-明確 textblock")

樣式套用、明確或隱含地套用之後，就會變成密封的，而且無法變更。 如果您想要變更已套用的樣式，請建立新的樣式來取代現有的樣式。 如需詳細資訊，請參閱 <xref:System.Windows.Style.IsSealed%2A> 屬性 (Property)。

您可以建立一個物件來根據自訂邏輯選擇要套用的樣式。 如需範例，請參閱針對類別提供的範例 <xref:System.Windows.Controls.StyleSelector> 。

## <a name="apply-a-style-programmatically"></a>以程式設計方式套用樣式

若要以程式設計方式將指定的樣式指派給專案，請從 resources 集合取得樣式，並將其指派給專案的 <xref:System.Windows.FrameworkElement.Style%2A> 屬性。 資源集合中的專案屬於類型 <xref:System.Object> 。 因此，您必須先將抓取的樣式轉換成， <xref:System.Windows.Style?displayProperty=fullName> 再將它指派給 `Style` 屬性。 例如，下列程式碼會將名為的樣式 `TextBlock` 設定 `textblock1` 為已定義的樣式 `TitleText` 。

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>擴充樣式

也許您想要讓兩個 <xref:System.Windows.Controls.TextBlock> 元素共用一些屬性值，例如 <xref:System.Windows.Controls.Control.FontFamily%2A> 和中間的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 。 但您也想要文字 [**我的圖片**] 有一些額外的屬性。 若要這麼做，您可以建立以第一個樣式為基礎的新樣式，如下所示。

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

此 `TextBlock` 樣式現在已置中，使用 `Comic Sans MS` 大小為的字型， `26` 而前景色彩設定為 <xref:System.Windows.Media.LinearGradientBrush> 範例中所示的。 請注意，它會覆寫 <xref:System.Windows.Controls.Control.FontSize%2A> 基底樣式的值。 如果有一個以上 <xref:System.Windows.Setter> 指向中的相同屬性 <xref:System.Windows.Style> ， `Setter` 則會優先使用宣告的。

以下顯示 <xref:System.Windows.Controls.TextBlock> 元素的樣子：

![已設定樣式的 TextBlock](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

此 `TitleText` 樣式會延伸已針對該類型所建立的樣式 <xref:System.Windows.Controls.TextBlock> （以參考） `BasedOn="{StaticResource {x:Type TextBlock}}"` 。 您也可以使用樣式的來擴充具有的樣式 `x:Key` `x:Key` 。 例如，如果有名稱為的樣式， `Header1` 而您想要擴充該樣式，則您會使用 `BasedOn="{StaticResource Header1}"` 。

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType 屬性和 X：Key 屬性的關聯性

如先前所示，將 <xref:System.Windows.Style.TargetType%2A> 屬性設定為 `TextBlock` 而不指派樣式， `x:Key` 會使樣式套用至所有 <xref:System.Windows.Controls.TextBlock> 元素。 在此情況下，`x:Key` 會隱含地設定為 `{x:Type TextBlock}`。 這表示如果您將值明確設定 `x:Key` 為以外的任何專案 `{x:Type TextBlock}` ，則 <xref:System.Windows.Style> 不會自動套用至所有 `TextBlock` 元素。 相反地，您必須將樣式（藉由使用 `x:Key` 值）明確地套用至 `TextBlock` 元素。 如果您的樣式是在 resources 區段中，而您未在 `TargetType` 樣式上設定屬性，則必須設定 `x:Key` 屬性。

除了提供的預設值 `x:Key` ， `TargetType` 屬性會指定 setter 屬性套用的類型。 如果您未指定 `TargetType` ，則必須 <xref:System.Windows.Setter> 使用語法，以類別名稱限定物件中的屬性 `Property="ClassName.Property"` 。 例如， `Property="FontSize"` 您必須將設定為或，而不是設定 <xref:System.Windows.Setter.Property%2A> `"TextBlock.FontSize"` `"Control.FontSize"` 。

另請注意，許多 WPF 控制項都是由其他 WPF 控制項的組合所組成。 如果您建立一個套用到某個型別所有控制項的樣式，可能會獲得非預期的結果。 例如，如果您建立以中的型別為目標的樣式 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Window> ，則樣式會套用至 `TextBlock` 視窗中的所有控制項，即使 `TextBlock` 是另一個控制項的一部分，例如 <xref:System.Windows.Controls.ListBox> 。

## <a name="see-also"></a>另請參閱

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [XAML 資源的總覽](xaml-resources-define.md)
- [XAML 總覽（WPF & .NET Core）](xaml.md)
