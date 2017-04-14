---
title: "逐步解說：建立自訂動畫按鈕 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動畫, 按鈕"
  - "按鈕"
  - "自訂動畫按鈕"
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 逐步解說：建立自訂動畫按鈕
就如它的名稱所述，[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 十分適合針對客戶製作豐富的呈現體驗。  這些逐步解說將顯示如何自訂按鈕的外觀和行為 \(包含動畫\)。  這項自訂是使用樣式和範本所完成，因此可以輕鬆地將這個自訂按鈕套用至應用程式中的任何按鈕。  下圖顯示您所要建立的自訂按鈕。  
  
 ![您將建立的自訂按鈕](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.png "custom\_button\_blend\_Intro")  
  
 組成按鈕外觀的向量圖形是使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 所建立。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 與 HTML 類似，不同之處在於它的功能較強大也比較具擴充性。  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 可以使用 Microsoft Visual Studio 或 \[記事本\] 手動輸入，也可以使用視覺化設計工具 \(如 Microsoft Expression Blend\)。  Expression Blend 的運作方式是建立基礎 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 程式碼，因此這兩種方法都會建立相同的圖形。  
  
## 在本節中  
 [使用 Microsoft Expression Blend 建立按鈕](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 示範如何使用 Expression Blend 的設計工具功能建立具有自訂行為的按鈕。  
  
 [使用 XAML 建立按鈕](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 示範如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 建立具有自訂行為的按鈕。  
  
## 相關章節  
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 描述如何使用樣式和範本來決定控制項的外觀和行為。  
  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 描述如何使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 動畫和計時系統建立物件的動畫。  
  
 [使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 描述如何使用筆刷物件來繪製純色、線形漸層和放射狀漸層。  
  
 [點陣圖效果概觀](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)  
 描述 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 支援的點陣圖效果，以及說明其套用方式。