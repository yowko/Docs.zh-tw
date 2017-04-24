---
title: "GlyphRun 物件和 Glyphs 項目簡介 | Microsoft Docs"
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
  - "印刷樣式圖像 （glyph） 項目"
  - "Glyphs 項目"
  - "GlyphRun 物件"
  - "圖像的文字"
  - "圖像 [WPF]"
  - "印刷樣式，GlyphRun 物件"
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# GlyphRun 物件和 Glyphs 項目簡介
本主題描述<xref:System.Windows.Media.GlyphRun>物件和<xref:System.Windows.Documents.Glyphs>項目。  
  
   
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>GlyphRun 簡介  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供進階的文字支援包括直接存取的圖像 （glyph） 層級標記<xref:System.Windows.Documents.Glyphs>的客戶想要進行攔截和保存格式化後的文字。 這些功能提供重大支援不同的文字轉譯中每個下列案例的需求。  
  
1.  固定格式文件的螢幕顯示。  
  
2.  列印案例。  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]為裝置印表機語言。  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   先前的印表機驅動程式，從輸出[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]固定格式的應用程式。  
  
    -   列印多工緩衝處理格式。  
  
3.  固定格式文件表示法，包括舊版的用戶端[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]和其他電腦的裝置。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>專為固定格式文件呈現及列印案例。                      [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供數個項目的一般配置和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]案例，例如<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.TextBlock>。 如需有關配置和[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]案例，請參閱[WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)。  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>GlyphRun 物件  
 <xref:System.Windows.Media.GlyphRun>物件都代表單一的大小，並以單一呈現樣式的單一字型單一字體一連串的圖像 （glyph）。  
  
 <xref:System.Windows.Media.GlyphRun>包含這兩種字型詳細資料，例如圖像<xref:System.Windows.Documents.Glyphs.Indices%2A>，以及個別的圖像 （glyph） 的位置。 它也包含原始[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]字碼的指標執行所產生的字元-圖像緩衝區位移的對應資訊，以及每個字元和每個字符旗標。  
  
 <xref:System.Windows.Media.GlyphRun>都有對應的高層級<xref:System.Windows.FrameworkElement>，<xref:System.Windows.Documents.Glyphs>。                  <xref:System.Windows.Documents.Glyphs>可用項目樹狀結構中，並在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]表示標記<xref:System.Windows.Media.GlyphRun>輸出。  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Glyphs 項目  
 <xref:System.Windows.Documents.Glyphs>項目代表的輸出<xref:System.Windows.Media.GlyphRun>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 下列標記語法用來描述<xref:System.Windows.Documents.Glyphs>項目。  
  
 [!code-xml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 下列屬性定義對應至範例標記中的前四個屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|指定資源識別元︰ 檔案名稱，Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]，或在應用程式的.exe 或容器資源參考。|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|指定的字型大小以繪圖介面的單位 （預設值為.96 英吋為單位）。|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|指定旗標為粗體和斜體樣式。|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|指定雙向版面配置層級。 偶數和零值表示由左到右的版面配置。奇數值代表從右至左配置。|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>索引屬性  
 <xref:System.Windows.Documents.Glyphs.Indices%2A>屬性是一個字串的圖像 （glyph） 規格。 在一系列圖像形成單一叢集，叢集中的第一個圖像的規格被加上多少圖像 （glyph） 的規格和幾個字碼指標相結合形成叢集。 <xref:System.Windows.Documents.Glyphs.Indices%2A>屬性收集在一個字串中的下列屬性。  
  
-   圖像索引  
  
-   圖像前進距離寬度  
  
-   合併圖像附加向量  
  
-   從程式碼的叢集對應指向圖像 （glyph）  
  
-   圖像 （glyph） 旗標  
  
 每個圖像 （glyph） 規格的格式如下。  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>圖像度量  
 每個圖像 （glyph） 會定義指定如何使其與對齊其他度量<xref:System.Windows.Documents.Glyphs>。 下圖定義兩個不同的圖像 （glyph） 字元的各種印刷品質。  
  
 ![圖像量測繪圖器圖像度量](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>圖像 （glyph） 標記  
 下列程式碼範例示範如何使用的各種屬性<xref:System.Windows.Documents.Glyphs>中的項目[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>另請參閱  
 [在 WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [在 WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)