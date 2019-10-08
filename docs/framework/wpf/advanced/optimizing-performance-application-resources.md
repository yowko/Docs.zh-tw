---
title: 優化效能：應用程式資源
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 759d02afe1934d2ace4ed226d5d911db2d676d98
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005036"
---
# <a name="optimizing-performance-application-resources"></a>優化效能：應用程式資源
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您共用應用程式資源，如此一來，您就可以在相似類型的元素之間支援一致的外觀或行為。 本主題提供此區域中的幾項建議，可協助您改善應用程式的效能。  
  
 如需詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。  
  
## <a name="sharing-resources"></a>共用資源  
 如果您的應用程式使用自訂控制項，並在 <xref:System.Windows.ResourceDictionary> （或 XAML 資源）節點中定義資源，建議您在 <xref:System.Windows.Application> 或 @no__t 2 物件層級定義資源，或在自訂控制項的預設主題中加以定義。 在自訂控制項的 <xref:System.Windows.ResourceDictionary> 中定義資源，會對該控制項的每個實例造成效能上的影響。 例如，如果您有一項需要大量效能的筆刷作業定義為自訂控制項的資源定義以及自訂控制項的許多實例，應用程式的工作集就會大幅增加。  
  
 為了說明這一點，請考慮下列事項。 假設您正在使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 來開發撲克牌遊戲。 對於大部分的撲克牌遊戲，您需要52張具有52不同臉部的卡片。 您決定要執行卡片自訂控制項，並在卡片自訂控制項的資源中定義52筆刷（每個都代表卡片臉部）。 在您的主要應用程式中，您一開始會建立此卡片自訂控制項的52實例。 卡片自訂控制項的每個實例都會產生 <xref:System.Windows.Media.Brush> 個物件的52實例，在您的應用程式中，總共提供 52 * 52 <xref:System.Windows.Media.Brush> 個物件。 將筆刷從卡片自訂控制項資源移到 <xref:System.Windows.Application> 或 @no__t 1 物件層級，或在自訂控制項的預設主題中加以定義，就會減少應用程式的工作集，因為您現在會在52之間共用52筆刷卡片控制項的實例。  
  
## <a name="sharing-a-brush-without-copying"></a>共用筆刷而不復制  
 如果您有多個使用相同 <xref:System.Windows.Media.Brush> 物件的元素，請將筆刷定義為資源並加以參考，而不是在 XAML 中定義筆刷內嵌。 這個方法會建立一個實例並重複使用它，而在 XAML 中定義以內嵌的筆刷會針對每個專案建立新的實例。  
  
 下列標記範例說明這一點：  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>盡可能使用靜態資源  
 靜態資源會藉由查閱已定義資源的參考，提供任何 XAML 屬性屬性的值。 該資源的查閱行為類似于編譯時間查閱。  
  
 另一方面，動態資源會在初始編譯期間建立暫存運算式，因此會延遲資源的查閱，直到實際需要要求的資源值才能建立物件為止。 該資源的查閱行為類似于執行時間查詢，這會影響效能。 請盡可能在您的應用程式中使用靜態資源，只有在必要時才使用動態資源。  
  
 下列標記範例示範如何使用這兩種類型的資源：  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [Text](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
