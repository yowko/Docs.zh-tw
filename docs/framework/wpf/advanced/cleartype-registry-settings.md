---
title: ClearType 登錄設定
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: bedd99fcf9b4ca1d10b4c24d7cff9de320e6fd12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186167"
---
# <a name="cleartype-registry-settings"></a>ClearType 登錄設定
本主題概述了 WPF 應用程式使用的 Microsoft ClearType 註冊表設置。  

<a name="overview"></a>
## <a name="technology-overview"></a>技術概觀  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]向顯示裝置呈現文本的應用程式使用 ClearType 功能提供增強的閱讀體驗。 ClearType 是 Microsoft 開發的一種軟體技術，可提高現有 LCD（液晶顯示器）文本的可讀性，例如筆記本電腦螢幕、袖珍 PC 螢幕和平板顯示器。 ClearType 的工作原理是訪問 LCD 螢幕每個圖元中的單個垂直顏色條紋元素。 有關清除類型的詳細資訊，請參閱[清除類型概述](cleartype-overview.md)。  
  
 在各種顯示裝置上查看時，使用 ClearType 呈現的文本可能會明顯不同。 例如，少量監視器以藍色、綠色、紅色順序實現顏色條紋元素，而不是更常見的紅色、綠色、藍色 （RGB） 順序。  
  
 當具有不同顏色敏感度等級的個人查看時，使用 ClearType 呈現的文本也會出現顯著差異。 有些人比其他人更能感知色彩的細微差異。  
  
 在每種情況下，都需要修改 ClearType 功能，以便為每個人提供最佳的閱讀體驗。  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>登錄設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]指定用於控制 ClearType 功能的四個註冊表設置：  
  
|設定|描述|  
|-------------|-----------------|  
|清除類型級別|描述清晰類型顏色清晰度級別。|  
|色差補正層級|說明顯示裝置的像素色彩元件層級。|  
|像素結構|說明顯示裝置的像素排列。|  
|文字對比層級|說明顯示文字的對比層級。|  
  
 這些設置可以通過外部配置實用程式訪問，該實用程式知道如何引用已識別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的 ClearType 註冊表設置。 還可以通過使用 Windows 登錄編輯程式直接存取這些值來創建或修改這些設置。  
  
 如果未設置[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType 註冊表設置（這是預設狀態），[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式將查詢 Windows 系統參數資訊以進行字體平滑設置。  
  
> [!NOTE]
> 有關枚舉顯示裝置名稱的資訊，請參閱`SystemParametersInfo`Win32 函數。  
  
<a name="ClearType_level"></a>
## <a name="cleartype-level"></a>ClearType 層級  
 ClearType 級別允許您根據個人的顏色敏感度和感知來調整文本的呈現。 對於某些個人，在最高級別使用 ClearType 的文本的呈現不會產生最佳的閱讀體驗。  
  
 ClearType 級別是一個介於 0 到 100 的整數值。 預設級別為 100，這意味著 ClearType 使用顯示裝置的顏色條帶元素的最大功能。 但是，ClearType 級別為 0 會將文本渲染為灰色比例。 通過將 ClearType 級別設置為介於 0 和 100 之間，可以創建適合個人顏色敏感度的中間級別。  
  
### <a name="registry-setting"></a>登錄設定  
 ClearType 級別的註冊表設置位置是對應于特定顯示裝置名稱的單個使用者設置：  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 對於使用者的每個顯示裝置名稱，將定義一`ClearTypeLevel`個 DWORD 值。 以下螢幕截圖顯示了 ClearType 級別的登錄編輯程式設置。  
  
 ![清除登錄編輯程式中的設置。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式以兩種模式之一呈現文本，帶和沒有 ClearType。 在未顯示 ClearType 的情況下呈現文本時，它稱為灰度渲染。  
  
<a name="gamma_level"></a>
## <a name="gamma-level"></a>Gamma 層級  
 Gamma 層級是指像素值和明亮度之間的非線性關聯性。 Gamma 層級設定應該對應至顯示裝置的實體特性，否則轉譯的輸出可能會失真。 例如，文本可能顯得過於寬或太窄，或者顏色條紋可能出現在字形垂直莖的邊緣。  
  
 Gamma 層級是範圍從 1000 到 2200 的整數值。 預設層級為 1900。  
  
### <a name="registry-setting"></a>登錄設定  
 Gamma 層級的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 對於使用者的每個顯示裝置名稱，將定義一`GammaLevel`個 DWORD 值。 以下的螢幕擷取畫面顯示 Gamma 層級的登錄編輯程式設定。  
  
 ![清除登錄編輯程式中的伽馬級設置](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>
## <a name="pixel-structure"></a>像素結構  
 像素結構說明構成顯示裝置的像素類型。 像素結構定義有三種類型︰  
  
|類型|值|描述|  
|----------|-----------|-----------------|  
|一般|0|顯示裝置沒有像素結構。 這表示每種色彩光源都平均分布在像素區域，此即為灰階轉譯。 這是標準顯示裝置運作的方式。 ClearType 永遠不會應用於渲染的文本。|  
|RGB|1|顯示裝置的像素色帶組成順序如下︰紅色、綠色和藍色。 清除類型應用於渲染的文本。|  
|BGR|2|顯示裝置的像素色帶組成順序如下︰藍色、綠色和紅色。 清除類型應用於渲染的文本。 請注意順序由 RGB 類型反轉的方式。|  
  
 像素結構對應至範圍從 0 到 2 的整數值。 預設層級為 0 表示一般的像素結構。  
  
> [!NOTE]
> 有關枚舉顯示裝置名稱的資訊，請參閱`EnumDisplayDevices`Win32 函數。  
  
### <a name="registry-setting"></a>登錄設定  
 像素結構的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 對於使用者的每個顯示裝置名稱，將定義一`PixelStructure`個 DWORD 值。 以下的螢幕擷取畫面顯示像素結構的登錄編輯程式設定。  
  
 ![清除登錄編輯程式中的伽馬級設置](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>
## <a name="text-contrast-level"></a>文字對比層級  
 文字對比層級可讓您根據字符的主體寬度調整文字的轉譯。 文字對比層級是一個範圍從 0 到 6 的整數值，整數值愈大，主體愈寬。 預設層級為 1。  
  
### <a name="registry-setting"></a>登錄設定  
 文字對比層級的登錄設定位置是對應到特定顯示裝置名稱的個別使用者設定：  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 對於使用者的每個顯示裝置名稱，將定義一`TextContrastLevel`個 DWORD 值。 下列螢幕擷取畫面顯示文字對比層級的登錄編輯程式設定。  
  
 ![清除登錄編輯程式中的設置。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a>另請參閱

- [ClearType 概觀](cleartype-overview.md)
- [ClearType 消除鋸齒功能](/windows/desktop/gdi/cleartype-antialiasing)
