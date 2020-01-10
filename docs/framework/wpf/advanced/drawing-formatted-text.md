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
ms.openlocfilehash: c786137a471e0199a8ac60f8d82b4ce440e33b7e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740392"
---
# <a name="drawing-formatted-text"></a>繪製格式化的文字
本主題提供 <xref:System.Windows.Media.FormattedText> 物件功能的總覽。 這個物件提供在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中繪製文字的低階控制項。  

## <a name="technology-overview"></a>技術概觀  
 <xref:System.Windows.Media.FormattedText> 物件可讓您繪製多行文字，而文字中的每個字元都可以個別格式化。 下例顯示已套用多種格式的文字。  
  
 ![使用 FormattedText 物件顯示的文字](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> 針對從 WIN32 API 遷移的開發人員，[ [Win32 遷移](#win32_migration)] 區段中的資料表會列出 win32 DrawText 旗標和 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中的近似對等用法。  
  
### <a name="reasons-for-using-formatted-text"></a>使用格式化文字的原因  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製到螢幕的控制項。 每個控制項都是不同案例的目標，且有自己的功能與限制清單。 一般而言，需要有限的文字支援時（例如 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]中的簡短句子），應該使用 <xref:System.Windows.Controls.TextBlock> 元素。 當需要最少的文字支援時，可以使用 <xref:System.Windows.Controls.Label>。 如需詳細資訊，請參閱 [WPF 中的文件](documents-in-wpf.md)。  
  
 <xref:System.Windows.Media.FormattedText> 物件提供比 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 文字控制項更大的文字格式功能，而且在您想要使用文字做為裝飾元素的情況下很有用。 如需詳細資訊，請參閱[將格式化文字轉換成幾何](#converting_formatted_text)一節。  
  
 此外，<xref:System.Windows.Media.FormattedText> 物件也適用于建立文字導向的 <xref:System.Windows.Media.DrawingVisual>衍生物件。 <xref:System.Windows.Media.DrawingVisual> 是輕量繪圖類別，可用來呈現圖形、影像或文字。 如需詳細資訊，請參閱[使用 DrawingVisuals 範例的點擊測試](https://go.microsoft.com/fwlink/?LinkID=159994)。  
  
## <a name="using-the-formattedtext-object"></a>使用 FormattedText 物件  
 若要建立格式化的文字，請呼叫 <xref:System.Windows.Media.FormattedText.%23ctor%2A> 的函式，以建立 <xref:System.Windows.Media.FormattedText> 物件。 建立初始的格式化文字字串之後，您就可以套用一系列的格式化樣式。  
  
 使用 [<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>] 屬性，將文字限制為特定的寬度。 文字會自動換行，避免超出指定的寬度。 使用 [<xref:System.Windows.Media.FormattedText.MaxTextHeight%2A>] 屬性，將文字限制為特定的高度。 超過指定高度的文字會顯示省略符號 "…"。  
  
 ![以自動換行和省略號顯示的文字。](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 您可以將多個格式化樣式套用到一或多個字元。 例如，您可以同時呼叫 <xref:System.Windows.Media.FormattedText.SetFontSize%2A> 和 <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> 方法，以變更文字中前五個字元的格式。  
  
 下列程式碼範例會建立 <xref:System.Windows.Media.FormattedText> 物件，然後將數個格式樣式套用至文字。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>字型大小測量單位  
 如同 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中的其他文字物件，<xref:System.Windows.Media.FormattedText> 物件會使用裝置獨立圖元作為測量單位。 不過，大部分的 Win32 應用程式會使用點做為測量單位。 如果您想要在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中使用以點為單位的顯示文字，您必須將裝置獨立單位（每單位 1/計算1/96 英寸）轉換成點。 下列程式碼範例會示範如何執行此轉換。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>將格式化文字轉換成幾何  
 您可以將格式化的文字轉換成 <xref:System.Windows.Media.Geometry> 物件，讓您建立其他類型的視覺效果文字。 例如，您可以根據文字字串的外框來建立 <xref:System.Windows.Media.Geometry> 物件。  
  
 ![以線性漸層筆刷繪製外框的文字](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 下列範例示範數種方式，可透過修改筆劃、填滿和反白顯示轉換的文字，來建立有趣的視覺效果。  
  
 ![使用不同填色和筆觸色彩的文字](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![影像筆刷套用至筆觸的文字](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![影像筆刷套用至筆劃和反白顯示的文字](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 當文字轉換成 <xref:System.Windows.Media.Geometry> 物件時，它就不再是字元的集合—您無法修改文字字串中的字元。 不過，您可以修改其筆劃與填滿屬性來影響轉換文字的外觀。 筆劃是指轉換文字的外框，填滿是指轉換文字外框內的區域。 如需詳細資訊，請參閱[建立外框文字](how-to-create-outlined-text.md)。  
  
 您也可以將格式化的文字轉換成 <xref:System.Windows.Media.PathGeometry> 物件，並使用物件來反白顯示文字。 例如，您可以將動畫套用至 <xref:System.Windows.Media.PathGeometry> 物件，讓動畫遵循格式化文字的外框。  
  
 下列範例會顯示已轉換成 <xref:System.Windows.Media.PathGeometry> 物件的已格式化文字。 以動畫顯示的橢圓形會沿著轉譯文字的筆劃路徑行進。  
  
 ![遵循文字之路徑幾何的範圍](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
遵循文字之路徑幾何的範圍  
  
 如需詳細資訊，請參閱[如何：建立文字的 PathGeometry 動畫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))。  
  
 轉換成 <xref:System.Windows.Media.PathGeometry> 物件之後，您可以為格式化的文字建立其他有趣的用法。 例如，您可以裁剪視訊以顯示在其中。  
  
 ![顯示於文字之路徑幾何中的視訊](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Win32 移轉  
 繪製文字的 <xref:System.Windows.Media.FormattedText> 功能與 Win32 DrawText 函式的功能類似。 針對從 WIN32 API 遷移的開發人員，下表列出 Win32 DrawText 旗標和 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中的近似對等用法。  
  
|DrawText 旗標|WPF 對等項目|注意事項|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|使用 <xref:System.Windows.Media.FormattedText.Height%2A> 屬性來計算適當的 Win32 DrawText ' y ' 位置。|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>、 <xref:System.Windows.Media.FormattedText.Width%2A>|使用 <xref:System.Windows.Media.FormattedText.Height%2A> 和 <xref:System.Windows.Media.FormattedText.Width%2A> 屬性來計算輸出矩形。|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|使用 [<xref:System.Windows.Media.FormattedText.TextAlignment%2A>] 屬性，並將值設定為 [<xref:System.Windows.TextAlignment.Center>]。|  
|DT_EDITCONTROL|None|非必要 架構編輯控制項中的空間寬度和最後一行轉譯相同。|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|使用具有 <xref:System.Windows.TextTrimming.CharacterEllipsis>值的 <xref:System.Windows.Media.FormattedText.Trimming%2A> 屬性。<br /><br /> 使用 <xref:System.Windows.TextTrimming.WordEllipsis> 來取得具有 DT_WORD_ELIPSIS 結尾省略號的 Win32 DT_END_ELLIPSIS-在此情況下，字元省略號只會出現在不符合單一行的單字上。|  
|DT_EXPAND_TABS|None|非必要 索引標籤每 4 ems 就會自動展開至停駐點，大約 8 個語言獨立字元的寬度。|  
|DT_EXTERNALLEADING|None|非必要 行距中一律包含外部前置。 使用 <xref:System.Windows.Media.FormattedText.LineHeight%2A> 屬性來建立使用者定義的行間距。|  
|DT_HIDEPREFIX|None|不支援。 請先從字串中移除 ' & '，然後再建立 <xref:System.Windows.Media.FormattedText> 物件。|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|這是預設的文字對齊方式。 使用 [<xref:System.Windows.Media.FormattedText.TextAlignment%2A>] 屬性，並將值設定為 [<xref:System.Windows.TextAlignment.Left>]。 (僅限 WPF)|  
|DT_MODIFYSTRING|None|不支援。|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|不自動執行裁剪。 如果您想要裁剪文字，請使用 [<xref:System.Windows.Media.Visual.VisualClip%2A>] 屬性。|  
|DT_NOFULLWIDTHCHARBREAK|None|不支援。|  
|DT_NOPREFIX|None|非必要 字串中的 '&' 字元一律視為一般字元。|  
|DT_PATHELLIPSIS|None|使用具有 <xref:System.Windows.TextTrimming.WordEllipsis>值的 <xref:System.Windows.Media.FormattedText.Trimming%2A> 屬性。|  
|DT_PREFIX|None|不支援。 如果您想要使用底線做為文字（例如快速鍵或連結），請使用 <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> 方法。|  
|DT_PREFIXONLY|None|不支援。|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|使用 [<xref:System.Windows.Media.FormattedText.TextAlignment%2A>] 屬性，並將值設定為 [<xref:System.Windows.TextAlignment.Right>]。 (僅限 WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|將 <xref:System.Windows.Media.FormattedText.FlowDirection%2A> 屬性設定為 <xref:System.Windows.FlowDirection.RightToLeft>。|  
|DT_SINGLELINE|None|非必要 除非已設定 <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> 屬性，或者文字包含一個換行字元（CR/LF），否則 <xref:System.Windows.Media.FormattedText> 物件的行為都是單一線條控制項。|  
|DT_TABSTOP|None|不支援使用者定義的定位停駐點位置。|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|非必要 預設值為靠上對齊。 您可以使用 <xref:System.Windows.Media.FormattedText.Height%2A> 屬性來定義其他垂直定位值，以計算適當的 Win32 DrawText ' y ' 位置。|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|使用 <xref:System.Windows.Media.FormattedText.Height%2A> 屬性來計算適當的 Win32 DrawText ' y ' 位置。|  
|DT_WORDBREAK|None|非必要 斷詞會使用 <xref:System.Windows.Media.FormattedText> 物件自動發生。 您無法停用它。|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|使用具有 <xref:System.Windows.TextTrimming.WordEllipsis>值的 <xref:System.Windows.Media.FormattedText.Trimming%2A> 屬性。|  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Media.FormattedText>
- [WPF 中的文件](documents-in-wpf.md)
- [WPF 中的印刷樣式](typography-in-wpf.md)
- [建立外框文字](how-to-create-outlined-text.md)
- [如何︰建立文字的 PathGeometry 動畫](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
