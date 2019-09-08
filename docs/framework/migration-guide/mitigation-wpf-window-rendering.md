---
title: 風險降低：WPF 視窗呈現
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13091c06561da24d2fc03f810fd8b8687b21d9a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789799"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="4b872-102">風險降低：WPF 視窗呈現</span><span class="sxs-lookup"><span data-stu-id="4b872-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="4b872-103">在 Windows 8 和更新版本中執行的 .NET Framework 4.6 多重監視器案例中，如果視窗擴充到單一顯示畫面之外，可呈現完整視窗而不會將其裁剪。</span><span class="sxs-lookup"><span data-stu-id="4b872-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="4b872-104">影響</span><span class="sxs-lookup"><span data-stu-id="4b872-104">Impact</span></span>

<span data-ttu-id="4b872-105">一般而言，當跨多個監視器時，不裁剪而呈現整個視窗是預期的行為。</span><span class="sxs-lookup"><span data-stu-id="4b872-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="4b872-106">不過，在 Windows 7 和舊版中，如果 WPF 視窗超過單一顯示畫面，會將其裁剪，主要是因為要在第二個監視器呈現部分視窗時，會造成顯著的效能影響。</span><span class="sxs-lookup"><span data-stu-id="4b872-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="4b872-107">在 Windows 8 和更新版本中，跨監視器呈現 WPF 視窗的影響涉及太多因素，因此無法精確量化。</span><span class="sxs-lookup"><span data-stu-id="4b872-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="4b872-108">在某些情況下，它仍可能會產生不良的效能影響，特別是針對執行使用大量圖形的應用程式並有跨監視器顯示視窗的使用者來說，更是明顯。</span><span class="sxs-lookup"><span data-stu-id="4b872-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="4b872-109">在其他情況下，您可能只需要 .NET Framework 版本之間保持一致的行為。</span><span class="sxs-lookup"><span data-stu-id="4b872-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="4b872-110">緩和</span><span class="sxs-lookup"><span data-stu-id="4b872-110">Mitigation</span></span>

<span data-ttu-id="4b872-111">您可以停用這項變更並還原為先前的行為，即可在超出單一顯示畫面時裁剪 WPF 視窗。</span><span class="sxs-lookup"><span data-stu-id="4b872-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="4b872-112">執行此作業的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="4b872-112">There are two ways to do this:</span></span>

- <span data-ttu-id="4b872-113">您可將 `<EnableMultiMonitorDisplayClipping>` 項目加入應用程式組態檔的 `<appSettings>` 區段，以針對在 Windows 8 或更新版本中執行的應用程式停用或啟用此行為。</span><span class="sxs-lookup"><span data-stu-id="4b872-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="4b872-114">例如，下列組態區段會停用呈現時不裁剪的行為：</span><span class="sxs-lookup"><span data-stu-id="4b872-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="4b872-115">`<EnableMultiMonitorDisplayClipping>` 組態設定可以為下列兩個值之一：</span><span class="sxs-lookup"><span data-stu-id="4b872-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="4b872-116">若要在呈現期間，啟用將視窗裁剪至監視器界限的行為，即為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4b872-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="4b872-117">若要在呈現期間，停用將視窗裁剪至監視器界限的行為，即為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4b872-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="4b872-118">方法是在應用程式啟動時，將 <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4b872-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b872-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b872-119">See also</span></span>

- [<span data-ttu-id="4b872-120">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="4b872-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
