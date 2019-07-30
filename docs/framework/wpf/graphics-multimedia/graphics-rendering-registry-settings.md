---
title: 圖形轉譯登錄設定
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: c3544769480a45068be0ca64e90f91253daf3e16
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629785"
---
# <a name="graphics-rendering-registry-settings"></a><span data-ttu-id="d905e-102">圖形轉譯登錄設定</span><span class="sxs-lookup"><span data-stu-id="d905e-102">Graphics Rendering Registry Settings</span></span>
<span data-ttu-id="d905e-103">本主題會概略說明會影響 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形轉譯登錄設定。</span><span class="sxs-lookup"><span data-stu-id="d905e-103">This topic provides an overview of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphics rendering registry settings that affect [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>  

<a name="overview"></a>   
## <a name="when-to-use-graphics-rendering-registry-settings"></a><span data-ttu-id="d905e-104">使用圖形轉譯登錄設定的時機</span><span class="sxs-lookup"><span data-stu-id="d905e-104">When to Use Graphics Rendering Registry Settings</span></span>  
 <span data-ttu-id="d905e-105">這些登錄設定是為了進行疑難排解、偵錯，以及產品支援目的而提供。</span><span class="sxs-lookup"><span data-stu-id="d905e-105">These registry settings are provided for troubleshooting, debugging, and product support purposes.</span></span> <span data-ttu-id="d905e-106">因為變更登錄會影響所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式，所以您的應用程式永遠不應自動或在安裝期間更改這些登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="d905e-106">Because changes to the registry affect all [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, your application should never alter these registry keys automatically, or during installation.</span></span>  
  
<a name="xpdmandwddm"></a>   
## <a name="what-are-xpdm-and-wddm"></a><span data-ttu-id="d905e-107">什麼是 XPDM 和 WDDM？</span><span class="sxs-lookup"><span data-stu-id="d905e-107">What are XPDM and WDDM?</span></span>  
 <span data-ttu-id="d905e-108">一些圖形轉譯登錄設定有不同的預設值，取決於您的視訊卡使用 XPDM 或 WDDM 驅動程式。</span><span class="sxs-lookup"><span data-stu-id="d905e-108">Some of the graphics rendering registry settings have different default values, depending on whether your video card uses an XPDM or WDDM driver.</span></span> <span data-ttu-id="d905e-109">XPDM 是 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 顯示驅動程式模型，而 WDDM 是 Windows 顯示驅動程式模型。</span><span class="sxs-lookup"><span data-stu-id="d905e-109">XPDM is the [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] Display Driver Model and WDDM is the Windows Display Driver Model.</span></span> <span data-ttu-id="d905e-110">WDDM 是在執行 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] 和 [!INCLUDE[win7](../../../../includes/win7-md.md)] 的電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="d905e-110">WDDM is available on computers running [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] and [!INCLUDE[win7](../../../../includes/win7-md.md)].</span></span> <span data-ttu-id="d905e-111">XPDM 是在執行 [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]、[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 和 [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)] 的電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="d905e-111">XPDM is available on computers running [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)], and [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)].</span></span> <span data-ttu-id="d905e-112">如需 WDDM 的詳細資訊，請參閱 [Windows Vista 顯示驅動程式模型設計指南](https://go.microsoft.com/fwlink/?LinkId=178394)。</span><span class="sxs-lookup"><span data-stu-id="d905e-112">For more information about WDDM, see [Windows Vista Display Driver Model Design Guide](https://go.microsoft.com/fwlink/?LinkId=178394).</span></span>  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a><span data-ttu-id="d905e-113">登錄設定</span><span class="sxs-lookup"><span data-stu-id="d905e-113">Registry Settings</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="d905e-114">提供四個登錄設定來控制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 轉譯：</span><span class="sxs-lookup"><span data-stu-id="d905e-114">provides four registry settings for controlling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rendering:</span></span>  
  
|<span data-ttu-id="d905e-115">設定</span><span class="sxs-lookup"><span data-stu-id="d905e-115">Setting</span></span>|<span data-ttu-id="d905e-116">描述</span><span class="sxs-lookup"><span data-stu-id="d905e-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d905e-117">**停用硬體加速選項**</span><span class="sxs-lookup"><span data-stu-id="d905e-117">**Disable Hardware Acceleration Option**</span></span>|<span data-ttu-id="d905e-118">指定是否應該啟用硬體加速。</span><span class="sxs-lookup"><span data-stu-id="d905e-118">Specifies whether hardware acceleration should be enabled.</span></span>|  
|<span data-ttu-id="d905e-119">**最大多重取樣值**</span><span class="sxs-lookup"><span data-stu-id="d905e-119">**Maximum Multisample Value**</span></span>|<span data-ttu-id="d905e-120">指定將3D 內容消除鋸齒的取樣程度。</span><span class="sxs-lookup"><span data-stu-id="d905e-120">Specifies the degree of multisampling for antialiasing 3-D content.</span></span>|  
|<span data-ttu-id="d905e-121">**需要的視訊驅動程式日期設定**</span><span class="sxs-lookup"><span data-stu-id="d905e-121">**Required Video Driver Date Setting**</span></span>|<span data-ttu-id="d905e-122">指定系統是否停用 2004 年 11 月之前所發行驅動程式的硬體加速。</span><span class="sxs-lookup"><span data-stu-id="d905e-122">Specifies whether the system disables hardware acceleration for drivers released before November 2004.</span></span>|  
|<span data-ttu-id="d905e-123">**使用軟體模擬轉譯器選項**</span><span class="sxs-lookup"><span data-stu-id="d905e-123">**Use Reference Rasterizer Option**</span></span>|<span data-ttu-id="d905e-124">指定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是否應該使用軟體模擬轉譯器。</span><span class="sxs-lookup"><span data-stu-id="d905e-124">Specifies whether [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] should use the reference rasterizer.</span></span>|  
  
 <span data-ttu-id="d905e-125">這些設定可由知道如何參考 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 登錄設定的外部組態公用程式所存取。</span><span class="sxs-lookup"><span data-stu-id="d905e-125">These settings can be accessed by any external configuration utility that knows how to reference the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] registry settings.</span></span> <span data-ttu-id="d905e-126">您也可以使用 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 登錄編輯程式直接存取這些值來建立或修改這些設定。</span><span class="sxs-lookup"><span data-stu-id="d905e-126">These settings can also be created or modified by accessing the values directly by using the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Registry Editor.</span></span>  
  
<a name="disablehardwareacceleration"></a>   
## <a name="disable-hardware-acceleration-option"></a><span data-ttu-id="d905e-127">停用硬體加速選項</span><span class="sxs-lookup"><span data-stu-id="d905e-127">Disable Hardware Acceleration Option</span></span>  
  
|<span data-ttu-id="d905e-128">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="d905e-128">Registry key</span></span>|<span data-ttu-id="d905e-129">值類型</span><span class="sxs-lookup"><span data-stu-id="d905e-129">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|<span data-ttu-id="d905e-130">DWORD</span><span class="sxs-lookup"><span data-stu-id="d905e-130">DWORD</span></span>|  
  
 <span data-ttu-id="d905e-131">「停用硬體加速選項」  可讓您關閉硬體加速功能以進行偵錯和測試。</span><span class="sxs-lookup"><span data-stu-id="d905e-131">The **disable hardware acceleration option** enables you to turn off hardware acceleration for debugging and test purposes.</span></span> <span data-ttu-id="d905e-132">當您在應用程式中看到轉譯成品時，請嘗試關閉硬體加速功能。</span><span class="sxs-lookup"><span data-stu-id="d905e-132">When you see rendering artifacts in an application, try turning off hardware acceleration.</span></span> <span data-ttu-id="d905e-133">如果成品消失，問題可能在您的視訊驅動程式。</span><span class="sxs-lookup"><span data-stu-id="d905e-133">If the artifact disappears, the problem might be with your video driver.</span></span>  
  
 <span data-ttu-id="d905e-134">「停用硬體加速選項」  是指 0 或 1 的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="d905e-134">The **disable hardware acceleration option** is a DWORD value that is either 0 or 1.</span></span> <span data-ttu-id="d905e-135">值為 1 會停用硬體加速功能。</span><span class="sxs-lookup"><span data-stu-id="d905e-135">A value of 1 disables hardware acceleration.</span></span> <span data-ttu-id="d905e-136">值為 0 會啟用硬體加速功能，前提是系統符合硬體加速需求。如需詳細資訊，請參閱[圖形轉譯層](../advanced/graphics-rendering-tiers.md)。</span><span class="sxs-lookup"><span data-stu-id="d905e-136">A value of 0 enables hardware acceleration, provided the system meets hardware acceleration requirements; for more information, see [Graphics Rendering Tiers](../advanced/graphics-rendering-tiers.md).</span></span>  
  
<a name="maxmultisample"></a>   
## <a name="maximum-multisample-value"></a><span data-ttu-id="d905e-137">最大多重取樣值</span><span class="sxs-lookup"><span data-stu-id="d905e-137">Maximum Multisample Value</span></span>  
  
|<span data-ttu-id="d905e-138">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="d905e-138">Registry key</span></span>|<span data-ttu-id="d905e-139">值類型</span><span class="sxs-lookup"><span data-stu-id="d905e-139">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|<span data-ttu-id="d905e-140">DWORD</span><span class="sxs-lookup"><span data-stu-id="d905e-140">DWORD</span></span>|  
  
 <span data-ttu-id="d905e-141">**最大的多型值**可讓您調整立體內容的最大消除鋸齒量。</span><span class="sxs-lookup"><span data-stu-id="d905e-141">The **maximum multisample value** enables you to adjust the maximum amount of antialiasing of 3-D content.</span></span> <span data-ttu-id="d905e-142">使用此層級可停用中[!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]的立體消除鋸齒功能, 或在中[!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]加以啟用。</span><span class="sxs-lookup"><span data-stu-id="d905e-142">Use this level to disable 3-D antialiasing in [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] or enable it in [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span>  
  
 <span data-ttu-id="d905e-143">「最大多重取樣值」  是範圍介於 0 到 16 之間的 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="d905e-143">The **maximum multisample value** is a DWORD value that ranges from 0 to 16.</span></span> <span data-ttu-id="d905e-144">值為 0 指定應該停用 3D 內容的多重取樣消除鋸齒功能，而值為 16 會嘗試使用最多 16x 多重取樣消除鋸齒功能 (如果視訊卡支援的話)。</span><span class="sxs-lookup"><span data-stu-id="d905e-144">A value of 0 specifies that multisample antialiasing of 3-D content should be disabled, and a value of 16 will attempt to use up to 16x multisample antialiasing, if supported by the video card.</span></span> <span data-ttu-id="d905e-145">請注意, 在使用 XPDM 驅動程式的電腦上設定此登錄機碼值, 會導致應用程式使用大量額外的視訊記憶體, 降低3D 轉譯的效能, 而且可能會引進呈現錯誤和穩定性問題.</span><span class="sxs-lookup"><span data-stu-id="d905e-145">Beware that setting this registry key value on computers using XPDM drivers will cause applications to use a large amount of additional video memory, decrease the performance of 3-D rendering, and has the potential to introduce rendering errors and stability problems.</span></span>  
  
 <span data-ttu-id="d905e-146">未設定此登錄機碼時，XPDM 驅動程式的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 預設值為 0，而 WDDM 驅動程式的預設值為 4。</span><span class="sxs-lookup"><span data-stu-id="d905e-146">When this registry key is not set, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] defaults to 0 for XPDM drivers and 4 for WDDM drivers.</span></span>  
  
<a name="requiredvideodriverdatesetting"></a>   
## <a name="required-video-driver-date-setting"></a><span data-ttu-id="d905e-147">需要的視訊驅動程式日期設定</span><span class="sxs-lookup"><span data-stu-id="d905e-147">Required Video Driver Date Setting</span></span>  
  
|<span data-ttu-id="d905e-148">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="d905e-148">Registry key</span></span>|<span data-ttu-id="d905e-149">值類型</span><span class="sxs-lookup"><span data-stu-id="d905e-149">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|<span data-ttu-id="d905e-150">String</span><span class="sxs-lookup"><span data-stu-id="d905e-150">String</span></span>|  
  
 <span data-ttu-id="d905e-151">在 2004 年 11 月，[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 發行新版的驅動程式測試指導方針，在此日期後撰寫的驅動程式提供的穩定性更佳。</span><span class="sxs-lookup"><span data-stu-id="d905e-151">In November, 2004, [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] released a new version of the driver testing guidelines; the drivers written after this date offer better stability.</span></span> <span data-ttu-id="d905e-152">對於這些驅動程式，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 預設會使用硬體加速管線，並回到此日期之前發行的 XPDM 驅動程式軟體轉譯方式。</span><span class="sxs-lookup"><span data-stu-id="d905e-152">By default, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] will use the hardware acceleration pipeline for these drivers and will fall back to software rendering for XPDM drivers published before this date.</span></span>  
  
 <span data-ttu-id="d905e-153">「需要的視訊驅動程式日期設定」  可讓您指定 XPDM 驅動程式的替代最小日期。</span><span class="sxs-lookup"><span data-stu-id="d905e-153">The **required video driver date setting** enables you to specify an alternate minimum date for XPDM drivers.</span></span> <span data-ttu-id="d905e-154">如果您確定您的視訊驅動程式穩定度足以支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，您應該只指定 2004 年 11 月之前的日期。</span><span class="sxs-lookup"><span data-stu-id="d905e-154">You should only specify a date earlier than November, 2004 if you are confident that your video driver is stable enough to support [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="d905e-155">需要的視訊驅動程式設定會採用下列格式的字串︰</span><span class="sxs-lookup"><span data-stu-id="d905e-155">The required video driver setting takes a string of the following format:</span></span>  
  
| |  
|-|  
|<span data-ttu-id="d905e-156">*YYYY* `/` *MM* `/` *DD*</span><span class="sxs-lookup"><span data-stu-id="d905e-156">*YYYY* `/` *MM* `/` *DD*</span></span>|  
  
 <span data-ttu-id="d905e-157">其中 *YYYY* 是四位數年份，*MM* 是兩位數的月份，以及 *DD* 是兩位數的日期。</span><span class="sxs-lookup"><span data-stu-id="d905e-157">Where *YYYY* is the four-digit year, *MM* is the two-digit month, and *DD* is the two digit day.</span></span> <span data-ttu-id="d905e-158">未設定此值時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會使用 2004 年 11 月，做為其需要的視訊驅動程式日期。</span><span class="sxs-lookup"><span data-stu-id="d905e-158">When this value is unset, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uses November, 2004 as its required video driver date.</span></span>  
  
<a name="usereferencerasterizeroption"></a>   
## <a name="use-reference-rasterizer-option"></a><span data-ttu-id="d905e-159">使用軟體模擬轉譯器選項</span><span class="sxs-lookup"><span data-stu-id="d905e-159">Use Reference Rasterizer Option</span></span>  
  
|<span data-ttu-id="d905e-160">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="d905e-160">Registry key</span></span>|<span data-ttu-id="d905e-161">值類型</span><span class="sxs-lookup"><span data-stu-id="d905e-161">Value type</span></span>|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|<span data-ttu-id="d905e-162">DWORD</span><span class="sxs-lookup"><span data-stu-id="d905e-162">DWORD</span></span>|  
  
 <span data-ttu-id="d905e-163">**使用參考**轉譯器選項可讓您強制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]進入模擬的硬體轉譯模式以進行調試[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]程式: 進入硬體模式, 但使用 Microsoft Direct3D 參考軟體轉譯器 (d3dref9.dll)。而不是實際的硬體裝置。</span><span class="sxs-lookup"><span data-stu-id="d905e-163">The **use reference rasterizer option** enables you to force [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] into a simulated hardware rendering mode for debugging: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] goes into hardware mode, but uses the Microsoft Direct3D reference software rasterizer, d3dref9.dll, instead of an actual hardware device.</span></span>  
  
 <span data-ttu-id="d905e-164">軟體模擬轉譯器速度非常慢，但會略過您的視訊驅動程式，以避免發生任何由驅動程式問題造成的轉譯問題。</span><span class="sxs-lookup"><span data-stu-id="d905e-164">The reference rasterizer is very slow, but bypasses your video driver to avoid any rendering issues caused by driver problems.</span></span> <span data-ttu-id="d905e-165">因此，您可以使用軟體模擬轉譯器來判斷轉譯問題是否由視訊驅動程式造成。</span><span class="sxs-lookup"><span data-stu-id="d905e-165">For this reason, you can use the reference rasterizer to determine if rendering issues are caused by the video driver.</span></span> <span data-ttu-id="d905e-166">D3dref9.dll 檔案必須位於應用程式可存取的位置，例如在系統路徑中的任何位置，或在應用程式的本機目錄中。</span><span class="sxs-lookup"><span data-stu-id="d905e-166">The d3dref9.dll file must be in a location where the application can access it, such as in any location in the system path or in the local directory of the application.</span></span>  
  
 <span data-ttu-id="d905e-167">「使用軟體模擬轉譯器選項」  採用 DWORD 值。</span><span class="sxs-lookup"><span data-stu-id="d905e-167">The **use reference rasterizer option** takes a DWORD value.</span></span> <span data-ttu-id="d905e-168">值為 0 表示未使用軟體模擬轉譯器。</span><span class="sxs-lookup"><span data-stu-id="d905e-168">A value of 0 indicates that the reference rasterizer is not used.</span></span> <span data-ttu-id="d905e-169">任何其他非零的值都會強制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用軟體模擬轉譯器。</span><span class="sxs-lookup"><span data-stu-id="d905e-169">Any other non-zero value forces [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to use the reference rasterizer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d905e-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d905e-170">See also</span></span>

- [<span data-ttu-id="d905e-171">圖形轉譯層</span><span class="sxs-lookup"><span data-stu-id="d905e-171">Graphics Rendering Tiers</span></span>](../advanced/graphics-rendering-tiers.md)
- [<span data-ttu-id="d905e-172">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="d905e-172">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
