---
title: WPF 中的雙向功能概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 16cf232ccbdcca496aaa18fc2cfac280072ca24f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655480"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF 中的雙向功能概觀
不同於任何其他開發平台[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有許多支援雙向內容的快速開發功能，例如混合使用由左至右和由右至左相同的文件中的資料。 在此同時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]建立需要雙向功能，如阿拉伯文和希伯來文談到使用者之使用者的絕佳體驗。  
  
 下列各節說明許多雙向功能以及說明如何達到最佳雙向內容顯示的範例。 大部分的範例使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]，但是您可以輕鬆地套用到的概念C#或 Microsoft Visual Basic 程式碼。  

<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 基本的屬性，定義中的內容流向[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式是<xref:System.Windows.FrameworkElement.FlowDirection%2A>。 這個屬性可以設定為其中一個列舉值，<xref:System.Windows.FlowDirection.LeftToRight>或<xref:System.Windows.FlowDirection.RightToLeft>。 屬性是提供給所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]繼承自項目<xref:System.Windows.FrameworkElement>。  
  
 下列範例設定的流向<xref:System.Windows.Controls.TextBox>項目。  
  
 **由左至右的流向**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **由右至左的流向**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 下圖顯示如何轉譯先前的程式碼。  
    
 ![說明不同的方向的圖形。](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 內的項目[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]樹狀結構會繼承<xref:System.Windows.FrameworkElement.FlowDirection%2A>從其容器。 在下列範例中，<xref:System.Windows.Controls.TextBlock>內<xref:System.Windows.Controls.Grid>，而後者則位在<xref:System.Windows.Window>。 設定<xref:System.Windows.FrameworkElement.FlowDirection%2A>for<xref:System.Windows.Window>隱含設定進行<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Controls.TextBlock>以及。  
  
 下列範例示範如何設定<xref:System.Windows.FrameworkElement.FlowDirection%2A>。  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 最上層<xref:System.Windows.Window>已經<xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>，因此，其內所含的所有項目也會繼承相同<xref:System.Windows.FrameworkElement.FlowDirection%2A>。 若要覆寫指定的項目<xref:System.Windows.FrameworkElement.FlowDirection%2A>它必須新增明確方向變更，例如第二個<xref:System.Windows.Controls.TextBlock>變更為上一個範例中<xref:System.Windows.FlowDirection.LeftToRight>。 若未<xref:System.Windows.FrameworkElement.FlowDirection%2A>定義，則預設<xref:System.Windows.FlowDirection.LeftToRight>套用。  
  
 下圖顯示上述範例的輸出：

 ![說明明確的流程方向變更的圖形。](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 許多開發平台，例如[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]，[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]和 Java 進行雙向內容開發提供特殊支援。 這類的標記語言[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]提供內容的寫入器所需的標記，以顯示文字中任何必要的方向，例如[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]4.0 標記、"dir"會採用"rtl"或"ltr"作為值。 此標記是類似<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性，但<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性運作方式更進階的方式，以配置文字內容，並可以用於文字以外的內容。  
  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，則<xref:System.Windows.Documents.FlowDocument>靈活[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]可以裝載的文字、 表格、 影像和其他項目組合的項目。 下列各節中的範例會使用這個項目。  
  
 新增文字至<xref:System.Windows.Documents.FlowDocument>可以透過多種方式。 若要這樣做的簡單方式是透過<xref:System.Windows.Documents.Paragraph>這是用來將群組內容，例如文字的區塊層級項目。 若要將文字加入此範例會使用的內嵌層級項目<xref:System.Windows.Documents.Span>和<xref:System.Windows.Documents.Run>。 <xref:System.Windows.Documents.Span> 是用於分組其他內嵌項目中，內嵌層級流動內容項目時<xref:System.Windows.Documents.Run>是內嵌層級非固定格式內容項目来包含未格式化的文字執行。 A<xref:System.Windows.Documents.Span>可以包含多個<xref:System.Windows.Documents.Run>項目。  
  
 第一個文件的範例包含具有許多網路共用的名稱; 的文件比方說`\\server1\folder\file.ext`。 不論此網路連結出現在阿拉伯文文件還是英文文件中，您一定都會想要以相同的方式來顯示它。 下圖說明使用 Span 項目，並以阿拉伯數字顯示連結<xref:System.Windows.FlowDirection.RightToLeft>文件：

 ![說明如何使用 Span 項目的圖形。](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 因為文字<xref:System.Windows.FlowDirection.RightToLeft>、 所有特殊字元，例如 「\\"，區隔文字由右至左的順序。 這會導致不正確的順序顯示的連結，因此若要解決此問題，必須內嵌文字，以保留個別<xref:System.Windows.Documents.Run>流動<xref:System.Windows.FlowDirection.LeftToRight>。 而不是個別<xref:System.Windows.Documents.Run>針對每種語言，更好的方法，來解決問題就是將較不常用的英文文字內嵌到較大的阿拉伯文<xref:System.Windows.Documents.Span>。  
  
 下圖說明這個使用內嵌在 Span 項目中的執行項目：

 ![圖形中所示範的執行項目內嵌在 Span 項目。](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 下列範例示範如何使用<xref:System.Windows.Documents.Run>和<xref:System.Windows.Documents.Span>文件中的項目。  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span 項目  
 <xref:System.Windows.Documents.Span>項目是作為具有不同流向之文字間的界限分隔符號。  甚至<xref:System.Windows.Documents.Span>具有相同的文字方向的項目都會被視為具有不同的雙向範圍，這表示<xref:System.Windows.Documents.Span>項目在容器的排序<xref:System.Windows.FlowDirection>中的內容<xref:System.Windows.Documents.Span>項目遵循<xref:System.Windows.FlowDirection>的<xref:System.Windows.Documents.Span>。  
  
 下圖顯示數個流向<xref:System.Windows.Controls.TextBlock>項目。  
    
 ![說明方向不同的文字區塊的圖形。](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 下列範例示範如何使用<xref:System.Windows.Documents.Span>和<xref:System.Windows.Documents.Run>項目來產生上圖所示結果。  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 在<xref:System.Windows.Controls.TextBlock>項目，在範例中，<xref:System.Windows.Documents.Span>項目根據配置<xref:System.Windows.FlowDirection>其父代，但在每個文字<xref:System.Windows.Documents.Span>根據自己的項目流程<xref:System.Windows.FlowDirection>。 這適用於拉丁文和阿拉伯文，或任何其他語言。  
  
### <a name="adding-xmllang"></a>新增 xml:lang  
 下圖顯示另一個範例使用數字和算術運算式，例如`"200.0+21.4=221.4"`。 請注意，只有<xref:System.Windows.FlowDirection>設定。  
    
 ![顯示數字，使用只有 FlowDirection 的圖形。](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 此應用程式的使用者將會對輸出失望，即使<xref:System.Windows.FlowDirection>正確無誤，會形成阿拉伯數字，不會形成數字。  
  
 XAML 項目可以包含[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]屬性 (`xml:lang`)，定義每個項目的語言。 XAML 也支援[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]語言原則讓`xml:lang`套用至父項目樹狀結構中的值會由子元素。 在上述範例中，因為語言不定義為<xref:System.Windows.Documents.Run>項目或任何它上方層級項目，預設值`xml:lang`使用，也就是`en-US`的 XAML。 內部數字形成演算法[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]選取數字，對應的語言 – 在此情況下英文。 若要到阿拉伯數字呈現正確`xml:lang`需要設定。  
  
 下圖顯示範例`xml:lang`加入。  
    
 ![圖形說明如何從右至左的阿拉伯數字。](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 下列範例會將`xml:lang`應用程式。  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 請注意，許多語言會有不同`xml:lang`取決於目標區域，例如，值`"ar-SA"`和`"ar-EG"`代表阿拉伯文的兩種變化。 先前的範例說明您需要同時定義`xml:lang`和<xref:System.Windows.FlowDirection>值。  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>具有非文字項目的 FlowDirection  
 <xref:System.Windows.FlowDirection> 定義不僅文字流動方式中文字的項目，但幾乎每個其他流向[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目。 下圖顯示<xref:System.Windows.Controls.ToolBar>使用水平<xref:System.Windows.Media.LinearGradientBrush>正確的漸層繪製其背景以左。  

 ![顯示與左到右的漸層之工具列的圖形。](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 在設定之後<xref:System.Windows.FlowDirection>要<xref:System.Windows.FlowDirection.RightToLeft>，不只<xref:System.Windows.Controls.ToolBar>由右至左，但即使排列按鈕<xref:System.Windows.Media.LinearGradientBrush>會其位移來由右至左。  
  
 下圖顯示重新調配，集中<xref:System.Windows.Media.LinearGradientBrush>。  
    
 ![顯示工具列的圖形與由右至左的漸層。](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 下列範例會繪製<xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>。 (若要繪製左到右，移除<xref:System.Windows.FlowDirection>屬性上<xref:System.Windows.Controls.ToolBar>。  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection 例外狀況  
 有幾個情況其中<xref:System.Windows.FlowDirection>未如預期般運作。 本節涵蓋其中的兩個例外狀況。  
  
 **影像**  
  
 <xref:System.Windows.Controls.Image>代表顯示影像的控制項。 在 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]它可以搭配<xref:System.Windows.Controls.Image.Source%2A>屬性，定義[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]的<xref:System.Windows.Controls.Image>來顯示。  
  
 不同於其他[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目，<xref:System.Windows.Controls.Image>不會繼承<xref:System.Windows.FlowDirection>從容器。 不過，如果<xref:System.Windows.FlowDirection>明確設定為<xref:System.Windows.FlowDirection.RightToLeft>、<xref:System.Windows.Controls.Image>水平翻轉方式來顯示。 這會實作為方便使用的功能，讓開發人員用於雙向內容；因為在某些情況下，水平翻轉影像會產生所要的效果。  
  
 下圖顯示翻轉<xref:System.Windows.Controls.Image>。  
    
 ![說明已翻轉的影像的圖形。](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 下列範例示範<xref:System.Windows.Controls.Image>無法繼承<xref:System.Windows.FlowDirection>從<xref:System.Windows.Controls.StackPanel>包含它。 **附註**您必須擁有名為的檔案**ms_logo.jpg**在您的 C:\ 上若要執行此範例中的磁碟機。  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **附註**下載檔案中的包含已**ms_logo.jpg**檔案。 這個程式碼假設 .jpg 檔案不在您的專案內，而是在 C:\ 磁碟機的某個位置。 您必須將 .jpg 從專案檔複製至 C:\ 磁碟機，或變更程式碼來尋找專案內的檔案。 若要執行這項變更`Source="file://c:/ms_logo.jpg"`至`Source="ms_logo.jpg"`。  
  
 **路徑**  
  
 除了<xref:System.Windows.Controls.Image>，另一個有趣的項目是<xref:System.Windows.Shapes.Path>。 路徑是物件，可繪製一系列連接的線條和曲線。 它的行為類似<xref:System.Windows.Controls.Image>有關其<xref:System.Windows.FlowDirection>; 例如其<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>是水平鏡像其<xref:System.Windows.FlowDirection.LeftToRight>其中一個。 不過，不同於<xref:System.Windows.Controls.Image>，<xref:System.Windows.Shapes.Path>繼承其<xref:System.Windows.FlowDirection>從容器和一個不需要明確予以指定。  
  
 下列範例會繪製一個使用 3 條線的簡單箭號。 第一個箭號繼承<xref:System.Windows.FlowDirection.RightToLeft>資料流程方向從<xref:System.Windows.Controls.StackPanel>使其開始和結束點測量從右側的根。 具有明確的第二個箭號<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>也會啟動在右邊。 不過，第三個箭號的起始根在左邊。 如需有關繪圖，請參閱<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.GeometryGroup>。  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 下圖顯示上述範例的輸出使用繪製箭號`Path`項目：

 ![圖形，說明使用 Path 項目繪製箭號。](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 <xref:System.Windows.Controls.Image>並<xref:System.Windows.Shapes.Path>是兩個範例[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用<xref:System.Windows.FlowDirection>。 旁邊的版面配置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素在容器內，以特定方向<xref:System.Windows.FlowDirection>適用於項目這類<xref:System.Windows.Controls.InkPresenter>會呈現在介面上的筆墨<xref:System.Windows.Media.LinearGradientBrush>， <xref:System.Windows.Media.RadialGradientBrush>。 每當您正確的行為，模擬的內容需由右至左的行為，反之亦然，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供這項功能。  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>數字替代  
 在過去，[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]已藉由使用不同的文化特性形狀為相同數字表示，同時在不同的地區設定之間統一這些數字的內部儲存體範例數字會儲存在支援數字替代其已知十六進位值 0x40、 0x41，但根據選取的語言顯示。  
  
 此舉有助處理數值，而不需要將它們轉換成另一種語言的應用程式，例如使用者可以開啟[!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]試算表，在當地語系化的阿拉伯文[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]並查看以阿拉伯數字，形狀的數字，但中開啟歐洲版[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]並查看歐洲表示相同的數字。 針對逗號分隔符號和百分比符號這類其他符號，這也是必要的，因為在相同的文件中，它們通常會伴隨數字。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 會持續使用相同的傳統，並新增此替代的進一步支援，讓使用者更深入控制該何時和如何使用這項功能。 雖然這項功能設計用於任何語言，但特別適用於雙向內容，其中特定語言的成形數字通常會是應用程式開發人員的挑戰，因為應用程式可能會在各種文化特性中執行。  
  
 的運作方式的數字替代的核心屬性[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]是<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>相依性屬性。 <xref:System.Windows.Media.NumberSubstitution>類別可讓您指定要顯示的文字中的數字的方式。 它有三個定義其行為的公用屬性。 以下是每個屬性的摘要。  
  
 **CultureSource**：  
  
 這個屬性指定如何判斷數字的文化特性。 它會採用三個問題之一<xref:System.Windows.Media.NumberCultureSource>列舉值。  
  
- 覆寫：數字的文化特性就是<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>屬性。  
  
- 文字：數字文化特性為文字執行的文化特性。 在標記中，這會是`xml:lang`，或其別名`Language`屬性 (<xref:System.Windows.FrameworkElement.Language%2A>或<xref:System.Windows.FrameworkContentElement.Language%2A>)。 此外，它是衍生自的類別的預設值<xref:System.Windows.FrameworkContentElement>。 這類類別包括<xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>， <xref:System.Windows.Documents.Table?displayProperty=nameWithType>，<xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>等等。  
  
- 使用者: 數字文化特性是目前執行緒文化特性。 這個屬性是所有的子類別的預設值<xref:System.Windows.FrameworkElement>這類<xref:System.Windows.Controls.Page>，<xref:System.Windows.Window>和<xref:System.Windows.Controls.TextBlock>。  
  
 **CultureOverride**：  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>屬性時才使用<xref:System.Windows.Media.NumberSubstitution.CultureSource%2A>屬性設定為<xref:System.Windows.Media.NumberCultureSource.Override>否則會予以忽略。 它指定數字文化特性。 值為`null`，預設值會解譯為 EN-US。  
  
 **替代**：  
  
 這個屬性指定要執行的數字替代類型。 它會採用下列其中一種<xref:System.Windows.Media.NumberSubstitutionMethod>列舉值。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>：替代方法取決於數字的文化特性<xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType>屬性。 這是預設值。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>：如果數字的文化特性為阿拉伯文或波斯文文化特性，它會指定數字依賴內容。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.European>：數字永遠會轉譯為歐洲數字。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>：數字的轉譯國家數字用於數字的文化特性，所指定的文化特性的<xref:System.Globalization.CultureInfo.NumberFormat%2A>。  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>：使用傳統數字的數字的文化特性會呈現數字。 對於大部分的文化特性，這等同於<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>。 不過，<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>導致拉丁數字用於一些阿拉伯文文化特性，而這個值會導致阿拉伯數字用於所有阿拉伯文文化特性。  
  
 這些值對雙向內容開發人員的意義為何？ 在大部分情況下，開發人員可能只需要定義<xref:System.Windows.FlowDirection>及每個文字的語言[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目，例如`Language="ar-SA"`並<xref:System.Windows.Media.NumberSubstitution>邏輯會負責顯示根據正確的數字[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 下列範例示範如何使用阿拉伯和英文中的數字[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]阿拉伯文版本中執行的應用程式[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]。  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 如果您執行在阿拉伯文版的 Windows 中顯示的阿拉伯和英文數字與下圖會顯示先前範例的輸出：

 ![顯示阿拉伯和英文數字的圖形。](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 <xref:System.Windows.FlowDirection>很重要，在此情況下因為設定<xref:System.Windows.FlowDirection>到<xref:System.Windows.FlowDirection.LeftToRight>而是會產生歐洲數字。 下列各節討論如何統一顯示整個文件的數字。 如果此範例不是在阿拉伯文 Windows 上執行，則所有數字會顯示為歐洲數字。  
  
 **定義替代規則**  
  
 在實際的應用程式中，您可能需要以程式設計方式來設定語言。 例如，您要設定`xml:lang`屬性設為系統所使用的相同[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，或變更的語言取決於應用程式的狀態。  
  
 如果您想要變更根據應用程式的狀態，請使用所提供的其他功能[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  
  
 首先，設定應用程式元件的`NumberSubstitution.CultureSource="Text"`。 使用此設定可確保設定並非由[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]針對文字項目，具有 「 使用者 」 為預設值，例如<xref:System.Windows.Controls.TextBlock>。  
  
例如:   

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

在對應C#程式碼、 設定`Language`屬性，例如，若要`"ar-SA"`。  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

如果您需要設定`Language`目前使用者的 UI 語言的屬性使用下列程式碼。  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 代表由目前的執行緒在執行階段目前的文化特性。  
  
 您的最終[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]範例應該類似下列的範例。  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 您的最終C#範例應該類似下面的。  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 下圖顯示視窗的任一程式設計語言，顯示阿拉伯數字的外觀：
     
 ![顯示阿拉伯數字的圖形。](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **使用替代屬性**  
  
 在中的運作方式的數字的替代[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]取決於這兩種語言的文字項目及其<xref:System.Windows.FlowDirection>。 如果<xref:System.Windows.FlowDirection>由左到右，則會轉譯歐洲數字。 不過如果它加上阿拉伯文文字，或將語言設定為"ar"，<xref:System.Windows.FlowDirection>是<xref:System.Windows.FlowDirection.RightToLeft>，改為轉譯阿拉伯數字。  
  
 不過，在某些情況下，您可能想建立統一的應用程式，例如所有使用者都使用歐洲數字。 或在阿拉伯數字<xref:System.Windows.Documents.Table>與特定的資料格<xref:System.Windows.Style>。 一個簡單的方法是使用<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>屬性。  
  
 在下列範例中，第一個<xref:System.Windows.Controls.TextBlock>沒有<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>設定屬性，因此演算法會如預期般，顯示阿拉伯數字。 不過在第二個<xref:System.Windows.Controls.TextBlock>，替代會設定為 「 歐洲覆寫阿拉伯數字的預設替代，並顯示歐洲數字。  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
