---
title: 優化效能:運用硬體
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- hardware rendering pipeline [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
- software rendering pipeline [WPF]
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
ms.openlocfilehash: 7acf5a3f48ac4987037873c63111d988ec3a4979
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629658"
---
# <a name="optimizing-performance-taking-advantage-of-hardware"></a>優化效能:運用硬體
的內部架構[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]有兩個轉譯管線: 硬體和軟體。 本主題提供這些轉譯管線的相關資訊, 可協助您決定應用程式的效能優化。  
  
## <a name="hardware-rendering-pipeline"></a>硬體呈現管線  
 判斷[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]效能最重要的因素之一就是它會呈現系結, 您必須轉譯的圖元越多, 效能成本就愈高。 不過, 可以卸載到的[!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)]更多轉譯, 您可以獲得更多的效能優勢。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式硬體轉譯管線在支援最低 microsoft directx 7.0 版的硬體上, 可享有 microsoft directx 功能的完整優勢。 支援 Microsoft DirectX 7.0 版和無效 2.0 + 功能的硬體可以取得進一步的優化。  
  
## <a name="software-rendering-pipeline"></a>軟體呈現管線  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]軟體轉譯管線完全受限於 CPU。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]利用 CPU 中的 SSE 和 SSE2 指令集來執行優化、功能完整的軟體轉譯器。 只要應用程式功能無法使用硬體轉譯管線轉譯, 就可以順暢地回溯到軟體。  
  
 以軟體模式轉譯時, 您會遇到的最大效能問題, 與填滿速率相關, 其定義為您要轉譯的圖元數目。 如果您擔心軟件轉譯模式中的效能, 請嘗試將圖元重繪的次數減至最少。 例如, 如果您的應用程式具有藍色背景, 然後在其上呈現稍微透明的影像, 您會將應用程式中的所有圖元呈現兩次。 因此, 使用影像轉譯應用程式所需的時間會比只有藍色背景來得多兩倍。  
  
### <a name="graphics-rendering-tiers"></a>圖形轉譯層  
 預測您的應用程式將在其上執行的硬體設定可能非常棘手。 不過, 您可能會想要考慮允許應用程式在不同硬體上執行時順暢地切換功能的設計, 讓它可以充分利用每個不同的硬體設定。  
  
 為了達到這個目的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , 提供了在執行時間決定系統圖形功能的功能。 圖形功能的決定方式是將視訊卡分類為三種轉譯功能層的其中一個。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]公開可讓應用程式查詢轉譯功能層的 API。 然後, 您的應用程式可以在執行時間根據硬體所支援的轉譯層來採取不同的程式碼路徑。  
  
 對轉譯層級的影響最大的圖形硬體功能如下︰  
  
- **視訊 RAM**：圖形硬體上的視訊記憶體數量決定可用於組合圖形的緩衝區大小和數目。  
  
- **像素著色器**：像素著色器是根據像素來計算效果的圖形處理函式。 根據所顯示圖形的解析度，每個顯示框架都可能需要處理數百萬個像素。  
  
- **頂點著色器**：頂點著色器是在物件頂點資料上執行數學運算的圖形處理函式。  
  
- **多紋理支援**：多紋理支援指的是可以在混色作業期間於 3D 圖形物件上套用兩個以上的不同紋理。 多紋理支援的程度取決於圖形硬體上的多紋理單位數目。  
  
 [圖元著色器]、[頂點著色器] 和 [多紋理] 功能是用來定義特定的 DirectX 版本層級, 而後者則是用來[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在中定義不同的呈現層。  
  
 圖形硬體的功能決定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的轉譯功能。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 系統定義三個轉譯層︰  
  
- **轉譯層 0**：沒有圖形硬體加速。 DirectX 版本層級小於7.0 版。  
  
- 轉譯**層 1**部分圖形硬體加速。 DirectX 版本層級大於或等於7.0 版, 且小於9.0 版  。  
  
- **轉譯層 2**：大部分圖形功能都使用圖形硬體加速。 DirectX 版本層級大於或等於9.0 版。  
  
 如需[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]呈現層的詳細資訊, 請參閱[圖形轉譯層](graphics-rendering-tiers.md)。  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
