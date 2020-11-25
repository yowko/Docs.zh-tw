---
title: 重大變更：非 Windows 平臺上沒有 A/W 尾碼探查
description: 瞭解 .NET 5.0 中的 interop 重大變更，在非 Windows 平臺上探查 P/Invoke 期間，不會再將尾碼新增至函式匯出名稱。
ms.date: 08/13/2020
ms.openlocfilehash: a4c612a81796faf80fa257df21232a54f7b95431
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760717"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="ad800-103">非 Windows 平臺上沒有任何/W 尾碼探查</span><span class="sxs-lookup"><span data-stu-id="ad800-103">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="ad800-104">在 `A` `W` 非 Windows 平臺上進行 P/invoke 探查時，.net 執行時間不會再將或後置詞新增至函式匯出名稱。</span><span class="sxs-lookup"><span data-stu-id="ad800-104">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ad800-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ad800-105">Version introduced</span></span>

<span data-ttu-id="ad800-106">5.0</span><span class="sxs-lookup"><span data-stu-id="ad800-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="ad800-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="ad800-107">Change description</span></span>

<span data-ttu-id="ad800-108">[Windows 的慣例是](/windows/win32/intl/conventions-for-function-prototypes) 將或後置詞新增 `A` 至 Windows SDK 函式 `W` 名稱，分別對應至 Windows 字碼頁和 Unicode 版本。</span><span class="sxs-lookup"><span data-stu-id="ad800-108">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="ad800-109">在舊版的 .NET 中，CoreCLR 和 Mono 執行時間會在 `A` `W` 匯出探索期間針對 *所有平臺上* 的 P/invoke，將或後置詞新增至匯出名稱。</span><span class="sxs-lookup"><span data-stu-id="ad800-109">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="ad800-110">在 .NET 5.0 和更新版本中， `A` `W` 只會在 *Windows 上* 的匯出探索期間，將或後置詞新增至匯出名稱。</span><span class="sxs-lookup"><span data-stu-id="ad800-110">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="ad800-111">在 Unix 平臺上，不會新增尾碼。</span><span class="sxs-lookup"><span data-stu-id="ad800-111">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="ad800-112">Windows 平臺上兩個執行時間的語法會保持不變。</span><span class="sxs-lookup"><span data-stu-id="ad800-112">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ad800-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ad800-113">Reason for change</span></span>

<span data-ttu-id="ad800-114">這是為了簡化跨平臺探查所進行的變更。</span><span class="sxs-lookup"><span data-stu-id="ad800-114">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="ad800-115">由於非 Windows 的平臺不包含此語義，因此不應該產生的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ad800-115">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ad800-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ad800-116">Recommended action</span></span>

<span data-ttu-id="ad800-117">若要減輕變更，您可以在非 Windows 平臺上手動新增所需的尾碼。</span><span class="sxs-lookup"><span data-stu-id="ad800-117">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="ad800-118">例如：</span><span class="sxs-lookup"><span data-stu-id="ad800-118">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a><span data-ttu-id="ad800-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ad800-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
