---
title: WPF 和 Windows 表單互通
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 76d1e97c92946267aa1217f52c93594fb63d20de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187156"
---
# <a name="wpf-and-windows-forms-interoperation"></a>WPF 和 Windows Form 互通
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Windows 表單提供了兩種不同的體系結構來創建應用程式介面。 命名<xref:System.Windows.Forms.Integration?displayProperty=nameWithType>空間提供啟用常見交互操作方案的類。 實現交互操作功能的兩個關鍵類是<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>。 本主題描述支援的交互操作情節以及不支援的情節。  
  
> [!NOTE]
> 「混合控制項」** 情節有其特殊考量。 混合控制項中有某種技術的控制項巢狀於另一種技術的控制項中。 這也稱為「巢狀交互操作」**。 「多層混合控制項」** 具有多個層級的混合控制項巢狀結構。 多級嵌套交互操作的示例是包含控制項的 Windows 表單控制項，該控制項包含[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]另一個 Windows 表單控制項。 不支援多層混合控制項。  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>
## <a name="hosting-windows-forms-controls-in-wpf"></a>在 WPF 中裝載 Windows Forms 控制項  
 當控制項承載 Windows 表單控制項時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援以下操作間方案：  
  
- 該[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項可以使用 XAML 承載一個或多個 Windows 表單控制項。  
  
- 它可以使用代碼承載一個或多個 Windows 表單控制項。  
  
- 它可以承載包含其他 Windows 表單控制項的 Windows 表單容器控制項。  
  
- 它可以承載主/詳細資訊的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]母版/詳細資訊。  
  
- 它可以承載具有 Windows 表單主表單和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細資訊的主/詳細資訊表單。  
  
- 它可以承載一個或多個 ActiveX 控制項。  
  
- 它可能會裝載一或多個複合控制項。  
  
- 它可能會使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 裝載混合控制項。  
  
- 它可能會使用程式碼裝載混合控制項。  
  
### <a name="layout-support"></a>版面配置支援  
 以下清單描述<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素嘗試將其託管 Windows 表單控制項集成到佈局系統中時的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]已知限制。  
  
- 在某些情況下，Windows 表單控制項無法調整大小，或者只能調整到特定維度的大小。 例如，Windows 表單<xref:System.Windows.Forms.ComboBox>控制項僅支援單個高度，該高度由控制項的字體大小定義。 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]動態佈局中，假定元素可以垂直拉伸，託管<xref:System.Windows.Forms.ComboBox>控制項不會按預期拉伸。  
  
- 無法旋轉或傾斜 Windows 表單控制項。 例如，當您將使用者介面旋轉 90 度時，託管 Windows 表單控制項將保持其直立位置。  
  
- 在大多數情況下，Windows 表單控制項不支援星號調整。 雖然會縮放控制項的整體維度，但是可能無法如預期調整控制項的子控制項和元件大小。 此限制取決於每個 Windows 表單控制項支援縮放的功能。  
  
- 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，您可以變更項目的 Z 順序以控制重疊行為。 託管 Windows 表單控制項在單獨的 HWND 中繪製，因此始終在元素上[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]繪製。  
  
- Windows 表單控制項支援根據字體大小進行自動縮放。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用者介面中，變更字型大小並不會調整整個版面配置大小，雖然可能會動態調整個別項目。  
  
### <a name="ambient-properties"></a>環境屬性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項的某些環境屬性具有等效的 Windows 表單。 這些環境屬性傳播到託管的 Windows 表單控制項，並作為控制項上的<xref:System.Windows.Forms.Integration.WindowsFormsHost>公共屬性公開。 該<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項將每個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]環境屬性轉換為其 Windows 表單等效項。  
  
 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)。  
  
### <a name="behavior"></a>行為  
 下表描述交互操作行為。  
  
|行為|支援|不支援|  
|--------------|---------------|-------------------|  
|透明度|Windows 表單控制項呈現支援透明度。 父[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項的背景可以成為託管 Windows 表單控制項的背景。|某些 Windows 表單控制項不支援透明度。 例如，在<xref:System.Windows.Forms.TextBox>託管<xref:System.Windows.Forms.ComboBox>時， 和 控制項將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]不透明。|  
|定位處理|託管 Windows 表單控制項的選項卡順序與這些控制項在基於 Windows 表單的應用程式中託管時相同。<br /><br /> 使用 TAB[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]鍵和 SHIFT_TAB 鍵從控制項到 Windows 表單控制項的 Tab 工作正常。<br /><br /> 當使用者通過控制項選項卡時，<xref:System.Windows.Forms.Control.TabStop%2A>具有 屬性`false`值的 Windows 表單控制項不會接收焦點。<br /><br /> -<xref:System.Windows.Forms.Integration.WindowsFormsHost>每個控制項都有<xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>一個值，該值<xref:System.Windows.Forms.Integration.WindowsFormsHost>確定該控制項何時接收焦點。<br />- 包含在容器中的<xref:System.Windows.Forms.Integration.WindowsFormsHost>Windows 表單控制項遵循<xref:System.Windows.Forms.Control.TabIndex%2A>屬性指定的順序。 從最後一個定位點索引進行定位處理時，會將焦點放在下一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項 (如果有的話)。 如果沒有其他可[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]聚焦控制項，選項卡將返回到選項卡順序中的第一個 Windows 表單控制項。<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>中控制項的值<xref:System.Windows.Forms.Integration.WindowsFormsHost>與<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項中包含的同級 Windows 表單控制項相關。<br />-   定位處理接受控制項特定行為。 例如，按<xref:System.Windows.Forms.TextBox>控制項中的 TAB 鍵，該<xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A>控制項的屬性值為`true`"在文字方塊中輸入選項卡，而不是移動焦點。|不適用。|  
|使用方向鍵巡覽|-<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項中帶有方向鍵的導航與普通 Windows 表單容器控制項中的導航相同：向上箭號和左方向鍵選擇上一個控制項，向下箭頭和右方向鍵選擇下一個控制項。<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項中包含的第一個控制項的上箭頭和 LEFT ARROW 鍵執行與 SHIFT_TAB 鍵盤快捷方式相同的操作。 如果存在可[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]聚焦控制項，則焦點將移出<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。 此行為不同于標準<xref:System.Windows.Forms.ContainerControl>行為，因為不會發生對最後一個控制項的換行。 如果沒有其他可[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]聚焦控制項，則焦點將返回到選項卡順序中的最後一個 Windows 表單控制項。<br />-<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項中包含的最後一個控制項的向下箭頭和右方向鍵執行與 TAB 鍵相同的操作。 如果存在可[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]聚焦控制項，則焦點將移出<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。 此行為不同于標準<xref:System.Windows.Forms.ContainerControl>行為，因為未對第一個控制項進行換行。 如果沒有其他可[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]聚焦控制項，則焦點將返回到選項卡順序中的第一個 Windows 表單控制項。|不適用。|  
|快速鍵|除非在「不支援」的資料行中註明，否則快速鍵會如常運作。|跨技術的重複快速鍵不會像一般重複快速鍵一樣運作。 當跨技術複製加速器時，Windows 表單控制項中至少有一個，另一個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在控制項上，Windows 表單控制項始終接收加速器。 按下重複快速鍵時，不會切換控制項之間的焦點。|  
|快速鍵|除非在「不支援」的資料行中註明，否則快速鍵會如常運作。|- 在預處理階段處理的 Windows 表單快速鍵始終優先于[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]快速鍵。 例如，如果您有一個<xref:System.Windows.Forms.ToolStrip>定義了 CTRL_S 快速鍵的控制項，並且有一個[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]綁定到 CTRL_S 的命令<xref:System.Windows.Forms.ToolStrip>，則無論焦點如何，始終首先調用控制項處理常式。<br />- 事件處理的<xref:System.Windows.Forms.Control.KeyDown>Windows 表單快速鍵在 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]最後處理。 您可以通過重寫 Windows 表單控制項<xref:System.Windows.Forms.Control.IsInputKey%2A>的方法或處理<xref:System.Windows.Forms.Control.PreviewKeyDown>事件來防止此行為。 從`true`<xref:System.Windows.Forms.Control.IsInputKey%2A>方法返回，或在<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType>`true`<xref:System.Windows.Forms.Control.PreviewKeyDown>事件處理常式中將屬性的值設置為。|  
|AcceptsReturn、AcceptsTab 和其他控制項特定行為|更改預設鍵盤行為的屬性照常工作，假定 Windows 表單控制項重寫要返回<xref:System.Windows.Forms.Control.IsInputKey%2A>`true`的方法。|Windows 表單控制項通過處理<xref:System.Windows.Forms.Control.KeyDown>事件更改預設鍵盤行為，最後在主機[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項中處理。 因為這些控制項會最後處理，所以它們會產生非預期的行為。|  
|Enter 和 Leave 事件|當焦點不進入包含<xref:System.Windows.Forms.Integration.ElementHost>控制項時，當焦點在單個<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項中更改時，將像往常一樣引發 Enter 和 Leave 事件。|發生下列焦點變更時，不會引發 Enter 和 Leave 事件：<br /><br /> - 從內部到控制<xref:System.Windows.Forms.Integration.WindowsFormsHost>外部。<br />- 從外部到<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項內部。<br />- 在<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項之外<br />- 從託管在控制項中的 Windows<xref:System.Windows.Forms.Integration.WindowsFormsHost>表單控制項<xref:System.Windows.Forms.Integration.ElementHost>到託管在同<xref:System.Windows.Forms.Integration.WindowsFormsHost>一控制項中的控制項。|  
|多執行緒|支援各種多執行緒。|Windows 表單[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和技術都假定為單線程併發模型。 在偵錯期間，其他執行緒中架構物件的呼叫將會引發例外狀況，來強制執行這項需求。|  
|安全性|所有交互操作情節都需要完全信任。|在部分信任中，不允許交互操作情節。|  
|Accessibility|支援所有協助工具情節。 輔助技術產品用於包含 Windows 表單和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項的混合應用程式時，它們能夠正常工作。|不適用。|  
|剪貼簿|所有剪貼簿作業都會如常運作。 這包括在 Windows 表單和控制項之間進行剪切[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和粘貼。|不適用。|  
|拖放功能|所有拖放作業都會如常運作。 這包括 Windows 表單和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項之間的操作。|不適用。|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>
## <a name="hosting-wpf-controls-in-windows-forms"></a>將 WPF 控制項裝載在 Windows Forms 中  
 當 Windows 表單控制項承載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項時，支援以下操作間方案：  
  
- 使用程式碼來裝載一或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項。  
  
- 建立屬性工作表與一或多個裝載之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的關聯。  
  
- 在表單中裝載一或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面。  
  
- 啟動 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視窗。  
  
- 使用 Windows 表單主表單和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]詳細資訊託管主/詳細資訊表單。  
  
- 使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]主表單和 Windows 表單詳細資訊託管主/詳細資訊表單。  
  
- 裝載自訂的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項。  
  
- 裝載混合控制項。  
  
### <a name="ambient-properties"></a>環境屬性  
 Windows 表單控制項的某些環境屬性具有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]等效項。 這些環境屬性傳播到託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項，並作為控制項上的<xref:System.Windows.Forms.Integration.ElementHost>公共屬性公開。 該<xref:System.Windows.Forms.Integration.ElementHost>控制項將每個 Windows 表單環境屬性轉換為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]等效屬性。  
  
 如需詳細資訊，請參閱 [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)。  
  
### <a name="behavior"></a>行為  
 下表描述交互操作行為。  
  
|行為|支援|不支援|  
|--------------|---------------|-------------------|  
|透明度|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項轉譯支援透明度。 父 Windows 表單控制項的背景可以成為託管[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項的背景。|不適用。|  
|多執行緒|支援各種多執行緒。|Windows 表單[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和技術都假定為單線程併發模型。 在偵錯期間，其他執行緒中架構物件的呼叫將會引發例外狀況，來強制執行這項需求。|  
|安全性|所有交互操作情節都需要完全信任。|在部分信任中，不允許交互操作情節。|  
|Accessibility|支援所有協助工具情節。 輔助技術產品用於包含 Windows 表單和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項的混合應用程式時，它們能夠正常工作。|不適用。|  
|剪貼簿|所有剪貼簿作業都會如常運作。 這包括在 Windows 表單和控制項之間進行剪切[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和粘貼。|不適用。|  
|拖放功能|所有拖放作業都會如常運作。 這包括 Windows 表單和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項之間的操作。|不適用。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [逐步解說：在 WPF 中裝載 Windows Forms 控制項](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Form 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)
