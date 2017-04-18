---
title: "物件存留期事件 | Microsoft Docs"
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
  - "Activated 事件"
  - "應用程式物件, 存留期事件"
  - "類別, Frame"
  - "類別, NavigationWindow"
  - "Closed 事件"
  - "Closing 事件"
  - "ContentRendered 事件"
  - "Deactivated 事件"
  - "事件, Activated"
  - "事件, 已關閉"
  - "事件, Closing"
  - "事件, ContentRendered"
  - "事件, Deactivated"
  - "事件, Initialized"
  - "事件, Loaded"
  - "事件, Unloaded"
  - "結束事件"
  - "Frame 類別"
  - "Initialized 事件"
  - "物件的存留期事件"
  - "Loaded 事件"
  - "NavigationWindow 類別"
  - "物件的存留期事件"
  - "啟動事件"
  - "Unloaded 事件"
ms.assetid: face6fc7-465b-4502-bfe5-e88d2e729a78
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 物件存留期事件
本主題說明通知物件存留期當中建立、使用和解構各階段的特定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已了解[相依性屬性](GTMT)，知道如何使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別上的現有相依性屬性，而且已閱讀過[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)主題。  為了能夠理解本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] \(請參閱 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)\)，並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="intro"></a>   
## 物件存留期事件  
 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] Managed 程式碼中的所有物件都會經歷類似的生命週期階段，即建立、使用和解構。  許多物件也有發生在解構期間的最終化階段。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件 \(更具體來說，是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 識別為項目的視覺物件\) 也有一組物件生命週期階段。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 程式設計和應用程式模型會將這些階段公開為一系列的事件。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 有四種主要的物件類型與存留期事件相關，分別是一般項目、視窗項目、巡覽裝載和應用程式物件。  視窗和巡覽裝載也屬於較大的視覺物件 \(項目\) 群組。  本主題說明所有項目通用的存留期事件，然後再介紹適用於應用程式定義、視窗或巡覽裝載的事件。  
  
<a name="common_events"></a>   
## 項目的通用存留期事件  
 任何 [WPF 架構層級](GTMT)項目 \(即衍生自 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 的物件\) 都有三個通用存留期事件：<xref:System.Windows.FrameworkElement.Initialized>、<xref:System.Windows.FrameworkElement.Loaded> 和 <xref:System.Windows.FrameworkElement.Unloaded>。  
  
### Initialized  
 <xref:System.Windows.FrameworkElement.Initialized> 會先引發，這大致上相當於呼叫物件的建構函式來對它進行初始設定。  由於事件會引發來回應初始設定，因此物件的所有屬性都確保能設定   \(但像是動態資源或繫結等運算式用法則例外，這些會是未評估的運算式\)。 由於所有屬性都必須設定，因此標記中定義的巢狀項目引發的 <xref:System.Windows.FrameworkElement.Initialized> 順序會是項目樹狀結構中最深層的項目最優先，然後是朝根部的父項目。  此順序是因為父\-子關係 \(Parent\-Child Relationship\) 和內含項目都是屬性，因此父項目要等到填入屬性的子項目都完全初始設定後，才能報告完成初始設定。  
  
 當您撰寫回應 <xref:System.Windows.FrameworkElement.Initialized> 事件的處理常式時，必須考慮到，項目樹狀結構 \(無論是[邏輯樹狀結構](GTMT)或[視覺化樹狀結構](GTMT)\) 中附加處理常式的位置前後的所有其他項目不一定都已建立，特別是父項目。  成員變數可能為 null，或者資料來源尚未由基礎繫結填入 \(即使在運算式層級\)。  
  
### Loaded  
 <xref:System.Windows.FrameworkElement.Loaded> 會接著引發。  <xref:System.Windows.FrameworkElement.Loaded> 事件引發的時機是在最後轉譯之前，但是在配置系統計算出轉譯需要的所有值之後。  <xref:System.Windows.FrameworkElement.Loaded> 會需要包含項目的邏輯樹狀結構是完整的，並且連接至提供 HWND 和轉譯介面的展示來源。  標準資料繫結 \(繫結至本機來源，例如其他屬性或直接定義的資料來源\) 將在 <xref:System.Windows.FrameworkElement.Loaded> 之前發生。  非同步資料繫結 \(外部或動態來源\) 可能會發生，但根據其非同步性質的定義，則不保證一定會發生。  
  
 引發 <xref:System.Windows.FrameworkElement.Loaded> 事件的機制與 <xref:System.Windows.FrameworkElement.Initialized> 不同。  <xref:System.Windows.FrameworkElement.Initialized> 事件是依個別項目引發，而沒有完整的項目樹狀結構直接協調。  相對地，<xref:System.Windows.FrameworkElement.Loaded> 事件則是透過整個項目樹狀結構 \(具體來說，就是[邏輯樹狀結構](GTMT)\) 協調而引發。  當樹狀結構中的所有項目都視為載入時，就會先在根項目上引發 <xref:System.Windows.FrameworkElement.Loaded> 事件。  接著會在後面的每個子項目上引發 <xref:System.Windows.FrameworkElement.Loaded> 事件。  
  
> [!NOTE]
>  此行為在表面上可能類似[路由事件](GTMT)的通道。  不過，事件之間不會傳遞資訊。  每個項目都有機會處理其 <xref:System.Windows.FrameworkElement.Loaded> 事件，而將事件資料標記為已處理對該項目以外並無作用。  
  
### Unloaded  
 <xref:System.Windows.FrameworkElement.Unloaded> 會最後引發，而且是由展示來源或要移除的視覺父項目所啟始。  引發和處理 <xref:System.Windows.FrameworkElement.Unloaded> 時，事件來源父項目 \(由 <xref:System.Windows.FrameworkElement.Parent%2A> 屬性決定\) 或在邏輯或視覺化樹狀結構中上層的任何指定項目可能已經取消設定，表示資料繫結、資源參考和樣式可能未設成一般或最後已知的執行階段值。  
  
<a name="application_model_elements"></a>   
## 存留期事件應用程式模型項目  
 項目以通用存留期事件為基礎的包括下列應用程式模型項目：<xref:System.Windows.Application>、<xref:System.Windows.Window>、<xref:System.Windows.Controls.Page>、<xref:System.Windows.Navigation.NavigationWindow> 和 <xref:System.Windows.Controls.Frame>。  這些項目以與其特定用途相關的更多事件延伸了通用存留期事件。  下列章節將詳細討論這些項目：  
  
-   <xref:System.Windows.Application>: [應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
-   <xref:System.Windows.Window>: [WPF 視窗概觀](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).  
  
-   <xref:System.Windows.Controls.Page>、<xref:System.Windows.Navigation.NavigationWindow> 和 <xref:System.Windows.Controls.Frame>: [巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
## 請參閱  
 [相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)