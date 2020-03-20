---
title: 風險降低︰以指標為基礎的觸控及手寫筆支援
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77094471"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="1af79-102">風險降低︰以指標為基礎的觸控及手寫筆支援</span><span class="sxs-lookup"><span data-stu-id="1af79-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="1af79-103">面向 .NET 框架 4.7 並在 Windows 上運行的 WPF 應用程式從 Windows 10`WM_POINTER`建立者更新開始，可以啟用可選的基於 WPF 的觸摸/手寫堆疊。</span><span class="sxs-lookup"><span data-stu-id="1af79-103">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="1af79-104">影響</span><span class="sxs-lookup"><span data-stu-id="1af79-104">Impact</span></span>

<span data-ttu-id="1af79-105">開發人員若未明確地啟用以指標為基礎的觸控/手寫筆支援，應該不會看到任何 WPF 觸控/手寫筆行為的變更。</span><span class="sxs-lookup"><span data-stu-id="1af79-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="1af79-106">以下是選擇性的 `WM_POINTER` 式觸控/手寫筆堆疊目前已知的問題︰</span><span class="sxs-lookup"><span data-stu-id="1af79-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="1af79-107">不支援即時筆跡。</span><span class="sxs-lookup"><span data-stu-id="1af79-107">No support for real-time inking.</span></span>

   <span data-ttu-id="1af79-108">雖然筆跡和手寫筆外掛程式還能運作，但它們是在 UI 執行緒上處理，可能會導致效能不佳。</span><span class="sxs-lookup"><span data-stu-id="1af79-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="1af79-109">從觸控/手寫筆事件提升為滑鼠事件的變更，因而產生行為變更。</span><span class="sxs-lookup"><span data-stu-id="1af79-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="1af79-110">操作可能有不同的行為。</span><span class="sxs-lookup"><span data-stu-id="1af79-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="1af79-111">拖放動作無法對觸控輸入顯示適當的回應。</span><span class="sxs-lookup"><span data-stu-id="1af79-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="1af79-112">(這不影響手寫筆輸入。)</span><span class="sxs-lookup"><span data-stu-id="1af79-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="1af79-113">無法再針對觸控/手寫筆事件起始拖放動作。</span><span class="sxs-lookup"><span data-stu-id="1af79-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="1af79-114">這可能會導致應用程式停止回應，直到偵測到滑鼠輸入為止。</span><span class="sxs-lookup"><span data-stu-id="1af79-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="1af79-115">開發人員應改為從滑鼠事件起始拖放動作。</span><span class="sxs-lookup"><span data-stu-id="1af79-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="1af79-116">選擇加入 WM_POINTER 式觸控/手寫筆支援</span><span class="sxs-lookup"><span data-stu-id="1af79-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="1af79-117">希望啟用此堆疊的開發人員可以向其應用程式的*app.config*檔添加以下內容。</span><span class="sxs-lookup"><span data-stu-id="1af79-117">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="1af79-118">移除此項目或將其值設為 `false` 可關閉這個選擇性的堆疊。</span><span class="sxs-lookup"><span data-stu-id="1af79-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="1af79-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1af79-119">See also</span></span>

- [<span data-ttu-id="1af79-120">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="1af79-120">Application compatibility</span></span>](application-compatibility.md)
