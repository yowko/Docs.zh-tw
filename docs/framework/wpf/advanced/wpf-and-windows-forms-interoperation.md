---
title: WPF 和 Windows Forms interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 2dc2ea10ce8f723a0ee34c4774253e1357ba6afa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735115"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF 和 Windows Form 互通
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 呈現兩個建立應用程式介面的不同架構。 <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> 命名空間提供類別，可啟用常見的互通性案例。 執行互通性功能的兩個主要類別是 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 和 <xref:System.Windows.Forms.Integration.ElementHost>。 本主題描述支援的交互操作情節以及不支援的情節。  
  
> [!NOTE]
> 「混合控制項」情節有其特殊考量。 混合控制項中有某種技術的控制項巢狀於另一種技術的控制項中。 這也稱為「巢狀交互操作」。 「多層混合控制項」具有多個層級的混合控制項巢狀結構。 多層巢狀交互操作的範例是包含 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，而前者又包含另一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。 不支援多層混合控制項。  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>在 WPF 中裝載 Windows Forms 控制項  
 當 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項裝載 Windows Forms 控制項時，支援下列交互操作案例：  
  
- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項可能會使用 XAML 來裝載一或多個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
- 它可能會使用程式碼來裝載一或多個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
- 它可能會裝載包含其他 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 容器控制項。  
  
- 它可能會裝載具有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 主版和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 詳細資料的主從式表單。  
  
- 它可能會裝載具有 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 主版和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 詳細資料的主從式表單。  
  
- 它可能會裝載一或多個 ActiveX 控制項。  
  
- 它可能會裝載一或多個複合控制項。  
  
- 它可能會使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 裝載混合控制項。  
  
- 它可能會使用程式碼裝載混合控制項。  
  
### <a name="layout-support"></a>版面配置支援  
 下列清單描述當 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素嘗試將其裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項整合到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 版面配置系統時的已知限制。  
  
- 在某些情況下，無法調整 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項大小，或只能將它調整為特定維度。 例如，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> 控制項僅支援單一高度，這是由控制項的字型大小所定義。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動態配置中，假設元素可以垂直延展，裝載的 <xref:System.Windows.Forms.ComboBox> 控制項將無法如預期般延展。  
  
- 無法旋轉或扭曲 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。 例如，將使用者介面旋轉 90 度時，裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項將維持其垂直位置。  
  
- 在大部分情況下，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不支援等比例縮放。 雖然會縮放控制項的整體維度，但是可能無法如預期調整控制項的子控制項和元件大小。 這項限制取決於每個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援縮放比例的程度。  
  
- 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，您可以變更項目的 Z 順序以控制重疊行為。 裝載的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會以不同的 HWND 進行繪製，因此一律會將它繪製在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目頂端。  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項支援根據字型大小來進行自動縮放。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，變更字型大小並不會調整整個版面配置大小，雖然可能會動態調整個別項目。  
  
### <a name="ambient-properties"></a>環境屬性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的部分環境屬性具有 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 對等項目。 這些環境屬性會傳播至主控的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，並公開為 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項上的公用屬性。 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會將每個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 環境屬性轉譯為其對等 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]。  
  
 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)。  
  
### <a name="behavior"></a>行為  
 下表描述交互操作行為。  
  
|行為|已支援|不支援|  
|--------------|---------------|-------------------|  
|透明度|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項轉譯支援透明度。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 父控制項的背景可能會變成裝載之 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的背景。|部分 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項不支援透明度。 例如，當 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]裝載時，<xref:System.Windows.Forms.TextBox> 和 <xref:System.Windows.Forms.ComboBox> 控制項不會是透明的。|  
|定位處理|裝載之 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的定位順序會與在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式中裝載這些控制項時相同。<br /><br /> 使用 TAB 鍵和 SHIFT+TAB 鍵從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項跳到 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會如常運作。<br /><br /> 具有 <xref:System.Windows.Forms.Control.TabStop%2A> 屬性值 `false` 的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，在使用者透過控制項進行索引標籤時，不會收到焦點。<br /><br /> -每個 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項都有 <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> 值，可決定 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項何時會收到焦點。<br /><xref:System.Windows.Forms.Integration.WindowsFormsHost> 容器內所包含的 -   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，遵循 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性所指定的順序。 從最後一個定位點索引進行定位處理時，會將焦點放在下一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項 (如果有的話)。 如果沒有其他可設為焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，則定位處理會傳回定位順序中的第一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。<br /><xref:System.Windows.Forms.Integration.WindowsFormsHost> 內控制項的 -   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> 值，會相對於包含在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中的兄弟 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。<br />-   定位處理接受控制項特定行為。 例如，在具有 <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> 屬性值 `true` 的 <xref:System.Windows.Forms.TextBox> 控制項中按下 TAB 鍵，就會在文字方塊中輸入索引標籤，而不是移動焦點。|不適用。|  
|使用方向鍵巡覽|-在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中具有方向鍵的導覽與一般 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 容器控制項相同：向上鍵和向左鍵選取上一個控制項，而向下箭號和向右方向鍵則會選取下一個控制項。<br />-包含在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中的第一個控制項的向上箭號和向左鍵，會執行與 SHIFT + TAB 鍵盤快捷方式相同的動作。 如果有可設定焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，則焦點會移至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項之外。 這個行為與中的標準 <xref:System.Windows.Forms.ContainerControl> 行為不同，因為不會換行到最後一個控制項。 如果沒有其他可設為焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，則焦點會回到定位順序中的最後一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項所包含之最後一個控制項中的向下箭號和向右鍵，會執行與 TAB 鍵相同的動作。 如果有可設定焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，則焦點會移至 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項之外。 這個行為與中的標準 <xref:System.Windows.Forms.ContainerControl> 行為不同之處在于，不會對第一個控制項進行換行。 如果沒有其他可設為焦點的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，則焦點會回到定位順序中的第一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。|不適用。|  
|快速鍵|除非在「不支援」的資料行中註明，否則快速鍵會如常運作。|跨技術的重複快速鍵不會像一般重複快速鍵一樣運作。 跨技術重複快速鍵時，即至少一個快速鍵位於 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，而另一個快速鍵位於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，則 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項一律會收到快速鍵。 按下重複快速鍵時，不會切換控制項之間的焦點。|  
|快速鍵|除非在「不支援」的資料行中註明，否則快速鍵會如常運作。|在前置處理階段處理的 -   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 快速鍵，其優先順序高於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 快速鍵。 例如，如果您的 <xref:System.Windows.Forms.ToolStrip> 控制項已定義 CTRL + S 快速鍵，而且有一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 命令系結至 CTRL + S，則一律會叫用 <xref:System.Windows.Forms.ToolStrip> 控制處理常式，而不論焦點為何。<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.KeyDown> 事件所處理的快速鍵會最後在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中處理。 您可以藉由覆寫 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的 <xref:System.Windows.Forms.Control.IsInputKey%2A> 方法或處理 <xref:System.Windows.Forms.Control.PreviewKeyDown> 事件來避免此行為。 從 <xref:System.Windows.Forms.Control.IsInputKey%2A> 方法傳回 `true`，或將 <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> 屬性的值設定為 <xref:System.Windows.Forms.Control.PreviewKeyDown> 事件處理常式中的 `true`。|  
|AcceptsReturn、AcceptsTab 和其他控制項特定行為|變更預設鍵盤行為的屬性會如往常般運作，假設 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項會覆寫 <xref:System.Windows.Forms.Control.IsInputKey%2A> 方法以傳回 `true`。|藉由處理 <xref:System.Windows.Forms.Control.KeyDown> 事件來變更預設鍵盤行為的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，最後會在主機 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項中處理。 因為這些控制項會最後處理，所以它們會產生非預期的行為。|  
|Enter 和 Leave 事件|當焦點不進入包含的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項時，當焦點在單一 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項中變更時，Enter 和 Leave 事件會如往常般引發。|發生下列焦點變更時，不會引發 Enter 和 Leave 事件：<br /><br /> -從內部到 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項外部。<br />-從外部到 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項內。<br />-在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項外部。<br />-從裝載于 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，到裝載于相同 <xref:System.Windows.Forms.Integration.WindowsFormsHost>內的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。|  
|多執行緒|支援各種多執行緒。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 技術採用單一執行緒並行模型。 在偵錯期間，其他執行緒中架構物件的呼叫將會引發例外狀況，來強制執行這項需求。|  
|安全性|所有交互操作情節都需要完全信任。|在部分信任中，不允許交互操作情節。|  
|協助工具|支援所有協助工具情節。 輔助技術產品用於包含 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的混合應用程式時，可正常運作。|不適用。|  
|剪貼簿|所有剪貼簿作業都會如常運作。 這包括 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之間的剪下和貼上。|不適用。|  
|拖放功能|所有拖放作業都會如常運作。 這包括 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之間的作業。|不適用。|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>將 WPF 控制項裝載在 Windows Forms 中  
 當 Windows Forms 控制項裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項時，支援下列交互操作案例：  
  
- 使用程式碼來裝載一或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項。  
  
- 建立屬性工作表與一或多個裝載之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的關聯。  
  
- 在表單中裝載一或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面。  
  
- 啟動 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視窗。  
  
- 裝載具有 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 主版和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 詳細資料的主從式表單。  
  
- 裝載具有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 主版和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 詳細資料的主從式表單。  
  
- 裝載自訂的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項。  
  
- 裝載混合控制項。  
  
### <a name="ambient-properties"></a>環境屬性  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項的部分環境屬性具有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 對等項目。 這些環境屬性會傳播至主控的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項，並公開為 <xref:System.Windows.Forms.Integration.ElementHost> 控制項上的公用屬性。 <xref:System.Windows.Forms.Integration.ElementHost> 控制項會將每個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 環境屬性轉譯為其對等 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)。  
  
### <a name="behavior"></a>行為  
 下表描述交互操作行為。  
  
|行為|已支援|不支援|  
|--------------|---------------|-------------------|  
|透明度|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項轉譯支援透明度。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 父控制項的背景可能會變成裝載之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的背景。|不適用。|  
|多執行緒|支援各種多執行緒。|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 技術採用單一執行緒並行模型。 在偵錯期間，其他執行緒中架構物件的呼叫將會引發例外狀況，來強制執行這項需求。|  
|安全性|所有交互操作情節都需要完全信任。|在部分信任中，不允許交互操作情節。|  
|協助工具|支援所有協助工具情節。 輔助技術產品用於包含 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的混合應用程式時，可正常運作。|不適用。|  
|剪貼簿|所有剪貼簿作業都會如常運作。 這包括 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之間的剪下和貼上。|不適用。|  
|拖放功能|所有拖放作業都會如常運作。 這包括 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之間的作業。|不適用。|  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [逐步解說：在 WPF 中裝載 Windows Forms 控制項](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)
