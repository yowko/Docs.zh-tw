---
title: "圖形轉譯登錄設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1a86d715edb68564d6ebfcc8a419e333da4ea03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="graphics-rendering-registry-settings"></a>圖形轉譯登錄設定
本主題會概略說明會影響 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形轉譯登錄設定。  
  

  
<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a>使用圖形轉譯登錄設定的時機  
 這些登錄設定是為了進行疑難排解、偵錯，以及產品支援目的而提供。 因為變更登錄會影響所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式，所以您的應用程式永遠不應自動或在安裝期間更改這些登錄機碼。  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a>什麼是 XPDM 和 WDDM？  
 一些圖形轉譯登錄設定有不同的預設值，取決於您的視訊卡使用 XPDM 或 WDDM 驅動程式。 XPDM 是 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 顯示驅動程式模型，而 WDDM 是 Windows 顯示驅動程式模型。 WDDM 是在執行 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 和 [!INCLUDE[win7](../../../../includes/win7-md.md)] 的電腦上使用。 XPDM 是在執行 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]、[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 和 [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)] 的電腦上使用。 如需 WDDM 的詳細資訊，請參閱 [Windows Vista 顯示驅動程式模型設計指南](http://go.microsoft.com/fwlink/?LinkId=178394)。  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>登錄設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供四個登錄設定來控制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 轉譯：  
  
|設定|描述|  
|-------------|-----------------|  
|**停用硬體加速選項**|指定是否應該啟用硬體加速。|  
|**最大多重取樣值**|指定消除鋸齒 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 內容的多重取樣程度。|  
|**需要的視訊驅動程式日期設定**|指定系統是否停用 2004 年 11 月之前所發行驅動程式的硬體加速。|  
|**使用軟體模擬轉譯器選項**|指定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是否應該使用軟體模擬轉譯器。|  
  
 這些設定可由知道如何參考 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 登錄設定的外部組態公用程式所存取。 您也可以使用 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 登錄編輯程式直接存取這些值來建立或修改這些設定。  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a>停用硬體加速選項  
  
|登錄機碼|值類型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 「停用硬體加速選項」可讓您關閉硬體加速功能以進行偵錯和測試。 當您在應用程式中看到轉譯成品時，請嘗試關閉硬體加速功能。 如果成品消失，問題可能在您的視訊驅動程式。  
  
 「停用硬體加速選項」是指 0 或 1 的 DWORD 值。 值為 1 會停用硬體加速功能。 值為 0 會啟用硬體加速功能，前提是系統符合硬體加速需求。如需詳細資訊，請參閱[圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)。  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a>最大多重取樣值  
  
|登錄機碼|值類型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 「最大多重取樣值」可讓您調整 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 內容消除鋸齒功能的最大數量。 使用這個層級來在 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 中停用 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 消除鋸齒功能，或在 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 中加以啟用。  
  
 「最大多重取樣值」是範圍介於 0 到 16 之間的 DWORD 值。 值為 0 指定應該停用 3D 內容的多重取樣消除鋸齒功能，而值為 16 會嘗試使用最多 16x 多重取樣消除鋸齒功能 (如果視訊卡支援的話)。 請注意，在使用 XPDM 驅動程式的電腦上設定此登錄機碼值，將導致應用程式大量使用額外的視訊記憶體，使 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 轉譯的效能降低，並且可能會引發轉譯錯誤和穩定性問題。  
  
 未設定此登錄機碼時，XPDM 驅動程式的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 預設值為 0，而 WDDM 驅動程式的預設值為 4。  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a>需要的視訊驅動程式日期設定  
  
|登錄機碼|值類型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|字串|  
  
 在 2004 年 11 月，[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 發行新版的驅動程式測試指導方針，在此日期後撰寫的驅動程式提供的穩定性更佳。 對於這些驅動程式，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 預設會使用硬體加速管線，並回到此日期之前發行的 XPDM 驅動程式軟體轉譯方式。  
  
 「需要的視訊驅動程式日期設定」可讓您指定 XPDM 驅動程式的替代最小日期。 如果您確定您的視訊驅動程式穩定度足以支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，您應該只指定 2004 年 11 月之前的日期。  
  
 需要的視訊驅動程式設定會採用下列格式的字串︰  
  
||  
|-|  
|*YYYY* `/` *MM* `/` *DD*|  
  
 其中 *YYYY* 是四位數年份，*MM* 是兩位數的月份，以及 *DD* 是兩位數的日期。 未設定此值時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會使用 2004 年 11 月，做為其需要的視訊驅動程式日期。  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a>使用軟體模擬轉譯器選項  
  
|登錄機碼|值類型|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 「使用軟體模擬轉譯器選項」可讓您強制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 進入模擬硬體轉譯模式以進行偵錯：[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會進入硬體模式，但使用 [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)] 軟體模擬轉譯器 d3dref9.dll，而不是實際的硬體裝置。  
  
 軟體模擬轉譯器速度非常慢，但會略過您的視訊驅動程式，以避免發生任何由驅動程式問題造成的轉譯問題。 因此，您可以使用軟體模擬轉譯器來判斷轉譯問題是否由視訊驅動程式造成。 D3dref9.dll 檔案必須位於應用程式可存取的位置，例如在系統路徑中的任何位置，或在應用程式的本機目錄中。  
  
 「使用軟體模擬轉譯器選項」採用 DWORD 值。 值為 0 表示未使用軟體模擬轉譯器。 任何其他非零的值都會強制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用軟體模擬轉譯器。  
  
## <a name="see-also"></a>另請參閱  
 [圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
