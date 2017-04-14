---
title: "最佳化效能：應用程式資源 | Microsoft Docs"
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
  - "應用程式資源, 效能"
  - "筆刷, 效能"
  - "資源, 效能"
  - "在未複製的情況下共用筆刷"
  - "資源分享"
  - "靜態資源"
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 最佳化效能：應用程式資源
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您共用應用程式資源，因此可以支援類似型別項目的一致外觀或行為。  本主題提供這個區域的一些建議，以協助您改善應用程式的效能。  
  
 如需資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
## 共用資源  
 如果應用程式使用自訂控制項，並在 <xref:System.Windows.ResourceDictionary> \(或「XAML 資源」節點\) 中定義資源，則建議您在 <xref:System.Windows.Application> 或 <xref:System.Windows.Window> 物件層級定義資源，或將它們定義於自訂控制項的預設佈景主題中。  而在自訂控制項的 <xref:System.Windows.ResourceDictionary> 中定義資源，會影響該控制項之每個執行個體的效能。  例如，如果您將損耗效能的筆刷作業定義為自訂控制項的資源定義一部分，而且擁有自訂控制項的多個執行個體，則應用程式的工作集會明顯增加。  
  
 為了說明這一點，請考慮下列事項。  假設您使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 開發撲克牌遊戲。  在大部分的撲克牌遊戲中，都需要有 52 張撲克牌，具有 52 種不同卡面。  而您決定實作撲克牌自訂控制項，並且在撲克牌自訂控制項的資源中定義 52 種筆刷 \(每個都代表一種卡面\)。  在主要應用程式中，一開始會為這個撲克牌自訂控制項建立 52 個執行個體。  撲克牌自訂控制項的每個執行個體都會產生 52 個 <xref:System.Windows.Media.Brush> 物件的執行個體，因此在應用程式中總共會提供 52 \* 52 個 <xref:System.Windows.Media.Brush> 物件。  若將筆刷移出撲克牌自訂控制項資源並放至 <xref:System.Windows.Application> 或 <xref:System.Windows.Window> 物件層級，或將它們定義於自訂控制項的預設佈景主題中，則可減少應用程式的工作集，因為現在是在 52 個撲克牌控制項執行個體之間共用 52 個筆刷。  
  
## 在未複製的情況下共用筆刷  
 如果有多個使用相同 <xref:System.Windows.Media.Brush> 物件的項目，請將筆刷定義為資源並進行參考，而不是以 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 定義筆刷內嵌 \(Inline\)。  這種方法會建立一個執行個體，並重新使用該執行個體，而在 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 中定義筆刷內嵌則會為每個項目建立新的執行個體。  
  
 下列標記範例會說明這一點：  
  
 [!code-xml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## 盡可能使用靜態資源  
 靜態資源是透過查閱已定義資源的參考，提供任何 XAML 屬性的值。  該資源的查閱行為與編譯階段查閱類似。  
  
 換句話說，動態資源會在初始編譯期間建立暫存運算式，因此在實際需要所要求的資源值以建構物件之前，並不會進行資源的查閱。  該資源的查閱行為與執行階段查閱類似，但會影響效能。  請盡可能在應用程式中使用靜態資源，而動態資源則請在必要時才使用。  
  
 下列標記範例顯示使用兩種類型的資源：  
  
 [!code-xml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## 請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)