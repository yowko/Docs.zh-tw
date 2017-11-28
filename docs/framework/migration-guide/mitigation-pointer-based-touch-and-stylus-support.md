---
title: "風險降低︰以指標為基礎的觸控及手寫筆支援"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
caps.latest.revision: "2"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 053ff4c5fba7b4f2b5a4c29a35c954e888cb095a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="9caf3-102">風險降低︰以指標為基礎的觸控及手寫筆支援</span><span class="sxs-lookup"><span data-stu-id="9caf3-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="9caf3-103">以 .NET Framework 4.7 為目標並在從 Windows 10 Creators Update 開始的 Windows 系統上執行的 WPF 應用程式，可啟用選擇性的 `WM_POINTER` 式 WPF 觸控/手寫筆堆疊。</span><span class="sxs-lookup"><span data-stu-id="9caf3-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="9caf3-104">影響</span><span class="sxs-lookup"><span data-stu-id="9caf3-104">Impact</span></span>

<span data-ttu-id="9caf3-105">開發人員若未明確地啟用以指標為基礎的觸控/手寫筆支援，應該不會看到任何 WPF 觸控/手寫筆行為的變更。</span><span class="sxs-lookup"><span data-stu-id="9caf3-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="9caf3-106">以下是選擇性的 `WM_POINTER` 式觸控/手寫筆堆疊目前已知的問題︰</span><span class="sxs-lookup"><span data-stu-id="9caf3-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="9caf3-107">不支援即時筆跡。</span><span class="sxs-lookup"><span data-stu-id="9caf3-107">No support for real-time inking.</span></span>

   <span data-ttu-id="9caf3-108">雖然筆跡和手寫筆外掛程式還能運作，但它們是在 UI 執行緒上處理，可能會導致效能不佳。</span><span class="sxs-lookup"><span data-stu-id="9caf3-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="9caf3-109">從觸控/手寫筆事件提升為滑鼠事件的變更，因而產生行為變更。</span><span class="sxs-lookup"><span data-stu-id="9caf3-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="9caf3-110">操作可能有不同的行為。</span><span class="sxs-lookup"><span data-stu-id="9caf3-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="9caf3-111">拖放動作無法對觸控輸入顯示適當的回應。</span><span class="sxs-lookup"><span data-stu-id="9caf3-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="9caf3-112">(這不影響手寫筆輸入。)</span><span class="sxs-lookup"><span data-stu-id="9caf3-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="9caf3-113">無法再針對觸控/手寫筆事件起始拖放動作。</span><span class="sxs-lookup"><span data-stu-id="9caf3-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="9caf3-114">這可能會使應用程式停止回應到偵測到滑鼠輸入為止。</span><span class="sxs-lookup"><span data-stu-id="9caf3-114">This can potentially hang the application until mouse input is detected.</span></span> <span data-ttu-id="9caf3-115">開發人員應改為從滑鼠事件起始拖放動作。</span><span class="sxs-lookup"><span data-stu-id="9caf3-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="9caf3-116">選擇加入 WM_POINTER 式觸控/手寫筆支援</span><span class="sxs-lookup"><span data-stu-id="9caf3-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="9caf3-117">想要啟用此堆疊的開發人員可以將以下內容加入至他們應用程式的 app.config 檔案︰</span><span class="sxs-lookup"><span data-stu-id="9caf3-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="9caf3-118">移除此項目或將其值設為 `false` 可關閉這個選擇性的堆疊。</span><span class="sxs-lookup"><span data-stu-id="9caf3-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="9caf3-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="9caf3-119">See also</span></span>

[<span data-ttu-id="9caf3-120">.NET Framework 4.7 中的重定目標變更</span><span class="sxs-lookup"><span data-stu-id="9caf3-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
