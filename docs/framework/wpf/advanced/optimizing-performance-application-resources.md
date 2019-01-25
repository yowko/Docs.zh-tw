---
title: 最佳化效能：應用程式資源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: fa412a4f900179c22868b2ef3e7429e7dc2acc9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507547"
---
# <a name="optimizing-performance-application-resources"></a>最佳化效能：應用程式資源
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您共用應用程式資源，以便您可以透過類似類型的項目支援一致的外觀或行為。 本主題提供可協助您這方面的一些建議改善您的應用程式的效能。  
  
 如需詳細資訊，請參閱 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
## <a name="sharing-resources"></a>共用資源  
 如果您的應用程式會使用自訂控制項，並定義中的資源<xref:System.Windows.ResourceDictionary>（或 XAML 資源節點），建議您其中一個定義的資源<xref:System.Windows.Application>或<xref:System.Windows.Window>物件層級，或定義中的預設佈景主題自訂控制項。 在 自訂控制項中定義資源<xref:System.Windows.ResourceDictionary>會影響效能，該控制項的每個執行個體。 比方說，如果您有需要大量效能的筆刷作業定義為屬於自訂控制項的資源定義和自訂控制項的許多執行個體，則應用程式的工作集將會大幅增加。  
  
 為了說明這點，請考慮下列項目。 假設您正在開發卡遊戲使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 大部分的撲克牌遊戲，您必須使用 52 不同臉部的 52 張紙牌。 您決定實作卡片自訂控制項，您定義 （每個都代表卡 face） 的 52 筆刷卡自訂控制項的資源中。 主要的應用程式中您一開始會建立此卡的自訂控制項 52 執行個體。 卡片的自訂控制項的每個執行個體產生 52 個執行個體<xref:System.Windows.Media.Brush>物件，可讓您總共 52 * 52<xref:System.Windows.Media.Brush>應用程式中的物件。 藉由移動到卡片的自訂控制項資源不足的筆刷<xref:System.Windows.Application>或<xref:System.Windows.Window>物件層級，或定義它們預設佈景主題自訂控制項，因為您現在共用 52 筆刷，減少應用程式的工作集52 的卡片控制項的執行個體。  
  
## <a name="sharing-a-brush-without-copying"></a>未複製的情況下共用筆刷  
 如果您有多個使用相同的項目<xref:System.Windows.Media.Brush>物件，定義為資源的筆刷並參考它，而不是定義在內嵌的筆刷[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]。 這個方法會建立一個執行個體，並重複使用，而定義中的筆刷內嵌[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]建立新的執行個體，每個項目。  
  
 下列標記範例說明這一點：  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>使用靜態資源，可能的話  
 靜態資源會提供任何 XAML 內容屬性的值，藉由查閱已定義之資源的參考。 該資源查閱行為相當於編譯時期查閱。  
  
 相反地，動態資源，可能會將裝置建立初始的編譯期間的暫時運算式，並因此延後資源的查閱，直到實際需要以建構物件，而要求的資源值。 該資源查閱行為相當於執行階段對應，它會影響效能。 使用靜態資源，請盡可能使用動態資源，只在必要時在您的應用程式中。  
  
 下列標記範例示範如何使用這兩種類型的資源：  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>另請參閱
- [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
- [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)
- [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)
- [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
- [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)
- [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
