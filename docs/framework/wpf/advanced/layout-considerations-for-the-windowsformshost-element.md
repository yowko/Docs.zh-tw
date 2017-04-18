---
title: "WindowsFormsHost 項目的配置考量 | Microsoft Docs"
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
  - "與裝置無關的像素"
  - "動態配置 [WPF 互通性]"
  - "互通性 [WPF], Windows Form"
  - "Windows Form [WPF], 互通性"
  - "Windows Form, WPF 互通"
  - "WindowsFormsHost 項目的配置考量"
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# WindowsFormsHost 項目的配置考量
本主題說明 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置系統的互動方式。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 與 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 支援不同但類似的邏輯，以供在表單或頁面上調整項目的大小及加以定位。  當您建立可在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中裝載 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的混合使用者介面 \(UI\) 時，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會整合這兩種配置機制。  
  
## WPF 和 Windows Form 的配置差異  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會使用無關解析度的配置。  所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置維度 \(Dimension\) 都使用「*與裝置無關的像素*」\(Device\-Independent Pixel\) 加以指定。  與裝置無關的像素就是大小為一英吋的九十六分之一而且與解析度無關，所以不論您是呈現至 72 dpi 監視器或 19,200 dpi 印表機，都會得到類似的結果。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也是以「*動態配置*」\(Dynamic Layout\) 為基礎。  這表示 UI 項目會根據其內容、其父配置容器和可用螢幕大小，自行排列於表單或頁面上。  當 UI 項目包含的字串變更長度時，動態配置會自動調整 UI 項目的大小和位置，進而促成當地語系化。  
  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 的配置與裝置相關，且較有可能是靜態的。  通常，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會使用以硬體像素指定的維度，以絕對方式定位於表單上。  然而，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 不支援某些動態配置功能，如下表簡述。  
  
|配置功能|描述|  
|----------|--------|  
|自動調整大小|有些 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會自行調整大小，以便正確顯示其內容。  如需詳細資訊，請參閱 [AutoSize 屬性概觀](../../../../docs/framework/winforms/controls/autosize-property-overview.md)。|  
|錨定和停駐|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援以父容器為基準的定位與調整大小。  如需詳細資訊，請參閱<xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName>與<xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>。|  
|自動縮放|容器控制項會根據輸出裝置的解析度或預設容器字型的大小 \(以像素為單位\)，調整本身與其子系的大小。  如需詳細資訊，請參閱 [Windows Form 中的自動縮放比例](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)。|  
|配置容器|<xref:System.Windows.Forms.FlowLayoutPanel> 和 <xref:System.Windows.Forms.TableLayoutPanel> 控制項會根據其內容來排列其子控制項並調整本身大小。|  
  
## 配置限制  
 一般而言，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項無法縮放及轉換成 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中可能的範圍。  下列清單說明當 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目嘗試將其裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項整合到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置系統時的已知限制。  
  
-   在某些情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項無法調整大小，或只能調整為特定維度。  例如，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> 控制項僅支援由控制項的字型大小所定義的單一高度。  在項目可以自動垂直縮放的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動態配置中，裝載的 <xref:System.Windows.Forms.ComboBox> 控制項並不會如預期地自動縮放。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項無法旋轉或傾斜。  如果您套用傾斜或旋轉轉換，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 會引發 <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> 事件。  如果您不處理 <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> 事件，則會引發 <xref:System.InvalidOperationException>。  
  
-   在大部分的情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不支援按比例縮放。  雖然控制項的整個維度都會縮放，但控制項的子控制項和元件項目可能無法如預期般地調整大小。  這項限制取決於每個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援縮放的程度。  此外，您無法將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項縮小至大小為 0 像素。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項可支援自動縮放，於是表單會根據字型大小來自動調整本身及其控制項的大小。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，變更字型大小並不會調整整個配置的大小，但個別項目可能會動態調整大小。  
  
### 疊置順序  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，您可以變更項目的疊置順序 \(Z\-order\)，以控制重疊行為。  裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會繪製於不同的 HWND 中，以永遠繪製在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目的上面。  
  
 裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項也會繪製於任何 <xref:System.Windows.Documents.Adorner> 項目的上面。  
  
## 配置行為  
 下列章節說明在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中裝載 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項時，配置行為的特定層面。  
  
### 縮放比例、單位轉換和裝置獨立  
 每當 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目執行與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 維度有關的作業時，會牽涉到兩個座標系統：[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的與裝置無關像素以及 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 的硬體像素。  因此，您必須套用適當的單位與縮放轉換，才能達成一致的配置。  
  
 座標系統之間的轉換，取決於目前的裝置解析度以及任何已套用至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目或其祖系的配置或呈現轉換。  
  
 如果輸出裝置為 96 dpi，而且 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目尚未套用任何縮放比例，則一個與裝置無關像素就等於一個硬體像素。  
  
 其他所有狀況都需要座標系統縮放功能。  裝載的控制項並未調整大小。  反而，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會嘗試縮放裝載的控制項與其所有的子控制項。  因為 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 不完全支援縮放功能，所以 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會縮放至特定控制項所支援的程度。  
  
 覆寫 <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> 方法，可為裝載的 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項提供自訂縮放行為。  
  
 除了縮放以外，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目還可處理如下表所述的四捨五入與溢位情形。  
  
|轉換問題|描述|  
|----------|--------|  
|四捨五入|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 與裝置無關的像素維度會指定為 `double`，而 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 硬體像素維度則會指定為 `int`。  在 `double` 型維度轉換成 `int` 型維度的情形中，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會使用標準四捨五入，所以小於 0.5 的小數值會捨去為 0。|  
|溢位|當 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目從 `double` 值轉換成 `int` 值時，可能會發生溢位。  大於 <xref:System.Int32.MaxValue> 的值會設定為 <xref:System.Int32.MaxValue>。|  
  
### 與配置相關的屬性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會適當地對應在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目中控制配置行為的屬性。  如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)。  
  
### 所裝載控制項的配置變更  
 所裝載 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的配置變更會傳播至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，以觸發配置更新。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 上的 <xref:System.Windows.UIElement.InvalidateMeasure%2A> 方法可確保所裝載控制項的配置變更，能促使 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置引擎執行。  
  
### 連續調整大小的 Windows Forms 控制項  
 支援連續縮放的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，可與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置系統完整互動。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會一如往常使用 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法，來調整所裝載 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的大小並加以排列。  
  
### 調整大小演算法  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目使用下列程序來調整所裝載控制項的大小：  
  
1.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會覆寫 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法。  
  
2.  為了要決定所裝載控制項的大小，<xref:System.Windows.FrameworkElement.MeasureOverride%2A> 方法會使用從已傳遞至 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 方法之條件約束轉譯而來的條件約束，呼叫所裝載控制項的 <xref:System.Windows.Forms.Control.GetPreferredSize%2A> 方法。  
  
3.  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法會嘗試將裝載的控制項設定為指定的大小條件約束。  
  
4.  如果所裝載控制項的 <xref:System.Windows.Forms.Control.Size%2A> 屬性符合指定的條件約束，所裝載控制項的大小便會調整成此條件約束。  
  
 如果 <xref:System.Windows.Forms.Control.Size%2A> 屬性不符合指定的條件約束，則裝載的控制項不支援連續調整大小。  例如，<xref:System.Windows.Forms.MonthCalendar> 控制項只允許不連續的大小。  此控制項的許可大小是由高度與寬度的整數 \(表示月份數\) 所構成。  在此種情況下，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的行為如下：  
  
-   如果 <xref:System.Windows.Forms.Control.Size%2A> 屬性所傳回的大小大於指定的條件約束，則 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會裁剪裝載的控制項。  系統會分開處理高度和寬度，所以可能會裁剪所裝載控制項的某一個方向。  
  
-   如果 <xref:System.Windows.Forms.Control.Size%2A> 屬性所傳回的大小小於指定的條件約束，則 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 會接受此大小值並將此值傳回至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置系統。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [逐步解說：在 WPF 中排列 Windows Form 控制項](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)   
 [排列 WPF 範例的 Windows Form 控制項](http://go.microsoft.com/fwlink/?LinkID=159971)   
 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)