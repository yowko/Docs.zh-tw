---
title: 風險降低︰以指標為基礎的觸控及手寫筆支援
description: 瞭解針對以 .NET Framework 4.7 為目標的 WPF 應用程式啟用選用的 WPF 觸控/手寫筆堆疊的效果。
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475420"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="29fa6-103">風險降低︰以指標為基礎的觸控及手寫筆支援</span><span class="sxs-lookup"><span data-stu-id="29fa6-103">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="29fa6-104">以 .NET Framework 4.7 為目標，且從 Windows 10 建立者更新開始在 Windows 上執行的 WPF 應用程式，可以啟用選擇性 `WM_POINTER` 的 wpf 觸控/手寫筆堆疊。</span><span class="sxs-lookup"><span data-stu-id="29fa6-104">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="29fa6-105">影響</span><span class="sxs-lookup"><span data-stu-id="29fa6-105">Impact</span></span>

<span data-ttu-id="29fa6-106">開發人員若未明確地啟用以指標為基礎的觸控/手寫筆支援，應該不會看到任何 WPF 觸控/手寫筆行為的變更。</span><span class="sxs-lookup"><span data-stu-id="29fa6-106">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="29fa6-107">以下是選擇性的 `WM_POINTER` 式觸控/手寫筆堆疊目前已知的問題︰</span><span class="sxs-lookup"><span data-stu-id="29fa6-107">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="29fa6-108">不支援即時筆跡。</span><span class="sxs-lookup"><span data-stu-id="29fa6-108">No support for real-time inking.</span></span>

   <span data-ttu-id="29fa6-109">雖然筆跡和手寫筆外掛程式還能運作，但它們是在 UI 執行緒上處理，可能會導致效能不佳。</span><span class="sxs-lookup"><span data-stu-id="29fa6-109">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="29fa6-110">從觸控/手寫筆事件提升為滑鼠事件的變更，因而產生行為變更。</span><span class="sxs-lookup"><span data-stu-id="29fa6-110">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="29fa6-111">操作可能有不同的行為。</span><span class="sxs-lookup"><span data-stu-id="29fa6-111">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="29fa6-112">拖放動作無法對觸控輸入顯示適當的回應。</span><span class="sxs-lookup"><span data-stu-id="29fa6-112">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="29fa6-113">(這不影響手寫筆輸入。)</span><span class="sxs-lookup"><span data-stu-id="29fa6-113">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="29fa6-114">無法再針對觸控/手寫筆事件起始拖放動作。</span><span class="sxs-lookup"><span data-stu-id="29fa6-114">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="29fa6-115">這可能會導致應用程式停止回應，直到偵測到滑鼠輸入為止。</span><span class="sxs-lookup"><span data-stu-id="29fa6-115">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="29fa6-116">開發人員應改為從滑鼠事件起始拖放動作。</span><span class="sxs-lookup"><span data-stu-id="29fa6-116">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="29fa6-117">選擇加入 WM_POINTER 式觸控/手寫筆支援</span><span class="sxs-lookup"><span data-stu-id="29fa6-117">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="29fa6-118">想要啟用此堆疊的開發人員可以將下列新增至其應用程式的*app.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="29fa6-118">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="29fa6-119">移除此項目或將其值設為 `false` 可關閉這個選擇性的堆疊。</span><span class="sxs-lookup"><span data-stu-id="29fa6-119">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="29fa6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29fa6-120">See also</span></span>

- [<span data-ttu-id="29fa6-121">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="29fa6-121">Application compatibility</span></span>](application-compatibility.md)
