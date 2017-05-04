---
title: "混合應用程式疑難排解 | Microsoft Docs"
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
  - "混合應用程式 [WPF 互通性]"
  - "互通性 [WPF], Windows Form"
  - "訊息迴圈 [WPF]"
  - "重疊控制項"
  - "Windows Form [WPF], 互通性"
  - "Windows Form, WPF 互通"
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# 混合應用程式疑難排解
<a name="introduction"></a> 本主題會列出撰寫同時使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 技術的混合應用程式時，所發生的一些常見問題。  
  
   
  
<a name="overlapping_controls"></a>   
## 重疊控制項  
 控制項可能不會如您預期般地重疊。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 會針對每個控制項使用不同的 HWND。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 則會針對頁面上的所有內容使用同一個 HWND。  這項實作上的差異會造成未預期的重疊行為。  
  
 裝載於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項一定會顯示在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容的頂端。  
  
 裝載於 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容會依疊置順序 \(Z\-order\) 顯示在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。  您可以重疊 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，但是裝載的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容不會合併或互動。  
  
<a name="child_property"></a>   
## Child 屬性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 類別只能裝載單一子控制項或項目。  若要裝載多個控制項或項目，您必須使用容器做為子內容。  例如，您可以將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 按鈕和核取方塊控制項加入至 <xref:System.Windows.Forms.Panel?displayProperty=fullName> 控制項，然後將面板指派給 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> 屬性。  不過，您無法將按鈕和核取方塊控制項個別加入至相同的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項。  
  
<a name="scaling"></a>   
## 縮放  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 具有不同的縮放模型。  部分 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 縮放轉換對 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項是有意義的，但是其他的轉換則無。  例如，將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項縮放為 0 就行得通，但是如果嘗試將同一個控制項縮放回非零的值，則控制項的大小會維持 0。  如需詳細資訊，請參閱 [WindowsFormsHost 項目的配置考量](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="adapter"></a>   
## 配接器  
 當您使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 類別時可能會有疑惑，因為它們包含隱藏的容器。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 類別都有隱藏的容器，稱為「*配接器*」\(Adapter\)，用來裝載內容。  對於 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目而言，配接器是衍生自 <xref:System.Windows.Forms.ContainerControl?displayProperty=fullName> 類別。  對於 <xref:System.Windows.Forms.Integration.ElementHost> 控制項而言，配接器是衍生自 <xref:System.Windows.Controls.DockPanel> 項目。  如果其他互通主題中提到了配接器，就是在討論這個容器。  
  
<a name="nesting"></a>   
## 巢狀  
 不支援在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項內包含 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目，  也不支援在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目內包含 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。  
  
<a name="focus"></a>   
## 焦點  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中的焦點 \(Focus\) 運作方式不同，也就是說在混合應用程式中可能會發生焦點問題。  例如，如果焦點是在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目內，而您將頁面最小化並還原，或顯示強制回應 \(Modal\) 對話方塊，則 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目內的焦點可能就會遺失。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目仍然具有焦點，但是其中的控制項則無。  
  
 資料驗證也會受焦點影響。  驗證在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目中可以正常運作，但是當您按 Tab 鍵離開 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目，或是在兩個不同的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目之間切換時，驗證就沒有作用。  
  
<a name="property_mapping"></a>   
## 屬性對應  
 有些屬性對應需要大量解譯才能銜接 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 技術之間的不同實作。  屬性對應可以讓您的程式碼回應字型、色彩及其他屬性的變更。  一般來說，屬性對應的運作方式是接聽 *Property*Changed 事件或 On*Property*Changed 呼叫，然後在子控制項或其配接器上設定適當的屬性。  如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## 裝載的內容上與配置相關的屬性  
 指派 <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=fullName> 或 <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=fullName> 屬性時，會自動設定裝載的內容上數個與配置相關的屬性。  變更這些內容屬性會造成未預期的配置行為。  
  
 您的裝載內容會停駐以填滿 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 父代 \(Parent\)。  若要啟用這個填滿行為，在設定子屬性時要設定數個屬性。  下表列出由 <xref:System.Windows.Forms.Integration.ElementHost> 和 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別所設定的內容屬性。  
  
|主類別|內容屬性|  
|---------|----------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 請勿直接在裝載的內容上設定這些屬性。  如需詳細資訊，請參閱 [WindowsFormsHost 項目的配置考量](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="navigation_applications"></a>   
## 巡覽應用程式  
 巡覽應用程式可能不會維護使用者狀態。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目會在用於巡覽應用程式中時重新建立其控制項。  當使用者離開裝載 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的頁面後又返回時，就會重新建立子控制項。  使用者輸入的任何內容都會遺失。  
  
<a name="message_loop_interoperation"></a>   
## 訊息迴圈互通  
 使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈時，可能無法如預期般地處理訊息。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 建構函式會呼叫 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> 方法。  這個方法會將訊息篩選條件加入至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈。  如果 <xref:System.Windows.Forms.Control?displayProperty=fullName> 是訊息的目標並且會轉譯\/分派訊息，這個篩選條件會呼叫 <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=fullName> 方法。  
  
 如果您在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈中使用 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=fullName> 顯示 <xref:System.Windows.Window>，則除非呼叫 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> 方法，否則無法輸入任何文字。  <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> 方法會採用 <xref:System.Windows.Window>，並且在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈中加入會重新傳送索引鍵相關訊息的 <xref:System.Windows.Forms.IMessageFilter?displayProperty=fullName>。  如需詳細資訊，請參閱 [Windows Form 和 WPF 互通性輸入架構](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)。  
  
<a name="opacity_and_layering"></a>   
## 不透明度與分層  
 <xref:System.Windows.Interop.HwndHost> 類別不支援分層。  這表示設定 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目上的 <xref:System.Windows.UIElement.Opacity%2A> 屬性沒有效果，而且不會與 <xref:System.Windows.Window.AllowsTransparency%2A> 設為 `true` 的其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視窗混色。  
  
<a name="dispose"></a>   
## 處置  
 類別處置 \(Dispose\) 不當會使資源外洩。  在混合應用程式中，請確實處置 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost> 類別，否則資源可能會外洩。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 會在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的非強制回應 <xref:System.Windows.Forms.Form> 父代關閉時處置該控制項，而 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會在應用程式關閉時處置 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目。  您可以在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈的 <xref:System.Windows.Window> 中顯示 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目。  在此情況下，您的程式碼可能不會收到應用程式正在關閉的告知。  
  
<a name="enabling_visual_styles"></a>   
## 啟用視覺化樣式  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項上的 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 視覺化樣式可能未啟用。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式的範本中會呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> 方法。  雖然預設不會呼叫這個方法，如果您使用， [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 建立專案，您會取得 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 控制項的視覺化樣式，，且 Comctl32.dll 的 6.0 版是可用的。在控制項的程式碼在執行緒上建立，您必須呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法。  如需詳細資訊，請參閱 [如何：在混合應用程式中啟用視覺化樣式](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)。  
  
<a name="licensed_controls"></a>   
## 授權控制項  
 在訊息方塊中對使用者顯示授權資訊的授權 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，可能會造成混合應用程式的未預期的行為。  某些授權控制項會顯示對話方塊以回應控制代碼建立作業。  例如，授權控制項可能會通知使用者需要授權，或使用者對控制項還有三次試用機會。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目是衍生自 <xref:System.Windows.Interop.HwndHost> 類別，而子控制項的控制代碼會在 <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> 方法內建立。  <xref:System.Windows.Interop.HwndHost> 類別不允許用 <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> 方法處理訊息，但是顯示對話方塊時會傳送訊息。  若要啟用這個授權案例，請在將 <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=fullName> 方法指派為 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的子項目之前，先呼叫該方法。  
  
<a name="wpf_designer"></a>   
## WPF 設計工具  
 您可以使用 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 設計 WPF 內容。  下列各節列出使用 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]撰寫混合應用式時可能發生的一些常見問題。  
  
### 設計階段忽略 BackColorTransparent  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 屬性在設計階段可能無法達到預期的效果。  
  
 如果 WPF 控制項不是可見的父代 \(Parent\)，WPF 執行階段便會忽略 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 值。  可能忽略 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 的原因是因為 <xref:System.Windows.Forms.Integration.ElementHost> 物件是在個別的 <xref:System.AppDomain> 中建立。  不過，當您執行應用程式時，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> 卻無法產生預期的效果。  
  
### 刪除 obj 資料夾時出現設計階段錯誤清單  
 若刪除 obj 物件，設計階段錯誤清單便會出現。  
  
 當您使用 <xref:System.Windows.Forms.Integration.ElementHost> 進行設計時，Windows Forms 設計工具會使用專案 obj 資料夾內 Debug 或 Release 資料夾中產生的檔案。  如果您刪除這些檔案，設計階段錯誤清單便會出現。  若要修正這個問題，請重建專案。  如需詳細資訊，請參閱 [Windows Form 設計工具的設計階段錯誤](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)。  
  
<a name="elementhost_and_ime"></a>   
## ElementHost 和 IME  
 裝載在 <xref:System.Windows.Forms.Integration.ElementHost> 中的 WPF 控制項目前不支援 <xref:System.Windows.Forms.Control.ImeMode%2A> 屬性。  裝載的控制項會忽略 <xref:System.Windows.Forms.Control.ImeMode%2A>。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF 設計工具的互通性](http://msdn.microsoft.com/zh-tw/2cb7c1ca-2a75-463b-8801-fba81e2b7042)   
 [Windows Form 和 WPF 互通性輸入架構](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)   
 [如何：在混合應用程式中啟用視覺化樣式](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)   
 [WindowsFormsHost 項目的配置考量](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)   
 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [Windows Form 設計工具的設計階段錯誤](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)   
 [移轉和互通性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)