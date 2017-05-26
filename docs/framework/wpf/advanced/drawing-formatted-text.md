---
title: "繪製格式化的文字 | Microsoft Docs"
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
  - "繪製, 格式化文字"
  - "格式化文字 [WPF]"
  - "文字 [WPF]"
  - "印刷樣式, 繪製格式化的文字"
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 繪製格式化的文字
本主題概要說明 <xref:System.Windows.Media.FormattedText> 物件的功能。  這個物件提供在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中繪製文字的低階控制項。  
  
   
  
<a name="technology_overview"></a>   
## 技術概觀  
 <xref:System.Windows.Media.FormattedText> 物件可讓您繪製多行文字，文字中的每個字元都可以個別格式化。  下列範例顯示已套用幾種格式的文字。  
  
 ![使用 FormattedText 物件顯示的文字](../../../../docs/framework/wpf/advanced/media/formattedtext01.png "FormattedText01")  
使用 FormattedText 方法的顯示文字  
  
> [!NOTE]
>  [Win32 移轉](#win32_migration)一節為從 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API 進行移轉的程式開發人員，列出 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 旗標和 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的近似對等項目。  
  
### 使用格式化文字的原因  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製至螢幕的控制項。  每個控制項都鎖定不同的案例，而且擁有自己的功能與限制清單。  一般而言，在需要有限的文字支援 \(例如[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中的簡短句子\) 時，應該使用 <xref:System.Windows.Controls.TextBlock> 項目。  而在需要最少文字支援時，則可使用 <xref:System.Windows.Controls.Label>。  如需詳細資訊，請參閱 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)。  
  
 <xref:System.Windows.Media.FormattedText> 物件提供的文字格式化功能比 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 文字控制項更強大，而且在您想要使用文字做為裝飾項目的情況下十分有用。如需詳細資訊，請參閱後面的[將格式化文字轉換為幾何圖案](#converting_formatted_text)一節。  
  
 此外，<xref:System.Windows.Media.FormattedText> 物件適合用來建立文字導向的 <xref:System.Windows.Media.DrawingVisual> 衍生物件。  <xref:System.Windows.Media.DrawingVisual> 為輕量型繪圖類別，可用於呈現圖案、影像或文字。  如需詳細資訊，請參閱[使用 DrawingVisual 進行點擊測試範例](http://go.microsoft.com/fwlink/?LinkID=159994) \(英文\)。  
  
<a name="using_the_formattedtext_object"></a>   
## 使用 FormattedText 物件  
 若要建立格式化文字，請呼叫 <xref:System.Windows.Media.FormattedText.%23ctor%2A> 建構函式建立 <xref:System.Windows.Media.FormattedText> 物件。  建立初始格式化文字字串之後，就可以套用某個範圍的格式化樣式。  
  
 請使用 <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> 屬性將文字限制為特定寬度。  文字將會自動換行，以避免超過指定的寬度。  請使用 <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> 屬性將文字限制為特定高度。  超過指定高度的文字將會顯示省略符號 "…"。  
  
 ![使用 FormattedText 物件顯示的文字](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
顯示自動換行和自略符號的顯示文字  
  
 您可以將多個格式化樣式套用至一個或多個字元。  例如，您可以同時呼叫 <xref:System.Windows.Media.FormattedText.SetFontSize%2A> 和 <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> 方法，變更文字前五個字元的格式。  
  
 下列程式碼範例會建立 <xref:System.Windows.Media.FormattedText> 物件，並在文字上套用幾個格式化樣式。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### 字型大小測量單位  
 如同 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中的其他文字物件，<xref:System.Windows.Media.FormattedText> 物件也會使用與裝置無關的像素做為測量單位。  不過，大部分的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式都會使用點做為測量單位。  如果您想在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中使用以點為單位的顯示文字，必須將[!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] 轉換為點。  下列程式碼範例示範如何執行這個轉換動作。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### 將格式化文字轉換為幾何圖案  
 您可以將格式化文字轉換為 <xref:System.Windows.Media.Geometry> 物件，以便建立具有有趣外觀的其他文字類型。  例如，您可以根據文字字串的外框來建立 <xref:System.Windows.Media.Geometry> 物件。  
  
 ![以線性漸層筆刷繪製外框的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext02.png "OutlinedText02")  
使用線形漸層筆刷的文字外框  
  
 下列範例說明藉由修改轉換文字的筆劃、填滿和反白顯示，建立有趣視覺效果的多個方法。  
  
 ![使用不同填色和筆觸色彩的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext03.png "OutlinedText03")  
將筆劃和填滿設定為不同色彩的範例  
  
 ![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext04.png "OutlinedText04")  
在筆劃上套用影像筆刷的範例  
  
 ![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext05.png "OutlinedText05")  
在筆劃和反白顯示上套用影像筆刷的範例  
  
 將文字轉換為 <xref:System.Windows.Media.Geometry> 物件後，文字就不再是字元的集合，因此您無法修改文字字串中的字元。  不過，您可以透過修改轉換後文字的描邊和填滿屬性，影響文字的外觀。  描邊是指轉換後文字的外框，填滿則是指轉換後文字之外框內的區域。  如需詳細資訊，請參閱 [建立外框文字](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)。  
  
 您也可以將格式化文字轉換為 <xref:System.Windows.Media.PathGeometry> 物件，然後使用這個物件來反白顯示文字。  例如，您可以將動畫套用至 <xref:System.Windows.Media.PathGeometry> 物件，讓動畫沿著格式化文字的外框行進。  
  
 下列範例顯示已轉換為 <xref:System.Windows.Media.PathGeometry> 物件的格式化文字。  動畫中顯示的橢圓形會沿著呈現文字的描邊路徑行進。  
  
 ![遵循文字之路徑幾何的範圍](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.png "TextPathGeometry01")  
沿著文字路徑幾何行進的球體  
  
 如需詳細資訊，請參閱 [How to: Create a PathGeometry Animation for Text](http://msdn.microsoft.com/zh-tw/29f8051e-798a-463f-a926-a099a99e9c67)。  
  
 將格式化文字轉換為 <xref:System.Windows.Media.PathGeometry> 文字之後，您就可以建立格式化文字的其他有趣用法。  例如，您可以裁剪視訊以便在格式化文字內顯示。  
  
 ![顯示於文字之路徑幾何中的視訊](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
文字路徑幾何中顯示的視訊  
  
<a name="win32_migration"></a>   
## Win32 移轉  
 用來繪製文字的 <xref:System.Windows.Media.FormattedText> 功能與 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 函式的功能類似。  下表針對從 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API 進行移轉的程式開發人員，列出 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 旗標和 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的近似對等項目。  
  
|DrawText 旗標|WPF 對等用法|備註|  
|-----------------|--------------|--------|  
|DT\_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|請使用 <xref:System.Windows.Media.FormattedText.Height%2A> 屬性計算適當的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' 位置。|  
|DT\_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|請使用 <xref:System.Windows.Media.FormattedText.Height%2A> 和 <xref:System.Windows.Media.FormattedText.Width%2A> 屬性計算輸出矩形。|  
|DT\_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|請使用 <xref:System.Windows.Media.FormattedText.TextAlignment%2A> 屬性，並將值設定為 <xref:System.Windows.TextAlignment>。|  
|DT\_EDITCONTROL|None|不需要  空間寬度和最後一行呈現與架構編輯控制項相同。|  
|DT\_END\_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|請使用值為 <xref:System.Windows.TextTrimming> 的 <xref:System.Windows.Media.FormattedText.Trimming%2A> 屬性。<br /><br /> 請使用 <xref:System.Windows.TextTrimming> 取得 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT\_END\_ELLIPSIS 與 DT\_WORD\_ELIPSIS 結尾省略符號；在這種情況下，字元省略符號只會出現在無法以單行顯示的文字。|  
|DT\_EXPAND\_TABS|None|不需要  定位點會自動擴展成每隔 4 em \(約等於 8 個語言無關字元的寬度\) 停駐一次。|  
|DT\_EXTERNALLEADING|None|不需要  行距中一律包含外部前置字元。  請使用 <xref:System.Windows.Media.FormattedText.LineHeight%2A> 屬性建立使用者定義的行距。|  
|DT\_HIDEPREFIX|None|不支援。  建構 <xref:System.Windows.Media.FormattedText> 物件之前，請先從字串移除 '&'。|  
|DT\_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|這是預設文字對齊方式。  請使用 <xref:System.Windows.Media.FormattedText.TextAlignment%2A> 屬性，並將值設定為 <xref:System.Windows.TextAlignment> \(僅適用於 WPF\)。|  
|DT\_MODIFYSTRING|None|不支援。|  
|DT\_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|裁剪動作不會自動執行。  如果要裁剪文字，請使用 <xref:System.Windows.Media.Visual.VisualClip%2A> 屬性。|  
|DT\_NOFULLWIDTHCHARBREAK|None|不支援。|  
|DT\_NOPREFIX|None|不需要  字串中的 '&' 字元一律當做一般字元處理。|  
|DT\_PATHELLIPSIS|None|請使用值為 <xref:System.Windows.TextTrimming> 的 <xref:System.Windows.Media.FormattedText.Trimming%2A> 屬性。|  
|DT\_PREFIX|None|不支援。  如果要在文字 \(例如快速鍵或連結\) 中使用底線，請使用 <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> 方法。|  
|DT\_PREFIXONLY|None|不支援。|  
|DT\_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|請使用 <xref:System.Windows.Media.FormattedText.TextAlignment%2A> 屬性，並將值設定為 <xref:System.Windows.TextAlignment> \(僅適用於 WPF\)。|  
|DT\_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|將 <xref:System.Windows.Media.FormattedText.FlowDirection%2A> 屬性設為 <xref:System.Windows.FlowDirection>。|  
|DT\_SINGLELINE|None|不需要  除非設定 <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> 屬性或是文字中包含歸位字元\/換行字元 \(CR\/LF\)，否則 <xref:System.Windows.Media.FormattedText> 物件的運作方式與單行控制項相同。|  
|DT\_TABSTOP|None|不支援使用者定義的定位停駐點 \(Tab Stop\) 位置。|  
|DT\_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|不需要  預設為靠上對齊。  透過使用 <xref:System.Windows.Media.FormattedText.Height%2A> 屬性計算適當的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' 位置，即可定義其他垂直定位值。|  
|DT\_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|請使用 <xref:System.Windows.Media.FormattedText.Height%2A> 屬性計算適當的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' 位置。|  
|DT\_WORDBREAK|None|不需要  <xref:System.Windows.Media.FormattedText> 物件可自動斷字。  您不能停用它。|  
|DT\_WORD\_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|請使用值為 <xref:System.Windows.TextTrimming> 的 <xref:System.Windows.Media.FormattedText.Trimming%2A> 屬性。|  
  
## 請參閱  
 <xref:System.Windows.Media.FormattedText>   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [建立外框文字](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)   
 [How to: Create a PathGeometry Animation for Text](http://msdn.microsoft.com/zh-tw/29f8051e-798a-463f-a926-a099a99e9c67)