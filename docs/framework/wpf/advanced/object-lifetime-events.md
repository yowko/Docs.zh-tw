---
title: 物件存留期事件
ms.date: 03/30/2017
helpviewer_keywords:
- events [WPF], ContentRendered
- events [WPF], Deactivated
- events [WPF], Unloaded
- Activated events [WPF]
- events [WPF], Loaded
- Application objects [WPF], lifetime events
- events [WPF], Activated
- ContentRendered events [WPF]
- Deactivated events [WPF]
- events [WPF], Initialized
- events [WPF], Closing
- Unloaded events [WPF]
- exit events [WPF]
- objects' lifetime events [WPF]
- Loaded events [WPF]
- Closing events [WPF]
- events [WPF], Closed
- Initialized events [WPF]
- Closed events [WPF]
- startup events [WPF]
- lifetime events of objects [WPF]
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
ms.openlocfilehash: dd2e116c4241a44786af3a56b931b0c3c0571814
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933495"
---
# <a name="object-lifetime-events"></a>物件存留期事件
本主題說明特定的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件，表示物件的建立、使用和解構存留期階段。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)主題。 為了解本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (請參閱 [XAML 概觀 (WPF)](xaml-overview-wpf.md)) 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>物件存留期事件  
 Microsoft .NET Framework managed 程式碼中的所有物件都經過一組類似的生命週期, 例如建立、使用及銷毀。 許多物件的生命最終階段也會發生在解構階段，成為此階段的一部分。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件，更確切的說就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 識別為項目的視覺物件，也有一系列常見的物件生命階段。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計和應用程式模型會將這些階段公開為一系列的事件。 關於存留期事件，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有四種主要的物件類型：一般項目、視窗項目、巡覽裝載和應用程式物件。 視窗和巡覽裝載也在較大的群組視覺物件 (項目) 內。 本主題說明通用於所有項目的存留期事件，再介紹適用於應用程式定義、視窗或巡覽裝載的較特定存留期事件。  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>項目共通的存留期事件  
 任何 WPF 架構層級元素 (衍生自<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>的物件) 都有三個常見的存留<xref:System.Windows.FrameworkElement.Initialized>期<xref:System.Windows.FrameworkElement.Loaded>事件: <xref:System.Windows.FrameworkElement.Unloaded>、和。  
  
### <a name="initialized"></a>Initialized  
 <xref:System.Windows.FrameworkElement.Initialized>會先引發, 而大致對應于呼叫其函式的初始化物件。 因為事件是回應初始化而發生，所以保證設定物件的所有屬性。 (例外狀況是運算式使用方式，例如動態資源或繫結，這些是未評估的運算式。)由於設定了所有屬性的需求, 因此在標記中定義的嵌套<xref:System.Windows.FrameworkElement.Initialized>元素所引發的順序似乎會依照專案樹狀結構中最深層的元素順序出現, 然後指向根項目的上層專案。 此順序是因為父子式關聯性和內含項目都是屬性，因此在填滿屬性的子項目也完全初始化之前，父代無法報告初始化。  
  
 當您撰寫處理常式以回應<xref:System.Windows.FrameworkElement.Initialized>事件時, 您必須考慮到專案樹狀結構 (邏輯樹狀結構或視覺化樹狀結構) 中的所有其他元素都已建立, 特別是父元素。 成員變數可能是 Null，或資料來源可能未填入基礎繫結 (即使在運算式層級)。  
  
### <a name="loaded"></a>已載入  
 <xref:System.Windows.FrameworkElement.Loaded>下一步會引發。 <xref:System.Windows.FrameworkElement.Loaded>事件會在最終轉譯之前引發, 但是在配置系統已計算出所有必要的值以進行轉譯之後。 <xref:System.Windows.FrameworkElement.Loaded>需要包含專案的邏輯樹狀結構已完成, 並連接到提供 HWND 和轉譯介面的呈現來源。 之前已發生標準資料系結 (系結至本機來源, 例如其他屬性或直接定義的資料來源) <xref:System.Windows.FrameworkElement.Loaded>。 非同步資料繫結 (外部或動態來源) 可能已發生，但根據其非同步性質的定義不能保證其已發生。  
  
 引發<xref:System.Windows.FrameworkElement.Loaded>事件的機制不同于<xref:System.Windows.FrameworkElement.Initialized>。 <xref:System.Windows.FrameworkElement.Initialized>事件是依專案引發元素, 而不需要由完成的專案樹狀結構直接協調。 相較之下, <xref:System.Windows.FrameworkElement.Loaded>事件會以協調的方式引發在整個專案樹狀結構中 (特別是邏輯樹狀結構)。 當樹狀結構中的所有元素都處於被視為已載入的狀態時, <xref:System.Windows.FrameworkElement.Loaded>會先在根項目上引發事件。 接著<xref:System.Windows.FrameworkElement.Loaded> , 事件會在每個子專案上連續引發。  
  
> [!NOTE]
> 此行為表面上可能類似路由事件的通道。 但是事件與事件之間不傳遞任何資訊。 每個元素一律有機會處理其<xref:System.Windows.FrameworkElement.Loaded>事件, 並將事件資料標示為已處理, 不會影響該元素。  
  
### <a name="unloaded"></a>已卸載  
 <xref:System.Windows.FrameworkElement.Unloaded>是最後引發, 而且是由呈現來源或要移除的視覺父代起始。 當<xref:System.Windows.FrameworkElement.Unloaded>引發和處理時, 屬於事件來源父系的專案 (由<xref:System.Windows.FrameworkElement.Parent%2A>屬性判斷), 或在邏輯或視覺樹狀結構中向上或任何指定的專案, 可能已經取消設定, 表示資料系結, 資源參考、和樣式可能不會設定為其一般或上次已知的運行時間值。  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>存留期事件應用程式模型項目  
 以元素的常見存留期事件為基礎, 是下列應用程式模型<xref:System.Windows.Application>元素<xref:System.Windows.Window>: <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Navigation.NavigationWindow>、、 <xref:System.Windows.Controls.Frame>和。 這些會延伸共通存留期事件及與其特定用途相關的其他事件。 下列位置對這些有詳細討論：  
  
- <xref:System.Windows.Application>：[應用程式管理總覽](../app-development/application-management-overview.md)。  
  
- <xref:System.Windows.Window>：[WPF 視窗總覽](../app-development/wpf-windows-overview.md)。  
  
- <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Navigation.NavigationWindow>和:<xref:System.Windows.Controls.Frame>[流覽總覽](../app-development/navigation-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [相依性屬性值優先順序](dependency-property-value-precedence.md)
- [路由事件概觀](routed-events-overview.md)
