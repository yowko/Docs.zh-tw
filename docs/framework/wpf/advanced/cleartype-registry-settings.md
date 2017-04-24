---
title: "ClearType 登錄設定 | Microsoft Docs"
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
  - "ClearType, 登錄設定"
  - "印刷樣式, ClearType 登錄設定"
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ClearType 登錄設定
本主題提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所使用之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] 登錄設定的概觀。  
  
   
  
<a name="overview"></a>   
## 技術概觀  
 將文字呈現至顯示裝置的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式使用 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 功能來加強可讀性。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 開發的軟體技術，能夠改善現有 LCD \(液晶顯示，例如膝上型電腦螢幕、Pocket PC 螢幕和平面監視器\) 文字的可讀性。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的運作方式是在 LCD 螢幕的每個像素中存取個別的垂直色碼元素。  如需 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的詳細資訊，請參閱 [ClearType 概觀](../../../../docs/framework/wpf/advanced/cleartype-overview.md)。  
  
 在各種不同的顯示裝置上，以 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 呈現的文字外觀上可能有相當明顯的差異。  例如，少數監視器是以藍、綠、紅的順序實作色碼元素，而不是較常見的紅、綠、藍 \([!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]\) 順序。  
  
 對色彩感受度不同的個人檢視以 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 呈現的文字時，文字外觀的差異可能也很大。  某些個人比其他人更能察覺色彩中的些微差異。  
  
 在這些情況中，[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 功能必須經過修改，才能為每個人提供最佳的閱讀經驗。  
  
<a name="registry_settings"></a>   
## 登錄設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 指定四種控制 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 功能的登錄設定：  
  
|設定|描述|  
|--------|--------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 層級|描述 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 色彩清晰度。|  
|Gamma 層級|描述顯示裝置之像素色彩元件的層級。|  
|像素結構|描述顯示裝置的像素排列方式。|  
|文字對比層級|描述顯示文字的對比層級。|  
  
 這些設定可由知道如何參考所述 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 登錄設定的外部組態公用程式存取。  您也可以使 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 登錄編輯程式，直接建立或修改這些設定的值。  
  
 若未設定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 登錄設定 \(處於預設狀態\)，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式會查詢 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 系統參數資訊，找出字型平滑化設定。  
  
> [!NOTE]
>  如需列舉顯示裝置名稱的詳細資訊，請參閱 `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 函式。  
  
<a name="ClearType_level"></a>   
## ClearType 層級  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 層級可讓您根據個人的色彩感受度和感覺調整文字的呈現。對於某些個人來說，使用 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 最高層級呈現的文字並不會產生最佳的閱讀經驗。  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 層級是範圍從 0 到 100 的整數值。  預設值為 100，表示 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 會使用顯示裝置之色碼元素的最高性能。  不過，[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 層級 0 則會將文字呈現成灰階。  將 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 層級設定為 0 到 100 之間的值，您就可以建立符合個人色彩感受度的中間層級。  
  
### 登錄設定  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 層級的登錄設定位置是對應於特定顯示裝置名稱的個別使用者設定：  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 使用者的每個顯示裝置名稱都會定義一個 `ClearTypeLevel` DWORD 值。  下列螢幕擷取畫面顯示 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 層級的登錄編輯程式設定。  
  
 ![登錄編輯程式中的 ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式使用包含或不含 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的模式呈現文字。  以不含 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的模式呈現文字稱為灰階呈現。  
  
<a name="gamma_level"></a>   
## Gamma 層級  
 Gamma 層級是指像素值和亮度間的非線性關聯。  Gamma 層級設定應該對應於顯示裝置的實體特性，否則可能會發生呈現輸出失真的情況。  例如，測試可能看似過寬或過窄，或是色邊可能會出現在圖像 \(Glyph\) 垂直主體的邊緣。  
  
 Gamma 層級是範圍從 1000 到 2200 的整數值。  預設層級為 1900。  
  
### 登錄設定  
 Gamma 層級的登錄設定位置是對應於特定顯示裝置名稱的本機電腦 \(Local Machine\) 設定。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 使用者的每個顯示裝置名稱都會定義一個 `GammaLevel` DWORD 值。  下列螢幕擷取畫面顯示 Gamma 層級的登錄編輯程式設定。  
  
 ![登錄編輯程式中的 ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## 像素結構  
 像素結構描述構成顯示裝置之像素的類型。  像素結構會定義成下列三種類型其中一種：  
  
|型別|值|描述|  
|--------|-------|--------|  
|平面|0|顯示裝置沒有像素結構。  這表示每一種色彩的光源都是平均散佈在像素區域；這種模式稱為灰階呈現。  標準顯示裝置便是採用這種運作模式。  呈現的文字上絕對不會套用 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]。|  
|RGB|1|顯示裝置具有由下列順序的三種色碼組成的像素：紅、綠、藍。  呈現的文字上會套用 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]。|  
|BGR|2|顯示裝置具有由下列順序的三種色碼組成的像素：藍、綠、紅。  呈現的文字上會套用 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]。  請注意此順序與 RGB 類型相反。|  
  
 像素結構對應於範圍從 0 到 2 的整數值。  預設值為 0，代表平面像素結構。  
  
> [!NOTE]
>  如需列舉顯示裝置名稱的詳細資訊，請參閱 `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 函式。  
  
### 登錄設定  
 像素層級的登錄設定位置是對應於特定顯示裝置名稱的本機電腦設定。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 使用者的每個顯示裝置名稱都會定義一個 `PixelStructure` DWORD 值。  下列螢幕擷取畫面顯示像素結構的登錄編輯程式設定。  
  
 ![登錄編輯程式中的 ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## 文字對比層級  
 文字對比層級可讓您根據圖像的主體寬度調整文字的呈現。  文字對比層級是範圍從 0 到 6 的整數值；此整數值愈大，主體寬度也愈寬。  預設層級為 1。  
  
### 登錄設定  
 文字對比層級的登錄設定位置是對應於特定顯示裝置名稱的個別使用者設定。  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 使用者的每個顯示裝置名稱都會定義一個 `TextContrastLevel` DWORD 值。  下列螢幕擷取畫面顯示文字對比層級的登錄編輯程式設定。  
  
 ![登錄編輯程式中的 ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## 請參閱  
 [ClearType 概觀](../../../../docs/framework/wpf/advanced/cleartype-overview.md)   
 [ClearType 消除鋸齒](_win32_ClearType_Antialiasing)