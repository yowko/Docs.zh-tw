---
title: "將玻璃框架擴充至 WPF 應用程式中 | Microsoft Docs"
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
  - "應用程式, 將玻璃框架擴充至"
  - "將玻璃框架擴充至應用程式"
  - "玻璃框架, 擴充至應用程式"
  - "圖形, 將玻璃框架擴充至應用程式"
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 將玻璃框架擴充至 WPF 應用程式中
本主題示範如何將 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] 玻璃框架擴充至 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 應用程式的用戶端區域。  
  
> [!NOTE]
>  這個範例只適用於執行桌面視窗管理員 \(DWM\) 且已啟用玻璃效果的 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 機器上運作。  [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Home Basic Edition 不支援透明玻璃效果。  通常會以透明玻璃效果呈現的區域在其他 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 版上會呈現不透明。  
  
## 範例  
 下圖說明擴充至 Internet Explorer 7 位址列的玻璃框架。  
  
 **Internet Explorer 在位址列後具有擴充的玻璃框架。**  
  
 ![在位址列後方已擴充玻璃框架的 IE7。](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")  
  
 若要擴充 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式上的玻璃框架，需要存取 Unmanaged [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]。  下列程式碼範例會對將框架擴充至用戶端區域時需要的兩個 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 進行平台叫用。  每個 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 都會在名為 **NonClientRegionAPI** 的類別中宣告。  
  
<!-- TODO: review snippet reference  [!CODE [AvalonClientGlass#DWMExtendFramePInvokeAPI](AvalonClientGlass#DWMExtendFramePInvokeAPI)]  -->  
  
 [DwmExtendFrameIntoClientArea](_udwm_dwmextendframeintoclientarea) [](_udwm_dwmextendframeintoclientarea) 是 DWM 功能，會將框架擴充至用戶端區域。  它會採用兩個參數，一個是視窗控制代碼，一個是 [MARGINS](inet_MARGINS) 結構。  [MARGINS](inet_MARGINS) 是用以告知 DWM 要將框架的多少部分額外擴充至用戶端區域。  
  
## 範例  
 若要使用 [DwmExtendFrameIntoClientArea](_udwm_dwmextendframeintoclientarea) 函式，必須取得視窗控制代碼。  在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，可以從 <xref:System.Windows.Interop.HwndSource> 的 <xref:System.Windows.Interop.HwndSource.Handle%2A> 屬性取得視窗控制代碼。  在下列範例中，框架會在視窗發生 <xref:System.Windows.FrameworkElement.Loaded> 事件時擴充至用戶端區域。  
  
<!-- TODO: review snippet reference  [!CODE [AvalonClientGlass#AvalonGlassOnLoadedCSharp](AvalonClientGlass#AvalonGlassOnLoadedCSharp)]  -->  
  
## 範例  
 下列範例顯示簡單的視窗，其中的框架會擴充至用戶端區域。  框架會擴充至包含兩個 <xref:System.Windows.Controls.TextBox> 物件的上框線之後。  
  
<!-- TODO: review snippet reference  [!CODE [AvalonClientGlass#AvalonGlassFullWindowXAML](AvalonClientGlass#AvalonGlassFullWindowXAML)]  -->  
  
 下圖說明擴充至 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的玻璃框架。  
  
 **玻璃框架擴充至**  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **應用程式。**  
  
 ![擴充至 WPF 應用程式中的玻璃框架。](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.png "WPFextendedGlassIntoClient")  
  
## 請參閱  
 [桌面視窗管理員概觀](_udwm_overview)   
 [桌面視窗管理員模糊概觀](_udwm_blur_ovw)   
 [DwmExtendFrameIntoClientArea](_udwm_dwmextendframeintoclientarea)