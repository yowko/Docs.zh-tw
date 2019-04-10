---
title: ClearType 登錄設定
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: a776c3d4060b9ca291e4e919ab6ca33fb713434c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079990"
---
# <a name="cleartype-registry-settings"></a>ClearType 登錄設定
本主題概述[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]所使用的登錄設定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  

<a name="overview"></a>   
## <a name="technology-overview"></a>技術概觀  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 呈現文字至顯示裝置使用的應用程式[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]特性可提供增強的閱讀體驗。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 軟體技術開發[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]，改進了現有 Lcd （液晶顯示器），例如膝上型電腦螢幕、 Pocket PC 螢幕和平面監視器上文字的可讀性。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 藉由存取個別垂直色帶項目在每個像素的 LCD 螢幕中的運作方式。 如需詳細資訊[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]，請參閱 < [ClearType 概觀](cleartype-overview.md)。  
  
 使用呈現的文字[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]可以出現在不同的顯示裝置上檢視時的明顯不同。 例如，少數監視器實作色帶項目以藍色、 綠色、 紅色的順序，而不是較常見的紅色、 綠色、 藍色 ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) 順序。  
  
 使用呈現的文字[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]也會出現大不相同，每個人使用不同的層級的色彩敏感度檢視時。 有些人比其他人更能感知色彩的細微差異。  
  
 在這些情況下，[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]需要修改以提供最佳的閱讀經驗，為每個個別的功能。  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>登錄設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 指定四個登錄設定來控制[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]功能：  
  
|設定|描述|  
|-------------|-----------------|  
|[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] level|描述的層級[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]色彩清晰度。|  
|色差補正層級|說明顯示裝置的像素色彩元件層級。|  
|像素結構|說明顯示裝置的像素排列。|  
|文字對比層級|說明顯示文字的對比層級。|  
  
 這些設定可由知道如何參考識別之外部組態公用程式存取[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]登錄設定。 您也可以使用 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 登錄編輯程式直接存取這些值來建立或修改這些設定。  
  
 如果[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]登錄設定不設定 （也就是預設狀態），[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式查詢[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]系統字型平滑化設定的參數資訊。  
  
> [!NOTE]
>  如需列舉顯示裝置名稱的詳細資訊，請參閱`SystemParametersInfo`[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式。  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>ClearType 層級  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級可讓您調整文字的色彩敏感度和接受度個人為基礎的轉譯。 對某些人而言轉譯的文字，會使用[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]以最高層級不會產生最佳的閱讀體驗。  
  
 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級是範圍從 0 到 100 的整數值。 預設層級為 100，這表示[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]使用色帶項目顯示裝置的最大功能。 不過，[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級為 0 會轉譯成灰階文字。 藉由設定[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級 0 與 100 之間的某處，您可以建立適合個人的色彩敏感度的中間層級。  
  
### <a name="registry-setting"></a>登錄設定  
 登錄設定位置[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]等級會對應到特定顯示裝置名稱的個別使用者設定：  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 每個顯示裝置名稱的使用者，`ClearTypeLevel`定義 DWORD 值。 下列螢幕擷取畫面顯示的 登錄編輯程式設定[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]層級。  
  
 ![在登錄編輯器中的 ClearType 設定。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式呈現的文字中包含或不含下列任一種模式的其中一個[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]。 文字時將不會呈現[!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]，它指以灰階轉譯。  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Gamma 層級  
 Gamma 層級是指像素值和明亮度之間的非線性關聯性。 Gamma 層級設定應該對應至顯示裝置的實體特性，否則轉譯的輸出可能會失真。 例如，測試結果可能會太寬或太窄，或字符的垂直主體邊緣會出現色彩鬚邊。  
  
 Gamma 層級是範圍從 1000 到 2200 的整數值。 預設層級為 1900。  
  
### <a name="registry-setting"></a>登錄設定  
 Gamma 層級的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 每個顯示裝置名稱的使用者，`GammaLevel`定義 DWORD 值。 以下的螢幕擷取畫面顯示 Gamma 層級的登錄編輯程式設定。  
  
 ![ClearType gamma 層級設定在 登錄編輯器](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>像素結構  
 像素結構說明構成顯示裝置的像素類型。 像素結構定義有三種類型︰  
  
|類型|值|描述|  
|----------|-----------|-----------------|  
|一般|0|顯示裝置沒有像素結構。 這表示每種色彩光源都平均分布在像素區域，此即為灰階轉譯。 這是標準顯示裝置運作的方式。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 永遠不會套用至轉譯的文字。|  
|RGB|1|顯示裝置的像素色帶組成順序如下︰紅色、綠色和藍色。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 會套用至轉譯的文字。|  
|BGR|2|顯示裝置的像素色帶組成順序如下︰藍色、綠色和紅色。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 會套用至轉譯的文字。 請注意順序由 RGB 類型反轉的方式。|  
  
 像素結構對應至範圍從 0 到 2 的整數值。 預設層級為 0 表示一般的像素結構。  
  
> [!NOTE]
>  如需列舉顯示裝置名稱的詳細資訊，請參閱`EnumDisplayDevices`[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式。  
  
### <a name="registry-setting"></a>登錄設定  
 像素結構的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 每個顯示裝置名稱的使用者，`PixelStructure`定義 DWORD 值。 以下的螢幕擷取畫面顯示像素結構的登錄編輯程式設定。  
  
 ![ClearType gamma 層級設定在 登錄編輯器](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>文字對比層級  
 文字對比層級可讓您根據字符的主體寬度調整文字的轉譯。 文字對比層級是一個範圍從 0 到 6 的整數值，整數值愈大，主體愈寬。 預設層級為 1。  
  
### <a name="registry-setting"></a>登錄設定  
 文字對比層級的登錄設定位置是對應到特定顯示裝置名稱的個別使用者設定：  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 每個顯示裝置名稱的使用者，`TextContrastLevel`定義 DWORD 值。 下列螢幕擷取畫面顯示文字對比層級的登錄編輯程式設定。  
  
 ![在登錄編輯器中的 ClearType 設定。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>另請參閱

- [ClearType 概觀](cleartype-overview.md)
- [ClearType 消除鋸齒功能](/windows/desktop/gdi/cleartype-antialiasing)
