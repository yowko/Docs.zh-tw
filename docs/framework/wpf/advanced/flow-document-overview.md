---
title: "非固定格式文件概觀 | Microsoft Docs"
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
  - "內容結構描述"
  - "文件, 非固定格式文件"
  - "非固定格式內容項目 [WPF], 非固定格式文件"
  - "非固定格式文件"
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
caps.latest.revision: 39
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# 非固定格式文件概觀
非固定格式文件 \(Flow Document\) 是設計來最佳化檢視和可讀性。  非固定格式文件並不會設為某種預先定義的配置，而是會根據執行階段變數 \(如視窗大小、裝置解析度和選擇性的使用者偏好設定\)，動態調整及重新排列其內容。  此外，非固定格式文件提供進階的文件功能，例如分頁和欄位。  本主題提供非固定格式文件的概觀及建立的方式。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="what_is_a_flow_document"></a>   
## 什麼是非固定格式文件  
 非固定格式文件可以根據視窗大小、裝置解析度及其他環境變數來「重新排列內容」。  此外，非固定格式文件具備許多內建功能，包括搜尋、將可讀性最佳化的檢視模式，以及變更字型大小與外觀的能力。  當文件使用上的主要考量是容易閱讀的時候，利用非固定格式文件是最好的方法。  相反地，固定格式文件是針對靜態展示設計。  固定格式文件在必須精確呈現來源內容時相當有用。  如需不同類型文件的詳細資訊，請參閱 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)。  
  
 下圖顯示在數種不同大小的視窗中檢視的非固定格式文件範例。  當顯示區域變更時，內容就會重新排列以運用可用的空間。  
  
 ![非固定格式文件內容重新排列](../../../../docs/framework/wpf/advanced/media/edocs-flowdocument.png "eDocs\_FlowDocument")  
  
 如同上圖所示，非固定格式內容可以包含許多元件，包括段落、清單、影像等等。  這些元件對應至標記 \(Markup\) 中的項目及程式碼中的物件。  我們稍後會在這篇簡介[非固定格式相關類別](#flow_related_classes)章節中詳細說明這些類別。  現在，請先參考這個簡單的程式碼範例，它會建立非固定格式文件，其中含有一個具部分粗體字的段落和一份清單。  
  
 [!code-xml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 下圖顯示這個程式碼片段的外觀。  
  
 ![螢幕擷取畫面：呈現的 FlowDocument 範例](../../../../docs/framework/wpf/advanced/media/flow-ovw-first-example.png "Flow\_Ovw\_First\_Example")  
  
 在這個範例中，<xref:System.Windows.Controls.FlowDocumentReader> 控制項是用於裝載非固定格式文件。  如需非固定格式文件裝載控制項的詳細資訊，請參閱[非固定格式文件類型](#flow_document_types)。  <xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.List>、<xref:System.Windows.Documents.ListItem> 及 <xref:System.Windows.Documents.Bold> 項目根據它們在標記 \(Markup\) 中的順序，來調整內容的顯示格式。  例如，<xref:System.Windows.Documents.Bold> 項目只包住段落中的部分文字，結果就只有這部分的文字會呈現粗體。  如果您使用過 HTML，對這一點應該相當熟悉。  
  
 如同在上圖中所強調的，非固定格式文件中有許多內建功能：  
  
-   搜尋：讓使用者對整份文件執行全文檢索搜尋。  
  
-   檢視模式：使用者可以選取偏好的檢視模式，包括單頁 \(一次顯示一頁\) 檢視模式、雙頁 \(書本閱讀格式\) 檢視模式，以及連續捲動 \(無底邊\) 檢視模式。  如需這些檢視模式的詳細資訊，請參閱 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>。  
  
-   頁面巡覽控制項：如果文件的檢視模式使用頁面，頁面巡覽控制項會包含可跳到下一頁 \(向下箭號\) 或上一頁 \(向上箭號\) 的按鈕，以及顯示目前頁碼與總頁數的指示區。  翻頁的動作也可以使用鍵盤方向鍵來完成。  
  
-   縮放：縮放控制項可讓使用者按下加號或減號按鈕來增加或減少縮放層級。  縮放控制項也包含可用於調整縮放層級的滑桿。  如需詳細資訊，請參閱 <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>。  
  
 這些功能可以根據用於裝載非固定格式內容的控制項來修改。  下一節會說明其他控制項。  
  
<a name="flow_document_types"></a>   
## 非固定格式文件類型  
 非固定格式文件內容的顯示和出現方式，取決於用來裝載非固定格式內容的物件。  有四個控制項支援檢視非固定格式內容：<xref:System.Windows.Controls.FlowDocumentReader>、<xref:System.Windows.Controls.FlowDocumentPageViewer>、<xref:System.Windows.Controls.RichTextBox> 及 <xref:System.Windows.Controls.FlowDocumentScrollViewer>。  這些控制項的簡略說明如下。  
  
 **注意**：直接裝載非固定格式內容時需要 <xref:System.Windows.Documents.FlowDocument>，所以所有檢視控制項都會使用 <xref:System.Windows.Documents.FlowDocument> 裝載非固定格式內容。  
  
### FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> 包含可讓使用者動態選擇各種檢視模式的功能，包括單頁 \(一次顯示一頁\) 檢視模式、雙頁 \(書本閱讀格式\) 檢視模式，以及連續捲動 \(無底邊\) 檢視模式。  如需這些檢視模式的詳細資訊，請參閱 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>。  如果您不需要動態切換不同檢視模式的功能，則 <xref:System.Windows.Controls.FlowDocumentPageViewer> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 可提供較輕量的非固定格式內容檢視器，這兩種會固定使用特定的檢視模式。  
  
### FlowDocumentPageViewer 和 FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> 會以一次顯示一頁的檢視模式顯示內容，而 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 會以連續捲動模式顯示內容。  <xref:System.Windows.Controls.FlowDocumentPageViewer> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 都有固定的特定檢視模式。  相較之下，<xref:System.Windows.Controls.FlowDocumentReader> 包含的功能可讓使用者動態選擇各種檢視模式 \(如 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> 列舉型別所提供\)，但代價是比 <xref:System.Windows.Controls.FlowDocumentPageViewer> 或 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 需要更多資源。  
  
 預設一定會顯示垂直捲軸，而水平捲動會視需要顯示。  <xref:System.Windows.Controls.FlowDocumentScrollViewer> 的預設 UI 不包含工具列，不過，您可以使用 <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> 屬性啟用內建工具列。  
  
### RichTextBox  
 當您要讓使用者編輯非固定格式內容時，使用 <xref:System.Windows.Controls.RichTextBox>。  例如，如果您要建立編輯器，讓使用者管理像是表格、斜體或粗體格式等等項目，請使用 <xref:System.Windows.Controls.RichTextBox>。  如需詳細資訊，請參閱 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)。  
  
 **注意**：<xref:System.Windows.Controls.RichTextBox> 內的非固定格式內容展現的行為與其他控制項中的非固定格式內容不完全相同。  例如，<xref:System.Windows.Controls.RichTextBox> 中並沒有欄位，因此不會有自動調整大小的行為。  此外，<xref:System.Windows.Controls.RichTextBox> 內沒有非固定格式內容的典型內建功能，例如搜尋、檢視模式、頁面巡覽及縮放等等。  
  
<a name="creating_flow_content"></a>   
## 建立非固定格式內容  
 非固定格式內容可以是複雜的，由各種項目組成，包括文字、影像、表格，甚至是像控制項的 <xref:System.Windows.UIElement> 衍生類別 \(Derived Class\)。  若要了解如何建立複雜的非固定格式內容，必須了解下列幾點：  
  
-   **非固定格式相關類別**：非固定格式內容中使用的每個類別都有特定目的。  此外，非固定格式類別之間的階層關係可以協助您了解其使用方式。  例如，從 <xref:System.Windows.Documents.Block> 衍生的類別是用於包含其他物件，而從 <xref:System.Windows.Documents.Inline> 衍生的類別則包含顯示的物件。  
  
-   **內容結構描述**：非固定格式文件可能需要大量的巢狀項目。  內容結構描述會指定項目之間可能的父代\/子系關係。  
  
 下列各節會針對各個部分做詳細說明。  
  
<a name="flow_related_classes"></a>   
## 非固定格式相關類別  
 下圖顯示非固定格式內容中最常使用的物件：  
  
 ![圖表：非固定格式內容項目類別階層架構](../../../../docs/framework/wpf/advanced/media/flow-class-hierarchy.png "Flow\_Class\_Hierarchy")  
  
 就非固定格式內容用途，有兩個重要分類：  
  
1.  **Block 衍生類別**：也稱為「Block 內容項目」或只稱為「Block 項目」。  繼承自 <xref:System.Windows.Documents.Block> 的項目可以用來將共同父代下的項目放在一起形成群組，或將共同屬性套用至群組。  
  
2.  **Inline 衍生類別**：也稱為「Inline 內容項目」或只稱為「Inline 項目」。  繼承自 <xref:System.Windows.Documents.Inline> 的項目會包含在「Block 項目」內或其他「Inline 項目」內。  「Inline 項目」通常做為直接呈現至螢幕之內容的直接容器 \(Container\)。  例如，<xref:System.Windows.Documents.Paragraph> \(Block 項目\) 可以包含 <xref:System.Windows.Documents.Run> \(Inline 項目\)，而 <xref:System.Windows.Documents.Run> 則包含螢幕上呈現的文字。  
  
 這兩個分類中的每個類別會簡略說明如下。  
  
### Block 衍生類別  
 **Paragraph**  
  
 <xref:System.Windows.Documents.Paragraph> 通常用於將內容分組成段落。  Paragraph 最簡單和最常見的用途是建立文字段落。  
  
 [!code-xml[FlowOvwSnippets_snip#ParagraphExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 不過，您也可以包含其他 Inline 衍生項目，如下所示。  
  
 **章節**  
  
 <xref:System.Windows.Documents.Section> 只能用於包含其他 <xref:System.Windows.Documents.Block> 衍生項目。  它不會對所包含的項目套用任何預設格式。  不過，<xref:System.Windows.Documents.Section> 上設定的屬性值會套用至它的子項目。  區段也會讓您以程式設計的方式逐一查看其子集合。  <xref:System.Windows.Documents.Section> 的使用方式與 HTML 中的 \<DIV\> 標記類似。  
  
 在下列範例中，一個 <xref:System.Windows.Documents.Section> 底下定義了三個段落 \(Paragraph\)。  區段的 <xref:System.Windows.Documents.TextElement.Background%2A> 屬性值為 Red，因此段落的背景色彩也會是紅色的。  
  
 [!code-xml[FlowOvwSnippets_snip#SectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> 可讓 <xref:System.Windows.UIElement> 項目 \(也就是  <xref:System.Windows.Controls.Button>\) 內嵌於 Block 衍生非固定格式內容中。  <xref:System.Windows.Documents.InlineUIContainer> \(請參閱以下內容\) 是用於將 <xref:System.Windows.UIElement> 項目內嵌至 Inline 衍生非固定格式內容。  <xref:System.Windows.Documents.BlockUIContainer> 和 <xref:System.Windows.Documents.InlineUIContainer> 相當重要，因為沒有其他方式可以在非固定格式內容中使用 <xref:System.Windows.UIElement>，除非是包含在這兩個項目之一。  
  
 下列範例顯示如何使用 <xref:System.Windows.Documents.BlockUIContainer> 項目，在非固定格式內容內裝載 <xref:System.Windows.UIElement> 物件。  
  
 [!code-xml[SpanSnippets#_BlockUIXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 下圖顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：內嵌於非固定格式內容中的 UIElement](../../../../docs/framework/wpf/advanced/media/blockuicontainer.png "BlockUIContainer")  
  
 **List**  
  
 <xref:System.Windows.Documents.List> 是用於建立項目符號或數值清單。  將 <xref:System.Windows.Documents.List.MarkerStyle%2A> 屬性設為 <xref:System.Windows.TextMarkerStyle> 列舉值會決定清單的樣式。  下列範例會顯示如何建立簡單的清單。  
  
 [!code-xml[FlowOvwSnippets_snip#ListExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **注意**：<xref:System.Windows.Documents.List> 是唯一使用 <xref:System.Windows.Documents.ListItemCollection> 管理子項目的非固定格式項目。  
  
 **表格**  
  
 <xref:System.Windows.Documents.Table> 是用於建立表格。  <xref:System.Windows.Documents.Table> 類似於 <xref:System.Windows.Controls.Grid> 項目，但其功能較多，因此需要更多資源負荷。  因為 <xref:System.Windows.Controls.Grid> 是 <xref:System.Windows.UIElement>，所以無法在非固定格式內容中使用，除非是包含在 <xref:System.Windows.Documents.BlockUIContainer> 或 <xref:System.Windows.Documents.InlineUIContainer>。  如需 <xref:System.Windows.Documents.Table> 的詳細資訊，請參閱[資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)。  
  
### Inline 衍生類別  
 **回合**  
  
 <xref:System.Windows.Documents.Run> 是用來包含未格式化的文字。  您可能預期 <xref:System.Windows.Documents.Run> 物件會廣泛用在動態內容中。  不過在標記中，不需要明確使用 <xref:System.Windows.Documents.Run> 項目。  使用程式碼建立或管理非固定格式文件時，需要使用 <xref:System.Windows.Documents.Run>。  例如，在下列標記 \(Markup\) 中，第一個 <xref:System.Windows.Documents.Paragraph> 明確指定 <xref:System.Windows.Documents.Run> 項目，而第二個則未明確指定。  兩個段落會產生相同的輸出。  
  
 [!code-xml[FlowOvwSnippets_snip#RunExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **注意：**從 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 開始，<xref:System.Windows.Documents.Run> 物件的 <xref:System.Windows.Documents.Run.Text%2A> 屬性為相依性屬性。  您可以將 <xref:System.Windows.Documents.Run.Text%2A> 屬性繫結至資料來源，如 <xref:System.Windows.Controls.TextBlock>。  <xref:System.Windows.Documents.Run.Text%2A> 屬性完全支援單向繫結。  <xref:System.Windows.Documents.Run.Text%2A> 屬性也支援雙向繫結，但 <xref:System.Windows.Controls.RichTextBox> 除外。  如需範例，請參閱 <xref:System.Windows.Documents.Run.Text%2A?displayProperty=fullName>。  
  
 **Span**  
  
 <xref:System.Windows.Documents.Span> 會將其他 Inline 內容項目分組在一起。  <xref:System.Windows.Documents.Span> 項目本身沒有內建轉譯可套用至所涵蓋的內容。  不過，繼承自 <xref:System.Windows.Documents.Span> 的項目，包括 <xref:System.Windows.Documents.Hyperlink>、<xref:System.Windows.Documents.Bold>、<xref:System.Windows.Documents.Italic> 及 <xref:System.Windows.Documents.Underline>，確實會將格式套用至文字。  
  
 以下是對內嵌 \(Inline\) 內容使用 <xref:System.Windows.Documents.Span> 的範例，這段內容包含文字、<xref:System.Windows.Documents.Bold> 項目及 <xref:System.Windows.Controls.Button> 控制項。  
  
 [!code-xml[FlowOvwSnippets_snip#SpanExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 下列螢幕擷取畫面顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：呈現的 Span 範例](../../../../docs/framework/wpf/advanced/media/flow-spanexample.png "Flow\_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> 可讓 <xref:System.Windows.UIElement> 項目 \(也就是  像 <xref:System.Windows.Controls.Button> 的控制項\) 內嵌於 <xref:System.Windows.Documents.Inline> 內容項目中。  這個項目是上述 <xref:System.Windows.Documents.BlockUIContainer> 的內嵌 \(Inline\) 對等項目。  以下的範例會使用 <xref:System.Windows.Documents.InlineUIContainer> 將 <xref:System.Windows.Controls.Button> 內嵌插入至 <xref:System.Windows.Documents.Paragraph>。  
  
 [!code-xml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **注意**：在標記 \(Markup\) 中不需要明確使用 <xref:System.Windows.Documents.InlineUIContainer>。  如果省略它，編譯程式碼時還是會建立 <xref:System.Windows.Documents.InlineUIContainer>。  
  
 **Figure 和 Floater**  
  
 <xref:System.Windows.Documents.Figure> 和 <xref:System.Windows.Documents.Floater> 可用來以置放屬性的方式，將內容內嵌在非固定格式文件中，而置放屬性可以另外自訂，不受主要內容行文影響。  <xref:System.Windows.Documents.Figure> 或 <xref:System.Windows.Documents.Floater> 項目通常用來反白顯示或強調部分內容、裝載支援影像或主要內容流程內的其他內容，或零散地注入相關內容 \(如廣告\)。  
  
 下列範例顯示如何將 <xref:System.Windows.Documents.Figure> 內嵌至文字的段落。  
  
 [!code-xml[FlowOvwSnippets_snip#FigureExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 下圖顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：Figure 範例](../../../../docs/framework/wpf/advanced/media/flow-ovw-figure-example.png "Flow\_Ovw\_Figure\_Example")  
  
 <xref:System.Windows.Documents.Figure> 及 <xref:System.Windows.Documents.Floater> 在幾個方面有所不同，而且適用於不同的情況。  
  
 **Figure：**  
  
-   可以定位：您可以設定其水平與垂直錨點，以相對於頁面、內容、欄或段落的方式加以定位。  您也可以使用其 <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> 及 <xref:System.Windows.Documents.Figure.VerticalOffset%2A> 屬性來指定任意位移。  
  
-   大小可以調整到超過一欄：您可以將 <xref:System.Windows.Documents.Figure> 高度及寬度設定為頁面、內容或欄高度或寬度的倍數。  請注意，在頁面及內容的情況中，不容許大於 1 的倍數。  例如，您可以將 <xref:System.Windows.Documents.Figure> 的寬度設定為「0.5 頁」或「0.25 內容」或「2 欄」。  也可以將高度與寬度設定為絕對像素值。  
  
-   不要分頁：如果 <xref:System.Windows.Documents.Figure> 內的內容無法完全放入 <xref:System.Windows.Documents.Figure> 中，則它將視大小呈現足夠的內容，而剩餘的內容則將遺失。  
  
 **Floater：**  
  
-   無法定位，而且將呈現任何可供其使用的空間。  您無法設定位移或錨定 <xref:System.Windows.Documents.Floater>。  
  
-   大小無法調整到超過一欄：<xref:System.Windows.Documents.Floater> 預設為在一欄中調整大小。  它有個可以設為絕對像素值的 <xref:System.Windows.Documents.Floater.Width%2A> 屬性，但是如果此值大於一欄的寬度，則會忽略它，而且浮動器會在一欄中調整大小。  您可以設定正確的像素值寬度，將它設為小於一個資料行，但是調整大小與資料行無關，所以「0.5 資料行」不是 <xref:System.Windows.Documents.Floater> 寬度的有效表示法。  <xref:System.Windows.Documents.Floater> 沒有高度特性，且無法設定其高度，其高度根據內容而定  
  
-   <xref:System.Windows.Documents.Floater> 分頁：如果位在指定之寬度的內容超過一欄的高度，則浮動器會中斷並分頁至下一欄、下一頁等。  
  
 如果您想要控制大小及定位，而且有信心內容將完全放入指定的大小，則 <xref:System.Windows.Documents.Figure> 是放置獨立內容的好位置。  <xref:System.Windows.Documents.Floater> 是放置更多自由流動內容的好位置，這種內容的流動與主要頁面內容的流動相似，但與它隔開。  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> 會使非固定格式內容中發生分行。  以下範例將說明 <xref:System.Windows.Documents.LineBreak> 的用法。  
  
 [!code-xml[FlowOvwSnippets_snip#LineBreakExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 下列螢幕擷取畫面顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：LineBreak 範例](../../../../docs/framework/wpf/advanced/media/flow-ovw-linebreakexample.png "Flow\_Ovw\_LineBreakExample")  
  
### 非固定格式集合項目  
 在上述的許多範例中，<xref:System.Windows.Documents.BlockCollection> 和 <xref:System.Windows.Documents.InlineCollection> 是用來以程式設計方式建構非固定格式內容。  例如，若要將項目加入至 <xref:System.Windows.Documents.Paragraph>，您可以使用下列語法：  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 這會將 <xref:System.Windows.Documents.Run> 加入至 <xref:System.Windows.Documents.Paragraph> 的 <xref:System.Windows.Documents.InlineCollection>。  這與在標記 \(Markup\) 中的 <xref:System.Windows.Documents.Paragraph> 內找到的隱含 <xref:System.Windows.Documents.Run> 相同：  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 下列範例是使用 <xref:System.Windows.Documents.BlockCollection> 的範例，它會建立新的 <xref:System.Windows.Documents.Section>，然後使用 **Add** 方法將新的 <xref:System.Windows.Documents.Paragraph> 加入至 <xref:System.Windows.Documents.Section> 內容。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 除了將項目加入至非固定格式集合以外，您也可以移除項目。  下列範例會刪除 <xref:System.Windows.Documents.Span> 中的最後一個 <xref:System.Windows.Documents.Inline> 項目。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 下列範例會清除 <xref:System.Windows.Documents.Span> 的所有內容 \(<xref:System.Windows.Documents.Inline> 項目\)。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 以程式設計方式使用非固定格式內容時，您通常會廣泛使用這些集合。  
  
 非固定格式項目是使用 <xref:System.Windows.Documents.InlineCollection> \(Inline\) 還是 <xref:System.Windows.Documents.BlockCollection> \(Block\) 包含其子項目，取決於父代可以包含的子項目型別 \(<xref:System.Windows.Documents.Block> 或 <xref:System.Windows.Documents.Inline>\)。  非固定格式內容項目的內含規則在下一節的內容結構描述中會有摘要說明。  
  
 **注意**：與非固定格式內容搭配使用的還有第三種集合，即 <xref:System.Windows.Documents.ListItemCollection>，但是這種集合只能與 <xref:System.Windows.Documents.List> 搭配使用。  此外，有數種集合可以與 <xref:System.Windows.Documents.Table> 搭配使用。  如需詳細資訊，請參閱[資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)。  
  
<a name="content_schema"></a>   
## 內容結構描述  
 有這麼多種不同的非固定格式內容項目，要追蹤項目可以包含的子項目型別，實在很累人。  下圖摘要指出非固定格式項目的內含規則。  箭頭代表可能的父代\/子系關係。  
  
 ![圖表：非固定格式內容內含項目結構描述](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow\_Content\_Schema")  
  
 如同上圖所示，項目能夠具有的子系不一定跟它是 <xref:System.Windows.Documents.Block> 項目還是 <xref:System.Windows.Documents.Inline> 項目有關。  例如，<xref:System.Windows.Documents.Span> \(<xref:System.Windows.Documents.Inline> 項目\) 只能具有 <xref:System.Windows.Documents.Inline> 子項目，而 <xref:System.Windows.Documents.Figure> \(也是 <xref:System.Windows.Documents.Inline> 項目\) 只能具有 <xref:System.Windows.Documents.Block> 子項目。  因此，這張圖表有助於快速判斷某個項目是否可以包含其他項目。  例如，我們將用圖表決定如何建構 <xref:System.Windows.Controls.RichTextBox> 的非固定格式內容。  
  
 **1.** <xref:System.Windows.Controls.RichTextBox> 必須包含 <xref:System.Windows.Documents.FlowDocument>，而後者必須包含 <xref:System.Windows.Documents.Block> 的衍生物件。  以下是上圖中的對應區段。  
  
 ![圖表：RichTextBox 內含項目規則](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow\_Ovw\_SchemaWalkThrough1")  
  
 因此，標記 \(Markup\) 的外觀可能如下。  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** 根據圖表，有數種 <xref:System.Windows.Documents.Block> 項目可供選擇，包括 <xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.Table>、<xref:System.Windows.Documents.List> 及 <xref:System.Windows.Documents.BlockUIContainer> \(請參閱上述的 Block 衍生類別\)。  假設我們要用 <xref:System.Windows.Documents.Table>。  根據上圖，<xref:System.Windows.Documents.Table> 包含 <xref:System.Windows.Documents.TableRowGroup>，TableRowGroup 包含 <xref:System.Windows.Documents.TableRow> 項目，TableRow 包含 <xref:System.Windows.Documents.TableCell> 項目，而 TableCell 包含 <xref:System.Windows.Documents.Block> 衍生物件。  以下是取自於上圖之 <xref:System.Windows.Documents.Table> 的對應區段。  
  
 ![圖表：Table 的父代&#47;子系結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow\_Ovw\_SchemaWalkThrough2")  
  
 以下是對應標記 \(Markup\)。  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** 同樣地，<xref:System.Windows.Documents.TableCell> 下必須要有一個或多個 <xref:System.Windows.Documents.Block> 項目。  為將其簡化，我們將在儲存格中加入一些文字。  我們可以使用 <xref:System.Windows.Documents.Paragraph> 與 <xref:System.Windows.Documents.Run> 項目來執行這個動作。  以下是圖表中的對應區段，其中顯示 <xref:System.Windows.Documents.Paragraph> 可包含 <xref:System.Windows.Documents.Inline> 項目，而 <xref:System.Windows.Documents.Run> \(<xref:System.Windows.Documents.Inline> 項目\) 只能包含純文字。  
  
 ![圖表：Paragraph 的父代&#47;子系結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow\_Ovw\_SchemaWalkThrough3")  
  
 ![圖表：Run 的父代&#47;子系結構描述](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow\_Ovw\_SchemaWalkThrough4")  
  
 以下是標記 \(Markup\) 的完整範例。  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## 自訂文字  
 通常文字是非固定格式文件中最普遍的內容類型。  雖然以上介紹的物件可以用來控制大部分文字呈現的方式，但是還有其他方法可以自訂文字，本節稍後會做說明。  
  
### 文字裝飾  
 文字裝飾讓您可以將底線、頂線、基準線及刪除線效果套用至文字 \(請見下圖\)。  這些裝飾是用 <xref:System.Windows.Documents.Inline.TextDecorations%2A> 屬性加入的，數個物件 \(包括 <xref:System.Windows.Documents.Inline>、<xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Controls.TextBlock> 及 <xref:System.Windows.Controls.TextBox>\) 都會公開這個屬性。  
  
 下列範例顯示如何設定 <xref:System.Windows.Documents.Paragraph> 的 <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> 屬性。  
  
 [!code-xml[InlineSnippets#_Paragraph_TextDecXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 下圖顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：套用預設刪除線效果的文字](../../../../docs/framework/wpf/advanced/media/inline-textdec-strike.png "Inline\_TextDec\_Strike")  
  
 下列各圖分別顯示「頂線」、「基線」及「底線」裝飾呈現的效果。  
  
 ![螢幕擷取畫面：頂線 TextDecorator](../../../../docs/framework/wpf/advanced/media/inline-textdec-over.png "Inline\_TextDec\_Over")  
  
 ![螢幕擷取畫面：對文字套用的預設基準線效果](../../../../docs/framework/wpf/advanced/media/inline-textdec-base.png "Inline\_TextDec\_Base")  
  
 ![螢幕擷取畫面：套用預設底線效果的文字](../../../../docs/framework/wpf/advanced/media/inline-textdec-under.png "Inline\_TextDec\_Under")  
  
### 印刷樣式  
 大多數與非固定格式相關的屬性 \(包括 <xref:System.Windows.Documents.TextElement>、<xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Controls.TextBlock> 及 <xref:System.Windows.Controls.TextBox>\) 都會公開 <xref:System.Windows.Documents.TextElement.Typography%2A> 屬性。  這個屬性是用來控制文字的印刷樣式特性\/種類 \(例如  大小寫、上標和下標等\)。  
  
 下列範例以 <xref:System.Windows.Documents.Paragraph> 為例，顯示如何設定 <xref:System.Windows.Documents.TextElement.Typography%2A> 屬性。  
  
 [!code-xml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 下圖顯示這個範例呈現的效果。  
  
 ![螢幕擷取畫面：已變更印刷的文字](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement\_Typog")  
  
 相反地，下圖顯示具有預設印制樣式屬性的類似範例如何呈現。  
  
 ![螢幕擷取畫面：已變更印刷的文字](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement\_Typog\_Default")  
  
 下列範例顯示如何以程式設計的方式設定 <xref:System.Windows.Controls.TextBox.Typography%2A> 屬性。  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 如需印刷樣式的詳細資訊，請參閱 [WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)。  
  
## 請參閱  
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/flow-content-elements-how-to-topics.md)   
 [TextElement 內容模型概觀](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [資料表概觀](../../../../docs/framework/wpf/advanced/table-overview.md)   
 [附註概觀](../../../../docs/framework/wpf/advanced/annotations-overview.md)