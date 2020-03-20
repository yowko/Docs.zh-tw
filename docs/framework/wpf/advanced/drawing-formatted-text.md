---
title: 繪製格式化的文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: 1e82795afbdd5b1b0a05f95600ebdb92fc134b7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186558"
---
# <a name="drawing-formatted-text"></a>繪製格式化的文字
本主題概述了<xref:System.Windows.Media.FormattedText>物件的功能。 這個物件提供在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中繪製文字的低階控制項。  

## <a name="technology-overview"></a>技術概觀  
 該<xref:System.Windows.Media.FormattedText>物件允許您繪製多行文本，其中文本中的每個字元都可以單獨設置格式。 下例顯示已套用多種格式的文字。  
  
 ![使用 FormattedText 物件顯示的文字](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> 對於從 WIN32 API 遷移的開發人員[，Win32 遷移](#win32_migration)部分中的表列出了 Win32 DrawText 標誌和 中的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]近似等效標誌。  
  
### <a name="reasons-for-using-formatted-text"></a>使用格式化文字的原因  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製到螢幕的控制項。 每個控制項都是針對不同案例，而且有自己的功能與限制清單。 通常，當需要<xref:System.Windows.Controls.TextBlock>有限的文本支援時，應使用元素，例如 中的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]簡短句子。 <xref:System.Windows.Controls.Label>可在需要最少的文本支援時使用。 如需詳細資訊，請參閱 [WPF 中的文件](documents-in-wpf.md)。  
  
 該<xref:System.Windows.Media.FormattedText>物件提供的文本格式功能比[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]文本控制項更大，並且在希望將文本用作裝飾元素的情況下非常有用。 如需詳細資訊，請參閱[將格式化文字轉換成幾何](#converting_formatted_text)一節。  
  
 此外，該<xref:System.Windows.Media.FormattedText>物件可用於創建面向<xref:System.Windows.Media.DrawingVisual>文本的派生物件。 <xref:System.Windows.Media.DrawingVisual>是用於渲染形狀、圖像或文本的羽量級繪圖類。 如需詳細資訊，請參閱[使用 DrawingVisuals 範例的點擊測試](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)。  
  
## <a name="using-the-formattedtext-object"></a>使用 FormattedText 物件  
 要創建格式化的文本，<xref:System.Windows.Media.FormattedText.%23ctor%2A>請調用建構函式以創建物件。 <xref:System.Windows.Media.FormattedText> 建立初始的格式化文字字串之後，您就可以套用一系列的格式化樣式。  
  
 使用<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>屬性將文本限制為特定寬度。 文字會自動換行，避免超出指定的寬度。 使用<xref:System.Windows.Media.FormattedText.MaxTextHeight%2A>屬性將文本限制到特定高度。 超過指定高度的文字會顯示省略符號 "…"。  
  
 ![顯示帶有字包和省略號的文本。](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)
  
 您可以將多個格式化樣式套用到一或多個字元。 例如，可以同時調用 和<xref:System.Windows.Media.FormattedText.SetFontSize%2A><xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>方法來更改文本中前五個字元的格式。  
  
 以下代碼示例創建一個<xref:System.Windows.Media.FormattedText>物件，然後將多個格式樣式應用於文本。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>字型大小測量單位  
 與[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中的其他文本物件一樣，<xref:System.Windows.Media.FormattedText>物件使用與設備無關的圖元作為度量單位。 但是，大多數 Win32 應用程式使用點作為度量單位。 如果要在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中以點為單位使用顯示文本，則需要將獨立于設備的單位（單位 1/96 英寸）轉換為點。 下列程式碼範例會示範如何執行此轉換。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>
### <a name="converting-formatted-text-to-a-geometry"></a>將格式化文字轉換成幾何  
 您可以將格式化的文本轉換為<xref:System.Windows.Media.Geometry>物件，從而創建其他類型的視覺上有趣的文本。 例如，可以基於文本字串的<xref:System.Windows.Media.Geometry>輪廓創建物件。  
  
 ![以線性漸層筆刷繪製外框的文字](./media/typography-in-wpf/text-outline-linear-gradient.jpg)
  
 下列範例示範數種方式，可透過修改筆劃、填滿和反白顯示轉換的文字，來建立有趣的視覺效果。  
  
 ![使用不同填色和筆觸色彩的文字](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![影像筆刷套用至筆觸的文字](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![應用影像筆刷進行描邊和高光的文本](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 將文本轉換為物件時<xref:System.Windows.Media.Geometry>，它不再是字元的集合，無法修改文本字串中的字元。 不過，您可以修改其筆劃與填滿屬性來影響轉換文字的外觀。 筆劃是指轉換文字的外框，填滿是指轉換文字外框內的區域。 如需詳細資訊，請參閱[建立外框文字](how-to-create-outlined-text.md)。  
  
 您還可以將格式化的文本轉換為<xref:System.Windows.Media.PathGeometry>物件，並使用該物件突出顯示文本。 例如，您可以將動畫應用於物件，<xref:System.Windows.Media.PathGeometry>以便動畫遵循格式化文字的輪廓。  
  
 下面的示例顯示已轉換為<xref:System.Windows.Media.PathGeometry>物件的格式化文字。 以動畫顯示的橢圓形會沿著轉譯文字的筆劃路徑行進。  
  
 ![遵循文字之路徑幾何的範圍](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
遵循文字之路徑幾何的範圍  
  
 如需詳細資訊，請參閱[如何：建立文字的 PathGeometry 動畫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))。  
  
 將格式化文字轉換為<xref:System.Windows.Media.PathGeometry>物件後，可以為它創建其他有趣的用途。 例如，您可以裁剪視訊以顯示在其中。  
  
 ![顯示於文字之路徑幾何中的視訊](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>
## <a name="win32-migration"></a>Win32 移轉  
 繪圖文本的功能<xref:System.Windows.Media.FormattedText>類似于 Win32 繪製文本功能的功能。 對於從 WIN32 API 遷移的開發人員，下表列出了 Win32 DrawText 標誌和 中的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]近似等效標誌。  
  
|DrawText 旗標|WPF 對等項目|注意|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|使用<xref:System.Windows.Media.FormattedText.Height%2A>屬性計算適當的 Win32 繪製文本"y"位置。|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|使用<xref:System.Windows.Media.FormattedText.Height%2A>和<xref:System.Windows.Media.FormattedText.Width%2A>屬性計算輸出矩形。|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|將<xref:System.Windows.Media.FormattedText.TextAlignment%2A>值設置為 的屬性使用<xref:System.Windows.TextAlignment.Center>。|  
|DT_EDITCONTROL|None|不需要。 架構編輯控制項中的空間寬度和最後一行轉譯相同。|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|使用<xref:System.Windows.Media.FormattedText.Trimming%2A>具有 值<xref:System.Windows.TextTrimming.CharacterEllipsis>的屬性 。<br /><br /> 用於<xref:System.Windows.TextTrimming.WordEllipsis>使用DT_WORD_ELIPSIS端橢圓獲取 Win32 DT_END_ELLIPSIS — 在這種情況下，字元省略號僅發生在不適合單行的單詞上。|  
|DT_EXPAND_TABS|None|不需要。 索引標籤每 4 ems 就會自動展開至停駐點，大約 8 個語言獨立字元的寬度。|  
|DT_EXTERNALLEADING|None|不需要。 行距中一律包含外部前置。 使用<xref:System.Windows.Media.FormattedText.LineHeight%2A>屬性創建使用者定義的行間距。|  
|DT_HIDEPREFIX|None|不支援。 在構造<xref:System.Windows.Media.FormattedText>物件之前，請從字串中刪除"&"。|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|這是預設的文字對齊方式。 將<xref:System.Windows.Media.FormattedText.TextAlignment%2A>值設置為 的屬性使用<xref:System.Windows.TextAlignment.Left>。 (僅限 WPF)|  
|DT_MODIFYSTRING|None|不支援。|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|不自動執行裁剪。 如果要剪輯文本，請使用 屬性<xref:System.Windows.Media.Visual.VisualClip%2A>。|  
|DT_NOFULLWIDTHCHARBREAK|None|不支援。|  
|DT_NOPREFIX|None|不需要。 字串中的 '&' 字元一律視為一般字元。|  
|DT_PATHELLIPSIS|None|使用<xref:System.Windows.Media.FormattedText.Trimming%2A>具有 值<xref:System.Windows.TextTrimming.WordEllipsis>的屬性 。|  
|DT_PREFIX|None|不支援。 如果要對文本（如快速鍵或連結）使用底線，請使用 方法<xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>。|  
|DT_PREFIXONLY|None|不支援。|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|將<xref:System.Windows.Media.FormattedText.TextAlignment%2A>值設置為 的屬性使用<xref:System.Windows.TextAlignment.Right>。 (僅限 WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|將 <xref:System.Windows.Media.FormattedText.FlowDirection%2A> 屬性設為 <xref:System.Windows.FlowDirection.RightToLeft>。|  
|DT_SINGLELINE|None|不需要。 <xref:System.Windows.Media.FormattedText>物件作為單行控制項行，除非設置<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>屬性或文本包含回車/換行 （CR/LF）。|  
|DT_TABSTOP|None|不支援使用者定義的定位停駐點位置。|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|不需要。 預設值為靠上對齊。 其他垂直定位值可以通過使用 屬性<xref:System.Windows.Media.FormattedText.Height%2A>計算適當的 Win32 DrawText 'y' 位置來定義。|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|使用<xref:System.Windows.Media.FormattedText.Height%2A>屬性計算適當的 Win32 繪製文本"y"位置。|  
|DT_WORDBREAK|None|不需要。 <xref:System.Windows.Media.FormattedText>物件會自動發生斷字。 您無法停用它。|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|使用<xref:System.Windows.Media.FormattedText.Trimming%2A>具有 值<xref:System.Windows.TextTrimming.WordEllipsis>的屬性 。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.FormattedText>
- [WPF 中的文件](documents-in-wpf.md)
- [WPF 中的印刷樣式](typography-in-wpf.md)
- [建立外框文字](how-to-create-outlined-text.md)
- [如何︰建立文字的 PathGeometry 動畫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
