---
title: "最佳化效能：應用程式資源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0a7c9920b321f15f3f01a64fbfc80693042a025
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-application-resources"></a>最佳化效能：應用程式資源
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可讓您共用應用程式資源，以便您可以透過類似具類型的項目支援一致的外觀或行為。 本主題提供的一些建議這個區域，可協助您改善應用程式的效能。  
  
 如需詳細資訊，請參閱 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
## <a name="sharing-resources"></a>共用資源  
 如果您的應用程式會使用自訂控制項，並定義中的資源<xref:System.Windows.ResourceDictionary>（或 XAML 資源節點），建議您是定義在資源<xref:System.Windows.Application>或<xref:System.Windows.Window>物件層級，或定義它們中的預設佈景主題自訂控制項。 定義自訂控制項中的資源<xref:System.Windows.ResourceDictionary>會影響效能，該控制項的每個執行個體。 例如，如果您有大量效能的筆刷作業定義為自訂控制項的資源定義的一部分，以及許多執行個體的自訂控制項，應用程式的工作集將會大幅增加。  
  
 為了說明這點，請考慮下列項目。 假設您正在開發卡遊戲 using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 大部分的撲克牌遊戲，您必須具有不同的字體 52 52 卡片。 您決定實作卡自訂控制項和您定義 52 筆刷 （每個都代表卡面） 中的資源，卡片自訂控制項。 在主應用程式一開始建立 52 此卡的自訂控制項的執行個體。 卡片自訂控制項的每個執行個體會產生 52 個執行個體<xref:System.Windows.Media.Brush>物件，可讓您總共 52 * 52<xref:System.Windows.Media.Brush>應用程式中的物件。 藉由移動卡自訂控制項資源不足筆刷<xref:System.Windows.Application>或<xref:System.Windows.Window>物件層級，或自訂控制項的預設佈景主題中定義您減少應用程式的工作集，因為您現在共用 52 筆刷在 52 卡控制項執行個體。  
  
## <a name="sharing-a-brush-without-copying"></a>無需先行複製共用筆刷  
 如果您有多個使用相同的項目<xref:System.Windows.Media.Brush>物件，定義為資源的筆刷，並參考它，而不是定義中內嵌的筆刷[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]。 這個方法會建立一個執行個體，並重複使用，而定義中的筆刷內嵌[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]建立新的執行個體，每個項目。  
  
 下列標記範例將說明這一點：  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>使用靜態資源時可能  
 靜態資源查閱已定義之資源的參考，用於任何 XAML 屬性提供值。 該資源的查閱行為相當於編譯時期查閱。  
  
 動態的資源，相反地，將會建立暫存的運算式，在初始的編譯期間和直到實際需要才能建構物件，而要求的資源值，因此延遲的資源查閱。 該資源的查閱行為相當於執行階段查閱，會影響效能。 使用靜態的資源，請盡可能使用動態的資源，只在必要時在您的應用程式中。  
  
 下列標記範例會示範如何使用兩種類型的資源：  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [版面配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
