---
title: "物件存留期事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e31997cfc1ff7500317bdfc59ac6ad12d3d27a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="object-lifetime-events"></a>物件存留期事件
本主題說明特定的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件，表示物件的建立、使用和解構存留期階段。  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)主題。 為了解本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] (請參閱 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)) 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="intro"></a>   
## <a name="object-lifetime-events"></a>物件存留期事件  
 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] Managed 程式碼中的所有物件都會經歷類似的生命、建立、使用和解構的系列階段。 許多物件的生命最終階段也會發生在解構階段，成為此階段的一部分。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件，更確切的說就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 識別為項目的視覺物件，也有一系列常見的物件生命階段。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計和應用程式模型會將這些階段公開為一系列的事件。 關於存留期事件，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有四種主要的物件類型：一般項目、視窗項目、巡覽裝載和應用程式物件。 視窗和巡覽裝載也在較大的群組視覺物件 (項目) 內。 本主題說明通用於所有項目的存留期事件，再介紹適用於應用程式定義、視窗或巡覽裝載的較特定存留期事件。  
  
<a name="common_events"></a>   
## <a name="common-lifetime-events-for-elements"></a>項目共通的存留期事件  
 任何 WPF 架構層級項目 (這些物件，從其中衍生<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>) 有三種常見的存留期事件： <xref:System.Windows.FrameworkElement.Initialized>， <xref:System.Windows.FrameworkElement.Loaded>，和<xref:System.Windows.FrameworkElement.Unloaded>。  
  
### <a name="initialized"></a>Initialized  
 <xref:System.Windows.FrameworkElement.Initialized>會先引發，並呼叫其建構函式對應至物件的初始化。 因為事件是回應初始化而發生，所以保證設定物件的所有屬性。 (例外狀況是運算式使用方式，例如動態資源或繫結，這些是未評估的運算式。)根據需求設定的所有屬性，順序<xref:System.Windows.FrameworkElement.Initialized>標記中定義的巢狀項目所產生似乎發生的項目樹狀結構中最深的項目順序中第一次，然後父系到根項目。 此順序是因為父子式關聯性和內含項目都是屬性，因此在填滿屬性的子項目也完全初始化之前，父代無法報告初始化。  
  
 當您要撰寫處理常式以回應<xref:System.Windows.FrameworkElement.Initialized>事件，您必須考慮的項目樹狀目錄中 （邏輯樹狀結構或視覺化樹狀結構） 附加的處理常式周圍的其他所有項目已建立，特別是不保證父項目。 成員變數可能是 Null，或資料來源可能未填入基礎繫結 (即使在運算式層級)。  
  
### <a name="loaded"></a>已載入  
 <xref:System.Windows.FrameworkElement.Loaded>接下來就會引發。 <xref:System.Windows.FrameworkElement.Loaded>最終呈現之前，但在版面配置系統有導出所有需要的值轉譯之後，就會引發事件。 <xref:System.Windows.FrameworkElement.Loaded>需要內含項目邏輯樹狀結構已完成，且連接到提供 HWND 和呈現表面的呈現來源。 標準的資料繫結 （繫結到本機的來源，例如其他屬性或直接定義的資料來源） 將會發生之前<xref:System.Windows.FrameworkElement.Loaded>。 非同步資料繫結 (外部或動態來源) 可能已發生，但根據其非同步性質的定義不能保證其已發生。  
  
 機制可以用<xref:System.Windows.FrameworkElement.Loaded>引發不同<xref:System.Windows.FrameworkElement.Initialized>。 <xref:System.Windows.FrameworkElement.Initialized>事件則是項目，而不直接的協調作業已完成的項目樹狀架構所引發的項目。 相反地，<xref:System.Windows.FrameworkElement.Loaded>為整個項目樹狀結構 （具體而言，邏輯樹狀結構） 的人員共同引發事件。 在樹狀目錄中的所有項目時載入，它們被視為狀態<xref:System.Windows.FrameworkElement.Loaded>根項目上第一次引發事件。 <xref:System.Windows.FrameworkElement.Loaded>每個子項目然後連續引發事件。  
  
> [!NOTE]
>  此行為表面上可能類似路由事件的通道。 但是事件與事件之間不傳遞任何資訊。 每個項目一律會有機會處理其<xref:System.Windows.FrameworkElement.Loaded>事件，並標示為已處理的事件資料已超過該元素沒有影響。  
  
### <a name="unloaded"></a>已卸載  
 <xref:System.Windows.FrameworkElement.Unloaded>最後引發，而由起始呈現來源或視覺化父項目，並被移除。 當<xref:System.Windows.FrameworkElement.Unloaded>會引發和處理，是事件來源父代的項目 (由<xref:System.Windows.FrameworkElement.Parent%2A>屬性) 或任何指定的項目中的邏輯或視覺化樹狀結構向上可能已經被取消，這表示該資料繫結，資源參考而樣式不設定為其標準或最後一個已知的執行階段值。  
  
<a name="application_model_elements"></a>   
## <a name="lifetime-events-application-model-elements"></a>存留期事件應用程式模型項目  
 建立一般的存留期事件項目為下列應用程式模型項目： <xref:System.Windows.Application>， <xref:System.Windows.Window>， <xref:System.Windows.Controls.Page>， <xref:System.Windows.Navigation.NavigationWindow>，和<xref:System.Windows.Controls.Frame>。 這些會延伸共通存留期事件及與其特定用途相關的其他事件。 下列位置對這些有詳細討論：  
  
-   <xref:System.Windows.Application>:[應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)。  
  
-   <xref:System.Windows.Window>: [WPF Windows 概觀](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)。  
  
-   <xref:System.Windows.Controls.Page><xref:System.Windows.Navigation.NavigationWindow>，和<xref:System.Windows.Controls.Frame>:[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
