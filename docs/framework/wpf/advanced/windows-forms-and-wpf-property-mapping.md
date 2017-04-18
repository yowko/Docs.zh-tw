---
title: "Windows Form 和 WPF 屬性對應 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "互通性 [WPF], Windows Form"
  - "屬性對應 [WPF 互通性]"
  - "Windows Form [WPF], 互通性"
  - "Windows Form, WPF 互通"
  - "WindowsFormsHost 項目屬性對應"
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Windows Form 和 WPF 屬性對應
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 技術有兩種類似但不同的屬性模型。  「*屬性對應*」\(Property Mapping\) 支援兩個架構之間的互通操作，並提供下列功能：  
  
-   輕鬆將主機環境中的相關屬性變更對應至所裝載的控制項或項目。  
  
-   提供用以對應最常用屬性的預設處理。  
  
-   可以輕鬆移除、覆寫或擴充預設屬性。  
  
-   確保會自動偵測主應用程式 \(Host\) 上的屬性值變更並加以轉譯成所裝載的控制項或項目。  
  
> [!NOTE]
>  屬性變更事件不會在裝載控制項或項目階層中向上傳播。  如果屬性的本機值並未因為直接設定、樣式、繼承 \(Inheritance\)、資料繫結或其他會變更屬性值的機制而變更，則不會執行屬性轉譯。  
  
 對 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> 屬性，以及對 <xref:System.Windows.Forms.Integration.ElementHost> 控制項使用 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> 屬性，即可存取屬性對應。  
  
## WindowsFormsHost 項目的屬性對應  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會根據下列轉譯表，將預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性轉譯為其 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 對等用法。  
  
|Windows Presentation Foundation 裝載|Windows Form|互通行為|  
|----------------------------------------|------------------|----------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會設定裝載之控制項的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性和裝載之控制項的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性。  系統會使用下列規則來執行對應：<br /><br /> -   如果 <xref:System.Windows.Controls.Control.Background%2A> 為純色，則會將其轉換並用於設定裝載之控制項的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性。  由於裝載的控制項可以繼承 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性的值，所以不會對裝載的控制項設定 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性。 **Note:**  裝載的控制項不支援透明度。  任何指派給 <xref:System.Windows.Forms.Control.BackColor%2A> 的色彩都必須完全不透明，其 Alpha 值為 0xFF。 <br /><br /> -   如果 <xref:System.Windows.Controls.Control.Background%2A> 不是純色，則 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會從 <xref:System.Windows.Controls.Control.Background%2A> 屬性建立點陣圖。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會將此點陣圖指派給已裝載之控制項的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性。  這可提供類似透明度的效果。 **Note:**  您可以覆寫這個行為，也可以移除 <xref:System.Windows.Controls.Control.Background%2A> 屬性對應。|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|如果尚未重新指派預設對應，則 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會周遊其祖系階層，直到它找到已設定其 <xref:System.Windows.FrameworkElement.Cursor%2A> 屬性的祖系為止。  然後會將這個值轉譯成最接近的對應 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 游標。<br /><br /> 如果尚未重新指派 <xref:System.Windows.FrameworkElement.ForceCursor%2A> 屬性的預設對應，則周遊作業會停在 <xref:System.Windows.FrameworkElement.ForceCursor%2A> 設定為 `true` 的第一個祖系上。|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> \(<xref:System.Windows.FlowDirection?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> \(<xref:System.Windows.Forms.RightToLeft?displayProperty=fullName>\)|<xref:System.Windows.FlowDirection> 對應到 <xref:System.Windows.Forms.RightToLeft>。<br /><br /> <xref:System.Windows.FlowDirection> 對應到 <xref:System.Windows.Forms.RightToLeft>。<br /><br /> <xref:System.Windows.Forms.RightToLeft> 沒有對應。<br /><br /> <xref:System.Windows.FlowDirection?displayProperty=fullName> 對應到 <xref:System.Windows.Forms.RightToLeft?displayProperty=fullName>。|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|所裝載控制項 <xref:System.Drawing.Font?displayProperty=fullName> 的 <xref:System.Drawing.Font.Style%2A>|這組 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性會轉譯為對應的 <xref:System.Drawing.Font>。  當其中一個屬性變更時，便會建立新的 <xref:System.Drawing.Font>。  如果是 <xref:System.Windows.FontStyles.Normal%2A>：<xref:System.Drawing.FontStyle> 已停用。  如果是 <xref:System.Windows.FontStyles.Italic%2A> 或 <xref:System.Windows.FontStyles.Oblique%2A>：<xref:System.Drawing.FontStyle> 已啟用。|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|所裝載控制項 <xref:System.Drawing.Font?displayProperty=fullName> 的 <xref:System.Drawing.Font.Style%2A>|這組 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性會轉譯為對應的 <xref:System.Drawing.Font>。  當其中一個屬性變更時，便會建立新的 <xref:System.Drawing.Font>。  如果是 <xref:System.Windows.FontWeights.Black%2A>、<xref:System.Windows.FontWeights.Bold%2A>、<xref:System.Windows.FontWeights.DemiBold%2A>、<xref:System.Windows.FontWeights.ExtraBold%2A>、<xref:System.Windows.FontWeights.Heavy%2A>、<xref:System.Windows.FontWeights.Medium%2A>、<xref:System.Windows.FontWeights.SemiBold%2A> 或 <xref:System.Windows.FontWeights.UltraBold%2A>：<xref:System.Drawing.FontStyle> 已啟用。  如果是 <xref:System.Windows.FontWeights.ExtraLight%2A>、<xref:System.Windows.FontWeights.Light%2A>、<xref:System.Windows.FontWeights.Normal%2A>、<xref:System.Windows.FontWeights.Regular%2A>、<xref:System.Windows.FontWeights.Thin%2A> 或 <xref:System.Windows.FontWeights.UltraLight%2A>：<xref:System.Drawing.FontStyle> 已停用。|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> \(<xref:System.Drawing.Font?displayProperty=fullName>\)|這組 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性會轉譯為對應的 <xref:System.Drawing.Font>。  當其中一個屬性變更時，便會建立新的 <xref:System.Drawing.Font>。  裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會根據字型大小而調整大小。<br /><br /> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的字型大小會以 1\/96 英吋表示，而在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中則以 1\/72 英吋表示。  對應的轉換如下：<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 字型大小 \= [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 字型大小 \* 72.0 \/ 96.0。|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|系統是藉由使用下列規則來執行 <xref:System.Windows.Controls.Control.Foreground%2A> 屬性對應：<br /><br /> -   如果 <xref:System.Windows.Controls.Control.Foreground%2A> 是 <xref:System.Windows.Media.SolidColorBrush>，則對 <xref:System.Windows.Forms.Control.ForeColor%2A> 使用 <xref:System.Windows.Media.SolidColorBrush.Color%2A>。<br />-   如果 <xref:System.Windows.Controls.Control.Foreground%2A> 是 <xref:System.Windows.Media.GradientBrush>，則對 <xref:System.Windows.Forms.Control.ForeColor%2A> 使用具有最低位移值之 <xref:System.Windows.Media.GradientStop> 的色彩。<br />-   至於任何其他的 <xref:System.Windows.Media.Brush> 型別，<xref:System.Windows.Forms.Control.ForeColor%2A> 則維持不變。  這表示會使用預設值。|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|設定 <xref:System.Windows.UIElement.IsEnabled%2A> 時，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會對裝載的控制項設定 <xref:System.Windows.Forms.Control.Enabled%2A> 屬性。|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|所裝載 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的四個 <xref:System.Windows.Forms.Control.Padding%2A> 屬性值都會設定為相同的 <xref:System.Windows.Thickness> 值。<br /><br /> -   大於 <xref:System.Int32.MaxValue> 的值會設定為 <xref:System.Int32.MaxValue>。<br />-   小於 <xref:System.Int32.MinValue> 的值會設定為 <xref:System.Int32.MinValue>。|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility> 對應到 <xref:System.Windows.Forms.Control.Visible%2A> \= `true`。  裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項為可見的。  不建議將所裝載控制項的 <xref:System.Windows.Forms.Control.Visible%2A> 屬性明確設定為 `false`。<br />-   <xref:System.Windows.Visibility> 對應到 <xref:System.Windows.Forms.Control.Visible%2A> \= `true` 或 `false`。  裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不會進行繪製，且其區域會摺疊。<br />-   <xref:System.Windows.Visibility>：裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會佔用配置空間，但卻看不見。  在此情況下，<xref:System.Windows.Forms.Control.Visible%2A> 屬性會設定為 `true`。  不建議將所裝載控制項的 <xref:System.Windows.Forms.Control.Visible%2A> 屬性明確設定為 `false`。|  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目完全支援容器項目上的附加屬性。  
  
 如需詳細資訊，請參閱[逐步解說：使用 WindowsFormsHost 項目對應屬性](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)。  
  
## 更新父屬性  
 變更大部分的父屬性會導致傳送告知給裝載的子控制項。  下列清單說明其值變更時不會產生告知的屬性。  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 例如，若您變更 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的 <xref:System.Windows.Controls.Control.Background%2A> 屬性值，則所裝載控制項的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性不會改變。  
  
## ElementHost 控制項的屬性對應  
 下列屬性提供內建變更告知。  對應這些屬性時，請勿呼叫 <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> 方法：  
  
-   AutoSize  
  
-   BackColor  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   BindingContext  
  
-   CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Cursor  
  
-   Dock  
  
-   Enabled  
  
-   Font  
  
-   ForeColor  
  
-   Location  
  
-   Margin  
  
-   Padding  
  
-   Parent  
  
-   Region  
  
-   RightToLeft  
  
-   Size  
  
-   TabIndex  
  
-   TabStop  
  
-   文字  
  
-   Visible  
  
 <xref:System.Windows.Forms.Integration.ElementHost> 控制項會根據下列轉譯表，將預設的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 屬性轉譯成其 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 對等用法。  
  
 如需詳細資訊，請參閱[逐步解說：使用 ElementHost 控制項對應屬性](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)。  
  
|Windows Form 裝載|Windows Presentation Foundation|互通行為|  
|---------------------|-------------------------------------|----------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> 所裝載項目的 \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|設定這個屬性會強制使用 <xref:System.Windows.Media.ImageBrush> 重新繪製。  如果 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 屬性設定為 `false` \(預設值\)，這個 <xref:System.Windows.Media.ImageBrush> 就會以 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的外觀為基礎，包含其 <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A> 及 <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> 屬性，以及所有附加的繪製處理常式。<br /><br /> 如果 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 屬性設定為 `true`，則 <xref:System.Windows.Media.ImageBrush> 會以 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的父代 \(Parent\) 外觀為基礎，包含父代的 <xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A> 及 <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> 屬性，以及所有附加的繪製處理常式。|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> \(<xref:System.Drawing.Image?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> 所裝載項目的 \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|設定這個屬性會造成針對 <xref:System.Windows.Forms.Control.BackColor%2A> 對應所描述的相同行為。|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> 所裝載項目的 \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|設定這個屬性會造成針對 <xref:System.Windows.Forms.Control.BackColor%2A> 對應所描述的相同行為。|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> \(<xref:System.Windows.Forms.Cursor?displayProperty=fullName>\)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> \(<xref:System.Windows.Input.Cursor?displayProperty=fullName>\)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 標準游標會轉譯為對應的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 標準游標。  如果 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 不是標準游標，則會指派預設值。|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|設定 <xref:System.Windows.Forms.Control.Enabled%2A> 時，<xref:System.Windows.Forms.Integration.ElementHost> 控制項會對裝載的項目設定 <xref:System.Windows.UIElement.IsEnabled%2A> 屬性。|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> \(<xref:System.Drawing.Font?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> 值會轉譯成對應的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 字型屬性集。|  
|<xref:System.Drawing.Font.Bold%2A>|所裝載項目的 <xref:System.Windows.Controls.Control.FontWeight%2A>|如果 <xref:System.Drawing.Font.Bold%2A> 為 `true`，則會將 <xref:System.Windows.Controls.Control.FontWeight%2A> 設為 <xref:System.Windows.FontWeights.Bold%2A>。<br /><br /> 如果 <xref:System.Drawing.Font.Bold%2A> 為 `false`，則會將 <xref:System.Windows.Controls.Control.FontWeight%2A> 設為 <xref:System.Windows.FontWeights.Normal%2A>。|  
|<xref:System.Drawing.Font.Italic%2A>|所裝載項目的 <xref:System.Windows.Controls.Control.FontStyle%2A>|如果 <xref:System.Drawing.Font.Italic%2A> 為 `true`，則會將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設為 <xref:System.Windows.FontStyles.Italic%2A>。<br /><br /> 如果 <xref:System.Drawing.Font.Italic%2A> 為 `false`，則會將 <xref:System.Windows.Controls.Control.FontStyle%2A> 設為 <xref:System.Windows.FontStyles.Normal%2A>。|  
|<xref:System.Drawing.Font.Strikeout%2A>|所裝載項目的 <xref:System.Windows.TextDecorations>|只有在裝載 <xref:System.Windows.Controls.TextBlock> 控制項時才適用。|  
|<xref:System.Drawing.Font.Underline%2A>|所裝載項目的 <xref:System.Windows.TextDecorations>|只有在裝載 <xref:System.Windows.Controls.TextBlock> 控制項時才適用。|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> \(<xref:System.Windows.Forms.RightToLeft?displayProperty=fullName>\)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> \(<xref:System.Windows.FlowDirection>\)|<xref:System.Windows.Forms.RightToLeft> 對應到 <xref:System.Windows.FlowDirection>。<br /><br /> <xref:System.Windows.Forms.RightToLeft> 對應到 <xref:System.Windows.FlowDirection>。|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> 控制項會使用下列規則，對裝載的控制項設定 <xref:System.Windows.UIElement.Visibility%2A> 屬性：<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> \= `true` 對應到 <xref:System.Windows.Visibility>。<br />-   <xref:System.Windows.Forms.Control.Visible%2A> \= `false` 對應到 <xref:System.Windows.Visibility>。|  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [WPF 和 Windows Form 互通](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)   
 [逐步解說：使用 WindowsFormsHost 項目對應屬性](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)   
 [逐步解說：使用 ElementHost 控制項對應屬性](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)