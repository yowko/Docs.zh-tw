---
title: "圖形轉譯登錄設定 | Microsoft Docs"
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
  - "圖形 [WPF], 呈現"
  - "轉譯圖形"
  - "轉譯圖形, 登錄設定"
  - "轉譯圖形, 疑難排解"
  - "圖形轉譯疑難排解"
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 圖形轉譯登錄設定
本主題提供會對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式造成影響之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形轉譯登錄設定的概觀。  
  
   
  
<a name="overview"></a>   
## 使用圖形轉譯登錄設定的時機  
 這些登錄設定是針對疑難排解、偵錯及產品支援的目的提供。  因為變更登錄會影響所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式，您的應用程式應永不自動變更或在安裝時變更這些登錄設定。  
  
<a name="xpdmandwddm"></a>   
## 什麼是 XPDM 和 WDDM  
 某些圖形轉譯登錄設定有不同的預設值，取決於您的視訊卡使用的是 XPDM 還是 WDDM 驅動程式。  XPDM 是 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 顯示驅動程式模型，而 WDDM 是 Windows 顯示驅動程式模型。  WDDM 可在執行 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 和 [!INCLUDE[win7](../../../../includes/win7-md.md)] 的電腦上使用。  XPDM 可在執行 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]、[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 和 [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)] 的電腦上使用。  如需 WDDM 的詳細資訊，請參閱 [Windows Vista 顯示驅動程式模型設計指南](http://go.microsoft.com/fwlink/?LinkId=178394) \(英文\)。  
  
<a name="registry_settings"></a>   
## 登錄設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供四種控制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 轉譯的登錄設定：  
  
|設定|描述|  
|--------|--------|  
|**停用硬體加速選項**|指定是否應該啟用硬體加速。|  
|**最大多重取樣值**|指定消除[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]內容鋸齒的多重取樣程度。|  
|**必要的視訊驅動程式日期設定**|指定系統是否停用在 2004 年 11 月之前發行之驅動程式的硬體加速。|  
|**使用參考光柵處理器選項**|指定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是否應該使用參考光柵處理器。|  
  
 所有知道如何參考 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 登錄設定的外部組態公用程式，都可以存取這些設定。  使用 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 登錄編輯程式器直接存取值，也可以建立或修改這些設定。  
  
<a name="disablehardwareacceleration"></a>   
## 停用硬體加速選項  
  
|登錄機碼|實值型別|  
|----------|----------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 「停用硬體加速選項」可以讓您基於偵錯和測試目的關閉硬體加速。  在應用程式中看見轉譯疊影時，請嘗試關閉硬體加速。  如果疊影消失，問題可能出在您的視訊驅動程式。  
  
 **停用硬體加速選項**是 DWORD 值，不是 0 就是 1。  值為 1 時會停用硬體加速。  值為 0 時會啟用硬體加速，前提是系統必須符合硬體加速需求。如需詳細資訊，請參閱[圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)。  
  
<a name="maxmultisample"></a>   
## 最大多重取樣值  
  
|登錄機碼|實值型別|  
|----------|----------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 「最大多重取樣值」可以讓您調整[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]內容的最大消除鋸齒量。  使用這個層級會在 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 中停用[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]消除鋸齒，或在 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 中加以啟用。  
  
 **最大多重取樣值**是 DWORD 值，範圍從 0 到 16。  值為 0 時會指定應該停用 3\-D 內容的多重取樣消除鋸齒，值為 16 時，則會在視訊卡支援的情況下，嘗試使用多達 16x 的多重取樣消除鋸齒。  請注意，在使用 XPDM 驅動程式的電腦上設定這個登錄機碼值，會使應用程式額外使用大量的視訊記憶體，降低[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]轉譯的效能，而且可能會引發轉譯錯誤和穩定性問題。  
  
 未設定這個登錄機碼時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會預設為 0 \(如為 XPDM 驅動程式\) 或 4 \(如為 WDDM 驅動程式\)。  
  
<a name="requiredvideodriverdatesetting"></a>   
## 必要的視訊驅動程式日期設定  
  
|登錄機碼|實值型別|  
|----------|----------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|字串|  
  
 在 2004 年 11 月時，[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 發行了新版的驅動程式測試方針，在這個日期之後撰寫的驅動程式具備較佳的穩定性。  根據預設，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會針對這些驅動程式使用硬體加速管線，並針對在這個日期之前發行的 XPDM 驅動程式使用軟體轉譯。  
  
 「必要的視訊驅動程式日期設定」可以讓您指定 XPDM 驅動程式的替代最小日期。  除非您很確定您的驅動程式夠穩定可支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，否則不要指定 2004 年 11 月之前的日期。  
  
 必要的視訊驅動程式設定會採用下列格式的字串：  
  
||  
|-|  
|*YYYY* `/` *MM* `/` *DD*|  
  
 其中 *YYYY* 是四位數的年份、*MM* 是兩位數的月份，而*DD* 是兩位數的日期。  未設定這個值時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會使用 2004 年 11 月做為必要的視訊驅動程式日期。  
  
<a name="usereferencerasterizeroption"></a>   
## 使用參考光柵處理器選項  
  
|登錄機碼|實值型別|  
|----------|----------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 「使用參考光柵處理器選項」可以讓您強制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 進入模擬硬體轉譯模式以進行偵錯：[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會進入硬體模式，但是使用 [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] 參考軟體光柵處理器 d3dref9.dll，而非實際的硬體裝置。  
  
 參考光柵處理器非常緩慢，但是會略過視訊驅動程式以避免驅動程式問題造成的任何轉譯問題。  因此，您可以使用參考光柵處理器判斷轉譯問題是否是由視訊驅動程式所造成。  d3dref9.dll 檔案必須位於應用程式可以存取的位置，例如系統路徑中的任何位置或是應用程式的本機目錄。  
  
 「使用參考光柵處理器選項」採用 DWORD 值。  值為 0 時表示不使用參考光柵處理器。  其他非零的值都會強制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用參考光柵處理器。  
  
## 請參閱  
 [圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)