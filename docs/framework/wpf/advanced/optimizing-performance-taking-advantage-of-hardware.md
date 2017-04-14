---
title: "最佳化效能：運用硬體 | Microsoft Docs"
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
  - "圖形轉譯層"
  - "圖形, 效能"
  - "圖形, 轉譯層"
  - "硬體轉譯管線"
  - "轉譯層"
  - "軟體轉譯管線"
ms.assetid: bfb89bae-7aab-4cac-a26c-a956eda8fce2
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 最佳化效能：運用硬體
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的內部架構有兩條轉譯管線，即硬體和軟體。  本主題提供這些轉譯管線的相關資訊，幫助您做出與您應用程式的效能最佳化相關的決定。  
  
## 硬體轉譯管線  
 決定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 效能最重要的因素之一就是轉譯範圍：要轉譯的像素愈多，效能就愈差。  但是，卸載給[!INCLUDE[TLA#tla_gpu](../../../../includes/tlasharptla-gpu-md.md)] 的轉譯作業愈多，就會得到愈好的效能。  在至少支援 [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] 7.0 版的硬體上，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的硬體轉譯管線能夠完全發揮 [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] 功能的優點。  在支援 [!INCLUDE[TLA#tla_dx](../../../../includes/tlasharptla-dx-md.md)] 7.0 版和 PixelShader 2.0\+ 版功能的硬體上，還能獲得更好的最佳化效能。  
  
## 軟體轉譯管線  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 軟體轉譯管線完全以 CPU 為範圍。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 運用 CPU 中的 SSE 和 SSE2 指令集實作最佳化、全功能的軟體光柵處理器。  只要應用程式的功能無法用硬體管線轉譯，就會立即經由軟體轉譯。  
  
 以軟體模式轉譯時會遭遇的最大效能問題，與填入速率 \(Fill Rate\) 有關；填入速率定義為您正在轉譯的像素數。  如果您在意軟體轉譯模式下的效能問題，請盡量將重繪像素的次數減到最少。  例如，如果您的應用程式有藍色的背景，然後又要在背景上轉譯一個稍微透明的影像，應用程式中的所有像素就要轉譯兩次。  因此，當應用程式有影像時就得花掉只有背景時的兩倍時間來轉譯。  
  
### 圖形轉譯層  
 想要預測將用以執行您應用程式的硬體組態不太可能。  但是，您可以考慮將應用程式設計為在不同硬體上執行時立即切換功能，這樣一來就可以完全發揮每種不同硬體組態的優點。  
  
 為達到這個目的，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了可在執行階段判斷系統之圖形能力的功能。  圖形能力的判斷，是經由將視訊卡歸類至三個轉譯功能層 \(Rendering Capability Tier\) 之一的方式達成。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 公開的 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 可以讓應用程式查詢轉譯功能層。  然後，應用程式可以根據硬體支援的轉譯層，在執行階段採用不同的程式碼路徑。  
  
 在圖形硬體中，對轉譯層等級影響最大的功能如下：  
  
-   **視訊 RAM**：圖形硬體上的視訊記憶體數量決定可用於複合圖形的緩衝區大小和數目。  
  
-   **像素著色引擎**：像素著色引擎 \(Pixel Shader\) 是以每像素為單位計算效果的圖形處理功能。  根據所顯示圖形的解析度而定，每個顯示框架 \(Frame\) 可能需要處理達數百萬個像素。  
  
-   **頂點著色引擎**：頂點著色引擎 \(Vertex Shader\) 是會對物件之頂點資料執行數學運算的圖形處理功能。  
  
-   **多重紋理支援**：多重紋理 \(Multitexture\) 支援是指能夠在 3D 圖形物件的混色階段，套用兩個以上不同紋理的能力。  多重紋理的程度取決於圖形硬體上的多重紋理單元數目。  
  
 像素著色引擎、頂點著色引擎和多重紋理功能用於定義特定 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本等級，而這些版本等級則會用來定義 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的不同轉譯層。  
  
 圖形硬體的功能決定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的轉譯功能。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 系統定義三個轉譯層：  
  
-   **轉譯層 0**：沒有圖形硬體加速。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本等級小於 7.0 版。  
  
-   **轉譯層 1**：局部圖形硬體加速。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本等級大於或等於 7.0 版，並「小於」9.0 版。  
  
-   **轉譯層 2**：大部分圖形功能會使用圖形硬體加速。  [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本等級大於或等於 9.0 版。  
  
 如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 轉譯層的詳細資訊，請參閱[圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)。  
  
## 請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [資料繫結](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)