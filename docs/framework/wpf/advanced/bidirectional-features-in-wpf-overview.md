---
title: WPF 中的雙向功能概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 2a599322ef955b9f702f8960f294f5d093ede74a
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834740"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF 中的雙向功能概觀

與其他任何開發平臺[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]不同的是，有許多功能可支援快速開發雙向內容，例如，在相同檔中由左至右和從右至左的資料混合。 同時， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為需要雙向功能的使用者（例如阿拉伯文和希伯來文說話的使用者）建立絕佳的體驗。

下列各節說明許多雙向功能以及說明如何達到最佳雙向內容顯示的範例。 大部分的範例都會使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]，不過您可以輕鬆地將概念套用C#至或 Microsoft Visual Basic 程式碼。

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中定義內容流程方向的基本屬性是<xref:System.Windows.FrameworkElement.FlowDirection%2A>。 這個屬性可以設定為兩個列舉值的其中一個<xref:System.Windows.FlowDirection.LeftToRight> ， <xref:System.Windows.FlowDirection.RightToLeft>或。 屬性可用於繼承自[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>的所有元素。

下列範例會設定<xref:System.Windows.Controls.TextBox>元素的流程方向。

**由左至右的流向**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**由右至左的流向**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

下圖顯示如何轉譯先前的程式碼。

![說明不同流程方向的圖形。](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]樹狀結構中的專案會繼承其<xref:System.Windows.FrameworkElement.FlowDirection%2A>容器的。 在下列範例中， <xref:System.Windows.Controls.TextBlock>位於<xref:System.Windows.Controls.Grid> <xref:System.Windows.Window>，位於中。 設定的表示也<xref:System.Windows.Controls.TextBlock>會將它設定為和。<xref:System.Windows.Controls.Grid> <xref:System.Windows.Window> <xref:System.Windows.FrameworkElement.FlowDirection%2A>

下列範例示範設定<xref:System.Windows.FrameworkElement.FlowDirection%2A>。

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

<xref:System.Windows.Window>最上層<xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FrameworkElement.FlowDirection%2A>具有，因此包含在其中的所有元素也會繼承相同的。 <xref:System.Windows.FlowDirection> 若要讓元素覆寫指定<xref:System.Windows.FrameworkElement.FlowDirection%2A>的，它必須加入明確方向變更，例如上<xref:System.Windows.Controls.TextBlock>一個範例中的第二個<xref:System.Windows.FlowDirection.LeftToRight>，會變更為。 若未<xref:System.Windows.FrameworkElement.FlowDirection%2A>定義，則會套用<xref:System.Windows.FlowDirection.LeftToRight>預設值。

下圖顯示上一個範例的輸出：

![說明明確流程方向變更的圖形。](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

許多開發平臺（例如 HTML 和[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] JAVA）都會提供雙向內容開發的特殊支援。 HTML 之類的標記語言會提供必要的標記來以任何必要的方向顯示文字，例如 HTML 4.0 標記、"dir" （採用 "rtl" 或 "ltr" 作為值）。 這個標記與<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性類似， <xref:System.Windows.FrameworkElement.FlowDirection%2A>但屬性的運作方式是更先進的文字內容版面配置，而且可以用於文字以外的內容。

在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中<xref:System.Windows.Documents.FlowDocument> ，是一種可裝載文字、資料表、影像和其他元素組合的多用途[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素。 下列各節中的範例會使用這個項目。

將文字加入至<xref:System.Windows.Documents.FlowDocument> ，可以使用一種方式來完成。 執行此動作的簡單方式是透過<xref:System.Windows.Documents.Paragraph> ，這是用來將內容（例如文字）分組的區塊層級元素。 若要將文字加入至內嵌層級元素， <xref:System.Windows.Documents.Span>範例<xref:System.Windows.Documents.Run>會使用和。 <xref:System.Windows.Documents.Span>是用來分組其他內嵌專案的內嵌層級非固定格式內容專案， <xref:System.Windows.Documents.Run>而則是一種內嵌層級的流動內容專案，目的是要包含未格式化的文字執行。 可以包含多個<xref:System.Windows.Documents.Run>元素。 <xref:System.Windows.Documents.Span>

第一個檔範例包含具有多個網路共用名的檔;`\\server1\folder\file.ext`例如。 不論此網路連結出現在阿拉伯文文件還是英文文件中，您一定都會想要以相同的方式來顯示它。 下圖說明如何使用 Span 元素，並顯示阿拉伯文<xref:System.Windows.FlowDirection.RightToLeft>檔中的連結：

![說明使用 Span 元素的圖形。](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

因為文字是， <xref:System.Windows.FlowDirection.RightToLeft>所以所有特殊字元（例如 "\\"）會以由右至左順序分隔文字。 這會導致連結不會以正確的順序顯示，因此若要解決此問題，則必須內嵌文字，以保留個別<xref:System.Windows.Documents.Run>的流動。 <xref:System.Windows.FlowDirection.LeftToRight> 若要解決此問題<xref:System.Windows.Documents.Run> ，最好的方法是將較不常用的英文文字內嵌到較大的阿拉伯文<xref:System.Windows.Documents.Span>，而不是每種語言各自使用。

下圖說明如何使用內嵌在 Span 元素中的 Run 元素：

![說明內嵌在 Span 元素中之 Run 元素的圖形。](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

下列範例示範如何在<xref:System.Windows.Documents.Run>檔<xref:System.Windows.Documents.Span>中使用和元素。

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Span 項目

<xref:System.Windows.Documents.Span>元素會在具有不同流程方向的文字之間以界限分隔符號的形式運作。  即使<xref:System.Windows.Documents.Span>是具有相同流程方向的專案也會被視為具有不同的雙向範圍， <xref:System.Windows.Documents.Span>這表示元素會在容器的<xref:System.Windows.FlowDirection>中排序，只有<xref:System.Windows.Documents.Span>元素中的內容<xref:System.Windows.FlowDirection> 遵循<xref:System.Windows.Documents.Span>的。

下圖顯示數個<xref:System.Windows.Controls.TextBlock>元素的流程方向。

![說明具有不同流程方向之文字區塊的圖形。](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

下列範例顯示如何使用<xref:System.Windows.Documents.Span>和<xref:System.Windows.Documents.Run>專案來產生上圖中顯示的結果。

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

在範例<xref:System.Windows.Controls.TextBlock>的元素中<xref:System.Windows.Documents.Span> ，會根據其父系的來<xref:System.Windows.FlowDirection>設定項目，但每個<xref:System.Windows.Documents.Span>專案內的文字會根據自己<xref:System.Windows.FlowDirection>的順序流動。 這適用於拉丁文和阿拉伯文，或任何其他語言。

### <a name="adding-xmllang"></a>新增 xml:lang

下圖顯示另一個使用數位和算術運算式的範例， `"200.0+21.4=221.4"`例如。 請注意，只<xref:System.Windows.FlowDirection>會設定。

![顯示只使用 System.windows.frameworkelement.flowdirection 之數位的圖形。](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

輸出將會失望此應用程式的使用者，即使<xref:System.Windows.FlowDirection>是正確的，也不會將數位塑造成應塑造阿拉伯文數位。

XAML 元素可以包含[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]屬性（`xml:lang`），以定義每個元素的語言。 XAML 也支援[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]語言原則，因此`xml:lang`子項目會使用套用至樹狀結構中父元素的值。 在上述範例中，因為未針對<xref:System.Windows.Documents.Run>元素或其最上層元素定義語言，所以使用了預設值`xml:lang` ，這`en-US`適用于 XAML。 內部數位成形演算法[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]會選取對應語言中的數位–在此案例中為英文。 若要讓阿拉伯文數位正確`xml:lang`轉譯，必須設定。

下圖顯示`xml:lang`已新增的範例。

![說明從右至左流動之阿拉伯文數位的圖形。](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

下列範例會將`xml:lang`新增至應用程式。

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

請注意，許多語言根據目標`xml:lang`區域有不同的值，例如， `"ar-SA"`和`"ar-EG"`代表阿拉伯文的兩個變化。 先前的範例說明您需要同時`xml:lang`定義和<xref:System.Windows.FlowDirection>值。

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>具有非文字項目的 FlowDirection

<xref:System.Windows.FlowDirection>不只會定義文字在文字專案中流動的方式，也會定義幾乎每個[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]其他元素的流程方向。 下圖顯示<xref:System.Windows.Controls.ToolBar>使用水準<xref:System.Windows.Media.LinearGradientBrush>繪製其背景的（使用由左到右漸層）。

![顯示具有由左到右漸層之工具列的圖形。](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

將設定<xref:System.Windows.FlowDirection>為<xref:System.Windows.FlowDirection.RightToLeft>之後，不只<xref:System.Windows.Controls.ToolBar>是<xref:System.Windows.Media.LinearGradientBrush>從右至左排列按鈕，甚至是 realigns 其位移由右至左流動。

下圖顯示的校準<xref:System.Windows.Media.LinearGradientBrush>。

![顯示具有由右至左漸層之工具列的圖形。](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

下列範例會繪製<xref:System.Windows.FlowDirection.RightToLeft>。 <xref:System.Windows.Controls.ToolBar> （若要從左至右繪製，請移除<xref:System.Windows.FlowDirection> <xref:System.Windows.Controls.ToolBar>上的屬性。

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>FlowDirection 例外狀況

在某些情況下， <xref:System.Windows.FlowDirection>其行為不會如預期般運作。 本節涵蓋其中的兩個例外狀況。

**影像**

<xref:System.Windows.Controls.Image>代表顯示影像的控制項。 在[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]中，它可以<xref:System.Windows.Controls.Image.Source%2A>與定義[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] <xref:System.Windows.Controls.Image>要顯示之的屬性搭配使用。

與其他[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素不同的<xref:System.Windows.Controls.Image>是，不會<xref:System.Windows.FlowDirection>從容器繼承。 不過，如果<xref:System.Windows.FlowDirection>明確設定為<xref:System.Windows.FlowDirection.RightToLeft>， <xref:System.Windows.Controls.Image>會以水準方向顯示翻轉。 這會實作為方便使用的功能，讓開發人員用於雙向內容；因為在某些情況下，水平翻轉影像會產生所要的效果。

下圖顯示翻轉<xref:System.Windows.Controls.Image>的。

![說明翻轉影像的圖形。](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

下列範例示範<xref:System.Windows.Controls.Image>無法<xref:System.Windows.FlowDirection>從<xref:System.Windows.Controls.StackPanel>包含它的繼承。

> [!NOTE]
> 您在 C：\ 上必須有一個名為**ms_logo**的檔案執行此範例的磁片磁碟機。

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> 下載檔案中包含的是**ms_logo .jpg**檔案。 這個程式碼假設 .jpg 檔案不在您的專案內，而是在 C:\ 磁碟機的某個位置。 您必須將 .jpg 從專案檔複製至 C:\ 磁碟機，或變更程式碼來尋找專案內的檔案。 若要這麼做`Source="file://c:/ms_logo.jpg"` ， `Source="ms_logo.jpg"`請將變更為。

**路徑**

除了之外<xref:System.Windows.Controls.Image>，另一個有趣的元素是<xref:System.Windows.Shapes.Path>。 路徑是物件，可繪製一系列連接的線條和曲線。 <xref:System.Windows.Controls.Image>其行為方式與相關，類似于其<xref:System.Windows.FlowDirection>，例如<xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> ，它是其<xref:System.Windows.FlowDirection.LeftToRight>本身的水準鏡像。 不過，與不同<xref:System.Windows.Controls.Image>的<xref:System.Windows.Shapes.Path>是， <xref:System.Windows.FlowDirection>會從容器繼承它，而不需要明確指定它。

下列範例會繪製一個使用 3 條線的簡單箭號。 第一個箭號會<xref:System.Windows.FlowDirection.RightToLeft>繼承的流程方向<xref:System.Windows.Controls.StackPanel> ，使其起點和終點是從右側的根進行測量。 具有明確<xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>的第二個箭號也會在右側啟動。 不過，第三個箭號的起始根在左邊。 如需有關繪製的詳細<xref:System.Windows.Media.LineGeometry>資訊<xref:System.Windows.Media.GeometryGroup>，請參閱和。

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

下圖顯示上一個範例的輸出，其中包含使用`Path`元素繪製的箭號：

![說明使用 Path 元素繪製之箭號的圖形。](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

<xref:System.Windows.Controls.Image>和是如何[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用的<xref:System.Windows.FlowDirection>兩個範例。 <xref:System.Windows.Shapes.Path> <xref:System.Windows.Controls.InkPresenter> <xref:System.Windows.FlowDirection> <xref:System.Windows.Media.RadialGradientBrush> <xref:System.Windows.Media.LinearGradientBrush>在容器內的特定方向設定項目時，可以搭配專案使用，例如在表面上呈現筆墨的專案、、。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 每當您需要對內容進行由右至左的行為來模擬由左至右的行為，或反之亦然， [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]就會提供該功能。

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>數字替代

在過去，Windows 支援數位替換，允許以相同的數位表示不同的文化特性，同時在不同的地區設定之間保持這些數位的內部儲存，例如數位儲存在其已知的十六進位值0x40、0x41 向，但根據選取的語言顯示。

這讓應用程式能夠處理數值，而不需要將它們從一種語言轉換成另一種語言，例如，使用者[!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]可以在當地語系化的阿拉伯文 Windows 中開啟試算表，並查看阿拉伯文的數位，但是在中開啟它歐洲版本的 Windows，並查看相同數位的歐洲標記法。 針對逗號分隔符號和百分比符號這類其他符號，這也是必要的，因為在相同的文件中，它們通常會伴隨數字。

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 會持續使用相同的傳統，並新增此替代的進一步支援，讓使用者更深入控制該何時和如何使用這項功能。 雖然這項功能設計用於任何語言，但特別適用於雙向內容，其中特定語言的成形數字通常會是應用程式開發人員的挑戰，因為應用程式可能會在各種文化特性中執行。

控制數字替代運作[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]方式的核心屬性<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>是相依性屬性。 <xref:System.Windows.Media.NumberSubstitution>類別會指定文字中的數字顯示方式。 它有三個定義其行為的公用屬性。 以下是每個屬性的摘要：

**CultureSource**：

這個屬性指定如何判斷數字的文化特性。 它會採用三個<xref:System.Windows.Media.NumberCultureSource>列舉值的其中一個。

- 覆寫數位文化特性是屬性<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>的。

- 文字數位文化特性是文字執行的文化特性。 在標記中，這會`xml:lang`是或其 alias `Language`屬性（<xref:System.Windows.FrameworkElement.Language%2A>或<xref:System.Windows.FrameworkContentElement.Language%2A>）。 此外，它也是衍生自<xref:System.Windows.FrameworkContentElement>之類別的預設值。 這類類別<xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>包括<xref:System.Windows.Documents.Table?displayProperty=nameWithType>、 <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>等等。

- 使用者: 數位文化特性是目前線程的文化特性。 這個屬性<xref:System.Windows.FrameworkElement>是所有子類別<xref:System.Windows.Controls.Page>的預設值，例如、 <xref:System.Windows.Window>和<xref:System.Windows.Controls.TextBlock>。

**CultureOverride**：

<xref:System.Windows.Media.NumberCultureSource.Override>只有<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>在<xref:System.Windows.Media.NumberSubstitution.CultureSource%2A>屬性設定為時，才會使用屬性，否則會予以忽略。 它指定數字文化特性。 的值`null`（預設值）會轉譯為 en-us。

**替代**：

這個屬性指定要執行的數字替代類型。 它會採用下列<xref:System.Windows.Media.NumberSubstitutionMethod>其中一個列舉值：

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>:替代方法是根據數位文化特性的<xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType>屬性來決定。 這是預設值。

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>:如果數位文化特性是阿拉伯文或波斯文化特性，則會指定數位取決於內容。

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>:數位一律會轉譯為歐洲數位。

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>:數位會使用數位文化特性的國家（地區）來呈現，如文化特性的<xref:System.Globalization.CultureInfo.NumberFormat%2A>所指定。

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>:數位會使用數位文化特性的傳統數位來呈現。 對於大部分的文化特性而言，這與<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>相同。 不過， <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>某些阿拉伯文文化特性會產生拉丁數位，而此值會產生所有阿拉伯文文化特性的阿拉伯數位。

這些值對雙向內容開發人員的意義為何？ 在大部分的情況下，開發人員可能只需要<xref:System.Windows.FlowDirection>定義和每個文字[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]專案的語言<xref:System.Windows.Media.NumberSubstitution> ， `Language="ar-SA"`例如，而邏輯會根據正確[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的來顯示數位。 下列範例示範在阿拉伯文版本的 Windows 中執行的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中，使用阿拉伯文和英文數位。

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

下圖顯示上一個範例的輸出，如果您是在阿拉伯文版本的 Windows 中執行，並顯示阿拉伯文和英文數位：

![顯示阿拉伯文和英文數位的圖形。](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

在<xref:System.Windows.FlowDirection>此情況下很重要，因為將<xref:System.Windows.FlowDirection>設定<xref:System.Windows.FlowDirection.LeftToRight>為，反而會產生歐洲數位。 下列各節討論如何統一顯示整個文件的數字。 如果此範例不是在阿拉伯文 Windows 上執行，則所有數字會顯示為歐洲數字。

**定義替代規則**

在實際的應用程式中，您可能需要以程式設計方式來設定語言。 例如，您想要將`xml:lang`屬性設定為與[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]系統所使用的相同，或可能根據應用程式狀態變更語言。

如果您想要根據應用程式的狀態進行變更，請使用所提供[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的其他功能。

首先，設定應用程式元件的`NumberSubstitution.CultureSource="Text"`。 使用此設定可確保設定不會來自[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]具有 "User" 做為預設值（ <xref:System.Windows.Controls.TextBlock>例如）的 for text 元素。

例如:

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

在對應C#的程式碼中， `Language`將屬性`"ar-SA"`設定為，例如。

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

如果您需要將`Language`屬性設定為目前使用者的 UI 語言，請使用下列程式碼。

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>表示目前線程在執行時間所使用的目前文化特性。

您的[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]最終範例應該類似下列範例。

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

您的C#最終範例應該如下所示。

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

下圖顯示這兩種程式設計語言的視窗外觀，其中顯示的是阿拉伯文數位：

![顯示阿拉伯文數位的圖形。](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**使用替代屬性**

數位替代的運作[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]方式取決於文字元素的語言<xref:System.Windows.FlowDirection>及其。 <xref:System.Windows.FlowDirection>如果由左到右，則會轉譯歐洲數位。 不過，如果之前是阿拉伯文文字，或其語言設定為 "ar" <xref:System.Windows.FlowDirection> ，而是，則會改為<xref:System.Windows.FlowDirection.RightToLeft>呈現阿拉伯文數位。

不過，在某些情況下，您可能想建立統一的應用程式，例如所有使用者都使用歐洲數字。 或阿拉伯文數位<xref:System.Windows.Documents.Table> ，具有特定<xref:System.Windows.Style>的資料格。 其中一個簡單的方法是使用<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>屬性。

在下列範例中，第一個<xref:System.Windows.Controls.TextBlock>不會設定<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>屬性，因此演算法會如預期般顯示阿拉伯文數位。 不過，在第<xref:System.Windows.Controls.TextBlock>二個中，會將替代設定為歐洲，覆寫阿拉伯文數位的預設替代，並顯示歐洲數位。

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
