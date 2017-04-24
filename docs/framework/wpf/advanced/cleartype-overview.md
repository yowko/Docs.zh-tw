---
title: "ClearType 概觀 | Microsoft Docs"
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
  - "ClearType, 技術"
  - "印刷樣式, ClearType 技術"
ms.assetid: 7e2392e0-75dc-463d-a716-908772782431
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ClearType 概觀
本主題概要說明 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] 技術。  
  
   
  
<a name="overview"></a>   
## 技術概觀  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 開發的軟體技術，能夠改善現有 LCD \(液晶顯示，例如膝上型電腦螢幕、Pocket PC 螢幕和平面監視器\) 文字的可讀性。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的運作方式是在 LCD 螢幕的每個像素中存取個別的垂直色碼元素。  在 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 之前，電腦可以顯示的最小細節是單一像素，但是透過 LCD 監視器上執行 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]，我們現在可以顯示寬度最小為十分之一個像素的文字特色。  極高解析度會增加文字顯示中微小細節的清晰度，讓長時間閱讀方便得多。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中提供的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 是最新一代的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]，其中包含幾項針對 [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] 提供之版本的改進功能。  
  
<a name="sub-pixel_positioning"></a>   
## 子像素定位  
 對舊版 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 所做最重大的改進之處是子像素定義的使用。  不同於 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 中的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 實作，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 可以讓圖像 \(Glyph\) 從像素內部開始，而不只是像素的週框。  由於在定位像素上的這種額外解析度，使得圖像的間距和比例更為精準也更為一致。  
  
 下列兩個範例顯示使用子像素定位時，圖像從任何子像素週框起始的外觀。  左邊的範例是使用舊版 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 產生器呈現的結果，並未採用子像素定位功能。  右邊的範例是使用新版的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 產生器，利用子像素定義所呈現的外觀。  請注意右側影像中每個 **e** 和 **l** 都稍有不同，因為每個字母的起點都在不同的子像素中。  在螢幕上檢視正常大小的文字時，由於圖像影像的高對比，使得這項差異並不顯著。  只有在 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 中已加入複雜的色彩篩選功能，才會產生這種結果。  
  
 ![以兩種 ClearType 版本顯示的文字](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-01.png "wcpsdk\_mmgraphics\_text\_cleartype\_overview\_01")  
舊版和新版 ClearType 顯示的文字  
  
 下列兩個範例比較舊版 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 產生器與新版 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 產生器的輸出。  如右邊範例所示，子像素定位大幅改善了螢幕上的文字間距，尤其是尺寸較小，而使得子像素和完整像素之間差距代表了圖像寬度的明顯比例時。  請注意第二個影像中的字母間距較為平均。  子像素定位在文字螢幕整體外觀上的優勢已大幅提升，同時也代表 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 技術的一項重大革命。  
  
 ![以舊版 ClearType 顯示的文字](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-02.png "wcpsdk\_mmgraphics\_text\_cleartype\_overview\_02")  
舊版和新版 ClearType 的文字  
  
<a name="y-direction_antialiasing"></a>   
## Y 方向消除鋸齒  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的另一項改善是 Y 方向消除鋸齒。  [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] 中的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 沒有 Y 方向消除鋸齒，因此只能在 X 軸提供較佳的解析度，但 Y 軸的解析度則較差。  在淺曲線的上下端，鋸齒邊緣降低了文字的可讀性。  
  
 下列範例顯示沒有 Y 方向消除鋸齒的效果。  在這個案例中，字母上下兩端的鋸齒邊緣非常明顯。  
  
 ![微曲部分產生鋸齒狀邊緣的文字](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-03.png "wcpsdk\_mmgraphics\_text\_cleartype\_overview\_03")  
淺曲線上有鋸齒邊緣的文字  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 提供 Y 方向層級的消除鋸齒功能，讓所有的鋸齒邊緣變得平滑。  這項功能對於改善東亞語系的可讀性尤其重要，因為在東亞語系中，表意文字之水平和垂直淺曲線的數量幾乎相等。  
  
 下列範例顯示 Y 方向消除鋸齒的效果。  在這個案例中，字母上下兩端顯示平滑的曲線。  
  
 ![套用 ClearType Y 方向消除鋸齒功能的文字](../../../../docs/framework/wpf/advanced/media/wcpsdk-mmgraphics-text-cleartype-overview-04.png "wcpsdk\_mmgraphics\_text\_cleartype\_overview\_04")  
使用 ClearType Y 方向消除鋸齒的文字  
  
<a name="hardware_acceleration"></a>   
## 硬體加速  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 可以利用硬體加速來提高效能，並降低 CPU 負載和系統記憶體需求。  透過圖形卡的像素著色器 \(Pixel Shader\) 和視訊記憶體，[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 提供了快速呈現文字的功能，尤其是在使用動畫時。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 不會修改全系統的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 設定。  停用 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 中的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 會將 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的消除鋸齒設定為灰階模式。此外，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 也不會修改 [ClearType Tuner PowerToy](http://www.microsoft.com/typography/ClearTypePowerToy.mspx) 的設定。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的其中一項架構設計決策是讓無關解析度的配置加強支援日漸普及的高解析度 DPI 監視器。  這項決策的結果是 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 無法在某些東亞字型中支援鋸齒文字呈現或點陣圖，因為這兩者都與解析度相關。  
  
<a name="further_information"></a>   
## 詳細資訊  
 [ClearType 資訊](http://www.microsoft.com/typography/ClearTypeInfo.mspx) \(英文\)  
  
 [ClearType Tuner PowerToy](http://www.microsoft.com/typography/ClearTypePowerToy.mspx) \(英文\)  
  
## 請參閱  
 [ClearType 登錄設定](../../../../docs/framework/wpf/advanced/cleartype-registry-settings.md)