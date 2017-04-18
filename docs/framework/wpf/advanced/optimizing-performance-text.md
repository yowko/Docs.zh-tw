---
title: "最佳化效能：文字 | Microsoft Docs"
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
  - "轉譯文字"
  - "超連結"
  - "格式化文字 [WPF]"
  - "效能的文字"
  - "圖像"
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 最佳化效能：文字
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]包含透過豐富的功能使用的文字內容的呈現方式的支援[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]控制項。 一般而言，您可以將三個層級中的文字呈現︰  
  
1.  使用<xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>直接物件。  
  
2.  使用<xref:System.Windows.Media.FormattedText>物件。  
  
3.  使用高層級的控制項，例如<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Documents.FlowDocument>物件。  
  
 本主題提供的文字呈現的效能建議。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>轉譯文字圖像 （glyph） 層級  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供進階的文字支援包括直接存取的圖像 （glyph） 層級標記<xref:System.Windows.Documents.Glyphs>的客戶想要進行攔截和保存格式化後的文字。 這些功能提供重大支援不同的文字轉譯中每個下列案例的需求。  
  
-   固定格式文件的螢幕顯示。  
  
-   列印案例。  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]為裝置印表機語言。  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   先前的印表機驅動程式，從輸出[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]固定格式的應用程式。  
  
    -   列印多工緩衝處理格式。  
  
-   固定格式文件表示法，包括舊版的用戶端[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]和其他電腦的裝置。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>專為固定格式文件呈現及列印案例。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供數個項目的一般配置和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]案例，例如<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.TextBlock>。 如需有關配置和[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]案例，請參閱[WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)。  
  
 下列範例顯示如何定義屬性<xref:System.Windows.Documents.Glyphs>物件存放至[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 <xref:System.Windows.Documents.Glyphs>物件所表示的輸出<xref:System.Windows.Media.GlyphRun>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 此範例假設新細明體，新細明體和新細明體字型會安裝在**C:\WINDOWS\Fonts**本機電腦上的資料夾。  
  
 [!code-xml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>使用 DrawGlyphRun  
 如果您有自訂控制項，而且您想要呈現圖像 （glyph），請使用<xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>方法。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也提供自訂的文字格式透過使用的較低層級服務<xref:System.Windows.Media.FormattedText>物件。 最有效率的方式轉譯中的文字[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]是藉由產生在圖像 （glyph） 層級使用的文字內容<xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>。 不過，這種效率的成本將會遺失您輕鬆使用 rtf 格式，也就是內建功能的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]控制項，例如<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Documents.FlowDocument>。  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>FormattedText 物件  
 <xref:System.Windows.Media.FormattedText>物件可讓您繪製多行文字，可以個別格式化文字中的每個字元。 如需詳細資訊，請參閱[繪圖格式化文字](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)。  
  
 若要建立格式化的文字，請呼叫<xref:System.Windows.Media.FormattedText.%23ctor%2A>建構函式建立<xref:System.Windows.Media.FormattedText>物件。 一旦您建立初始格式化的文字字串，您可以套用某個範圍的格式化樣式。 如果您的應用程式想要實作自己的配置，然後在<xref:System.Windows.Media.FormattedText>物件是較好的選擇，比使用一個控制項，例如<xref:System.Windows.Controls.TextBlock>。 如需有關<xref:System.Windows.Media.FormattedText>物件，請參閱[繪圖格式化文字](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)。  
  
 <xref:System.Windows.Media.FormattedText>物件會提供低階的文字格式設定功能。 您可以將多個的格式化樣式套用至一或多個字元。 例如，您可以呼叫兩者<xref:System.Windows.Media.FormattedText.SetFontSize%2A>和<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>方法，以變更文字中的前五個字元的格式。  
  
 下列程式碼範例會建立<xref:System.Windows.Media.FormattedText>物件，並呈現它。  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument、 TextBlock 和標籤控制項  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]包含多個控制項來繪製文字至螢幕。 每個控制項不同的案例的目標，且有它自己的功能與限制的清單。  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument 個以上的 TextBlock 或標籤會影響效能  
 一般而言， <xref:System.Windows.Controls.TextBlock>必要項目，例如一個簡短的句子中的支援有限的文字時，應使用項目[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 <xref:System.Windows.Controls.Label>可以在最小文字支援需要時使用。 <xref:System.Windows.Documents.FlowDocument>項目是容器，支援豐富的內容，重新 flowable 文件，因此，會有更高的效能影響，比使用<xref:System.Windows.Controls.TextBlock>或<xref:System.Windows.Controls.Label>控制項。  
  
 如需有關<xref:System.Windows.Documents.FlowDocument>，請參閱[非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)。  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>請避免使用 FlowDocument 中的 TextBlock  
 <xref:System.Windows.Controls.TextBlock>元素衍生自<xref:System.Windows.UIElement>。 <xref:System.Windows.Documents.Run>元素衍生自<xref:System.Windows.Documents.TextElement>，這是成本更低比<xref:System.Windows.UIElement>-衍生物件。 可能的話，請使用<xref:System.Windows.Documents.Run>而<xref:System.Windows.Controls.TextBlock>顯示文字內容， <xref:System.Windows.Documents.FlowDocument>。  
  
 下列標記範例說明兩種設定中的文字內容<xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xml[Performance#PerformanceSnippet13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>避免使用 [執行] 來設定文字屬性  
 一般情況下，使用<xref:System.Windows.Documents.Run>內<xref:System.Windows.Controls.TextBlock>是效能較不使用明確<xref:System.Windows.Documents.Run>根本物件。 如果您使用<xref:System.Windows.Documents.Run>若要設定文字屬性，設定這些屬性直接在<xref:System.Windows.Controls.TextBlock>改。  
  
 下列標記範例說明如何設定 text 屬性，在此情況下，這兩種方式<xref:System.Windows.Controls.TextBlock.FontWeight%2A>屬性︰  
  
 [!code-xml[Performance#PerformanceSnippet12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 下表顯示 1000年個成本<xref:System.Windows.Controls.TextBlock>物件逾時或無明確<xref:System.Windows.Documents.Run>。  
  
|**TextBlock 型別**|**建立時間 （毫秒）**|**轉譯時間 （毫秒）**|  
|------------------------|------------------------------|----------------------------|  
|回合設定文字屬性|146|540|  
|TextBlock 設定 text 屬性|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>避免資料繫結至 Label.Content 屬性  
 假設您有一種情況<xref:System.Windows.Controls.Label>從經常更新的物件<xref:System.String>來源。 當資料繫結<xref:System.Windows.Controls.Label>項目的<xref:System.Windows.Controls.ContentControl.Content%2A>屬性<xref:System.String>來源物件，您可能會遇到效能不佳。 每次來源<xref:System.String>更新時，舊<xref:System.String>物件是捨棄，並使用新<xref:System.String>會重新建立，因為<xref:System.String>物件是不可變，無法修改。 這又會導致<xref:System.Windows.Controls.ContentPresenter>的<xref:System.Windows.Controls.Label>捨棄舊的內容，並重新產生新的內容，以顯示此新物件<xref:System.String>。  
  
 這個問題解決方法很簡單。 如果<xref:System.Windows.Controls.Label>未設定為自訂<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>值，取代<xref:System.Windows.Controls.Label>與<xref:System.Windows.Controls.TextBlock>及資料繫結其<xref:System.Windows.Controls.TextBlock.Text%2A>來源字串的屬性。  
  
|**資料繫結屬性**|**更新時間 （毫秒）**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>超連結  
 <xref:System.Windows.Documents.Hyperlink>物件是可讓您將非固定格式內容中的主機超連結的內嵌層級非固定格式內容項目。  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>結合一個 TextBlock 物件中的超連結  
 您可以最佳化多個使用<xref:System.Windows.Documents.Hyperlink>組成群組在相同的項目<xref:System.Windows.Controls.TextBlock>。 這可協助您建立應用程式中的物件數目降到最低。 例如，您可能想要顯示多個超連結，如下所示︰  
  
 MSN 首頁 |我 MSN  
  
 下列範例中，標記會顯示多個<xref:System.Windows.Controls.TextBlock>用來顯示超連結的項目︰  
  
 [!code-xml[Performance#PerformanceSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 下列範例中，標記會顯示更有效率的方式顯示的超連結，這次請使用單一<xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xml[Performance#PerformanceSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>只能在 MouseEnter 事件上的超連結上顯示波浪底線  
 A <xref:System.Windows.TextDecoration>物件是您可以加入文字的視覺裝飾; 不過，它可以是耗用具現化的效能。 如果您使用大量的<xref:System.Windows.Documents.Hyperlink>項目，請考慮顯示底線，例如觸發事件時，才<xref:System.Windows.ContentElement.MouseEnter>事件。 如需詳細資訊，請參閱[指定超連結是否會加上底線](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)。  
  
 ![顯示 Textdecoration 的超連結](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
MouseEnter 上顯示的超連結  
  
 下列標記的範例顯示<xref:System.Windows.Documents.Hyperlink>定義包含和不含底線︰  
  
 [!code-xml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 下表顯示的效能成本顯示 1000年<xref:System.Windows.Documents.Hyperlink>包含和不含底線的項目。  
  
|**超連結**|**建立時間 （毫秒）**|**轉譯時間 （毫秒）**|  
|-------------------|------------------------------|----------------------------|  
|底線|289|1130|  
|沒有底線|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>文字格式化功能  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供 rtf 格式的服務，例如自動斷字。 這些服務可能會影響應用程式效能，而且應該只在需要時才使用。  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>避免使用不必要的斷字  
 自動斷字行的文字，找出連字號中斷點，並允許其他中斷的位置中程式碼行<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Documents.FlowDocument>物件。 根據預設，自動斷字功能已停用這些物件中。 您可以啟用此功能的物件 IsHyphenationEnabled 屬性設定為`true`。 不過，啟用此功能會導致[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]起始[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]互通性，可能會影響應用程式效能。 建議您務必使用自動斷字功能，除非您需要它。  
  
### <a name="use-figures-carefully"></a>小心使用數字  
 A<xref:System.Windows.Documents.Figure>項目代表可在一頁的內容絕對位置的非固定格式內容的一部分。 在某些情況下，<xref:System.Windows.Documents.Figure>可能會導致整個頁面自動重新設定格式，如果它的位置與已配置外的內容。 您可以藉由其中一個分組不需要重新格式化的可能性降至最低<xref:System.Windows.Documents.Figure>旁邊彼此靠近頂端的內容在固定的頁面大小的案例中宣告的項目。  
  
### <a name="optimal-paragraph"></a>最佳段落  
 最佳段落功能<xref:System.Windows.Documents.FlowDocument>讓的泛空白字元盡量平均分佈，段落配置物件。 根據預設，最佳段落功能已停用。 您可以啟用這項功能將物件設定<xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A>屬性`true`。 不過，啟用此功能會影響應用程式效能。 建議您不要使用最佳段落功能，除非您需要它。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [規劃應用程式效能](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [版面配置和設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)