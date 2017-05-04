---
title: "WPF 和 Windows Form 互通 | Microsoft Docs"
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
  - "混合控制項 [WPF 互通性]"
  - "互通性 [WPF], Windows Form"
  - "巢狀互通 [WPF]"
  - "Windows Form [WPF], 互通性"
  - "Windows Form, WPF 互通"
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# WPF 和 Windows Form 互通
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 在建立應用程式介面方面，會呈現兩個不同的架構。  <xref:System.Windows.Forms.Integration?displayProperty=fullName> 命名空間提供一般互通案例適用的類別。  可以實作互通功能的兩個重要類別為 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost>。  本主題說明支援和不支援的互通案例。  
  
> [!NOTE]
>  對「*混合控制項*」\(Hybrid Control\) 要有特殊的考量。  混合控制項是指一種技術的控制項中有另一種技術的控制項，  這也稱為「*巢狀互通*」\(Nested Interoperation\)。  「*多層混合控制項*」\(Multilevel Hybrid Control\) 具有一個以上的混合控制項巢狀層級。  多層巢狀互通的範例是 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項包含 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，而這個控制項又包含另一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  不支援多層混合控制項。  
  
   
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## 將 Windows Form 控制項裝載在 WPF 中  
 下列互通案例在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項裝載 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項時受到支援：  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項可以使用 XAML 裝載一個或多個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
-   可以使用程式碼裝載一個或多個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
-   可以裝載包含其他 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 容器控制項。  
  
-   可以裝載具有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 主要和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 詳細資料的主從式表單。  
  
-   可以裝載具有 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 主要和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 詳細資料的主從式表單。  
  
-   可以裝載一個或多個 [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] 控制項。  
  
-   可以裝載一個或多個複合控制項。  
  
-   可以使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 裝載混合控制項。  
  
-   可以使用程式碼裝載混合控制項。  
  
### 配置支援  
 下列清單說明當 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目嘗試將其裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項整合到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 配置系統時的已知限制。  
  
-   在某些情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項無法調整大小，或只能調整為特定維度。  例如，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> 控制項僅支援由控制項的字型大小所定義的單一高度。  在假設項目可以自動垂直縮放的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動態配置中，裝載的 <xref:System.Windows.Forms.ComboBox> 控制項並不會如預期般地自動縮放。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項無法旋轉或傾斜。  例如，當您以 90 度旋轉使用者介面時，裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會維持其垂直位置。  
  
-   在大部分的情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不支援按比例縮放。  雖然控制項的整個維度都會縮放，但控制項的子控制項和元件項目可能無法如預期般地調整大小。  這項限制取決於每個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援縮放的程度。  
  
-   在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，您可以變更項目的疊置順序 \(Z\-order\)，以控制重疊行為。  裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會繪製於不同的 HWND 中，以永遠繪製在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目的上面。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援根據字型大小來進行自動縮放。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，變更字型大小並不會調整整個配置的大小，但個別項目可能會動態調整大小。  
  
### 環境屬性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的部分環境屬性具有 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 對等用法。  這些環境屬性會傳播至裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，並且公開為 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項上的公用屬性。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會將每個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 環境屬性轉譯成其 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 對等用法。  
  
 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)。  
  
### 行為  
 下表說明互通行為。  
  
|行為|支援項目|不支援|  
|--------|----------|---------|  
|透明度|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項呈現支援透明度。  父 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的背景可以變成已裝載 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的背景。|部分 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不支援透明度。  例如，當 <xref:System.Windows.Forms.TextBox> 和 <xref:System.Windows.Forms.ComboBox> 控制項是由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 裝載時，就不會是透明的。|  
|Tab 鍵切換|已裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的 Tab 鍵順序與這些控制項裝載於 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 架構應用程式中時相同。<br /><br /> 從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項到另一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的 Tab 鍵切換可以如同往常般使用 TAB 鍵和 SHIFT\+TAB 鍵執行。<br /><br /> 當使用者利用 Tab 鍵在控制項之間切換時，<xref:System.Windows.Forms.Control.TabStop%2A> 屬性值為 `false` 的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不會收到焦點。<br /><br /> -   每個 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項都有 <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> 值，這個會值決定 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項收到焦點的時機。<br />-   包含在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 容器中的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會遵循 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性所指定的順序。  從最後一個 Tab 鍵索引進行 Tab 鍵切換會將焦點放在下一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項 \(如果有的話\)。  如果沒有其他可設定焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，Tab 鍵切換會回到 Tab 鍵順序中的第一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> 內之控制項的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> 值，相對於 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中包含的同層級 \(Sibling\) [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。<br />-   Tab 鍵切換遵守控制項特定的行為。  例如，在 <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> 屬性值為 `true` 的 <xref:System.Windows.Forms.TextBox> 控制項中按下 TAB 鍵，會在文字方塊中輸入定位點而非移動焦點。|不適用。|  
|使用方向鍵巡覽|-   在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中使用方向鍵巡覽，與在一般 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 容器控制項中相同：向上鍵與向左鍵會選取上一個控制項，向下鍵和向右鍵會選取下一個控制項。<br />-   在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中包含的第一個控制項使用向上鍵或向左鍵，會執行與 SHIFT\+TAB 鍵盤快速鍵一樣的動作。  如果有可設定焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，焦點會移至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項之外。  這個行為與標準 <xref:System.Windows.Forms.ContainerControl> 行為的不同之處在於它不會換到最後一個控制項。  如果沒有其他可設定焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，焦點就會回到 Tab 鍵順序中的最後一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。<br />-   在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中包含的最後一個控制項使用向下鍵或向右鍵，會執行與 TAB 鍵一樣的動作。  如果有可設定焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，焦點會移至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項之外。  這個行為與標準 <xref:System.Windows.Forms.ContainerControl> 行為的不同之處在於它不會換到第一個控制項。  如果沒有其他可設定焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，焦點會回到 Tab 鍵順序中的第一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。|不適用。|  
|快速鍵|除非 \[不支援\] 欄位中已經註明，否則快速鍵會如同往常一般運作。|跨技術的重複快速鍵不會像一般重複快速鍵一樣的運作。  當有跨技術的重複快速鍵 \(至少有一個快速鍵在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項上，而有另一個在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項上\) 時，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項就一定會收到快速鍵。  焦點不會在按下重複快速鍵時於控制項之間切換。|  
|快速鍵|除非 \[不支援\] 欄位中已經註明，否則快速鍵會如同往常一般運作。|-   在前置處理階段處理的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 快速鍵，其優先順序一律高於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 快速鍵。  例如，如果為 <xref:System.Windows.Forms.ToolStrip> 控制項定義了 CTRL\+S 快速鍵，而已經有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 命令繫結至 CTRL\+S，則不論焦點在哪裡，一律會先叫用 <xref:System.Windows.Forms.ToolStrip> 控制項處理常式。<br />-   在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，由 <xref:System.Windows.Forms.Control.KeyDown> 事件處理的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 快速鍵會最後處理。  您可以防止這個行為，方法是覆寫 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的 <xref:System.Windows.Forms.Control.IsInputKey%2A> 方法或處理 <xref:System.Windows.Forms.Control.PreviewKeyDown> 事件。  請從 <xref:System.Windows.Forms.Control.IsInputKey%2A> 方法傳回 `true`，或將 <xref:System.Windows.Forms.Control.PreviewKeyDown> 事件處理常式中的 <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=fullName> 屬性的值設定為 `true`。|  
|AcceptsReturn、AcceptsTab 及其他控制項特定行為|負責變更預設鍵盤行為的屬性會如同往常運作，並假設 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會覆寫 <xref:System.Windows.Forms.Control.IsInputKey%2A> 方法以傳回 `true`。|負責處理 <xref:System.Windows.Forms.Control.KeyDown> 事件來變更預設鍵盤行為的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，在主 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項中會最後處理。  因為這些控制項最後處理，所以可能會產生無法預期的行為。|  
|Enter 和 Leave 事件|當焦點不是要移至主 <xref:System.Windows.Forms.Integration.ElementHost> 控制項時，Enter 和 Leave 事件會在單一 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中發生焦點變更時如同以往引發。|Enter 和 Leave 事件不會在下列焦點變更發生時引發：<br /><br /> -   從 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的內部到外部。<br />-   從 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的外部到內部。<br />-   在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的外部。<br />-   從 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項到在同一個 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 內裝載的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。|  
|多執行緒|支援各種多執行緒。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 技術都假設採用單一執行緒並行模型。  偵錯期間，其他執行緒對架構物件的呼叫會引發例外狀況以強制執行這項需求。|  
|安全性|所有互通案例都需要完全信任。|不允許有互通案例只有部分信任。|  
|協助工具|支援所有協助工具案例。  輔助技術產品在用於同時包含 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的混合應用程式時可以正常運作。|不適用。|  
|剪貼簿|所有剪貼簿都會如同往常運作。  這包括在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之間的剪下和貼上動作。|不適用。|  
|拖放功能|所有拖放作業都會如往常運作。  這包括在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之間的作業。|不適用。|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## 將 WPF 控制項裝載在 Windows Form 中  
 下列互通案例在 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 控制項裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項時受到支援：  
  
-   使用程式碼裝載一個或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項。  
  
-   讓屬性工作表 \(Property Sheet\) 與一個或多個裝載的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項產生關聯。  
  
-   在表單中裝載一個或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面。  
  
-   啟動 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視窗。  
  
-   裝載具有 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 主要和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 詳細資料的主從式表單。  
  
-   裝載具有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 主要和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 詳細資料的主從式表單。  
  
-   裝載自訂 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項。  
  
-   裝載混合控制項。  
  
### 環境屬性  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的部分環境屬性具有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 對等用法。  這些環境屬性會傳播至裝載的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，並且公開為 <xref:System.Windows.Forms.Integration.ElementHost> 控制項上的公用屬性。  <xref:System.Windows.Forms.Integration.ElementHost> 控制項會將每個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 環境屬性轉譯成其 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 對等用法。  
  
 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)。  
  
### 行為  
 下表說明互通行為。  
  
|行為|支援項目|不支援|  
|--------|----------|---------|  
|透明度|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項呈現支援透明度。  父 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的背景可以變成已裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的背景。|不適用。|  
|多執行緒|支援各種多執行緒。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 技術都假設採用單一執行緒並行模型。  偵錯期間，其他執行緒對架構物件的呼叫會引發例外狀況以強制執行這項需求。|  
|安全性|所有互通案例都需要完全信任。|不允許有互通案例只有部分信任。|  
|協助工具|支援所有協助工具案例。  輔助技術產品在用於同時包含 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的混合應用程式時可以正常運作。|不適用。|  
|剪貼簿|所有剪貼簿都會如同往常運作。  這包括在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之間的剪下和貼上動作。|不適用。|  
|拖放功能|所有拖放作業都會如往常運作。  這包括在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之間的作業。|不適用。|  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [逐步解說：在 WPF 中裝載 Windows Form 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [Windows Form 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)