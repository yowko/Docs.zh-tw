---
title: "Windows Form 和 WPF 屬性對應"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a0af1015747e2f27b19c2cac2c896dd60214264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Form 和 WPF 屬性對應
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]技術有兩個類似但不同屬性的模型。 *屬性對應*支援兩種架構之間的互通性，並提供下列功能：  
  
-   可讓您輕鬆地在主機環境中的相關屬性變更對應至裝載的控制項或元素。  
  
-   提供處理對應最常用的預設屬性。  
  
-   可讓您輕鬆移除覆寫或擴充的預設屬性。  
  
-   可確保主機上的屬性值變更會自動偵測到並轉譯成裝載的控制項或元素。  
  
> [!NOTE]
>  屬性變更事件不會傳播裝載的控制項或項目階層架構。 只有本機屬性的值不會因為直接設定、 樣式、 繼承、 資料繫結或其他機制，變更屬性的值變更時，不會執行屬性翻譯。  
  
 使用<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目和<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>屬性<xref:System.Windows.Forms.Integration.ElementHost>控制存取的屬性對應。  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>與 WindowsFormsHost 元素的屬性對應  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會轉譯預設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性，以其[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]對等項目使用下列轉譯表格。  
  
|裝載 Windows Presentation Foundation|Windows Forms|交互操作的行為|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目集合<xref:System.Windows.Forms.Control.BackColor%2A>裝載控制項的屬性和<xref:System.Windows.Forms.Control.BackgroundImage%2A>裝載控制項的屬性。 使用下列規則來執行對應：<br /><br /> -如果<xref:System.Windows.Controls.Control.Background%2A>是純色，轉換，用來設定<xref:System.Windows.Forms.Control.BackColor%2A>裝載控制項的屬性。 <xref:System.Windows.Forms.Control.BackColor%2A>因為裝載的控制項可以繼承的值，在裝載控制項上未設定屬性<xref:System.Windows.Forms.Control.BackColor%2A>屬性。 **注意：**裝載的控制項不支援透明度。 指派給任何色彩<xref:System.Windows.Forms.Control.BackColor%2A>必須是完全不透明，且為 0xFF alpha 值。 <br /><br /> -如果<xref:System.Windows.Controls.Control.Background%2A>不是純色，<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項建立點陣圖，以從<xref:System.Windows.Controls.Control.Background%2A>屬性。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項指派至這個點陣圖<xref:System.Windows.Forms.Control.BackgroundImage%2A>裝載控制項的屬性。 這會提供類似於透明效果。 **注意：**您可以覆寫此行為，或者您可以移除<xref:System.Windows.Controls.Control.Background%2A>屬性對應。|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|如果不重新指派的預設對應，<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項周遊其祖系階層，直到找到具有上的階其<xref:System.Windows.FrameworkElement.Cursor%2A>屬性集。 這個值會轉換成最接近的對應[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]資料指標。<br /><br /> 如果預設對應<xref:System.Windows.FrameworkElement.ForceCursor%2A>屬性不重新指派，周遊會停止上第一階<xref:System.Windows.FrameworkElement.ForceCursor%2A>設`true`。|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> 對應至 <xref:System.Windows.Forms.RightToLeft.No>。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> 對應至 <xref:System.Windows.Forms.RightToLeft.Yes>。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>未對應。<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> 對應至 <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>裝載控制項上<xref:System.Drawing.Font?displayProperty=nameWithType>|一組[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性則會轉譯為相對應<xref:System.Drawing.Font>。 當其中一個屬性變更時，新<xref:System.Drawing.Font>建立。 如<xref:System.Windows.FontStyles.Normal%2A>:<xref:System.Drawing.FontStyle.Italic>已停用。 如<xref:System.Windows.FontStyles.Italic%2A>或<xref:System.Windows.FontStyles.Oblique%2A>:<xref:System.Drawing.FontStyle.Italic>已啟用。|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>裝載控制項上<xref:System.Drawing.Font?displayProperty=nameWithType>|一組[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性則會轉譯為相對應<xref:System.Drawing.Font>。 當其中一個屬性變更時，新<xref:System.Drawing.Font>建立。 如<xref:System.Windows.FontWeights.Black%2A>， <xref:System.Windows.FontWeights.Bold%2A>， <xref:System.Windows.FontWeights.DemiBold%2A>， <xref:System.Windows.FontWeights.ExtraBold%2A>， <xref:System.Windows.FontWeights.Heavy%2A>， <xref:System.Windows.FontWeights.Medium%2A>， <xref:System.Windows.FontWeights.SemiBold%2A>，或<xref:System.Windows.FontWeights.UltraBold%2A>:<xref:System.Drawing.FontStyle.Bold>已啟用。 如<xref:System.Windows.FontWeights.ExtraLight%2A>， <xref:System.Windows.FontWeights.Light%2A>， <xref:System.Windows.FontWeights.Normal%2A>， <xref:System.Windows.FontWeights.Regular%2A>， <xref:System.Windows.FontWeights.Thin%2A>，或<xref:System.Windows.FontWeights.UltraLight%2A>:<xref:System.Drawing.FontStyle.Bold>已停用。|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|一組[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性則會轉譯為相對應<xref:System.Drawing.Font>。 當其中一個屬性變更時，新<xref:System.Drawing.Font>建立。 裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項會調整大小基礎的字型大小。<br /><br /> 中的字型大小[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]會表示為一個 90-第 6 英吋，並在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]英吋的 1 seventy 秒。 是對應的轉換：<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]size =[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]字型大小 * 72.0 / 96.0。|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A>屬性對應由使用下列規則：<br /><br /> -如果<xref:System.Windows.Controls.Control.Foreground%2A>是<xref:System.Windows.Media.SolidColorBrush>，使用<xref:System.Windows.Media.SolidColorBrush.Color%2A>如<xref:System.Windows.Forms.Control.ForeColor%2A>。<br />-如果<xref:System.Windows.Controls.Control.Foreground%2A>是<xref:System.Windows.Media.GradientBrush>，使用的色彩<xref:System.Windows.Media.GradientStop>具有最低的位移值<xref:System.Windows.Forms.Control.ForeColor%2A>。<br />-若為任何其他<xref:System.Windows.Media.Brush>輸入，保留<xref:System.Windows.Forms.Control.ForeColor%2A>不變。 這表示會使用預設值。|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|當<xref:System.Windows.UIElement.IsEnabled%2A>設定，<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目集合<xref:System.Windows.Forms.Control.Enabled%2A>裝載控制項上的屬性。|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|所有四個值<xref:System.Windows.Forms.Control.Padding%2A>上主控屬性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項設定為相同<xref:System.Windows.Thickness>值。<br /><br /> 值大於<xref:System.Int32.MaxValue>設為<xref:System.Int32.MaxValue>。<br />的值小於<xref:System.Int32.MinValue>設為<xref:System.Int32.MinValue>。|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>對應至<xref:System.Windows.Forms.Control.Visible%2A>  =  `true`。 裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項為可見。 明確設定<xref:System.Windows.Forms.Control.Visible%2A>裝載控制項上的屬性`false`不建議使用。<br />-   <xref:System.Windows.Visibility.Collapsed>對應至<xref:System.Windows.Forms.Control.Visible%2A>  =  `true`或`false`。 裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]不繪製控制項，以及其區域是否摺疊。<br />-   <xref:System.Windows.Visibility.Hidden>: 裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制佔用的空間配置，但看不到。 在此情況下，<xref:System.Windows.Forms.Control.Visible%2A>屬性設定為`true`。 明確設定<xref:System.Windows.Forms.Control.Visible%2A>裝載控制項上的屬性`false`不建議使用。|  
  
 附加的屬性容器項目上完全受到<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目。  
  
 如需詳細資訊，請參閱[逐步解說： 使用 WindowsFormsHost 元素的對應屬性](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)。  
  
## <a name="updates-to-parent-properties"></a>更新父屬性  
 大部分的父屬性的變更會造成裝載的子控制項的通知。 下列清單描述屬性的值變更時不會導致通知。  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 例如，如果您變更的值<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目，<xref:System.Windows.Forms.Control.BackColor%2A>裝載控制項的屬性不會變更。  
  
## <a name="property-mapping-with-the-elementhost-control"></a>使用 ElementHost 控制項的屬性對應  
 下列屬性會提供內建的變更通知。 請勿呼叫<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>方法，當您對應這些屬性：  
  
-   AutoSize  
  
-   背景色彩  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   其他  
  
-   CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Cursor  
  
-   停駐  
  
-   已啟用  
  
-   字型  
  
-   前景色彩  
  
-   位置  
  
-   邊界  
  
-   與邊框距離  
  
-   父代  
  
-   Region  
  
-   RightToLeft  
  
-   大小  
  
-   TabIndex  
  
-   定位點  
  
-   Text  
  
-   可見  
  
 <xref:System.Windows.Forms.Integration.ElementHost>控制項轉譯預設[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]屬性，以其[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]藉由使用下列轉譯資料表的對等項目。  
  
 如需詳細資訊，請參閱[逐步解說： 使用 ElementHost 控制項的對應屬性](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)。  
  
|裝載 Windows Form|Windows Presentation Foundation|交互操作的行為|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) 上裝載的項目|設定這個屬性會強制重新繪製與<xref:System.Windows.Media.ImageBrush>。 如果<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>屬性設定為`false`（預設值），這<xref:System.Windows.Media.ImageBrush>為基礎的外觀<xref:System.Windows.Forms.Integration.ElementHost>控制，包括其<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>，<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>屬性和任何附加小畫家處理常式。<br /><br /> 如果<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>屬性設定為`true`、<xref:System.Windows.Media.ImageBrush>為基礎的外觀<xref:System.Windows.Forms.Integration.ElementHost>控制項的父代，包括在父系的<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>，<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>屬性和任何附加小畫家處理常式。|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) 上裝載的項目|設定這個屬性會導致相同的行為如所述<xref:System.Windows.Forms.Control.BackColor%2A>對應。|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) 上裝載的項目|設定這個屬性會導致相同的行為如所述<xref:System.Windows.Forms.Control.BackColor%2A>對應。|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]標準的資料指標會轉換成對應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]標準的資料指標。 如果[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]不是標準的資料指標，會指派預設值。|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|當<xref:System.Windows.Forms.Control.Enabled%2A>設定，<xref:System.Windows.Forms.Integration.ElementHost>控制集<xref:System.Windows.UIElement.IsEnabled%2A>上裝載的項目屬性。|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A>值會轉譯成一組對應的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]字型屬性。|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>裝載項目上|如果 <xref:System.Drawing.Font.Bold%2A> 為 `true`，則會將 <xref:System.Windows.Controls.Control.FontWeight%2A> 設為 <xref:System.Windows.FontWeights.Bold%2A>。<br /><br /> 如果 <xref:System.Drawing.Font.Bold%2A> 為 `false`，則會將 <xref:System.Windows.Controls.Control.FontWeight%2A> 設為 <xref:System.Windows.FontWeights.Normal%2A>。|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>裝載項目上|如果 <xref:System.Drawing.Font.Italic%2A> 為 `true`，則會將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設為 <xref:System.Windows.FontStyles.Italic%2A>。<br /><br /> 如果 <xref:System.Drawing.Font.Italic%2A> 為 `false`，則會將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設為 <xref:System.Windows.FontStyles.Normal%2A>。|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>裝載項目上|裝載時，才適用<xref:System.Windows.Controls.TextBlock>控制項。|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>裝載項目上|裝載時，才適用<xref:System.Windows.Controls.TextBlock>控制項。|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> 對應至 <xref:System.Windows.FlowDirection.LeftToRight>。<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> 對應至 <xref:System.Windows.FlowDirection.RightToLeft>。|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost>控制集<xref:System.Windows.UIElement.Visibility%2A>屬性上裝載的項目，使用下列規則：<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`對應至<xref:System.Windows.Visibility.Visible>。<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`對應至<xref:System.Windows.Visibility.Hidden>。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [WPF 和 Windows Forms 互通](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)  
 [逐步解說：使用 WindowsFormsHost 元素對應屬性](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)  
 [逐步解說：使用 ElementHost 控制項對應屬性](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)
