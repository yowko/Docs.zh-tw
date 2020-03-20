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
# <a name="cleartype-registry-settings"></a><span data-ttu-id="b7029-102">ClearType 登錄設定</span><span class="sxs-lookup"><span data-stu-id="b7029-102">ClearType Registry Settings</span></span>
<span data-ttu-id="b7029-103">本主題概述了 WPF 應用程式使用的 Microsoft ClearType 註冊表設置。</span><span class="sxs-lookup"><span data-stu-id="b7029-103">This topic provides an overview of the Microsoft ClearType registry settings that are used by WPF applications.</span></span>  

<a name="overview"></a>
## <a name="technology-overview"></a><span data-ttu-id="b7029-104">技術概觀</span><span class="sxs-lookup"><span data-stu-id="b7029-104">Technology Overview</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b7029-105">向顯示裝置呈現文本的應用程式使用 ClearType 功能提供增強的閱讀體驗。</span><span class="sxs-lookup"><span data-stu-id="b7029-105">applications that render text to a display device use ClearType features to provide an enhanced reading experience.</span></span> <span data-ttu-id="b7029-106">ClearType 是 Microsoft 開發的一種軟體技術，可提高現有 LCD（液晶顯示器）文本的可讀性，例如筆記本電腦螢幕、袖珍 PC 螢幕和平板顯示器。</span><span class="sxs-lookup"><span data-stu-id="b7029-106">ClearType is a software technology developed by Microsoft that improves the readability of text on existing LCDs (Liquid Crystal Displays), such as laptop screens, Pocket PC screens and flat panel monitors.</span></span> <span data-ttu-id="b7029-107">ClearType 的工作原理是訪問 LCD 螢幕每個圖元中的單個垂直顏色條紋元素。</span><span class="sxs-lookup"><span data-stu-id="b7029-107">ClearType works by accessing the individual vertical color stripe elements in every pixel of an LCD screen.</span></span> <span data-ttu-id="b7029-108">有關清除類型的詳細資訊，請參閱[清除類型概述](cleartype-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b7029-108">For more information on ClearType, see [ClearType Overview](cleartype-overview.md).</span></span>  
  
 <span data-ttu-id="b7029-109">在各種顯示裝置上查看時，使用 ClearType 呈現的文本可能會明顯不同。</span><span class="sxs-lookup"><span data-stu-id="b7029-109">Text that is rendered with ClearType can appear significantly different when viewed on various display devices.</span></span> <span data-ttu-id="b7029-110">例如，少量監視器以藍色、綠色、紅色順序實現顏色條紋元素，而不是更常見的紅色、綠色、藍色 （RGB） 順序。</span><span class="sxs-lookup"><span data-stu-id="b7029-110">For example, a small number of monitors implement the color stripe elements in blue, green, red order rather than the more common red, green, blue (RGB) order.</span></span>  
  
 <span data-ttu-id="b7029-111">當具有不同顏色敏感度等級的個人查看時，使用 ClearType 呈現的文本也會出現顯著差異。</span><span class="sxs-lookup"><span data-stu-id="b7029-111">Text that is rendered with ClearType can also appear significantly different when viewed by individuals with varying levels of color sensitivity.</span></span> <span data-ttu-id="b7029-112">有些人比其他人更能感知色彩的細微差異。</span><span class="sxs-lookup"><span data-stu-id="b7029-112">Some individuals can detect slight differences in color better than others.</span></span>  
  
 <span data-ttu-id="b7029-113">在每種情況下，都需要修改 ClearType 功能，以便為每個人提供最佳的閱讀體驗。</span><span class="sxs-lookup"><span data-stu-id="b7029-113">In each of these cases, ClearType features need to be modified in order to provide the best reading experience for each individual.</span></span>  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a><span data-ttu-id="b7029-114">登錄設定</span><span class="sxs-lookup"><span data-stu-id="b7029-114">Registry Settings</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b7029-115">指定用於控制 ClearType 功能的四個註冊表設置：</span><span class="sxs-lookup"><span data-stu-id="b7029-115">specifies four registry settings for controlling ClearType features:</span></span>  
  
|<span data-ttu-id="b7029-116">設定</span><span class="sxs-lookup"><span data-stu-id="b7029-116">Setting</span></span>|<span data-ttu-id="b7029-117">描述</span><span class="sxs-lookup"><span data-stu-id="b7029-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7029-118">清除類型級別</span><span class="sxs-lookup"><span data-stu-id="b7029-118">ClearType level</span></span>|<span data-ttu-id="b7029-119">描述清晰類型顏色清晰度級別。</span><span class="sxs-lookup"><span data-stu-id="b7029-119">Describes the level of ClearType color clarity.</span></span>|  
|<span data-ttu-id="b7029-120">色差補正層級</span><span class="sxs-lookup"><span data-stu-id="b7029-120">Gamma level</span></span>|<span data-ttu-id="b7029-121">說明顯示裝置的像素色彩元件層級。</span><span class="sxs-lookup"><span data-stu-id="b7029-121">Describes the level of the pixel color component for a display device.</span></span>|  
|<span data-ttu-id="b7029-122">像素結構</span><span class="sxs-lookup"><span data-stu-id="b7029-122">Pixel structure</span></span>|<span data-ttu-id="b7029-123">說明顯示裝置的像素排列。</span><span class="sxs-lookup"><span data-stu-id="b7029-123">Describes the arrangement of pixels for a display device.</span></span>|  
|<span data-ttu-id="b7029-124">文字對比層級</span><span class="sxs-lookup"><span data-stu-id="b7029-124">Text contrast level</span></span>|<span data-ttu-id="b7029-125">說明顯示文字的對比層級。</span><span class="sxs-lookup"><span data-stu-id="b7029-125">Describes the level of contrast for displayed text.</span></span>|  
  
 <span data-ttu-id="b7029-126">這些設置可以通過外部配置實用程式訪問，該實用程式知道如何引用已識別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的 ClearType 註冊表設置。</span><span class="sxs-lookup"><span data-stu-id="b7029-126">These settings can be accessed by an external configuration utility that knows how to reference the identified [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType registry settings.</span></span> <span data-ttu-id="b7029-127">還可以通過使用 Windows 登錄編輯程式直接存取這些值來創建或修改這些設置。</span><span class="sxs-lookup"><span data-stu-id="b7029-127">These settings can also be created or modified by accessing the values directly by using the Windows Registry Editor.</span></span>  
  
 <span data-ttu-id="b7029-128">如果未設置[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ClearType 註冊表設置（這是預設狀態），[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式將查詢 Windows 系統參數資訊以進行字體平滑設置。</span><span class="sxs-lookup"><span data-stu-id="b7029-128">If the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ClearType registry settings are not set (which is the default state), the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application queries the Windows system parameters information for font smoothing settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7029-129">有關枚舉顯示裝置名稱的資訊，請參閱`SystemParametersInfo`Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="b7029-129">For information on enumerating display device names, see the `SystemParametersInfo`Win32 function.</span></span>  
  
<a name="ClearType_level"></a>
## <a name="cleartype-level"></a><span data-ttu-id="b7029-130">ClearType 層級</span><span class="sxs-lookup"><span data-stu-id="b7029-130">ClearType Level</span></span>  
 <span data-ttu-id="b7029-131">ClearType 級別允許您根據個人的顏色敏感度和感知來調整文本的呈現。</span><span class="sxs-lookup"><span data-stu-id="b7029-131">The ClearType level allows you to adjust the rendering of text based on the color sensitivity and perception of an individual.</span></span> <span data-ttu-id="b7029-132">對於某些個人，在最高級別使用 ClearType 的文本的呈現不會產生最佳的閱讀體驗。</span><span class="sxs-lookup"><span data-stu-id="b7029-132">For some individuals, the rendering of text that uses ClearType at its highest level does not produce the best reading experience.</span></span>  
  
 <span data-ttu-id="b7029-133">ClearType 級別是一個介於 0 到 100 的整數值。</span><span class="sxs-lookup"><span data-stu-id="b7029-133">The ClearType level is an integer value that ranges from 0 to 100.</span></span> <span data-ttu-id="b7029-134">預設級別為 100，這意味著 ClearType 使用顯示裝置的顏色條帶元素的最大功能。</span><span class="sxs-lookup"><span data-stu-id="b7029-134">The default level is 100, which means ClearType uses the maximum capability of the color stripe elements of the display device.</span></span> <span data-ttu-id="b7029-135">但是，ClearType 級別為 0 會將文本渲染為灰色比例。</span><span class="sxs-lookup"><span data-stu-id="b7029-135">However, a ClearType level of 0 renders text as gray scale.</span></span> <span data-ttu-id="b7029-136">通過將 ClearType 級別設置為介於 0 和 100 之間，可以創建適合個人顏色敏感度的中間級別。</span><span class="sxs-lookup"><span data-stu-id="b7029-136">By setting the ClearType level somewhere between 0 and 100, you can create an intermediate level that is suitable to an individual's color sensitivity.</span></span>  
  
### <a name="registry-setting"></a><span data-ttu-id="b7029-137">登錄設定</span><span class="sxs-lookup"><span data-stu-id="b7029-137">Registry Setting</span></span>  
 <span data-ttu-id="b7029-138">ClearType 級別的註冊表設置位置是對應于特定顯示裝置名稱的單個使用者設置：</span><span class="sxs-lookup"><span data-stu-id="b7029-138">The registry setting location for the ClearType level is an individual user setting that corresponds to a specific display device name:</span></span>  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 <span data-ttu-id="b7029-139">對於使用者的每個顯示裝置名稱，將定義一`ClearTypeLevel`個 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="b7029-139">For each display device name for a user, a `ClearTypeLevel` DWORD value is defined.</span></span> <span data-ttu-id="b7029-140">以下螢幕截圖顯示了 ClearType 級別的登錄編輯程式設置。</span><span class="sxs-lookup"><span data-stu-id="b7029-140">The following screenshot shows the Registry Editor setting for the ClearType level.</span></span>  
  
 ![清除登錄編輯程式中的設置。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="b7029-142">應用程式以兩種模式之一呈現文本，帶和沒有 ClearType。</span><span class="sxs-lookup"><span data-stu-id="b7029-142">applications render text in one of either two modes, with and without ClearType.</span></span> <span data-ttu-id="b7029-143">在未顯示 ClearType 的情況下呈現文本時，它稱為灰度渲染。</span><span class="sxs-lookup"><span data-stu-id="b7029-143">When text is rendered without ClearType, it is referred to as gray scale rendering.</span></span>  
  
<a name="gamma_level"></a>
## <a name="gamma-level"></a><span data-ttu-id="b7029-144">Gamma 層級</span><span class="sxs-lookup"><span data-stu-id="b7029-144">Gamma Level</span></span>  
 <span data-ttu-id="b7029-145">Gamma 層級是指像素值和明亮度之間的非線性關聯性。</span><span class="sxs-lookup"><span data-stu-id="b7029-145">The gamma level refers to the nonlinear relationship between a pixel value and luminance.</span></span> <span data-ttu-id="b7029-146">Gamma 層級設定應該對應至顯示裝置的實體特性，否則轉譯的輸出可能會失真。</span><span class="sxs-lookup"><span data-stu-id="b7029-146">The gamma level setting should correspond to the physical characteristics of the display device; otherwise, distortions in rendered output may occur.</span></span> <span data-ttu-id="b7029-147">例如，文本可能顯得過於寬或太窄，或者顏色條紋可能出現在字形垂直莖的邊緣。</span><span class="sxs-lookup"><span data-stu-id="b7029-147">For example, text may appear too wide or too narrow, or color fringes may appear on the edges of vertical stems of glyphs.</span></span>  
  
 <span data-ttu-id="b7029-148">Gamma 層級是範圍從 1000 到 2200 的整數值。</span><span class="sxs-lookup"><span data-stu-id="b7029-148">The gamma level is an integer value that ranges from 1000 to 2200.</span></span> <span data-ttu-id="b7029-149">預設層級為 1900。</span><span class="sxs-lookup"><span data-stu-id="b7029-149">The default level is 1900.</span></span>  
  
### <a name="registry-setting"></a><span data-ttu-id="b7029-150">登錄設定</span><span class="sxs-lookup"><span data-stu-id="b7029-150">Registry Setting</span></span>  
 <span data-ttu-id="b7029-151">Gamma 層級的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：</span><span class="sxs-lookup"><span data-stu-id="b7029-151">The registry setting location for the gamma level is a local machine setting that corresponds to a specific display device name:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 <span data-ttu-id="b7029-152">對於使用者的每個顯示裝置名稱，將定義一`GammaLevel`個 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="b7029-152">For each display device name for a user, a `GammaLevel` DWORD value is defined.</span></span> <span data-ttu-id="b7029-153">以下的螢幕擷取畫面顯示 Gamma 層級的登錄編輯程式設定。</span><span class="sxs-lookup"><span data-stu-id="b7029-153">The following screenshot shows the Registry Editor setting for the gamma level.</span></span>  
  
 ![清除登錄編輯程式中的伽馬級設置](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="pixel_structure"></a>
## <a name="pixel-structure"></a><span data-ttu-id="b7029-155">像素結構</span><span class="sxs-lookup"><span data-stu-id="b7029-155">Pixel Structure</span></span>  
 <span data-ttu-id="b7029-156">像素結構說明構成顯示裝置的像素類型。</span><span class="sxs-lookup"><span data-stu-id="b7029-156">The pixel structure describes the type of pixels that make up a display device.</span></span> <span data-ttu-id="b7029-157">像素結構定義有三種類型︰</span><span class="sxs-lookup"><span data-stu-id="b7029-157">The pixel structure is defined as one of three types:</span></span>  
  
|<span data-ttu-id="b7029-158">類型</span><span class="sxs-lookup"><span data-stu-id="b7029-158">Type</span></span>|<span data-ttu-id="b7029-159">值</span><span class="sxs-lookup"><span data-stu-id="b7029-159">Value</span></span>|<span data-ttu-id="b7029-160">描述</span><span class="sxs-lookup"><span data-stu-id="b7029-160">Description</span></span>|  
|----------|-----------|-----------------|  
|<span data-ttu-id="b7029-161">一般</span><span class="sxs-lookup"><span data-stu-id="b7029-161">Flat</span></span>|<span data-ttu-id="b7029-162">0</span><span class="sxs-lookup"><span data-stu-id="b7029-162">0</span></span>|<span data-ttu-id="b7029-163">顯示裝置沒有像素結構。</span><span class="sxs-lookup"><span data-stu-id="b7029-163">The display device has no pixel structure.</span></span> <span data-ttu-id="b7029-164">這表示每種色彩光源都平均分布在像素區域，此即為灰階轉譯。</span><span class="sxs-lookup"><span data-stu-id="b7029-164">This means that light sources for each color are spread equally on the pixel area—this is referred to as gray scale rendering.</span></span> <span data-ttu-id="b7029-165">這是標準顯示裝置運作的方式。</span><span class="sxs-lookup"><span data-stu-id="b7029-165">This is how a standard display device works.</span></span> <span data-ttu-id="b7029-166">ClearType 永遠不會應用於渲染的文本。</span><span class="sxs-lookup"><span data-stu-id="b7029-166">ClearType is never applied to the rendered text.</span></span>|  
|<span data-ttu-id="b7029-167">RGB</span><span class="sxs-lookup"><span data-stu-id="b7029-167">RGB</span></span>|<span data-ttu-id="b7029-168">1</span><span class="sxs-lookup"><span data-stu-id="b7029-168">1</span></span>|<span data-ttu-id="b7029-169">顯示裝置的像素色帶組成順序如下︰紅色、綠色和藍色。</span><span class="sxs-lookup"><span data-stu-id="b7029-169">The display device has pixels that consist of three stripes in the following order: red, green, and blue.</span></span> <span data-ttu-id="b7029-170">清除類型應用於渲染的文本。</span><span class="sxs-lookup"><span data-stu-id="b7029-170">ClearType is applied to the rendered text.</span></span>|  
|<span data-ttu-id="b7029-171">BGR</span><span class="sxs-lookup"><span data-stu-id="b7029-171">BGR</span></span>|<span data-ttu-id="b7029-172">2</span><span class="sxs-lookup"><span data-stu-id="b7029-172">2</span></span>|<span data-ttu-id="b7029-173">顯示裝置的像素色帶組成順序如下︰藍色、綠色和紅色。</span><span class="sxs-lookup"><span data-stu-id="b7029-173">The display device has pixels that consist of three stripes in the following order: blue, green, and red.</span></span> <span data-ttu-id="b7029-174">清除類型應用於渲染的文本。</span><span class="sxs-lookup"><span data-stu-id="b7029-174">ClearType is applied to the rendered text.</span></span> <span data-ttu-id="b7029-175">請注意順序由 RGB 類型反轉的方式。</span><span class="sxs-lookup"><span data-stu-id="b7029-175">Notice how the order is inverted from the RGB type.</span></span>|  
  
 <span data-ttu-id="b7029-176">像素結構對應至範圍從 0 到 2 的整數值。</span><span class="sxs-lookup"><span data-stu-id="b7029-176">The pixel structure corresponds to an integer value that ranges from 0 to 2.</span></span> <span data-ttu-id="b7029-177">預設層級為 0 表示一般的像素結構。</span><span class="sxs-lookup"><span data-stu-id="b7029-177">The default level is 0, which represents a flat pixel structure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7029-178">有關枚舉顯示裝置名稱的資訊，請參閱`EnumDisplayDevices`Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="b7029-178">For information on enumerating display device names, see the `EnumDisplayDevices`Win32 function.</span></span>  
  
### <a name="registry-setting"></a><span data-ttu-id="b7029-179">登錄設定</span><span class="sxs-lookup"><span data-stu-id="b7029-179">Registry Setting</span></span>  
 <span data-ttu-id="b7029-180">像素結構的登錄設定位置是對應到特定顯示裝置名稱的本機電腦設定：</span><span class="sxs-lookup"><span data-stu-id="b7029-180">The registry setting location for the pixel structure is a local machine setting that corresponds to a specific display device name:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 <span data-ttu-id="b7029-181">對於使用者的每個顯示裝置名稱，將定義一`PixelStructure`個 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="b7029-181">For each display device name for a user, a `PixelStructure` DWORD value is defined.</span></span> <span data-ttu-id="b7029-182">以下的螢幕擷取畫面顯示像素結構的登錄編輯程式設定。</span><span class="sxs-lookup"><span data-stu-id="b7029-182">The following screenshot shows the Registry Editor setting for the pixel structure.</span></span>  
  
 ![清除登錄編輯程式中的伽馬級設置](./media/cleartype-registry-settings/cleartype-gamma-level-settings-registry-editor.png)  
  
<a name="text_contrast_level"></a>
## <a name="text-contrast-level"></a><span data-ttu-id="b7029-184">文字對比層級</span><span class="sxs-lookup"><span data-stu-id="b7029-184">Text Contrast Level</span></span>  
 <span data-ttu-id="b7029-185">文字對比層級可讓您根據字符的主體寬度調整文字的轉譯。</span><span class="sxs-lookup"><span data-stu-id="b7029-185">The text contrast level allows you to adjust the rendering of text based on the stem widths of glyphs.</span></span> <span data-ttu-id="b7029-186">文字對比層級是一個範圍從 0 到 6 的整數值，整數值愈大，主體愈寬。</span><span class="sxs-lookup"><span data-stu-id="b7029-186">The text contrast level is an integer value that ranges from 0 to 6—the larger the integer value, the wider the stem.</span></span> <span data-ttu-id="b7029-187">預設層級為 1。</span><span class="sxs-lookup"><span data-stu-id="b7029-187">The default level is 1.</span></span>  
  
### <a name="registry-setting"></a><span data-ttu-id="b7029-188">登錄設定</span><span class="sxs-lookup"><span data-stu-id="b7029-188">Registry Setting</span></span>  
 <span data-ttu-id="b7029-189">文字對比層級的登錄設定位置是對應到特定顯示裝置名稱的個別使用者設定：</span><span class="sxs-lookup"><span data-stu-id="b7029-189">The registry setting location for the text contrast level is an individual user setting that corresponds to a specific display device name:</span></span>  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 <span data-ttu-id="b7029-190">對於使用者的每個顯示裝置名稱，將定義一`TextContrastLevel`個 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="b7029-190">For each display device name for a user, a `TextContrastLevel` DWORD value is defined.</span></span> <span data-ttu-id="b7029-191">下列螢幕擷取畫面顯示文字對比層級的登錄編輯程式設定。</span><span class="sxs-lookup"><span data-stu-id="b7029-191">The following screenshot shows the Registry Editor setting for the text contrast level.</span></span>  
  
 ![清除登錄編輯程式中的設置。](./media/cleartype-registry-settings/cleartype-settings-registry-editor.png)  
  
## <a name="see-also"></a><span data-ttu-id="b7029-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7029-193">See also</span></span>

- [<span data-ttu-id="b7029-194">ClearType 概觀</span><span class="sxs-lookup"><span data-stu-id="b7029-194">ClearType Overview</span></span>](cleartype-overview.md)
- [<span data-ttu-id="b7029-195">ClearType 消除鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="b7029-195">ClearType Antialiasing</span></span>](/windows/desktop/gdi/cleartype-antialiasing)
