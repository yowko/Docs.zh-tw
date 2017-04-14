---
title: "應用程式效能規劃 | Microsoft Docs"
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
  - "應用程式, 最佳化"
  - "WPF 應用程式, 最佳化"
ms.assetid: c91bd0c5-a193-46ff-9da1-eb7a3a76a3b3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 應用程式效能規劃
您是否能達到效能目標，取決於您是否妥善開發效能策略。  規劃是開發產品的第一個階段。  本主題說明開發良好效能策略的某些簡單規則。  
  
## 以案例的角度思考  
 案例可協助您著重在應用程式的重要元件上。  案例通常衍生自您的客戶，以及競爭對手的產品。  請隨時關注您的客戶，並就您的產品與競爭對手的產品，找出真正令他們心動的產品特性。  客戶的回應可協助您決定應用程式的主要案例。  例如，若您要設計在啟動時使用的元件，此元件可能只會在應用程式啟動時被呼叫一次。  因此啟動時間即成為主要案例。  主要案例的其他範例可能包括動畫序列理想的畫面播放速率，或應用程式允許的最大工作集。  
  
## 定義目標  
 目標可協助您決定要以較快或較慢的速度執行應用程式。  您應定義所有案例的目標。  您定義的所有效能目標皆應以客戶的期望為依據。  在應用程式開發期間可能仍有許多尚未解決的問題，因此難以設定效能目標。  但與其完全不設定目標，最好還是先設定初期目標，後續再加以修訂。  
  
## 了解您的平台  
 在應用程式開發期間，請務必進行測量、調查、調整與更正等程序。  從開發程序開始到結束，您都必須在可靠而穩定的環境中測量應用程式的效能。  應避免外來因素所造成的變數。  例如，在測試效能時，您應停用防毒軟體或任何自動更新 \(如 SMS\)，以免影響效能測試結果。  測量應用程式的效能後，必須找出可產生最大改善的變更。  修改應用程式後，請重新執行測試。  
  
## 反覆進行效能調整  
 您應了解您所使用的每項功能的相對成本。  例如，在 [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] 中使用反映 \(Reflection\) 通常會耗用許多運算資源而影響效能，因此應謹慎使用。  這並不代表您應避免使用反映，而是說您應謹慎平衡應用程式的效能需求與您所使用之功能的效能需求。  
  
## 建置豐富的圖形  
 若要建立有彈性的方法以達成理想的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式效能，建置豐富而複雜的圖形是一項重要技巧。  一開始請務必以最不影響效能的資源來達成您的案例目標。  一旦達成目標後，即可使用較會耗損效能之功能來建置豐富的圖形，並請隨時考量您的案例目標。  切記，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是具有多樣化功能的平台，並可提供非常豐富的圖形功能。  在未經考慮的情況下使用會耗損效能的功能，可能會對整體應用程式效能造成負面影響。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項允許使用者有彈性地自訂其外觀，而不會改變其控制項行為，因此原本即具有擴充性。  您可以利用樣式、資料範本與控制項範本來建立及擬定自訂的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，以因應您的效能需求。  
  
## 請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)