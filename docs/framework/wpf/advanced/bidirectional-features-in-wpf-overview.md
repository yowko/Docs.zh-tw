---
title: "WPF 中的雙向功能概觀 | Microsoft Docs"
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
  - "雙向功能"
  - "FlowDirection 屬性"
  - "FlowDocument 屬性"
  - "Span 項目"
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# WPF 中的雙向功能概觀
和其他開發平台不同，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 具有許多功能可支援快速開發雙向 \(Bidirectional\) 內容，例如，在同一份文件中混合由左至右和由右至左的資料。  同時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 能替需要雙向功能的使用者 \(如說阿拉伯文和希伯來文的使用者\)，創造絕佳的經驗。  
  
 下列各節說明雙向功能，並提供用以說明如何達到雙向內容最佳顯示的範例。  大部分範例使用 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]，不過您可以輕易地將概念運用到 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 或 [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] 程式碼。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="FlowDirection"></a>   
## FlowDirection  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式中定義內容流向的基本屬性為 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。  這個屬性可用於設定下列其中一個列舉值：<xref:System.Windows.FlowDirection> 或 <xref:System.Windows.FlowDirection>。  此屬性可用於所有繼承自 <xref:System.Windows.FrameworkElement> 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目。  
  
 下列範例會設定 <xref:System.Windows.Controls.TextBox> 項目的流向。  
  
 **由左至右流向**  
  
 [!code-xml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **由右至左流向**  
  
 [!code-xml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 下圖顯示先前程式碼的呈現方式。  
  
 **說明 FlowDirection 的圖形**  
  
 ![TextBlock 對齊](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.png "LefttoRightRighttoLeft")  
  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 樹狀結構中的項目會從其容器 \(Container\) 繼承 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。  在下列範列中，<xref:System.Windows.Controls.TextBlock> 在 <xref:System.Windows.Controls.Grid> 之內，而 Grid 位於 <xref:System.Windows.Window> 中。  設定 <xref:System.Windows.Window> 的 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 意味同時針對 <xref:System.Windows.Controls.Grid> 和 <xref:System.Windows.Controls.TextBlock> 進行設定。  
  
 下列範例會示範如何設定 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。  
  
 [!code-xml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 最上層 <xref:System.Windows.Window> 具有 <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection>，所以其內含的所有項目也會繼承相同的 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。  至於要覆寫指定之 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 的項目，則必須加入明確的方向變更，例如前一個範例中的第二個 <xref:System.Windows.Controls.TextBlock> 會變更為 <xref:System.Windows.FlowDirection>。  未定義 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 的情況下，則會套用預設 <xref:System.Windows.FlowDirection>。  
  
 下圖顯示前一個範例的輸出。  
  
 **說明明確指定之 FlowDirection 的圖形**  
  
 ![文字顯示方向圖例](../../../../docs/framework/wpf/advanced/media/flowdir.png "FlowDir")  
  
<a name="FlowDocument"></a>   
## FlowDocument  
 許多開發平台 \(例如，[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 和 Java\) 都提供雙向內容開發的特殊支援。  [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 這類標記語言會將所需的標記提供給內容寫入器，以便以任何所需的方向顯示文字，以 [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 標記為例，"dir" 會採用 "rtl" 或 "ltr" 值。  這個標記類似於 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性，但 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性會以更進階個方式來配置文字內容，而且可用於文字以外的內容。  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，<xref:System.Windows.Documents.FlowDocument> 為多用途的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目，可以裝載 \(Host\) 文字、表格、影像和其他項目的組合。  下列各節中的範例會使用此項目。  
  
 有很多種方法可以將文字加入至 <xref:System.Windows.Documents.FlowDocument>。  其中一種簡單方法就是透過 <xref:System.Windows.Documents.Paragraph>，這是用於群組文字之類內容的區塊層級項目。  為了將文字加入至內嵌層級項目，範例會使用 <xref:System.Windows.Documents.Span> 和 <xref:System.Windows.Documents.Run>。  <xref:System.Windows.Documents.Span> 為內嵌層級非固定格式內容項目，適用於群組其他內嵌項目，而 <xref:System.Windows.Documents.Run> 則為內嵌層級非固定格式內容項目，主要用於包含一連串未格式化的文字。  <xref:System.Windows.Documents.Span> 可以包含多個 <xref:System.Windows.Documents.Run> 項目。  
  
 第一個文件範例所包含的文件具有許多網路共用名稱，例如 `\\server1\folder\file.ext`。  不論是在阿拉伯文或英文文件中有此網路連結，您都會希望該連結以相同的方式顯示。  下圖顯示在阿拉伯文 <xref:System.Windows.FlowDirection> 文件中的這個連結。  
  
 **說明如何使用 Span 項目的圖形**  
  
 ![文字顯示方向為由左至右的文件](../../../../docs/framework/wpf/advanced/media/flowdocument.png "FlowDocument")  
  
 因為文字是 <xref:System.Windows.FlowDirection>，所以 "\\" 之類的所有特殊字元都會以由右至左的順序分隔文字。  結果導致連結不是以正確的順序顯示，因此，若要解決此問題，就必須內嵌文字以保留個別的 <xref:System.Windows.Documents.Run> 流動 <xref:System.Windows.FlowDirection>。  除了讓每種語言具有個別的 <xref:System.Windows.Documents.Run> 以外，解決此問題的更好方法是將不常用的英文文字內嵌到較大的阿拉伯文 <xref:System.Windows.Documents.Span> 中。  
  
 下圖將說明這點。  
  
 **說明如何使用內嵌於 Span 項目中之 Run 項目的圖形**  
  
 ![XamlPad 螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/runspan.png "RunSpan")  
  
 下列範例會示範如何在文件中使用 <xref:System.Windows.Documents.Run> 和 <xref:System.Windows.Documents.Span> 項目。  
  
 [!code-xml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## Span 項目  
 <xref:System.Windows.Documents.Span> 項目的作用為具有不同流向的文字之間的界限分隔符號。  甚至具有相同流向的 <xref:System.Windows.Documents.Span> 項目都會被視為有不同雙向範圍，這表示 <xref:System.Windows.Documents.Span> 項目是以容器的 <xref:System.Windows.FlowDirection> 排序，而只有 <xref:System.Windows.Documents.Span> 項目內的內容會遵循 <xref:System.Windows.Documents.Span> 的 <xref:System.Windows.FlowDirection>。  
  
 下圖顯示數個 <xref:System.Windows.Controls.TextBlock> 項目的流向。  
  
 **說明數個 TextBlock 項目中之 FlowDirection 的圖形**  
  
 ![文字方向不同的文字區塊](../../../../docs/framework/wpf/advanced/media/span.png "Span")  
  
 下列範例顯示如何使用 <xref:System.Windows.Documents.Span> 和 <xref:System.Windows.Documents.Run> 項目，產生上圖所示的結果。  
  
 [!code-xml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 在本範例的 <xref:System.Windows.Controls.TextBlock> 項目中，<xref:System.Windows.Documents.Span> 項目會根據其父代 \(Parent\) 的 <xref:System.Windows.FlowDirection> 進行配置，但每個 <xref:System.Windows.Documents.Span> 項目內的文字則是根據其擁有的 <xref:System.Windows.FlowDirection> 而流動。  這適用於拉丁文和阿拉伯文 – 或任何其他語言。  
  
### 加入 xml:lang  
 下圖顯示另一個使用數字和算術運算式 \(如 `"200.0+21.4=221.4"`\) 的範例。  請注意，只會設定 <xref:System.Windows.FlowDirection>。  
  
 **僅使用 FlowDirection 顯示數字的圖形**  
  
 ![方向由右至左的數字](../../../../docs/framework/wpf/advanced/media/langattribute.png "LangAttribute")  
  
 即使 <xref:System.Windows.FlowDirection> 正確無誤，此應用程式的使用者將會對輸出感到失望，因為數字的外形並非阿拉伯數字應有的外形。  
  
 XAML 項目可以包含定義每個項目語言的 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 屬性 \(`xml:lang`\)。  XAML 也支援 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 語言主體，其中套用至樹狀結構中父項目的 `xml:lang` 值為子項目所使用。  在前一個範例中，因為未針對 <xref:System.Windows.Documents.Run> 項目或任何其最上層項目定義語言，所以會使用預設的 `xml:lang`，對於 XAML 就是 `en-US`。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的內部數字外形演算法會選取對應語言 \(在此例中為英文\) 中的數字。  若要使阿拉伯數字得以正確呈現，則必須設定 `xml:lang`。  
  
 下圖顯示加入 `xml:lang` 的範例。  
  
 **說明如何使用 xml:lang 屬性的圖形**  
  
 ![方向由右至左的阿拉伯數字](../../../../docs/framework/wpf/advanced/media/langattribute2.png "LangAttribute2")  
  
 下列範例會將 `xml:lang` 加入至應用程式。  
  
 [!code-xml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 請特別注意，許多語言會根據目標區域而定，而有不同的 `xml:lang` 值，例如 `"ar-SA"` 和 `"ar-EG"` 代表阿拉伯文的兩種變化。  先前範例說明您必須同時定義 `xml:lang` 和 <xref:System.Windows.FlowDirection> 值。  
  
<a name="FlowDirectionNontext"></a>   
## 非文字項目的 FlowDirection  
 <xref:System.Windows.FlowDirection> 不僅會定義文字項目中的文字流動方式，也會定義幾乎其他每個 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目的流動。  下圖所顯示的 <xref:System.Windows.Controls.ToolBar> 會使用水平 <xref:System.Windows.Media.LinearGradientBrush> 來繪製其背景。  
  
 **顯示具有由左至右漸層之 ToolBar 的圖形**  
  
 ![漸層螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/gradient.png "Gradient")  
  
 將 <xref:System.Windows.FlowDirection> 設為 <xref:System.Windows.FlowDirection> 之後，不僅 <xref:System.Windows.Controls.ToolBar> 按鈕會由右至左排列，甚至 <xref:System.Windows.Media.LinearGradientBrush> 也會重新對齊其位移 \(Offset\)，以便由右至左流動。  
  
 下圖顯示 <xref:System.Windows.Media.LinearGradientBrush> 的重新對齊方式。  
  
 **顯示具有由右至左漸層之 ToolBar 的圖形**  
  
 ![方向為由右至左的漸層](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.png "Gradient2\_WPF")  
  
 下列範例將繪製 <xref:System.Windows.FlowDirection> <xref:System.Windows.Controls.ToolBar>。  若要由左至右進行繪製，請移除 <xref:System.Windows.Controls.ToolBar> 的 <xref:System.Windows.FlowDirection> 屬性。  
  
 [!code-xml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### FlowDirection 例外狀況  
 在少數情況下，<xref:System.Windows.FlowDirection> 的行為不如預期。  本節涵蓋其中兩種例外狀況 \(Exception\)。  
  
 **Image**  
  
 <xref:System.Windows.Controls.Image> 表示會顯示影像的控制項。  在 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 中，它可搭配 <xref:System.Windows.Controls.Image.Source%2A> 屬性使用，該屬性會定義要顯示之 <xref:System.Windows.Controls.Image> 的[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。  
  
 和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目不同，<xref:System.Windows.Controls.Image> 不會從容器繼承 <xref:System.Windows.FlowDirection>。  但是，如果 <xref:System.Windows.FlowDirection> 已明確設定為 <xref:System.Windows.FlowDirection>，則 <xref:System.Windows.Controls.Image> 會以水平翻轉方式顯示。  雙向內容的開發人員會將此當做方便的功能實作，因為在某些情況下，水平翻轉影像可產生所要的效果。  
  
 下圖顯示已翻轉的 <xref:System.Windows.Controls.Image>。  
  
 **說明已翻轉影像的圖形**  
  
 ![XamlPad 螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/image.png "Image")  
  
 下列範例示範 <xref:System.Windows.Controls.Image> 無法從包含它的 <xref:System.Windows.Controls.StackPanel> 繼承 <xref:System.Windows.FlowDirection>。  **注意**：您的 C:\\ 磁碟機上必須要有名為 **ms\_logo.jpg** 的檔案，才能執行此範例。  
  
 [!code-xml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **注意**：下載的檔案中包括一個 **ms\_logo.jpg** 檔案。  程式碼會假定 .jpg 檔案不在您的專案中，但位在 C:\\ 磁碟機的某個位置。  您必須將專案檔案的 .jpg 複製至您的 C:\\ 磁碟機，或變更程式碼使其在專案中尋找。  若要這麼做，請將 `Source="file://c:/ms_logo.jpg"` 變更為 `Source="ms_logo.jpg"`。  
  
 **Path**  
  
 除了 <xref:System.Windows.Controls.Image> 以外，另一個有趣的項目為 <xref:System.Windows.Shapes.Path>。  Path 就是可以繪製一系列相連線條和曲線的物件。  至於其 <xref:System.Windows.FlowDirection> 的行為方式則類似於 <xref:System.Windows.Controls.Image>，例如它的 <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> 為其 <xref:System.Windows.FlowDirection> 流向的水平左右反轉。  但是，和 <xref:System.Windows.Controls.Image> 不同，<xref:System.Windows.Shapes.Path> 會從容器繼承它的 <xref:System.Windows.FlowDirection>，使用者不須進行明確指定。  
  
 下列範例會使用三條線來繪製簡單的箭號。  第一個箭號會從 <xref:System.Windows.Controls.StackPanel> 繼承 <xref:System.Windows.FlowDirection> 流向，以便從右邊的根測量其開始和結束點。  而具有明確 <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> 的第二個箭號也是從右邊開始。  但是，第三個箭號的起始根則在左邊。  如需繪圖的詳細資訊，請參閱 <xref:System.Windows.Media.LineGeometry> 和 <xref:System.Windows.Media.GeometryGroup>。  
  
 [!code-xml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 下圖顯示前一個範例的輸出。  
  
 **說明如何使用 Path 項目繪製箭號的圖形**  
  
 ![路徑](../../../../docs/framework/wpf/advanced/media/paths.png "Paths")  
  
 <xref:System.Windows.Controls.Image> 和 <xref:System.Windows.Shapes.Path> 為 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 如何使用 <xref:System.Windows.FlowDirection> 的兩個範例。  除了在容器內以特定方向配置 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目以外，<xref:System.Windows.FlowDirection> 可以搭配 <xref:System.Windows.Controls.InkPresenter> \(該項目可在表面上呈現筆跡\)、<xref:System.Windows.Media.LinearGradientBrush>、<xref:System.Windows.Media.RadialGradientBrush> 之類的項目使用。  每當模擬由左至右行為的內容需要由右至左行為時 \(反之亦然\)，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 都可提供該功能。  
  
<a name="NumberSubstitution"></a>   
## 數字替換  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 過去支援數字替換功能，其做法為允許相同的數字有不同的文化表示形式，並且使這些數字的內部儲存在不同的地區設定 \(Locale\) 內保持統一。例如：數字會以其知名的十六進位值 0x40、0x41 儲存，但會根據選取的語言予以顯示。  
  
 如此一來，應用程式不須將數值從某種語言轉換成另一種語言，便可處理數值。例如，使用者可以在當地語系化的阿拉文 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 中開啟 [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] 試算表，並且看見阿拉伯文形式的數字，但在歐語版的 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 中開啟試算表，卻會看見相同數字的歐語表示。  其他符號 \(如逗號分隔符號和百分比符號\) 也需要這項功能，因為這些符號通常會在同份文件中伴隨數字出現。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 延續了相同的傳統，並加入這項功能的進一步支援，而讓使用者更能夠掌控使用替換功能的時機和方式。  這項功能雖然是針對所有語言設計，但它卻特別適用於雙向內容。在雙向內容中，設計特定語言的數字外形通常是應用程式開發人員的一大挑戰，因為應用程式可能會在各種的文化特性 \(Culture\) 中執行。  
  
 控制如何在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中運用數字替換的核心屬性就是 <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> 相依性屬性。  <xref:System.Windows.Media.NumberSubstitution> 類別會指定文字中數字的顯示方式。  該類別有三個公用屬性可定義其行為。  以下是每個屬性的摘要。  
  
 **CultureSource：**  
  
 這個屬性可指定如何決定數字的文化特性。  它會採用三個 <xref:System.Windows.Media.NumberCultureSource> 列舉值的其中一個。  
  
-   覆寫：數字文化特性就是 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> 屬性的數字文化特性。  
  
-   文字：數字文化特性就是文字執行的文化特性。  在標記中，這會是 `xml:lang`，或其別名 `Language` 屬性 \(<xref:System.Windows.FrameworkElement.Language%2A> 或 <xref:System.Windows.FrameworkContentElement.Language%2A>\)。  此外，它也是衍生自 <xref:System.Windows.FrameworkContentElement> 之類別的預設值。  此種類別包含 <xref:System.Windows.Documents.Paragraph?displayProperty=fullName>、<xref:System.Windows.Documents.Table?displayProperty=fullName>、<xref:System.Windows.Documents.TableCell?displayProperty=fullName> 等。  
  
-   使用者：數字文化特性就是目前執行緒的文化特性。  此屬性為 <xref:System.Windows.FrameworkElement> 之所有子類別 \(如 <xref:System.Windows.Controls.Page>、<xref:System.Windows.Window> 和 <xref:System.Windows.Controls.TextBlock>\) 的預設值。  
  
 **CultureOverride**：  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> 屬性設為 <xref:System.Windows.Media.NumberCultureSource> 時，才會使用 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> 屬性，否則會予以忽略。  該屬性可指定數字文化特性。  值為 `null` \(預設值\) 會解譯為 en\-US。  
  
 **Substitution**：  
  
 這個屬性會指定要執行的數字替換類型。  它會採用下列其中一個 <xref:System.Windows.Media.NumberSubstitutionMethod> 列舉值。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>：替換方法是根據數字文化特定的 <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=fullName> 屬性決定。  這是預設值。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>：如果數字文化特性為阿拉伯或波斯文化特性，則會指定數字需視內容而定。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>：數字一律呈現為歐語數字。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>：使用國際數字的數字文化特性來呈現數字，如同文化特性的 <xref:System.Globalization.CultureInfo.NumberFormat%2A> 所指定。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>：使用傳統數字的數字文化特性來呈現數字。  對大多數的文化特性來說，這與 <xref:System.Windows.Media.NumberSubstitutionMethod> 相同。  不過，<xref:System.Windows.Media.NumberSubstitutionMethod> 會在某些阿拉伯文化特性中呈現拉丁數字，然而此值會在所有的阿拉伯文化特性中呈現阿拉伯數字。  
  
 這些值對雙向內容開發人員而言有何意義？  在大部分情況下，開發人員可能只需要定義每個文字 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目的 <xref:System.Windows.FlowDirection> 和語言，例如 `Language="ar-SA"`，而 <xref:System.Windows.Media.NumberSubstitution> 邏輯會根據正確的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 負責顯示數字。  下列範例會示範如何在執行於 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 阿拉伯文版的 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中使用阿拉伯和英文數字。  
  
 [!code-xml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 如果您是在 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 阿拉伯文版中執行，下圖會顯示前一個範例的輸出。  
  
 **顯示阿拉伯和英文數字的圖形**  
  
 ![顯示數字的 XamlPad 螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/numbers.png "Numbers")  
  
 在此情況下 <xref:System.Windows.FlowDirection> 很重要，因為將 <xref:System.Windows.FlowDirection> 改設為 <xref:System.Windows.FlowDirection> 會產生歐語數字。  下列各節討論如何讓整份文件中的數字有統一的顯示方式。  如果這個範例不是在 Windows 阿拉伯文版上執行，則所有數字都會顯示為歐語數字。  
  
 **定義替換規則**  
  
 在真正的應用程式中，您可能需要以程式設計的方式設定語言。  例如，您想要將 `xml:lang` 屬性設為與系統 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 所用的屬性相同，或者也可以根據應用程式狀態變更語言。  
  
 如果您想根據應用程式的狀態進行變更，請使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 所提供的其他功能。  
  
 首先，設定應用程式元件的 `NumberSubstitution.CultureSource="Text"`。  使用此設定可確保設定並非來自以「使用者」做為預設值之文字項目 \(如 <xref:System.Windows.Controls.TextBlock>\) 的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
 例如：  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 例如，在對應的 [!INCLUDE[TLA2#tla_lhcshrp](../../../../includes/tla2sharptla-lhcshrp-md.md)] 程式碼中，將 `Language` 屬性設為 `"ar-SA"`。  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 如果您需要將 `Language` 屬性設為目前使用者的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 語言，請使用下列程式碼。  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 表示目前執行緒在執行階段使用的目前文化特性。  
  
 您最後的 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 範例應該類似下列範例。  
  
 [!code-xml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 您最後的 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 範例應該類似下列範例。  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 下圖顯示各程式設計語言的視窗外觀。  
  
 **顯示阿拉伯數字的圖形**  
  
 ![阿拉伯數字](../../../../docs/framework/wpf/advanced/media/numbers2.png "Numbers2")  
  
 **使用 Substitution 屬性**  
  
 數字替換在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的運作方式，會取決於文字項目的語言與其 <xref:System.Windows.FlowDirection>。  如果 <xref:System.Windows.FlowDirection> 為由左至右，則會呈現歐語數字。  但是，如果數字前面接著阿拉伯文字，或語言設定為 "ar" 且 <xref:System.Windows.FlowDirection> 為 <xref:System.Windows.FlowDirection>，則會改為呈現阿拉伯數字。  
  
 然而，在某些情況下，您可能想建立統一的應用程式，例如：所有使用者都適用歐語數字。  或者，<xref:System.Windows.Documents.Table> 儲存格中的阿拉伯數字具有特定 <xref:System.Windows.Style>。  使用 <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> 屬性，便可輕易達成。  
  
 在下列範例中，第一個 <xref:System.Windows.Controls.TextBlock> 尚未設定 <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> 屬性，所以演算法會如預期顯示阿拉伯數字。  然而，在第二個 <xref:System.Windows.Controls.TextBlock> 中，替換功能設定為歐語覆寫阿拉伯數字的預設替換，所以會顯示歐語數字。  
  
 [!code-xml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]