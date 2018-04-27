---
title: WPF 中的雙向功能概觀
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa2349bca86676f4dc3e1703216a2b0dc50ccd59
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF 中的雙向功能概觀
不同於其他任何開發平台，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有許多功能可支援快速開發雙向內容，以滑鼠右鍵，並以滑鼠右鍵來混合的左比方說，資料處於相同文件。 同時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]建立需要雙向功能，如阿拉伯文與希伯來文讀出使用者之使用者的絕佳的體驗。  
  
 下列各節說明許多雙向功能以及說明如何達到最佳雙向內容顯示的範例。 大部分的範例使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]，但是您可以輕鬆地套用至 C# 或 Microsoft Visual Basic 程式碼的概念。  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 基本的屬性，定義中的內容流向[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式是<xref:System.Windows.FrameworkElement.FlowDirection%2A>。 這個屬性可以設定為其中一個列舉值，<xref:System.Windows.FlowDirection.LeftToRight>或<xref:System.Windows.FlowDirection.RightToLeft>。 屬性是可供所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]繼承的項目<xref:System.Windows.FrameworkElement>。  
  
 下列範例會設定文字方向的<xref:System.Windows.Controls.TextBox>項目。  
  
 **由左至右的流向**  
  
 [!code-xaml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **由右至左的流向**  
  
 [!code-xaml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 下圖顯示如何轉譯先前的程式碼。  
  
 **說明 FlowDirection 的圖形**  
  
 ![TextBlock 對齊](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.PNG "LefttoRightRighttoLeft")  
  
 中的項目[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]樹狀結構會繼承<xref:System.Windows.FrameworkElement.FlowDirection%2A>從它的容器。 在下列範例中，<xref:System.Windows.Controls.TextBlock>位於<xref:System.Windows.Controls.Grid>，其位於<xref:System.Windows.Window>。 設定<xref:System.Windows.FrameworkElement.FlowDirection%2A>如<xref:System.Windows.Window>隱含設定為<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Controls.TextBlock>以及。  
  
 下列範例會示範設定<xref:System.Windows.FrameworkElement.FlowDirection%2A>。  
  
 [!code-xaml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 最上層<xref:System.Windows.Window>具有<xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>，因此也包含在其中的所有項目會繼承相同<xref:System.Windows.FrameworkElement.FlowDirection%2A>。 若要覆寫指定的項目<xref:System.Windows.FrameworkElement.FlowDirection%2A>它必須加入明確的方向變更例如第二個<xref:System.Windows.Controls.TextBlock>在上述範例變更為<xref:System.Windows.FlowDirection.LeftToRight>。 若未<xref:System.Windows.FrameworkElement.FlowDirection%2A>定義，則預設<xref:System.Windows.FlowDirection.LeftToRight>套用。  
  
 下圖顯示上述範例的輸出。  
  
 **說明明確指派之 FlowDirection 的圖形**  
  
 ![向圖例](../../../../docs/framework/wpf/advanced/media/flowdir.PNG "FlowDir")  
  
<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 例如，許多開發平台[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]，[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]和 Java 提供特殊支援雙向內容開發。 標記語言，例如[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]提供必要的標記任何必要的方向，例如顯示的文字內容的寫入器[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]4.0 標記、"dir"做為值採用"rtl"或"ltr"。 此標記是類似於<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性，但<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性適用於更進階的方式配置的文字內容，並可用於文字以外的內容。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Documents.FlowDocument>用途多[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]可裝載的文字、 表格、 影像和其他項目組合項目。 下列各節中的範例會使用這個項目。  
  
 新增文字至<xref:System.Windows.Documents.FlowDocument>可以完成多一個方式。 若要這樣做的簡單方式是透過<xref:System.Windows.Documents.Paragraph>這是用來群組內容，例如文字區塊層級項目。 若要將文字加入內嵌層級元素的範例使用<xref:System.Windows.Documents.Span>和<xref:System.Windows.Documents.Run>。 <xref:System.Windows.Documents.Span> 是內嵌層級流動內容項目用於群組其他內嵌項目，雖然<xref:System.Windows.Documents.Run>是內嵌層級動態內容項目要用來包含執行的未格式化的文字。 A<xref:System.Windows.Documents.Span>可以包含多個<xref:System.Windows.Documents.Run>項目。  
  
 第一個文件的範例包含文件編號的網路共用的名稱;例如`\\server1\folder\file.ext`。 不論此網路連結出現在阿拉伯文文件還是英文文件中，您一定都會想要以相同的方式來顯示它。 下圖顯示連結阿拉伯<xref:System.Windows.FlowDirection.RightToLeft>文件。  
  
 **說明使用 Span 項目的圖形**  
  
 ![流向為由右至左的文件](../../../../docs/framework/wpf/advanced/media/flowdocument.PNG "FlowDocument")  
  
 因為文字是<xref:System.Windows.FlowDirection.RightToLeft>、 所有特殊字元，例如"\\"，區隔由右至左的順序中的文字。 這樣會造成不正確的順序顯示的連結，因此若要解決此問題，文字必須內嵌保留個別<xref:System.Windows.Documents.Run>流動<xref:System.Windows.FlowDirection.LeftToRight>。 而不需要個別<xref:System.Windows.Documents.Run>每種語言，更好的方法，以解決此問題是較不常用的英文字嵌入較大阿拉伯文<xref:System.Windows.Documents.Span>。  
  
 下圖說明這個程序。  
  
 **說明使用內嵌在 Span 項目之 Run 項目的圖形**  
  
 ![XamlPad 螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/runspan.PNG "RunSpan")  
  
 下列範例示範如何使用<xref:System.Windows.Documents.Run>和<xref:System.Windows.Documents.Span>文件中的項目。  
  
 [!code-xaml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span 項目  
 <xref:System.Windows.Documents.Span>項目的運作方式為界限之間的分隔符號文字方向不同。  即使<xref:System.Windows.Documents.Span>具有相同的文字方向的項目都會被視為具有不同的雙向領域，這表示<xref:System.Windows.Documents.Span>中容器的排序項目<xref:System.Windows.FlowDirection>中的內容<xref:System.Windows.Documents.Span>項目遵循<xref:System.Windows.FlowDirection>的<xref:System.Windows.Documents.Span>。  
  
 下圖顯示數個流向<xref:System.Windows.Controls.TextBlock>項目。  
  
 **說明數個 TextBlock 項目中 FlowDirection 的圖形**  
  
 ![向不同的文字區塊](../../../../docs/framework/wpf/advanced/media/span.PNG "Span")  
  
 下列範例示範如何使用<xref:System.Windows.Documents.Span>和<xref:System.Windows.Documents.Run>元素來產生結果前圖所示。  
  
 [!code-xaml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 在<xref:System.Windows.Controls.TextBlock>在範例中，項目<xref:System.Windows.Documents.Span>元素配置時根據<xref:System.Windows.FlowDirection>其父系，但在每個文字<xref:System.Windows.Documents.Span>根據自己的項目流程<xref:System.Windows.FlowDirection>。 這適用於拉丁文和阿拉伯文，或任何其他語言。  
  
### <a name="adding-xmllang"></a>新增 xml:lang  
 下圖顯示另一個範例使用數字和算術運算式，例如`"200.0+21.4=221.4"`。 請注意，只有<xref:System.Windows.FlowDirection>設定。  
  
 **顯示只使用 FlowDirection 之數字的圖形**  
  
 ![向由右至左的數字](../../../../docs/framework/wpf/advanced/media/langattribute.PNG "LangAttribute")  
  
 此應用程式的使用者將會失望輸出，即使<xref:System.Windows.FlowDirection>正確數字不應該形狀阿拉伯數字為形狀。  
  
 將 XAML 項目可以包含[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]屬性 (`xml:lang`)，定義每個項目的語言。 也支援 XAML[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]語言原則讓`xml:lang`套用到在樹狀目錄中的父項目值由子元素。 在上述範例中，因為語言不定義為<xref:System.Windows.Documents.Run>項目或任何它上方層級項目，預設值`xml:lang`被使用，也就是`en-US`xaml。 內部數字成形演算法的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]選取數字中的對應語言 – 在此情況下英文。 若要讓阿拉伯數字呈現正確`xml:lang`必須設定。  
  
 下圖顯示範例`xml:lang`加入。  
  
 **說明使用 xml:lang 屬性的圖形**  
  
 ![向由右至左的阿拉伯數字](../../../../docs/framework/wpf/advanced/media/langattribute2.PNG "LangAttribute2")  
  
 下列範例會將`xml:lang`應用程式。  
  
 [!code-xaml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 請注意，許多語言有不同`xml:lang`值的目標地區，例如，根據`"ar-SA"`和`"ar-EG"`代表阿拉伯文的兩種變化。 先前的範例將說明您需要同時定義`xml:lang`和<xref:System.Windows.FlowDirection>值。  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>具有非文字項目的 FlowDirection  
 <xref:System.Windows.FlowDirection> 定義不僅文字流動的方式在文字項目，但是幾乎每個其他的流向[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目。 下圖顯示<xref:System.Windows.Controls.ToolBar>使用水平<xref:System.Windows.Media.LinearGradientBrush>繪製它的背景。  
  
 **顯示具有由左至右漸層之工具列的圖形**  
  
 ![漸層螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/gradient.PNG "Gradient")  
  
 設定之後<xref:System.Windows.FlowDirection>至<xref:System.Windows.FlowDirection.RightToLeft>，不只<xref:System.Windows.Controls.ToolBar>從右至左，但即使排列按鈕<xref:System.Windows.Media.LinearGradientBrush>方向上重新對齊方向由右至左的位移。  
  
 下圖顯示對齊<xref:System.Windows.Media.LinearGradientBrush>。  
  
 **顯示具有由右至左漸層之工具列的圖形**  
  
 ![向由右至左的漸層](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.PNG "Gradient2_WPF")  
  
 下列範例會繪製<xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>。 (若要繪製左到右，移除<xref:System.Windows.FlowDirection>屬性<xref:System.Windows.Controls.ToolBar>。  
  
 [!code-xaml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection 例外狀況  
 少數的情況下其中<xref:System.Windows.FlowDirection>未如預期般運作。 本節涵蓋其中的兩個例外狀況。  
  
 **影像**  
  
 <xref:System.Windows.Controls.Image>代表顯示影像的控制項。 在[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]它可以搭配<xref:System.Windows.Controls.Image.Source%2A>屬性，定義[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]的<xref:System.Windows.Controls.Image>顯示。  
  
 不同於其他[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目，<xref:System.Windows.Controls.Image>不會繼承<xref:System.Windows.FlowDirection>從容器。 不過，如果<xref:System.Windows.FlowDirection>明確設定為<xref:System.Windows.FlowDirection.RightToLeft>、<xref:System.Windows.Controls.Image>會顯示水平翻轉。 這會實作為方便使用的功能，讓開發人員用於雙向內容；因為在某些情況下，水平翻轉影像會產生所要的效果。  
  
 下圖顯示翻轉<xref:System.Windows.Controls.Image>。  
  
 **說明已翻轉影像的圖形**  
  
 ![XamlPad 螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/image.PNG "Image")  
  
 下列範例會示範<xref:System.Windows.Controls.Image>無法繼承<xref:System.Windows.FlowDirection>從<xref:System.Windows.Controls.StackPanel>包含它。 **請注意**您必須擁有名為**ms_logo.jpg** C:\ 磁碟機執行此範例。  
  
 [!code-xaml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **請注意**包含在下載檔案是**ms_logo.jpg**檔案。 這個程式碼假設 .jpg 檔案不在您的專案內，而是在 C:\ 磁碟機的某個位置。 您必須將 .jpg 從專案檔複製至 C:\ 磁碟機，或變更程式碼來尋找專案內的檔案。 若要執行這項變更`Source="file://c:/ms_logo.jpg"`至`Source="ms_logo.jpg"`。  
  
 **路徑**  
  
 除了<xref:System.Windows.Controls.Image>，另一個有趣的項目是<xref:System.Windows.Shapes.Path>。 路徑是物件，可繪製一系列連接的線條和曲線。 其行為類似的方式<xref:System.Windows.Controls.Image>有關其<xref:System.Windows.FlowDirection>; 例如其<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>是水平的鏡像其<xref:System.Windows.FlowDirection.LeftToRight>其中一個。 不過，不同於<xref:System.Windows.Controls.Image>，<xref:System.Windows.Shapes.Path>繼承其<xref:System.Windows.FlowDirection>從容器，另一個不需要明確指定。  
  
 下列範例會繪製一個使用 3 條線的簡單箭號。 第一個箭號會繼承<xref:System.Windows.FlowDirection.RightToLeft>資料流程方向從<xref:System.Windows.Controls.StackPanel>使其開始和結束點起右邊的根。 具有明確的第二個箭頭<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>也會啟動在右邊。 不過，第三個箭號的起始根在左邊。 如需有關繪製，請參閱<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.GeometryGroup>。  
  
 [!code-xaml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 下圖顯示上述範例的輸出。  
  
 **說明使用 Path 項目所繪製箭號的圖形**  
  
 ![路徑](../../../../docs/framework/wpf/advanced/media/paths.PNG "Paths")  
  
 <xref:System.Windows.Controls.Image>和<xref:System.Windows.Shapes.Path>兩個範例說明如何[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用<xref:System.Windows.FlowDirection>。 旁邊的版面配置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]依特定方向的容器中的項目<xref:System.Windows.FlowDirection>適用於項目例如<xref:System.Windows.Controls.InkPresenter>的呈現表面的筆墨<xref:System.Windows.Media.LinearGradientBrush>， <xref:System.Windows.Media.RadialGradientBrush>。 每當您需要由右至左的行為，為您的內容，以模擬左到右的行為，或反之亦然，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供這項功能。  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>數字替代  
 在過去，[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]已藉由使用相同的數字不同文化特性的圖形表示法同時保護內部的儲存體整合之間不同的地區設定，這些數字的範例數字會儲存在支援的數字替代其已知十六進位值，0x40、 0x41，但根據選取的語言顯示。  
  
 這有允許的應用程式處理而不需要從一種語言轉換成另一個數值，例如使用者可以開啟[!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]試算表中當地語系化阿拉伯文[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]和看到形狀以阿拉伯數字，數字，但在中開啟它歐洲版本[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]並查看相同的數字的歐洲的表示法。 針對逗號分隔符號和百分比符號這類其他符號，這也是必要的，因為在相同的文件中，它們通常會伴隨數字。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 會持續使用相同的傳統，並新增此替代的進一步支援，讓使用者更深入控制該何時和如何使用這項功能。 雖然這項功能設計用於任何語言，但特別適用於雙向內容，其中特定語言的成形數字通常會是應用程式開發人員的挑戰，因為應用程式可能會在各種文化特性中執行。  
  
 控制如何數字替代的核心屬性適用於[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]是<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>相依性屬性。 <xref:System.Windows.Media.NumberSubstitution>類別會指定要顯示的文字中的數字的方式。 它有三個定義其行為的公用屬性。 以下是每個屬性的摘要。  
  
 **CultureSource**：  
  
 這個屬性指定如何判斷數字的文化特性。 它會使用其中一個三個<xref:System.Windows.Media.NumberCultureSource>列舉值。  
  
-   覆寫： 數字文化特性是屬於<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>屬性。  
  
-   文字︰數字文化特性是文字執行的文化特性。 在標記中，這會是`xml:lang`，或其別名`Language`屬性 (<xref:System.Windows.FrameworkElement.Language%2A>或<xref:System.Windows.FrameworkContentElement.Language%2A>)。 此外，它是衍生自類別的預設值<xref:System.Windows.FrameworkContentElement>。 這類類別都包括<xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>， <xref:System.Windows.Documents.Table?displayProperty=nameWithType>，<xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>等等。  
  
-   使用者︰數字文化特性是目前執行緒的文化特性。 這個屬性是所有的子類別的預設值<xref:System.Windows.FrameworkElement>例如<xref:System.Windows.Controls.Page>，<xref:System.Windows.Window>和<xref:System.Windows.Controls.TextBlock>。  
  
 **CultureOverride**：  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>屬性只使用<xref:System.Windows.Media.NumberSubstitution.CultureSource%2A>屬性設定為<xref:System.Windows.Media.NumberCultureSource.Override>，否則會被忽略。 它指定數字文化特性。 值為`null`，預設值，會解譯為 EN-US。  
  
 **替代**：  
  
 這個屬性指定要執行的數字替代類型。 它會採用下列其中一種<xref:System.Windows.Media.NumberSubstitutionMethod>列舉值。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>： 的替代方法取決於數字的文化特性<xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType>屬性。 這是預設值。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>： 如果數字的文化特性為阿拉伯文或波斯文文化特性，它會指定數字取決的內容。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>： 數字永遠會轉譯為歐洲的數字。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>： 使用國家 （地區） 的數字的數字的文化特性的文化特性所指定的轉譯數字<xref:System.Globalization.CultureInfo.NumberFormat%2A>。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>： 數字會轉譯使用傳統的位數的數字的文化特性。 對於大部分的文化特性，這等同於<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>。 不過，<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>導致某些阿拉伯文的文化特性的拉丁文數字，而這個值會導致所有阿拉伯文文化特性的阿拉伯數字。  
  
 這些值對雙向內容開發人員的意義為何？ 在大部分情況下，開發人員可能需要只定義<xref:System.Windows.FlowDirection>每個文字的語言及[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目，例如`Language="ar-SA"`和<xref:System.Windows.Media.NumberSubstitution>邏輯會負責顯示根據正確的數字[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 下列範例示範如何使用阿拉伯文和英文中的數字[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]阿拉伯文版本中執行的應用程式[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]。  
  
 [!code-xaml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 下圖顯示先前範例的輸出，如果您正在使用阿拉伯文的版本[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]。  
  
 **顯示其中顯示阿拉伯和英文數字的圖形**  
  
 ![顯示數字的 XamlPad 螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/numbers.PNG "Numbers")  
  
 <xref:System.Windows.FlowDirection>是非常重要的在此情況下設定因為<xref:System.Windows.FlowDirection>至<xref:System.Windows.FlowDirection.LeftToRight>而是會產生歐洲的數字。 下列各節討論如何統一顯示整個文件的數字。 如果此範例不是在阿拉伯文 Windows 上執行，則所有數字會顯示為歐洲數字。  
  
 **定義替代規則**  
  
 在實際的應用程式中，您可能需要以程式設計方式來設定語言。 例如，您要設定`xml:lang`系統所使用的相同屬性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，或可能已經變更的語言，根據應用程式狀態。  
  
 如果您想要變更根據應用程式的狀態，請使用所提供的其他功能[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  
  
 首先，設定應用程式元件的`NumberSubstitution.CultureSource="Text"`。 使用這項設定可確保該設定不是來自[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]文字項目，具有 「 使用者 」 做為預設值，例如<xref:System.Windows.Controls.TextBlock>。  
  
 例如:   
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 在對應的 C# 程式碼，設定`Language`屬性例如，若要`"ar-SA"`。  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 如果您需要設定`Language`屬性目前的使用者[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]使用下列程式碼的語言。  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 表示目前在執行階段目前的執行緒所使用的文化特性。  
  
 最終[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]範例應該類似下列的範例。  
  
 [!code-xaml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 您最後一個 C# 範例應如下所示。  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 下圖顯示任一程式設計語言之視窗的外觀。  
  
 **顯示阿拉伯數字的圖形**  
  
 ![阿拉伯數字](../../../../docs/framework/wpf/advanced/media/numbers2.PNG "Numbers2")  
  
 **使用替代屬性**  
  
 在中的運作方式數字的替代[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]取決於這兩種語言的文字項目和其<xref:System.Windows.FlowDirection>。 如果<xref:System.Windows.FlowDirection>由左到右，然後呈現歐洲的數字。 不過如果它前面阿拉伯文文字，或語言設定為"ar"和<xref:System.Windows.FlowDirection>是<xref:System.Windows.FlowDirection.RightToLeft>，改為呈現阿拉伯數字。  
  
 不過，在某些情況下，您可能想建立統一的應用程式，例如所有使用者都使用歐洲數字。 阿拉伯數字或者<xref:System.Windows.Documents.Table>具有特定的資料格<xref:System.Windows.Style>。 一個簡單的方法是使用<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>屬性。  
  
 在下列範例中，第一個<xref:System.Windows.Controls.TextBlock>沒有<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>設定屬性，因此演算法會如預期般，顯示阿拉伯數字。 不過，第二個<xref:System.Windows.Controls.TextBlock>、 替代設為歐洲覆寫預設替代的阿拉伯數字，且顯示歐洲的數字。  
  
 [!code-xaml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
