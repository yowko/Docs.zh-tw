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
ms.openlocfilehash: 3b761674bd2464ee87e07d9299c805431f8fdeb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141103"
---
# <a name="object-lifetime-events"></a>物件存留期事件
本主題說明特定的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件，表示物件的建立、使用和解構存留期階段。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)主題。 為了解本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (請參閱 [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)) 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="intro"></a>
## <a name="object-lifetime-events"></a>物件存留期事件  
 Microsoft .NET 框架託管代碼中的所有物件都經歷一組類似的生命週期、創建、使用和銷毀階段。 許多物件的生命最終階段也會發生在解構階段，成為此階段的一部分。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件，更確切的說就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 識別為項目的視覺物件，也有一系列常見的物件生命階段。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計和應用程式模型會將這些階段公開為一系列的事件。 關於存留期事件，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有四種主要的物件類型：一般項目、視窗項目、巡覽裝載和應用程式物件。 視窗和巡覽裝載也在較大的群組視覺物件 (項目) 內。 本主題說明通用於所有項目的存留期事件，再介紹適用於應用程式定義、視窗或巡覽裝載的較特定存留期事件。  
  
<a name="common_events"></a>
## <a name="common-lifetime-events-for-elements"></a>項目共通的存留期事件  
 任何 WPF 框架級元素（從<xref:System.Windows.FrameworkElement>任一或<xref:System.Windows.FrameworkContentElement>派生的物件）都有三個常見的生存<xref:System.Windows.FrameworkElement.Initialized>期<xref:System.Windows.FrameworkElement.Loaded>事件：<xref:System.Windows.FrameworkElement.Unloaded>和 。  
  
### <a name="initialized"></a>Initialized  
 <xref:System.Windows.FrameworkElement.Initialized>首先引發，並且大致對應于物件的初始化，由調用其建構函式。 因為事件是回應初始化而發生，所以保證設定物件的所有屬性。 （一個例外是運算式用法，如動態資源或綁定;這些運算式將是未計算的運算式。由於要求設置所有屬性，標記中定義的嵌套元素的引發順序<xref:System.Windows.FrameworkElement.Initialized>似乎首先以元素樹中最深的元素的順序發生，然後是父元素對根的順序。 此順序是因為父子式關聯性和內含項目都是屬性，因此在填滿屬性的子項目也完全初始化之前，父代無法報告初始化。  
  
 編寫處理常式以回應<xref:System.Windows.FrameworkElement.Initialized>事件時，必須考慮不能保證元素樹中附加處理常式的所有其他元素（邏輯樹或視覺化樹）已創建處理常式，尤其是父元素。 成員變數可能是 Null，或資料來源可能未填入基礎繫結 (即使在運算式層級)。  
  
### <a name="loaded"></a>已載入  
 <xref:System.Windows.FrameworkElement.Loaded>下次引發。 事件<xref:System.Windows.FrameworkElement.Loaded>在最終渲染之前引發，但在佈局系統計算了渲染所需的所有值之後。 <xref:System.Windows.FrameworkElement.Loaded>需要元素中包含的邏輯樹已完成，並連接到提供 HWND 和呈現曲面的表示源。 標準資料繫結（綁定到本地源，如其他屬性或直接定義的資料來源）將在<xref:System.Windows.FrameworkElement.Loaded>之前發生。 非同步資料繫結 (外部或動態來源) 可能已發生，但根據其非同步性質的定義不能保證其已發生。  
  
 引發<xref:System.Windows.FrameworkElement.Loaded>事件的機制與<xref:System.Windows.FrameworkElement.Initialized>不同。 事件<xref:System.Windows.FrameworkElement.Initialized>按元素引發，無需由已完成的元素樹直接協調。 相反，事件<xref:System.Windows.FrameworkElement.Loaded>在整個元素樹（特別是邏輯樹）中作為協調工作提出。 當樹中的所有元素都處於被視為載入狀態時，首先在<xref:System.Windows.FrameworkElement.Loaded>根項目上引發該事件。 然後<xref:System.Windows.FrameworkElement.Loaded>，在每個子項目上依次引發該事件。  
  
> [!NOTE]
> 此行為表面上可能類似路由事件的通道。 但是事件與事件之間不傳遞任何資訊。 每個元素始終有機會處理其<xref:System.Windows.FrameworkElement.Loaded>事件，並將事件資料標記為已處理，除了該元素之外，沒有任何效果。  
  
### <a name="unloaded"></a>已卸載  
 <xref:System.Windows.FrameworkElement.Unloaded>上次引發，由要刪除的表示源或可視父級啟動。 引發<xref:System.Windows.FrameworkElement.Unloaded>和處理時，作為事件源父元素的元素（由<xref:System.Windows.FrameworkElement.Parent%2A>屬性確定）或邏輯或視覺化樹中向上的任何給定元素可能已取消設置，這意味著資料繫結、資源引用和樣式可能未設置為其正常或最後已知的運行時值。  
  
<a name="application_model_elements"></a>
## <a name="lifetime-events-application-model-elements"></a>存留期事件應用程式模型項目  
 基於元素的常見存留期事件，下面是以下應用程式模型<xref:System.Windows.Application>元素： 、 <xref:System.Windows.Window> <xref:System.Windows.Controls.Page>、<xref:System.Windows.Navigation.NavigationWindow>和<xref:System.Windows.Controls.Frame>。 這些會延伸共通存留期事件及與其特定用途相關的其他事件。 下列位置對這些有詳細討論：  
  
- <xref:System.Windows.Application>：[應用程式管理概述](../app-development/application-management-overview.md)。  
  
- <xref:System.Windows.Window>[：WPF 視窗概述](../app-development/wpf-windows-overview.md)。  
  
- <xref:System.Windows.Controls.Page>、<xref:System.Windows.Navigation.NavigationWindow>和<xref:System.Windows.Controls.Frame>：[導航概述](../app-development/navigation-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [依賴項屬性值優先順序](dependency-property-value-precedence.md)
- [路由事件概觀](routed-events-overview.md)
