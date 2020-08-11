---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062417"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="fef94-101">非 Windows 平臺上沒有 A/W 尾碼探查</span><span class="sxs-lookup"><span data-stu-id="fef94-101">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="fef94-102">在 `A` `W` 非 Windows 平臺上進行 P/invoke 的探查期間，.net 執行時間不再為函式匯出名稱新增或尾碼。</span><span class="sxs-lookup"><span data-stu-id="fef94-102">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fef94-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="fef94-103">Version introduced</span></span>

<span data-ttu-id="fef94-104">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="fef94-104">5.0 Preview 4</span></span>

#### <a name="change-description"></a><span data-ttu-id="fef94-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="fef94-105">Change description</span></span>

<span data-ttu-id="fef94-106">[Windows 具有](/windows/win32/intl/conventions-for-function-prototypes)將 `A` 或尾碼新增至 Windows SDK 函式名稱的慣例 `W` ，分別對應至 Windows 字碼頁和 Unicode 版本。</span><span class="sxs-lookup"><span data-stu-id="fef94-106">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="fef94-107">在舊版的 .NET 中，CoreCLR 和 Mono 執行時間會在 `A` `W` *所有平臺上*的 P/invoke 的匯出探索期間，為匯出名稱新增或尾碼。</span><span class="sxs-lookup"><span data-stu-id="fef94-107">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="fef94-108">在 .NET 5.0 和更新版本中， `A` `W` *只有在 Windows 上*的匯出探索期間，會將或尾碼新增至匯出名稱。</span><span class="sxs-lookup"><span data-stu-id="fef94-108">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="fef94-109">在 Unix 平臺上，不會新增尾碼。</span><span class="sxs-lookup"><span data-stu-id="fef94-109">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="fef94-110">Windows 平臺上這兩個執行時間的語義會保持不變。</span><span class="sxs-lookup"><span data-stu-id="fef94-110">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fef94-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="fef94-111">Reason for change</span></span>

<span data-ttu-id="fef94-112">這是為了簡化跨平臺探查而進行的變更。</span><span class="sxs-lookup"><span data-stu-id="fef94-112">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="fef94-113">由於非 Windows 平臺不包含這個語義，因此不應該產生的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="fef94-113">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fef94-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="fef94-114">Recommended action</span></span>

<span data-ttu-id="fef94-115">若要減輕變更，您可以在非 Windows 平臺上手動新增所需的尾碼。</span><span class="sxs-lookup"><span data-stu-id="fef94-115">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="fef94-116">例如：</span><span class="sxs-lookup"><span data-stu-id="fef94-116">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a><span data-ttu-id="fef94-117">類別</span><span class="sxs-lookup"><span data-stu-id="fef94-117">Category</span></span>

<span data-ttu-id="fef94-118">Interop</span><span class="sxs-lookup"><span data-stu-id="fef94-118">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fef94-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fef94-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
