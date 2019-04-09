---
title: 最佳化效能：運用硬體
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: 683804acf43065543fa5d4ffb1a5ecf7e5b4c49a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163172"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>最佳化效能：運用硬體
內部架構[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有兩個呈現管線、 硬體和軟體。 本主題提供有關這些轉譯管線，以幫助您決定您的應用程式的效能最佳化的相關資訊。  
  
## <a name="hardware-rendering-pipeline"></a>硬體轉譯管線  
 其中一個最重要的因素，判斷[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]效能是可轉譯繫結，您可以呈現，較高成本的效能有更多的像素。 不過，轉譯會更可以卸載到[!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)]，您可以取得更多的效能優勢。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式的硬體轉譯管線可充分[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]支援的最少的硬體上的功能[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]7.0 版。 進一步最佳化後，可以支援硬體的[!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)]7.0 版和 PixelShader 2.0 + 功能。  
  
## <a name="software-rendering-pipeline"></a>軟體呈現管線  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]軟體呈現管線完全是 CPU 繫結。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SSE 及 SSE2 指令的利用設定 CPU 來實作最佳化的完整功能軟體模擬轉譯器。 軟體後援是的每當應用程式的功能無法使用硬體呈現管線呈現順暢。  
  
 最大的效能問題就會發生時軟體模式中的呈現與填滿率，定義為您要轉譯的像素數目。 如果您擔心在軟體轉譯模式中的效能，請嘗試重新繪製的像素的次數降到最低。 例如，如果您的應用程式，以藍色背景，然後呈現稍微透明的影像上方時，會呈現所有兩次的應用程式中的像素。 如此一來，它會花上兩次來呈現應用程式比您藍色的背景影像。  
  
### <a name="graphics-rendering-tiers"></a>圖形轉譯層  
 它可能很難預測的硬體組態，將會在執行您的應用程式。 不過，您可能要考慮的設計，可讓您順暢地切換功能在不同的硬體上執行時，讓它可以充分利用每個不同的硬體組態的應用程式。  
  
 若要達到這個目的，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供功能，以判斷系統在執行階段的圖形功能。 圖形功能取決於分類做為其中的三個轉譯功能層級的視訊卡。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會公開[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]，可讓應用程式查詢轉譯功能層。 您的應用程式可以在執行階段取決於硬體支援的轉譯層採取不同的程式碼路徑。  
  
 對轉譯層級的影響最大的圖形硬體功能如下︰  
  
-   **視訊 RAM**：圖形硬體上的視訊記憶體數量決定可用於組合圖形的緩衝區大小和數目。  
  
-   **像素著色器**：像素著色器是根據像素來計算效果的圖形處理函式。 根據所顯示圖形的解析度，每個顯示框架都可能需要處理數百萬個像素。  
  
-   **頂點著色器**：頂點著色器是在物件頂點資料上執行數學運算的圖形處理函式。  
  
-   **多紋理支援**：多紋理支援指的是可以在混色作業期間於 3D 圖形物件上套用兩個以上的不同紋理。 多紋理支援的程度取決於圖形硬體上的多紋理單位數目。  
  
 像素著色器、 頂點著色器，以及多紋理功能用來定義特定[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]版本層級，它反而用來定義中的不同的轉譯層[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
 圖形硬體的功能決定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的轉譯功能。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 系統定義三個轉譯層︰  
  
-   **轉譯層 0**：沒有圖形硬體加速。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]版本層級低於 7.0 版。  
  
-   **轉譯層 1**部分的圖形硬體加速。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]版本層級是大於或等於 7.0 版中，並**較小者**比 9.0 版。  
  
-   **轉譯層 2**：大部分圖形功能都使用圖形硬體加速。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本層級大於或等於 9.0 版。  
  
 如需詳細資訊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]轉譯層，請參閱[圖形轉譯層](graphics-rendering-tiers.md)。  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [文字](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
