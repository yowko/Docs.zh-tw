---
title: ClearType 登錄設定
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: cacdc47a35bfd197bcac29edc6f7c780d3b8578f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cleartype-registry-settings"></a>ClearType 登錄設定
本主題提供概觀[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]所使用的登錄設定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>技術概觀  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 顯示裝置使用的文字呈現的應用程式[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]功能提供增強的閱讀經驗。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 軟體技術是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 所開發，此技術改善了現有 LCD (液晶顯示器) 上的文字可讀性，例如膝上型電腦螢幕、Pocket PC 螢幕和平面監視器。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的運作方式是存取 LCD 螢幕中每個像素的個別垂直色帶項目。 如需有關[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]，請參閱[ClearType 概觀](../../../../docs/framework/wpf/advanced/cleartype-overview.md)。  
  
 與呈現的文字[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]可以出現在不同顯示裝置上檢視時，明顯不同。 例如，少量監視器實作在藍色、 綠色、 紅色順序中的色彩等量磁碟區的項目，而不是較常見的紅色、 綠色、 藍色 ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) 順序。  
  
 與呈現的文字[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]也會出現檢視的個人且具有不同的色彩敏感度層級時，會大幅不同。 有些人比其他人更能感知色彩的細微差異。  
  
 在這些情況下，每個[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]功能需要修改，以提供最佳的每個個別的閱讀經驗。  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>登錄設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 指定四個登錄設定來控制[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]功能：  
  
|設定|描述|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 層級|描述的層級[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]色彩清晰度。|  
|色差補正層級|說明顯示裝置的像素色彩元件層級。|  
|像素結構|說明顯示裝置的像素排列。|  
|文字對比層級|說明顯示文字的對比層級。|  
  
 這些設定可以透過外部組態公用程式知道如何參考識別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]登錄設定。 您也可以使用 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 登錄編輯程式直接存取這些值來建立或修改這些設定。  
  
 如果[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]登錄設定未設定 （此為預設狀態），[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式查詢[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]系統字型平滑化設定的參數資訊。  
  
> [!NOTE]
>  如需列舉顯示裝置名稱資訊，請參閱`SystemParametersInfo`[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式。  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>ClearType 層級  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級可讓您調整呈現的文字的色彩敏感度和個別的感覺。 對於某些個人，呈現的文字，會使用[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]在其最高的層級不會產生最佳的閱讀經驗。  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級是範圍從 0 到 100 的整數值。 預設層級是 100，這表示[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]使用色彩等量磁碟區項目的顯示裝置的最大功能。 不過，[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級為 0 會呈現為灰色的小數位數的文字。 藉由設定[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]介於 0 到 100 之間的層級，您可以建立適合個別色彩敏感度的中間層級。  
  
### <a name="registry-setting"></a>登錄設定  
 登錄設定位置[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級是對應至特定顯示裝置名稱的個別使用者設定：  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 每個顯示裝置名稱的使用者， `ClearTypeLevel` DWORD 值定義。 下圖顯示 登錄編輯程式設定[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級。  
  
 ![登錄編輯程式中的 ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式以呈現文字與不是兩種模式的其中一個[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]。 當不會呈現文字[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]，它指灰階呈現。  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Gamma 層級  
 Gamma 層級是指像素值和明亮度之間的非線性關聯性。 Gamma 層級設定應該對應至顯示裝置的實體特性，否則轉譯的輸出可能會失真。 例如，測試結果可能會太寬或太窄，或字符的垂直主體邊緣會出現色彩鬚邊。  
  
 Gamma 層級是範圍從 1000 到 2200 的整數值。 預設層級為 1900。  
  
### <a name="registry-setting"></a>登錄設定  
 Gamma 層級的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 每個顯示裝置名稱的使用者， `GammaLevel` DWORD 值定義。 以下的螢幕擷取畫面顯示 Gamma 層級的登錄編輯程式設定。  
  
 ![登錄編輯程式中的 ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>像素結構  
 像素結構說明構成顯示裝置的像素類型。 像素結構定義有三種類型︰  
  
|類型|值|描述|  
|----------|-----------|-----------------|  
|一般|0|顯示裝置沒有像素結構。 這表示每種色彩光源都平均分布在像素區域，此即為灰階轉譯。 這是標準顯示裝置運作的方式。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 永遠不會套用至轉譯的文字。|  
|RGB|1|顯示裝置的像素色帶組成順序如下︰紅色、綠色和藍色。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 套用至轉譯的文字。|  
|BGR|2|顯示裝置的像素色帶組成順序如下︰藍色、綠色和紅色。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 套用至轉譯的文字。 請注意順序由 RGB 類型反轉的方式。|  
  
 像素結構對應至範圍從 0 到 2 的整數值。 預設層級為 0 表示一般的像素結構。  
  
> [!NOTE]
>  如需列舉顯示裝置名稱資訊，請參閱`EnumDisplayDevices`[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式。  
  
### <a name="registry-setting"></a>登錄設定  
 像素結構的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 每個顯示裝置名稱的使用者， `PixelStructure` DWORD 值定義。 以下的螢幕擷取畫面顯示像素結構的登錄編輯程式設定。  
  
 ![登錄編輯程式中的 ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>文字對比層級  
 文字對比層級可讓您根據字符的主體寬度調整文字的轉譯。 文字對比層級是一個範圍從 0 到 6 的整數值，整數值愈大，主體愈寬。 預設層級為 1。  
  
### <a name="registry-setting"></a>登錄設定  
 文字對比層級的登錄設定位置是對應到特定顯示裝置名稱的個別使用者設定：  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 每個顯示裝置名稱的使用者， `TextContrastLevel` DWORD 值定義。 下列螢幕擷取畫面顯示文字對比層級的登錄編輯程式設定。  
  
 ![登錄編輯程式中的 ClearType 設定](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>另請參閱  
 [ClearType 概觀](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [ClearType 消除鋸齒功能](https://msdn.microsoft.com/library/dd183433(v=vs.85).aspx)
