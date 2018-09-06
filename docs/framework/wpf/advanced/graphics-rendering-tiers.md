---
title: 圖形轉譯層
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], performance
- rendering graphics [WPF]
- rendering tiers [WPF]
- graphics rendering tiers [WPF]
- graphics [WPF], rendering tiers
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
ms.openlocfilehash: 9fb24e13ab684170baf5ac3001d3a2d4bcd6df7e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036427"
---
# <a name="graphics-rendering-tiers"></a>圖形轉譯層
轉譯層定義執行 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式之裝置的圖形硬體及效能層級。  
  

  
<a name="graphics_hardware"></a>   
## <a name="graphics-hardware"></a>圖形硬體  
 對轉譯層級的影響最大的圖形硬體功能如下︰  
  
-   **視訊 RAM**：圖形硬體上的視訊記憶體數量決定可用於組合圖形的緩衝區大小和數目。  
  
-   **像素著色器**：像素著色器是根據像素來計算效果的圖形處理函式。 根據所顯示圖形的解析度，每個顯示框架都可能需要處理數百萬個像素。  
  
-   **頂點著色器**：頂點著色器是在物件頂點資料上執行數學運算的圖形處理函式。  
  
-   **多紋理支援**：多紋理支援指的是可以在混色作業期間於 3D 圖形物件上套用兩個以上的不同紋理。 多紋理支援的程度取決於圖形硬體上的多紋理單位數目。  
  
<a name="rendering_tier_definitions"></a>   
## <a name="rendering-tier-definitions"></a>轉譯層定義  
 圖形硬體的功能決定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的轉譯功能。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 系統定義三個轉譯層︰  
  
-   **轉譯層 0**：沒有圖形硬體加速。 所有圖形功能都會使用軟體加速。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本層級小於 9.0 版。  
  
-   **轉譯層 1**：部分圖形功能使用圖形硬體加速。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本層級大於或等於 9.0 版。  
  
-   **轉譯層 2**：大部分圖形功能都使用圖形硬體加速。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本層級大於或等於 9.0 版。  
  
 <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=nameWithType>屬性可讓您擷取應用程式執行階段的轉譯層。 您可以使用轉譯層來判斷裝置是否支援特定硬體加速的圖形功能。 您的應用程式接著可以在執行階段，根據裝置所支援的轉譯層來採用不同的程式碼路徑。  
  
### <a name="rendering-tier-0"></a>轉譯層 0  
 轉譯層值 0 表示裝置上的應用程式沒有任何圖形硬體加速。 在此層級，您應該假設軟體將會在沒有硬體加速的情況下轉譯所有圖形。 這一層的功能等同於小於 9.0 的 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本。  
  
### <a name="rendering-tier-1-and-rendering-tier-2"></a>轉譯層 1 和轉譯層 2  
  
> [!NOTE]
>  從 .NET Framework 4 開始，轉譯層 1 已重新定義成僅包括支援 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 9.0 或更新版本的圖形硬體。 支援 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 或 8 的圖形硬體現在定義為轉譯層 0。  
  
 轉譯層值 1 或 2 表示如果有必要系統資源可用，而且還沒有用完，則 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的大部分圖形功能將會使用硬體加速。 這等同於大於或等於 9.0 的 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本。  
  
 下表顯示轉譯層 1 和轉譯層 2 圖形硬體需求的差異︰  
  
|功能|第 1 層|第 2 層|  
|-------------|------------|------------|  
|[!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本|必須大於或等於 9.0。|必須大於或等於 9.0。|  
|視訊 RAM|必須大於或等於 60 MB。|必須大於或等於 120 MB。|  
|像素著色器|版本層級必須大於或等於 2.0。|版本層級必須大於或等於 2.0。|  
|頂點著色器|沒有需求。|版本層級必須大於或等於 2.0。|  
|多紋理單位|沒有需求。|單位數必須大於或等於 4。|  
  
 下列是針對轉譯層 1 和轉譯層 2 提供硬體加速的功能：  
  
|功能|注意|  
|-------------|-----------|  
|2D 轉譯|大部分 2D 轉譯都予以支援。|  
|3D 點陣化|支援大部分的 3D 點陣化。|  
|3D 非等向性篩選|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 嘗試在轉譯 3D 內容時使用非等向性篩選。 非等向性篩選指的是增強離相機最遠且角度最陡之表面上紋理的影像品質。|  
|3D MIP 對應|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 嘗試在轉譯 3D 內容時使用 MIP 對應。 紋理佔用較小的檢視欄位時，MIP 對應可改善紋理轉譯品質<xref:System.Windows.Controls.Viewport3D>。|  
|放射狀漸層|雖然支援，但避免使用<xref:System.Windows.Media.RadialGradientBrush>大型物件上。|  
|3D 光源計算|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會執行每個頂點光線，這表示必須計算每個套用至網狀結構之資料的每個頂點的光源強度。|  
|文字轉譯|子像素字型轉譯會在圖形硬體上使用可用的像素著色器。|  
  
 下列是僅針對轉譯層 2 提供硬體加速的功能：  
  
|功能|注意|  
|-------------|-----------|  
|3D 消除鋸齒|只有支援 Windows 顯示驅動程式模型 (WDDM) 的作業系統才支援 3D 消除鋸齒，例如 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 和 [!INCLUDE[win7](../../../../includes/win7-md.md)]。|  
  
 下列是**未**提供硬體加速的功能：  
  
|功能|注意|  
|-------------|-----------|  
|列印的內容|所有列印的內容都是使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 軟體管線所轉譯。|  
|使用點陣化內容 <xref:System.Windows.Media.Imaging.RenderTargetBitmap>|使用呈現任何內容<xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A>方法的<xref:System.Windows.Media.Imaging.RenderTargetBitmap>。|  
|使用並排顯示的內容 <xref:System.Windows.Media.TileBrush>|任何並排顯示內容所在<xref:System.Windows.Media.TileBrush.TileMode%2A>的屬性<xref:System.Windows.Media.TileBrush>設定為<xref:System.Windows.Media.TileMode.Tile>。|  
|超過圖形硬體之最大紋理大小的介面|針對大部分圖形硬體，大型表面的大小是 2048x2048 或 4096x4096 像素。|  
|視訊 RAM 需求超出圖形硬體記憶體的任何作業|您可以使用 Windows SDK 之 [WPF 效能套件](https://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)中所含的 Perforator 工具，來監視應用程式視訊 RAM 使用方式。|  
|多層式視窗|多層式視窗允許 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式轉譯非矩形視窗中的畫面內容。 在支援 Windows 顯示驅動程式模型 (WDDM) 的 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 和 [!INCLUDE[win7](../../../../includes/win7-md.md)] 這類作業系統上，多層式視窗會進行硬體加速。 在 [!INCLUDE[winxp](../../../../includes/winxp-md.md)] 這類其他系統上，沒有硬體加速的軟體會轉譯多層式視窗。<br /><br /> 您可以啟用中的多層式的視窗[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]藉由設定下列<xref:System.Windows.Window>屬性：<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> = <xref:System.Windows.WindowStyle.None><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> = `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> = <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## <a name="other-resources"></a>其他資源  
 下列資源可協助您分析 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的效能特性。  
  
### <a name="graphics-rendering-registry-settings"></a>圖形轉譯登錄設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供四個登錄設定來控制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 轉譯：  
  
|設定|描述|  
|-------------|-----------------|  
|**停用硬體加速選項**|指定是否應該啟用硬體加速。|  
|**最大多重取樣值**|指定消除鋸齒 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 內容的多重取樣程度。|  
|**需要的視訊驅動程式日期設定**|指定系統是否停用 2004 年 11 月之前所發行驅動程式的硬體加速。|  
|**使用軟體模擬轉譯器選項**|指定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是否應該使用軟體模擬轉譯器。|  
  
 這些設定可由知道如何參考 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 登錄設定的外部組態公用程式所存取。 您也可以使用 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 登錄編輯程式直接存取這些值來建立或修改這些設定。 如需詳細資訊，請參閱[圖形轉譯登錄設定](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md)。  
  
### <a name="wpf-performance-profiling-tools"></a>WPF 效能程式碼剖析工具  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一套效能分析工具，可讓您分析應用程式的執行階段行為，並判斷您可以套用的效能最佳化類型。 下表列出 [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] 工具 (WPF 效能套件) 所包含的效能剖析工具：  
  
|工具|描述|  
|----------|-----------------|  
|Perforator|用於分析轉譯行為。|  
|Visual Profiler|用於剖析 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 服務的使用情形，例如視覺化樹狀結構中由項目處理的版面配置和事件。|  
  
 WPF 效能套件提供效能資料的豐富圖形檢視。 如需 WPF 效能工具的詳細資訊，請參閱 [WPF 效能套件](https://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)。  
  
### <a name="directx-diagnostic-tool"></a>DirectX       
 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 診斷工具 Dxdiag.exe 旨在協助您對 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 相關問題進行疑難排解。 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 診斷工具的預設安裝資料夾是︰  
  
 `~\Windows\System32`  
  
 當您執行 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 診斷工具時，主要視窗包含一組索引標籤可讓您顯示和診斷 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 相關資訊。 例如，[系統] 索引標籤提供您電腦的系統資訊，並指定電腦上所安裝的 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 版本。  
  
 ![螢幕擷取畫面： DirectX 診斷工具](../../../../docs/framework/wpf/advanced/media/directxdiagnostictool-01.png "DirectXDiagnosticTool_01")  
DirectX 診斷工具主要視窗  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.RenderCapability>  
 <xref:System.Windows.Media.RenderOptions>  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [WPF 效能套件](https://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)  
 [圖形轉譯登錄設定](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md)  
 [動畫祕訣和訣竅](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
