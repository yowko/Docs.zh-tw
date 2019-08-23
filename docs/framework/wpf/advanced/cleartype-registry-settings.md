---
title: ClearType 登錄設定
ms.date: 03/30/2017
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
ms.openlocfilehash: f4b5a0c3764c173afe03adb67fd3df9d17d9fdcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964888"
---
# <a name="cleartype-registry-settings"></a><span data-ttu-id="e1de7-102">ClearType 登錄設定</span><span class="sxs-lookup"><span data-stu-id="e1de7-102">ClearType Registry Settings</span></span>
<span data-ttu-id="e1de7-103">本主題概要說明 WPF 應用程式所使用的 Microsoft ClearType 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="e1de7-103">This topic provides an overview of the Microsoft ClearType registry settings that are used by WPF applications.</span></span>  

<a name="overview"></a>   
## <a name="technology-overview"></a><span data-ttu-id="e1de7-104">技術概觀</span><span class="sxs-lookup"><span data-stu-id="e1de7-104">Technology Overview</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="e1de7-105">將文字呈現到顯示裝置的應用程式會使用 ClearType 功能來提供增強的閱讀體驗。</span><span class="sxs-lookup"><span data-stu-id="e1de7-105">applications that render text to a display device use ClearType features to provide an enhanced reading experience.</span></span> <span data-ttu-id="e1de7-106">ClearType 是由[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]所開發的軟體技術, 可改善現有 lcd (液晶顯示器) 的文字可讀性, 例如膝上型電腦螢幕、Pocket PC 螢幕和平面監視器。</span><span class="sxs-lookup"><span data-stu-id="e1de7-106">ClearType is a software technology developed by [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] that improves the readability of text on existing LCDs (Liquid Crystal Displays), such as laptop screens, Pocket PC screens and flat panel monitors.</span></span> <span data-ttu-id="e1de7-107">ClearType 的運作方式是存取 LCD 螢幕每個圖元內的個別垂直色彩 stripe 元素。</span><span class="sxs-lookup"><span data-stu-id="e1de7-107">ClearType works by accessing the individual vertical color stripe elements in every pixel of an LCD screen.</span></span> <span data-ttu-id="e1de7-108">如需 ClearType 的詳細資訊, 請參閱[Cleartype 總覽](cleartype-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e1de7-108">For more information on ClearType, see [ClearType Overview](cleartype-overview.md).</span></span>  
  
 <span data-ttu-id="e1de7-109">在各種顯示裝置上觀看時, 以 ClearType 轉譯的文字會明顯不同。</span><span class="sxs-lookup"><span data-stu-id="e1de7-109">Text that is rendered with ClearType can appear significantly different when viewed on various display devices.</span></span> <span data-ttu-id="e1de7-110">例如, 少數監視器會以藍色、綠色、紅色順序來執行彩色 stripe 元素, 而不是較常見的紅色、綠色、藍色 ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) 順序。</span><span class="sxs-lookup"><span data-stu-id="e1de7-110">For example, a small number of monitors implement the color stripe elements in blue, green, red order rather than the more common red, green, blue (    [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) order.</span></span>  
  
 <span data-ttu-id="e1de7-111">以 ClearType 轉譯的文字在以色彩敏感度層級不同的個人觀看時, 也會明顯不同。</span><span class="sxs-lookup"><span data-stu-id="e1de7-111">Text that is rendered with ClearType can also appear significantly different when viewed by individuals with varying levels of color sensitivity.</span></span> <span data-ttu-id="e1de7-112">有些人比其他人更能感知色彩的細微差異。</span><span class="sxs-lookup"><span data-stu-id="e1de7-112">Some individuals can detect slight differences in color better than others.</span></span>  
  
 <span data-ttu-id="e1de7-113">在上述每一種情況下, 都需要修改 ClearType 功能, 才能為每個人提供最佳的閱讀體驗。</span><span class="sxs-lookup"><span data-stu-id="e1de7-113">In each of these cases, ClearType features need to be modified in order to provide the best reading experience for each individual.</span></span>  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a><span data-ttu-id="e1de7-114">登錄設定</span><span class="sxs-lookup"><span data-stu-id="e1de7-114">Registry Settings</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="e1de7-115">指定用來控制 ClearType 功能的四個登錄設定:</span><span class="sxs-lookup"><span data-stu-id="e1de7-115">specifies four registry settings for controlling ClearType features:</span></span>  
  
|<span data-ttu-id="e1de7-116">設定</span><span class="sxs-lookup"><span data-stu-id="e1de7-116">Setting</span></span>|<span data-ttu-id="e1de7-117">說明</span><span class="sxs-lookup"><span data-stu-id="e1de7-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1de7-118">ClearType 層級</span><span class="sxs-lookup"><span data-stu-id="e1de7-118">ClearType level</span></span>|<span data-ttu-id="e1de7-119">描述 ClearType 色彩清晰度的層級。</span><span class="sxs-lookup"><span data-stu-id="e1de7-119">Describes the level of ClearType color clarity.</span></span>|  
|<span data-ttu-id="e1de7-120">色差補正層級</span><span class="sxs-lookup"><span data-stu-id="e1de7-120">Gamma level</span></span>|<span data-ttu-id="e1de7-121">說明顯示裝置的像素色彩元件層級。</span><span class="sxs-lookup"><span data-stu-id="e1de7-121">Describes the level of the pixel color component for a display device.</span></span>|  
|<span data-ttu-id="e1de7-122">像素結構</span><span class="sxs-lookup"><span data-stu-id="e1de7-122">Pixel structure</span></span>|<span data-ttu-id="e1de7-123">說明顯示裝置的像素排列。</span><span class="sxs-lookup"><span data-stu-id="e1de7-123">Describes the arrangement of pixels for a display device.</span></span>|  
|<span data-ttu-id="e1de7-124">文字對比層級</span><span class="sxs-lookup"><span data-stu-id="e1de7-124">Text contrast level</span></span>|<span data-ttu-id="e1de7-125">說明顯示文字的對比層級。</span><span class="sxs-lookup"><span data-stu-id="e1de7-125">Describes the level of contrast for displayed text.</span></span>|  
  
 <span data-ttu-id="e1de7-126">這些設定可由外部設定公用程式存取, 知道如何參考已識別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的 ClearType 登錄設定。</span><span class="sxs-lookup"><span data-stu-id="e1de7-126">These settings can be accessed by an external configuration utility that knows how to reference the identified [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType registry settings.</span></span> <span data-ttu-id="e1de7-127">您也可以使用 Windows 登錄編輯程式直接存取這些值來建立或修改這些設定。</span><span class="sxs-lookup"><span data-stu-id="e1de7-127">These settings can also be created or modified by accessing the values directly by using the Windows Registry Editor.</span></span>  
  
 <span data-ttu-id="e1de7-128">如果未設定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType登錄設定(這是預設狀態),應用程式會查詢Windows系統參數資訊中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]字型平滑設定。</span><span class="sxs-lookup"><span data-stu-id="e1de7-128">If the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType registry settings are not set (which is the default state), the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application queries the Windows system parameters information for font smoothing settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1de7-129">如需列舉顯示裝置名稱的詳細資訊, `SystemParametersInfo`請參閱[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式。</span><span class="sxs-lookup"><span data-stu-id="e1de7-129">For information on enumerating display device names, see the `SystemParametersInfo`[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function.</span></span>  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a><span data-ttu-id="e1de7-130">ClearType 層級</span><span class="sxs-lookup"><span data-stu-id="e1de7-130">ClearType Level</span></span>  
 <span data-ttu-id="e1de7-131">ClearType 層級可讓您根據個人的色彩敏感度和認知, 調整文字的呈現。</span><span class="sxs-lookup"><span data-stu-id="e1de7-131">The ClearType level allows you to adjust the rendering of text based on the color sensitivity and perception of an individual.</span></span> <span data-ttu-id="e1de7-132">對於某些人來說, 在其最高層級使用 ClearType 的文字轉譯, 並不會產生最佳的閱讀體驗。</span><span class="sxs-lookup"><span data-stu-id="e1de7-132">For some individuals, the rendering of text that uses ClearType at its highest level does not produce the best reading experience.</span></span>  
  
 <span data-ttu-id="e1de7-133">ClearType 層級是一個整數值, 範圍介於0到100之間。</span><span class="sxs-lookup"><span data-stu-id="e1de7-133">The ClearType level is an integer value that ranges from 0 to 100.</span></span> <span data-ttu-id="e1de7-134">預設層級為 100, 表示 ClearType 會使用顯示裝置的色彩 stripe 元素的最大功能。</span><span class="sxs-lookup"><span data-stu-id="e1de7-134">The default level is 100, which means ClearType uses the maximum capability of the color stripe elements of the display device.</span></span> <span data-ttu-id="e1de7-135">不過, ClearType 層級0會將文字呈現為灰色尺規。</span><span class="sxs-lookup"><span data-stu-id="e1de7-135">However, a ClearType level of 0 renders text as gray scale.</span></span> <span data-ttu-id="e1de7-136">藉由將 ClearType 層級設定為0到100之間的某個位置, 您可以建立適合個人色彩敏感度的中繼層級。</span><span class="sxs-lookup"><span data-stu-id="e1de7-136">By setting the ClearType level somewhere between 0 and 100, you can create an intermediate level that is suitable to an individual's color sensitivity.</span></span>  
  
### <a name="registry-setting"></a><span data-ttu-id="e1de7-137">登錄設定</span><span class="sxs-lookup"><span data-stu-id="e1de7-137">Registry Setting</span></span>  
 <span data-ttu-id="e1de7-138">ClearType 層級的登錄設定位置是對應到特定顯示裝置名稱的個別使用者設定:</span><span class="sxs-lookup"><span data-stu-id="e1de7-138">The registry setting location for the ClearType level is an individual user setting that corresponds to a specific display device name:</span></span>  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 <span data-ttu-id="e1de7-139">針對使用者的每個顯示裝置名稱, `ClearTypeLevel`會定義 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="e1de7-139">For each display device name for a user, a `ClearTypeLevel` DWORD value is defined.</span></span> <span data-ttu-id="e1de7-140">下列螢幕擷取畫面顯示 ClearType 層級的登錄編輯程式設定。</span><span class="sxs-lookup"><span data-stu-id="e1de7-140">The following screenshot shows the Registry Editor setting for the ClearType level.</span></span>  
  
 ![登錄編輯程式中的 ClearType 設定。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="e1de7-142">應用程式會以兩種模式的其中一種來轉譯文字, 而不論是否使用 ClearType。</span><span class="sxs-lookup"><span data-stu-id="e1de7-142">applications render text in one of either two modes, with and without ClearType.</span></span> <span data-ttu-id="e1de7-143">轉譯不含 ClearType 的文字時, 就稱為「灰階呈現」。</span><span class="sxs-lookup"><span data-stu-id="e1de7-143">When text is rendered without ClearType, it is referred to as gray scale rendering.</span></span>  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a><span data-ttu-id="e1de7-144">Gamma 層級</span><span class="sxs-lookup"><span data-stu-id="e1de7-144">Gamma Level</span></span>  
 <span data-ttu-id="e1de7-145">Gamma 層級是指像素值和明亮度之間的非線性關聯性。</span><span class="sxs-lookup"><span data-stu-id="e1de7-145">The gamma level refers to the nonlinear relationship between a pixel value and luminance.</span></span> <span data-ttu-id="e1de7-146">Gamma 層級設定應該對應至顯示裝置的實體特性，否則轉譯的輸出可能會失真。</span><span class="sxs-lookup"><span data-stu-id="e1de7-146">The gamma level setting should correspond to the physical characteristics of the display device; otherwise, distortions in rendered output may occur.</span></span> <span data-ttu-id="e1de7-147">例如，測試結果可能會太寬或太窄，或字符的垂直主體邊緣會出現色彩鬚邊。</span><span class="sxs-lookup"><span data-stu-id="e1de7-147">For example, test may appear too wide or too narrow, or color fringes may appear on the edges of vertical stems of glyphs.</span></span>  
  
 <span data-ttu-id="e1de7-148">Gamma 層級是範圍從 1000 到 2200 的整數值。</span><span class="sxs-lookup"><span data-stu-id="e1de7-148">The gamma level is an integer value that ranges from 1000 to 2200.</span></span> <span data-ttu-id="e1de7-149">預設層級為 1900。</span><span class="sxs-lookup"><span data-stu-id="e1de7-149">The default level is 1900.</span></span>  
  
### <a name="registry-setting"></a><span data-ttu-id="e1de7-150">登錄設定</span><span class="sxs-lookup"><span data-stu-id="e1de7-150">Registry Setting</span></span>  
 <span data-ttu-id="e1de7-151">Gamma 層級的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：</span><span class="sxs-lookup"><span data-stu-id="e1de7-151">The registry setting location for the gamma level is a local machine setting that corresponds to a specific display device name:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 <span data-ttu-id="e1de7-152">針對使用者的每個顯示裝置名稱, `GammaLevel`會定義 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="e1de7-152">For each display device name for a user, a `GammaLevel` DWORD value is defined.</span></span> <span data-ttu-id="e1de7-153">以下的螢幕擷取畫面顯示 Gamma 層級的登錄編輯程式設定。</span><span class="sxs-lookup"><span data-stu-id="e1de7-153">The following screenshot shows the Registry Editor setting for the gamma level.</span></span>  
  
 ![登錄編輯程式中的 ClearType gamma 層級設定](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a><span data-ttu-id="e1de7-155">像素結構</span><span class="sxs-lookup"><span data-stu-id="e1de7-155">Pixel Structure</span></span>  
 <span data-ttu-id="e1de7-156">像素結構說明構成顯示裝置的像素類型。</span><span class="sxs-lookup"><span data-stu-id="e1de7-156">The pixel structure describes the type of pixels that make up a display device.</span></span> <span data-ttu-id="e1de7-157">像素結構定義有三種類型︰</span><span class="sxs-lookup"><span data-stu-id="e1de7-157">The pixel structure is defined as one of three types:</span></span>  
  
|<span data-ttu-id="e1de7-158">類型</span><span class="sxs-lookup"><span data-stu-id="e1de7-158">Type</span></span>|<span data-ttu-id="e1de7-159">值</span><span class="sxs-lookup"><span data-stu-id="e1de7-159">Value</span></span>|<span data-ttu-id="e1de7-160">描述</span><span class="sxs-lookup"><span data-stu-id="e1de7-160">Description</span></span>|  
|----------|-----------|-----------------|  
|<span data-ttu-id="e1de7-161">一般</span><span class="sxs-lookup"><span data-stu-id="e1de7-161">Flat</span></span>|<span data-ttu-id="e1de7-162">0</span><span class="sxs-lookup"><span data-stu-id="e1de7-162">0</span></span>|<span data-ttu-id="e1de7-163">顯示裝置沒有像素結構。</span><span class="sxs-lookup"><span data-stu-id="e1de7-163">The display device has no pixel structure.</span></span> <span data-ttu-id="e1de7-164">這表示每種色彩光源都平均分布在像素區域，此即為灰階轉譯。</span><span class="sxs-lookup"><span data-stu-id="e1de7-164">This means that light sources for each color are spread equally on the pixel area—this is referred to as gray scale rendering.</span></span> <span data-ttu-id="e1de7-165">這是標準顯示裝置運作的方式。</span><span class="sxs-lookup"><span data-stu-id="e1de7-165">This is how a standard display device works.</span></span> <span data-ttu-id="e1de7-166">ClearType 永遠不會套用至呈現的文字。</span><span class="sxs-lookup"><span data-stu-id="e1de7-166">ClearType is never applied to the rendered text.</span></span>|  
|<span data-ttu-id="e1de7-167">RGB</span><span class="sxs-lookup"><span data-stu-id="e1de7-167">RGB</span></span>|<span data-ttu-id="e1de7-168">1</span><span class="sxs-lookup"><span data-stu-id="e1de7-168">1</span></span>|<span data-ttu-id="e1de7-169">顯示裝置的像素色帶組成順序如下︰紅色、綠色和藍色。</span><span class="sxs-lookup"><span data-stu-id="e1de7-169">The display device has pixels that consist of three stripes in the following order: red, green, and blue.</span></span> <span data-ttu-id="e1de7-170">ClearType 會套用至呈現的文字。</span><span class="sxs-lookup"><span data-stu-id="e1de7-170">ClearType is applied to the rendered text.</span></span>|  
|<span data-ttu-id="e1de7-171">BGR</span><span class="sxs-lookup"><span data-stu-id="e1de7-171">BGR</span></span>|<span data-ttu-id="e1de7-172">2</span><span class="sxs-lookup"><span data-stu-id="e1de7-172">2</span></span>|<span data-ttu-id="e1de7-173">顯示裝置的像素色帶組成順序如下︰藍色、綠色和紅色。</span><span class="sxs-lookup"><span data-stu-id="e1de7-173">The display device has pixels that consist of three stripes in the following order: blue, green, and red.</span></span> <span data-ttu-id="e1de7-174">ClearType 會套用至呈現的文字。</span><span class="sxs-lookup"><span data-stu-id="e1de7-174">ClearType is applied to the rendered text.</span></span> <span data-ttu-id="e1de7-175">請注意順序由 RGB 類型反轉的方式。</span><span class="sxs-lookup"><span data-stu-id="e1de7-175">Notice how the order is inverted from the RGB type.</span></span>|  
  
 <span data-ttu-id="e1de7-176">像素結構對應至範圍從 0 到 2 的整數值。</span><span class="sxs-lookup"><span data-stu-id="e1de7-176">The pixel structure corresponds to an integer value that ranges from 0 to 2.</span></span> <span data-ttu-id="e1de7-177">預設層級為 0 表示一般的像素結構。</span><span class="sxs-lookup"><span data-stu-id="e1de7-177">The default level is 0, which represents a flat pixel structure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1de7-178">如需列舉顯示裝置名稱的詳細資訊, `EnumDisplayDevices`請參閱[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式。</span><span class="sxs-lookup"><span data-stu-id="e1de7-178">For information on enumerating display device names, see the `EnumDisplayDevices`[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function.</span></span>  
  
### <a name="registry-setting"></a><span data-ttu-id="e1de7-179">登錄設定</span><span class="sxs-lookup"><span data-stu-id="e1de7-179">Registry Setting</span></span>  
 <span data-ttu-id="e1de7-180">像素結構的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：</span><span class="sxs-lookup"><span data-stu-id="e1de7-180">The registry setting location for the pixel structure is a local machine setting that corresponds to a specific display device name:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 <span data-ttu-id="e1de7-181">針對使用者的每個顯示裝置名稱, `PixelStructure`會定義 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="e1de7-181">For each display device name for a user, a `PixelStructure` DWORD value is defined.</span></span> <span data-ttu-id="e1de7-182">以下的螢幕擷取畫面顯示像素結構的登錄編輯程式設定。</span><span class="sxs-lookup"><span data-stu-id="e1de7-182">The following screenshot shows the Registry Editor setting for the pixel structure.</span></span>  
  
 ![登錄編輯程式中的 ClearType gamma 層級設定](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a><span data-ttu-id="e1de7-184">文字對比層級</span><span class="sxs-lookup"><span data-stu-id="e1de7-184">Text Contrast Level</span></span>  
 <span data-ttu-id="e1de7-185">文字對比層級可讓您根據字符的主體寬度調整文字的轉譯。</span><span class="sxs-lookup"><span data-stu-id="e1de7-185">The text contrast level allows you to adjust the rendering of text based on the stem widths of glyphs.</span></span> <span data-ttu-id="e1de7-186">文字對比層級是一個範圍從 0 到 6 的整數值，整數值愈大，主體愈寬。</span><span class="sxs-lookup"><span data-stu-id="e1de7-186">The text contrast level is an integer value that ranges from 0 to 6—the larger the integer value, the wider the stem.</span></span> <span data-ttu-id="e1de7-187">預設層級為 1。</span><span class="sxs-lookup"><span data-stu-id="e1de7-187">The default level is 1.</span></span>  
  
### <a name="registry-setting"></a><span data-ttu-id="e1de7-188">登錄設定</span><span class="sxs-lookup"><span data-stu-id="e1de7-188">Registry Setting</span></span>  
 <span data-ttu-id="e1de7-189">文字對比層級的登錄設定位置是對應到特定顯示裝置名稱的個別使用者設定：</span><span class="sxs-lookup"><span data-stu-id="e1de7-189">The registry setting location for the text contrast level is an individual user setting that corresponds to a specific display device name:</span></span>  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 <span data-ttu-id="e1de7-190">針對使用者的每個顯示裝置名稱, `TextContrastLevel`會定義 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="e1de7-190">For each display device name for a user, a `TextContrastLevel` DWORD value is defined.</span></span> <span data-ttu-id="e1de7-191">下列螢幕擷取畫面顯示文字對比層級的登錄編輯程式設定。</span><span class="sxs-lookup"><span data-stu-id="e1de7-191">The following screenshot shows the Registry Editor setting for the text contrast level.</span></span>  
  
 ![登錄編輯程式中的 ClearType 設定。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a><span data-ttu-id="e1de7-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1de7-193">See also</span></span>

- [<span data-ttu-id="e1de7-194">ClearType 概觀</span><span class="sxs-lookup"><span data-stu-id="e1de7-194">ClearType Overview</span></span>](cleartype-overview.md)
- [<span data-ttu-id="e1de7-195">ClearType 消除鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="e1de7-195">ClearType Antialiasing</span></span>](/windows/desktop/gdi/cleartype-antialiasing)
