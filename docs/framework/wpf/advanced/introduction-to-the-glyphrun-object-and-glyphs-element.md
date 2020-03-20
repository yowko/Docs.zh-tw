---
title: GlyphRun 物件和 Glyphs 項目簡介
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181956"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>GlyphRun 物件和 Glyphs 項目簡介
本主題介紹物件<xref:System.Windows.Media.GlyphRun>和<xref:System.Windows.Documents.Glyphs>元素。  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a>GlyphRun 簡介  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供高級文本支援，包括字形級標記，可直接存取<xref:System.Windows.Documents.Glyphs>希望在格式化後攔截和保留文本的客戶。 這些功能可針對下列每個案例中的不同文字轉譯需求提供重要支援。  
  
1. 固定格式文件的螢幕顯示。  
  
2. 列印案例。  
  
    - 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 作為裝置印表機語言。  
  
    - 微軟XPS文檔編寫器。  
  
    - 以前的印表機驅動程式，從 Win32 應用程式輸出到固定格式。  
  
    - 列印多工緩衝處理格式。  
  
3. 固定格式的文檔表示形式，包括早期版本的 Windows 和其他計算裝置的用戶端。  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs><xref:System.Windows.Media.GlyphRun>並專為固定格式的文檔演示和列印方案而設計。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]為常規佈局和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]方案（如 和<xref:System.Windows.Controls.Label><xref:System.Windows.Controls.TextBlock>）提供了多個元素。 有關佈局和[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]方案的詳細資訊，請參閱[WPF 中的排版](typography-in-wpf.md)。  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a>GlyphRun 物件  
 物件<xref:System.Windows.Media.GlyphRun>表示單個字體單個字體的單個面的字形序列，該字形具有單個呈現樣式。  
  
 <xref:System.Windows.Media.GlyphRun>包括字體詳細資訊，如字形<xref:System.Windows.Documents.Glyphs.Indices%2A>和單個字形位置。 它還包括運行生成的原始 Unicode 代碼點、字元到字形緩衝區偏移映射資訊以及每個字元和每個字形標誌。  
  
 <xref:System.Windows.Media.GlyphRun>具有相應的高級<xref:System.Windows.FrameworkElement>。 <xref:System.Windows.Documents.Glyphs> <xref:System.Windows.Documents.Glyphs>可用於元素樹和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記表示<xref:System.Windows.Media.GlyphRun>輸出。  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a>Glyphs 項目  
 元素<xref:System.Windows.Documents.Glyphs>表示<xref:System.Windows.Media.GlyphRun>in[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的輸出。 以下標記語法用於描述元素<xref:System.Windows.Documents.Glyphs>。  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 下列屬性定義對應至範例標記中的前四個屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|指定資源識別碼：檔案名、Web 統一資源識別項 （URI） 或應用程式 .exe 或容器中的資源引用。|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|指定字型大小 (以繪圖介面單位為單位) (預設值為 .96 英吋)。|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|指定粗體和斜體樣式的旗標。|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|指定雙向配置層級。 偶數值和零值表示由左至右的版面配置，奇數值則表示由右至左的版面配置。|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a>Indices 屬性  
 屬性<xref:System.Windows.Documents.Glyphs.Indices%2A>是一串字形規格。 如果由一系列字符形成單一叢集，則會先指定叢集中的第一個字符，再指定合併多少字符和多少字碼指標來形成叢集。 屬性<xref:System.Windows.Documents.Glyphs.Indices%2A>在一個字串中收集以下屬性。  
  
- 字符索引  
  
- 字符遞增寬度  
  
- 合併字符附加向量  
  
- 從字碼指標到字符的叢集對應  
  
- 字符旗標  
  
 每個字符規格的形式如下。  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a>字符度量  
 每個字形定義指標，指定它如何與其他<xref:System.Windows.Documents.Glyphs>對齊。 下圖定義兩個不同字符字元的各種印刷品質。  
  
 ![圖像量測的繪圖器](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a>字符標記  
 以下代碼示例演示如何在 中使用<xref:System.Windows.Documents.Glyphs>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]元素的各種屬性。  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>另請參閱

- [WPF 中的印刷樣式](typography-in-wpf.md)
- [WPF 中的文件](documents-in-wpf.md)
- [文本](optimizing-performance-text.md)
