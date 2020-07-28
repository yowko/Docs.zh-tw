---
title: 非固定格式文件概觀
description: 瞭解 Windows Presentation Foundation 中的非固定格式檔，其會根據視窗大小、裝置解析度和使用者喜好設定來動態調整內容。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: dac0cb91175a1398a0124020c048e14d7bcd1f76
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165242"
---
# <a name="flow-document-overview"></a>非固定格式文件概觀

非固定格式文件的設計是為最佳化檢視和可讀性。 非固定格式文件並不會設為某種預先定義的配置，而是會根據執行階段變數 (例如視窗大小、裝置解析度和選擇性的使用者喜好設定)，動態調整及自動重排其內容。 此外，非固定格式文件提供進階文件功能，例如編頁和資料行。 本主題提供非固定格式文件和建立方式的概觀。

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>什麼是非固定格式文件

非固定格式文件的設計是會根據視窗大小、裝置解析度及其他環境變數來「自動重排內容」。 此外，非固定格式文件具備許多內建功能，包括搜尋、將可讀性最佳化的檢視模式，以及變更字型大小與外觀的能力。 當可讀性是使用文件的主要考量時，最好使用非固定格式文件。 相反地，固定格式文件的設計是靜態展示。 當來源內容的精確度很重要時，固定格式文件很有用。 如需不同檔案類型的詳細資訊，請參閱[WPF 中的檔](documents-in-wpf.md)。

下圖顯示在數個不同大小的視窗中檢視非固定格式文件範例。 當顯示區域變更時，內容就會自動重排以充分利用可用的空間。

![非固定格式文件內容重新排列](./media/edocs-flowdocument.png "eDocs_FlowDocument")

如上圖所示，非固定格式內容可以包含許多元件，包括段落、清單、映像等等。 這些元件會對應至程序性程式碼中標記和物件的項目。 稍後在本總覽的[流程相關類別](#flow_related_classes)一節中，我們將詳細說明這些類別。 目前，以下是一個簡單的程式碼範例，它會建立一個由含有一些粗體文字和一個清單的段落組成的非固定格式檔。

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

下圖顯示此程式碼片段的外觀。

![螢幕擷取畫面：呈現的 FlowDocument 範例](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")

在此範例中， <xref:System.Windows.Controls.FlowDocumentReader> 控制項是用來裝載流程內容。 如需流程內容裝載控制項的詳細資訊，請參閱非固定格式[檔案類型](#flow_document_types)。 <xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.List> 、 <xref:System.Windows.Documents.ListItem> 和 <xref:System.Windows.Documents.Bold> 元素是用來根據其在標記中的順序來控制內容格式。 例如， <xref:System.Windows.Documents.Bold> 元素只橫跨段落中的部分文字，因此，只有該部分的文字會變成粗體。 如果您使用過 HTML，會覺得很熟悉。

如上圖中的反白顯示，非固定格式檔內建了數個功能：

- 搜尋︰讓使用者對整份文件執行全文檢索搜尋。

- 檢視模式︰使用者可以選取偏好的檢視模式，包括單一頁面 (一次一頁) 檢視模式、一次兩頁 (書本閱讀格式) 檢視模式，以及以連續捲動 (無底邊) 檢視模式。  如需這些查看模式的詳細資訊，請參閱 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> 。

- 頁面導覽控制項︰如果文件的檢視模式使用頁面，則頁面導覽控制項會包括移至下一頁 (向下箭號) 或上一頁 (向上箭號) 的按鈕，以及目前頁碼和總頁數的指示器。 使用鍵盤方向鍵也可以翻頁。

- 縮放︰縮放控制項可讓使用者按下加號或減號按鈕，分別放大或縮小縮放層級。 縮放控制項也包括調整縮放層級的滑桿。 如需詳細資訊，請參閱 <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>。

您可以根據裝載非固定格式內容所用的控制項來修改這些功能。 下一節說明不同的控制項。

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>非固定格式文件類型

非固定格式文件內容的外觀和顯示方式，取決於裝載非固定格式內容的物件。 有四個控制項支援流程內容的視圖： <xref:System.Windows.Controls.FlowDocumentReader> 、 <xref:System.Windows.Controls.FlowDocumentPageViewer> 、 <xref:System.Windows.Controls.RichTextBox> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 。 以下簡短說明這些控制項。

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>需要直接裝載非固定格式內容，因此所有這些視圖控制項都會使用 <xref:System.Windows.Documents.FlowDocument> 來啟用流動內容裝載。

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>包含的功能可讓使用者在各種不同的視圖模式之間進行動態選擇，包括單頁（一次一頁）的瀏覽模式、兩頁的一次性（書籍閱讀格式）觀賞模式，以及連續滾動（無底邊）查看模式。 如需這些查看模式的詳細資訊，請參閱 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> 。 如果您不需要在不同的視圖模式之間進行動態切換的功能， <xref:System.Windows.Controls.FlowDocumentPageViewer> 並 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 提供在特定的瀏覽模式中固定的較輕量流程內容檢視器。

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer 和 FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>在頁面一次的瀏覽模式中顯示內容，同時 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 以連續滾動模式顯示內容。 <xref:System.Windows.Controls.FlowDocumentPageViewer>和 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 都固定于特定的瀏覽模式。 相 <xref:System.Windows.Controls.FlowDocumentReader> 較于，其中包含的功能可讓使用者在各種不同的瀏覽模式（由列舉所提供）之間進行動態選擇 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> ，代價是比或更耗費資源的成本 <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> 。

預設一定會顯示垂直捲軸，而水平捲動則會視需要顯示。 的預設 UI <xref:System.Windows.Controls.FlowDocumentScrollViewer> 不包含工具列，但是 <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> 屬性可以用來啟用內建工具列。

### <a name="richtextbox"></a>RichTextBox

<xref:System.Windows.Controls.RichTextBox>當您想要允許使用者編輯流程內容時，請使用。 例如，如果您想要建立一個編輯器，讓使用者能夠操控像是資料表、斜體和粗體格式等專案，您可以使用 <xref:System.Windows.Controls.RichTextBox> 。 如需詳細資訊，請參閱[RichTextBox 總覽](../controls/richtextbox-overview.md)。

> [!NOTE]
> 內的 <xref:System.Windows.Controls.RichTextBox> 非固定格式內容，其行為與其他控制項中所包含的流程內容完全相同。 例如，中沒有任何資料行， <xref:System.Windows.Controls.RichTextBox> 因此不會自動調整大小行為。 此外，內建的流量內容一般功能（例如搜尋、瀏覽模式、頁面流覽和縮放）都無法在中使用 <xref:System.Windows.Controls.RichTextBox> 。

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>建立非固定格式內容

非固定格式內容可能很複雜，其中包含各種元素，包括文字、影像、資料表，甚至是 <xref:System.Windows.UIElement> 衍生的類別（例如控制項）。 若要了解如何建立複雜的非固定格式內容，下列幾點很重要︰

- **非固定格式相關的類別**：非固定格式內中使用的每種類別都有特定用途。 此外，非固定格式類別之間的階層式關聯性可協助您了解如何使用它們。 例如，衍生自類別的類別 <xref:System.Windows.Documents.Block> 會用來包含其他物件，而衍生自的類別會 <xref:System.Windows.Documents.Inline> 包含所顯示的物件。

- **內容結構描述**︰非固定格式文件會需要大量的巢狀項目。 內容結構描述指定項目之間可能的父/子關聯性。

下列各節會一一詳細介紹這些區域。

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>非固定格式相關的類別

下圖顯示非固定格式內容中最常使用的物件︰

![圖表：非固定格式內容項目類別階層架構](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

針對非固定格式內容的目的，有兩個重要分類︰

1. **區塊衍生類別**︰也稱為「區塊內容項目」或簡稱為「區塊項目」。 繼承自的專案 <xref:System.Windows.Documents.Block> 可以用來將通用父系下的專案分組，或將通用屬性套用至群組。

2. **內嵌衍生類別**︰也稱為「內嵌內容項目」或簡稱為「內嵌項目」。 繼承自的元素 <xref:System.Windows.Documents.Inline> 會包含在區塊專案或另一個內嵌專案中。 內嵌項目通常用為轉譯到螢幕之內容的直接容器。 例如， <xref:System.Windows.Documents.Paragraph> （區塊元素）可以包含 <xref:System.Windows.Documents.Run> （內嵌元素），但 <xref:System.Windows.Documents.Run> 實際上包含在螢幕上呈現的文字。

以下簡短描述這兩種分類中的每個類別。

### <a name="block-derived-classes"></a>區塊衍生類別

**Paragraph**

<xref:System.Windows.Documents.Paragraph>通常用來將內容分組到段落中。 段落最簡單且最常見的用法是建立一段文字。

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

不過，您也可以包含其他內嵌衍生的元素，如下所示。

**區段**

<xref:System.Windows.Documents.Section>僅用於包含其他 <xref:System.Windows.Documents.Block> 衍生的元素。 它不會將任何預設的格式設定套用到其所包含的項目。 不過，在上設定的任何屬性值都會 <xref:System.Windows.Documents.Section> 套用至其子項目。 區段也可讓您以程式設計的方式逐一查看其子集合。 <xref:System.Windows.Documents.Section>的使用方式與 HTML 中的 \<DIV> 標記類似。

在下列範例中，會在其中定義三個段落 <xref:System.Windows.Documents.Section> 。 區段的 <xref:System.Windows.Documents.TextElement.Background%2A> 屬性值為紅色，因此段落的背景色彩也會是紅色。

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**BlockUIContainer**

<xref:System.Windows.Documents.BlockUIContainer>讓 <xref:System.Windows.UIElement> 元素（亦即 a <xref:System.Windows.Controls.Button> ）內嵌在區塊衍生的流程內容中。 <xref:System.Windows.Documents.InlineUIContainer>（請參閱下文）用來 <xref:System.Windows.UIElement> 在內嵌衍生的流程內容中嵌入專案。 <xref:System.Windows.Documents.BlockUIContainer>和 <xref:System.Windows.Documents.InlineUIContainer> 很重要，因為沒有其他方法可在非固定格式內容中使用， <xref:System.Windows.UIElement> 除非它包含在這兩個元素的其中一個內。

下列範例顯示如何使用專案 <xref:System.Windows.Documents.BlockUIContainer> 來裝載非固定格式 <xref:System.Windows.UIElement> 內容中的物件。

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

下圖顯示此範例的呈現方式：

![顯示在 [流動內容] 中內嵌之 UIElement 的螢幕擷取畫面。](./media/flow-document-overview/embedded-blockuicontainer.png)

**清單**

<xref:System.Windows.Documents.List>是用來建立點符或數位清單。 將 <xref:System.Windows.Documents.List.MarkerStyle%2A> 屬性設定為 <xref:System.Windows.TextMarkerStyle> 列舉值，以決定清單的樣式。 下例示範如何建立簡單的清單。

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>是唯一的流程元素，會使用 <xref:System.Windows.Documents.ListItemCollection> 來管理子項目。

**Table**

<xref:System.Windows.Documents.Table>是用來建立資料表。 <xref:System.Windows.Documents.Table>類似于元素， <xref:System.Windows.Controls.Grid> 但具有更多功能，因此需要更大的資源負荷。 因為 <xref:System.Windows.Controls.Grid> 是 <xref:System.Windows.UIElement> ，所以不能用在非固定格式內容中，除非它包含在 <xref:System.Windows.Documents.BlockUIContainer> 或中 <xref:System.Windows.Documents.InlineUIContainer> 。 如需有關的詳細資訊 <xref:System.Windows.Documents.Table> ，請參閱[資料表總覽](table-overview.md)。

### <a name="inline-derived-classes"></a>內嵌衍生類別

**執行**

<xref:System.Windows.Documents.Run>用來包含未格式化的文字。 您可能希望 <xref:System.Windows.Documents.Run> 物件在非固定格式內容中廣泛使用。 不過，在標記中， <xref:System.Windows.Documents.Run> 不需要明確使用元素。 <xref:System.Windows.Documents.Run>使用程式碼建立或操作非固定格式檔時，必須使用。 例如，在下列標記中，第一個 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> 會明確地指定元素，而第二個則不會。 這兩個段落會產生相同的輸出。

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> 從 .NET Framework 4 開始，物件的 <xref:System.Windows.Documents.Run.Text%2A> 屬性是相依性 <xref:System.Windows.Documents.Run> 屬性。 您可以將屬性系結 <xref:System.Windows.Documents.Run.Text%2A> 至資料來源，例如 <xref:System.Windows.Controls.TextBlock> 。 <xref:System.Windows.Documents.Run.Text%2A>屬性完全支援單向系結。 <xref:System.Windows.Documents.Run.Text%2A>除了之外，屬性也支援雙向系結 <xref:System.Windows.Controls.RichTextBox> 。 如需範例，請參閱 <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>。

**跨**

<xref:System.Windows.Documents.Span>將其他內嵌內容元素群組在一起。 元素內的內容不會套用任何固有的轉譯 <xref:System.Windows.Documents.Span> 。 不過，繼承自的元素 <xref:System.Windows.Documents.Span> 包括 <xref:System.Windows.Documents.Hyperlink> 、 <xref:System.Windows.Documents.Bold> 和，會 <xref:System.Windows.Documents.Italic> <xref:System.Windows.Documents.Underline> 將格式套用至文字。

以下是 <xref:System.Windows.Documents.Span> 用來包含內嵌內容的範例，包括文字、專案 <xref:System.Windows.Documents.Bold> 和 <xref:System.Windows.Controls.Button> 。

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

以下的螢幕擷取畫面顯示此範例的轉譯方式。

![螢幕擷取畫面：呈現的 Span 範例](./media/flow-spanexample.gif "Flow_SpanExample")

**InlineUIContainer**

<xref:System.Windows.Documents.InlineUIContainer>讓專案 <xref:System.Windows.UIElement> （例如像這樣的控制項 <xref:System.Windows.Controls.Button> ）內嵌在 <xref:System.Windows.Documents.Inline> content 元素中。 這個專案是上面所述的內嵌對等專案 <xref:System.Windows.Documents.BlockUIContainer> 。 以下是使用 <xref:System.Windows.Documents.InlineUIContainer> 在中插入內嵌的範例 <xref:System.Windows.Controls.Button> <xref:System.Windows.Documents.Paragraph> 。

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>不需要在標記中明確使用。 如果您省略它， <xref:System.Windows.Documents.InlineUIContainer> 當程式碼編譯時，還是會建立。

**圖表和 Floater**

<xref:System.Windows.Documents.Figure>和 <xref:System.Windows.Documents.Floater> 是用來將內容內嵌在具有放置屬性的非固定格式檔中，可自訂為與主要內容流程無關。 <xref:System.Windows.Documents.Figure>或專案 <xref:System.Windows.Documents.Floater> 通常用來反白顯示或強調部分內容、裝載支援的影像或主要內容流程中的其他內容，或插入鬆散相關的內容（例如廣告）。

下列範例顯示如何將內嵌至 <xref:System.Windows.Documents.Figure> 文字的段落。

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

下圖顯示此範例的轉譯方式。

![螢幕擷取畫面：Figure 範例](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>和 <xref:System.Windows.Documents.Floater> 有幾種不同的方式，適用于不同的案例。

**圖表**

- 可以定位︰可以設定其水平和垂直錨點，將它固定在頁面、內容、資料行或段落的相對位置。 您也可以使用其 <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> 和 <xref:System.Windows.Documents.Figure.VerticalOffset%2A> 屬性來指定任意位移。

- 可調成一個以上的資料行：您可以將 <xref:System.Windows.Documents.Figure> 高度和寬度設定為頁面、內容或資料行高度或寬度的倍數。 請注意，如果是頁面及內容，倍數不能大於 1。 例如，您可以將的寬度設定為「 <xref:System.Windows.Documents.Figure> 0.5 頁面」或「0.25 內容」或「2個數據行」。 您也可以將高度和寬度設為絕對像素值。

- 未分頁：如果中的內容 <xref:System.Windows.Documents.Figure> 無法納入內部 <xref:System.Windows.Documents.Figure> ，它會轉譯任何符合的內容，並遺失剩餘的內容

**Floater：**

- 無法定位，但會轉譯任何可用的空間。 您不能設定 offset 或錨點 a <xref:System.Windows.Documents.Floater> 。

- 無法調整大小為一個以上的資料行：根據預設， <xref:System.Windows.Documents.Floater> 單一資料行的大小。 它具有 <xref:System.Windows.Documents.Floater.Width%2A> 可設定為絕對圖元值的屬性，但如果這個值大於一個資料行寬度，則會忽略它，而且 floater 會在一個資料行上調整大小。 您可以藉由設定正確的圖元寬度來將其大小調整為小於一欄，但調整大小不是資料行相對，因此 "0.5 Column" 不是有效的 <xref:System.Windows.Documents.Floater> 寬度運算式。 <xref:System.Windows.Documents.Floater>沒有 height 屬性，而且無法設定其高度，其高度取決於內容

- <xref:System.Windows.Documents.Floater>分頁：如果其指定寬度的內容延伸至超過1個數據行高度，則 floater 會中斷並分頁至下一個資料行、下一個頁面等等。

 <xref:System.Windows.Documents.Figure>是放在您想要控制大小和定位的獨立內容，並且確信內容將符合指定大小的好地方。 <xref:System.Windows.Documents.Floater>是放置更多自由流動內容的好地方，其流程與主頁面內容相似，但與其分開。

**LineBreak**

<xref:System.Windows.Documents.LineBreak>導致在非固定格式內容中出現分行符號。 下列範例示範 <xref:System.Windows.Documents.LineBreak> 的用法。

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

以下的螢幕擷取畫面顯示此範例的轉譯方式。

![螢幕擷取畫面：LineBreak 範例](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>流程集合項目

在上述許多範例中， <xref:System.Windows.Documents.BlockCollection> 和 <xref:System.Windows.Documents.InlineCollection> 是用來以程式設計方式來設計流程內容。 例如，若要將元素加入至 <xref:System.Windows.Documents.Paragraph> ，您可以使用語法：

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

這會將加入 <xref:System.Windows.Documents.Run> 至的 <xref:System.Windows.Documents.InlineCollection> <xref:System.Windows.Documents.Paragraph> 。  這與標記中的隱含在 <xref:System.Windows.Documents.Run> 中找到的相同 <xref:System.Windows.Documents.Paragraph> ：

```xml
<Paragraph>
Some Text
</Paragraph>
```

如需使用的範例 <xref:System.Windows.Documents.BlockCollection> ，下列範例會建立新的， <xref:System.Windows.Documents.Section> 然後使用**add**方法將新的新增 <xref:System.Windows.Documents.Paragraph> 至 <xref:System.Windows.Documents.Section> 內容。

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

除了將項目新增至流程集合，您也可以移除項目。  下列範例會刪除中的最後一個 <xref:System.Windows.Documents.Inline> 元素 <xref:System.Windows.Documents.Span> 。

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

下列範例會從中清除所有的內容（ <xref:System.Windows.Documents.Inline> 元素） <xref:System.Windows.Documents.Span> 。

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

以程式設計方式處理非固定格式內容時，您可能也會廣泛使用這些集合。

Flow 元素是否使用 <xref:System.Windows.Documents.InlineCollection> （內嵌）或 <xref:System.Windows.Documents.BlockCollection> （區塊）來包含其子專案，取決於父系可以包含的子專案類型（ <xref:System.Windows.Documents.Block> 或 <xref:System.Windows.Documents.Inline> ）。 下一節的＜內容結構描述＞會摘要說明非固定格式內容項目的內含項目規則。

> [!NOTE]
> 有第三種類型的集合搭配非固定格式內容使用， <xref:System.Windows.Documents.ListItemCollection> 但此集合僅與搭配使用 <xref:System.Windows.Documents.List> 。 此外，還有數個與搭配使用的集合 <xref:System.Windows.Documents.Table> 。 如需詳細資訊，請參閱[資料表總覽](table-overview.md)。

<a name="content_schema"></a>

## <a name="content-schema"></a>內容結構描述

假設有多種不同的非固定格式內容項目，追蹤項目可以包含哪些子項目類型可能很累人。 下圖摘要說明流程項目的內含項目規則。 箭號代表可能的父/子關聯性。

![圖表：非固定格式內容內含項目結構描述](./media/flow-content-schema.png "Flow_Content_Schema")

如上圖所示，專案所允許的子系不一定是由元素 <xref:System.Windows.Documents.Block> 或元素所決定 <xref:System.Windows.Documents.Inline> 。 例如， <xref:System.Windows.Documents.Span> （ <xref:System.Windows.Documents.Inline> 元素）只能有 <xref:System.Windows.Documents.Inline> 子專案 <xref:System.Windows.Documents.Figure> ，而（也是 <xref:System.Windows.Documents.Inline> 元素）只能有 <xref:System.Windows.Documents.Block> 子專案。 因此，可快速判斷哪個元素可包含於其他元素中的圖表就很有用。 例如，讓我們使用圖表來決定如何建立的流程內容 <xref:System.Windows.Controls.RichTextBox> 。

**1.** <xref:System.Windows.Controls.RichTextBox> 必須包含， <xref:System.Windows.Documents.FlowDocument> 而後者又必須包含衍生的 <xref:System.Windows.Documents.Block> 物件。 以下是來自上圖的對應區段。

![圖表：RichTextBox 內含項目規則](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

這是標記目前可能的樣子。

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** 根據圖表，有數個 <xref:System.Windows.Documents.Block> 元素可供選擇 <xref:System.Windows.Documents.Paragraph> ，包括、 <xref:System.Windows.Documents.Section> 、 <xref:System.Windows.Documents.Table> 、 <xref:System.Windows.Documents.List> 和 <xref:System.Windows.Documents.BlockUIContainer> （請參閱上述的區塊衍生類別）。 假設我們想要 <xref:System.Windows.Documents.Table> 。 根據上圖，包含包含專案 <xref:System.Windows.Documents.Table> ，其中 <xref:System.Windows.Documents.TableRowGroup> 包含 <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.TableCell> 包含 <xref:System.Windows.Documents.Block> 衍生物件的元素。 以下是 <xref:System.Windows.Documents.Table> 取自上圖的對應區段。

![圖表：父系&#47;資料表的子系架構](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")

以下是對應的標記。

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** 同樣地，底下需要一或多個 <xref:System.Windows.Documents.Block> 元素 <xref:System.Windows.Documents.TableCell> 。 為求簡便，我們在儲存格中放入一些文字。 我們可以使用搭配專案來執行這項操作 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> 。 以下是圖表中對應的區段，其中顯示 <xref:System.Windows.Documents.Paragraph> 可以接受 <xref:System.Windows.Documents.Inline> 元素，而 a （專案 <xref:System.Windows.Documents.Run> <xref:System.Windows.Documents.Inline> ）只會使用純文字。

![圖表：父&#47;段落的子系架構](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")

![圖表：父系&#47;執行的子系架構](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")

以下是標記的完整範例。

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>自訂文字

文字通常是非固定格式文件中最普遍的內容類型。 雖然您可以使用前文介紹的物件控制大部分的文字轉譯方式，但有一些其他方法可處理本節討論的自訂文字。

### <a name="text-decorations"></a>文字裝飾

文字裝飾讓您對文字套用底線、頂線、基準線及刪除線效果 (請參閱下圖)。 這些裝飾會使用 <xref:System.Windows.Documents.Inline.TextDecorations%2A> 由多個物件（包括 <xref:System.Windows.Documents.Inline> 、 <xref:System.Windows.Documents.Paragraph> 、和）公開的屬性來新增 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox> 。

下列範例將示範如何設定  的 屬性。

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

下圖顯示此範例的轉譯方式。

![螢幕擷取畫面：套用預設刪除線效果的文字](./media/inline-textdec-strike.png "Inline_TextDec_Strike")

下圖顯示如何分別呈現頂**線、****基線和底線****裝飾。**

![螢幕擷取畫面：頂線 TextDecorator](./media/inline-textdec-over.png "Inline_TextDec_Over")

![螢幕擷取畫面：對文字套用的預設基準線效果](./media/inline-textdec-base.png "Inline_TextDec_Base")

![螢幕擷取畫面：套用預設底線效果的文字](./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>印刷樣式

<xref:System.Windows.Documents.TextElement.Typography%2A>屬性是由大部分與流程相關的內容所公開 <xref:System.Windows.Documents.TextElement> ，包括、 <xref:System.Windows.Documents.FlowDocument> 、 <xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.TextBox> 。 這個屬性是用來控制文字的印刷特性/變化 (即小型或大型大寫字、上標和下標等等)。

下列範例顯示如何 <xref:System.Windows.Documents.TextElement.Typography%2A> 使用做為範例專案來設定屬性 <xref:System.Windows.Documents.Paragraph> 。

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

下圖顯示此範例的轉譯方式。

![螢幕擷取畫面：已變更印刷的文字](./media/textelement-typog.png "TextElement_Typog")

相反地，下圖顯示如何轉譯套用預設印刷樣式屬性的類似範例。

![螢幕擷取畫面：已變更印刷的文字](./media/textelement-typog-default.png "TextElement_Typog_Default")

下列範例顯示如何以程式設計 <xref:System.Windows.Controls.TextBox.Typography%2A> 方式設定屬性。

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

如需印刷樣式的詳細資訊，請參閱[WPF 中的印刷](typography-in-wpf.md)樣式。

## <a name="see-also"></a>另請參閱

- [Text](optimizing-performance-text.md)
- [WPF 中的印刷樣式](typography-in-wpf.md)
- [操作說明主題](flow-content-elements-how-to-topics.md)
- [TextElement 內容模型概觀](textelement-content-model-overview.md)
- [RichTextBox 概觀](../controls/richtextbox-overview.md)
- [WPF 中的文件](documents-in-wpf.md)
- [資料表概觀](table-overview.md)
- [附註概觀](annotations-overview.md)
