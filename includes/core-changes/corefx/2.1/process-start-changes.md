---
ms.openlocfilehash: 7c0930f6606aa96d2863dc740aef8e9cab724b37
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344890"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="1b44b-101">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="1b44b-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="1b44b-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 在 .NET Core 上有 `false` 的預設值。</span><span class="sxs-lookup"><span data-stu-id="1b44b-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="1b44b-103">在 .NET Framework 上，其預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="1b44b-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1b44b-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="1b44b-104">Change description</span></span>

<span data-ttu-id="1b44b-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 可讓您直接啟動應用程式（例如，使用啟動油漆的 `Process.Start("mspaint.exe")` 這類程式碼）。</span><span class="sxs-lookup"><span data-stu-id="1b44b-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="1b44b-106">如果 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 設定為 `true`，它也可讓您間接啟動相關聯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b44b-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="1b44b-107">在 .NET Framework 上，<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值是 `true`，這表示如果您已將 *.txt*檔案與該編輯器建立關聯，`Process.Start("mytextfile.txt")` 之類的程式碼就會啟動「記事本」。</span><span class="sxs-lookup"><span data-stu-id="1b44b-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="1b44b-108">若要防止在 .NET Framework 上間接啟動應用程式，您必須明確地將 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 設定為 [`false`]。</span><span class="sxs-lookup"><span data-stu-id="1b44b-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="1b44b-109">在 .NET Core 上，<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="1b44b-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="1b44b-110">這表示，當您呼叫 `Process.Start`時，預設不會啟動相關聯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b44b-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="1b44b-111">基於效能考慮，這項變更是在 .NET Core 中引進。</span><span class="sxs-lookup"><span data-stu-id="1b44b-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="1b44b-112">一般來說，<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 是用來直接啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b44b-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="1b44b-113">直接啟動應用程式不需要包含 Windows shell，而且會產生相關聯的效能成本。</span><span class="sxs-lookup"><span data-stu-id="1b44b-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="1b44b-114">為了讓此預設案例更快速，.NET Core 會將 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值變更為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1b44b-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="1b44b-115">您可以視需要選擇較慢的路徑。</span><span class="sxs-lookup"><span data-stu-id="1b44b-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1b44b-116">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1b44b-116">Version introduced</span></span>

<span data-ttu-id="1b44b-117">2.1</span><span class="sxs-lookup"><span data-stu-id="1b44b-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="1b44b-118">在舊版的 .NET Core 中，不會為 Windows 執行 `UseShellExecute`。</span><span class="sxs-lookup"><span data-stu-id="1b44b-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1b44b-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1b44b-119">Recommended action</span></span>

<span data-ttu-id="1b44b-120">如果您的應用程式依賴舊的行為，請呼叫 <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType>，並 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> 設定為 <xref:System.Diagnostics.ProcessStartInfo> 物件上的 `true`。</span><span class="sxs-lookup"><span data-stu-id="1b44b-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="1b44b-121">分類</span><span class="sxs-lookup"><span data-stu-id="1b44b-121">Category</span></span>

<span data-ttu-id="1b44b-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="1b44b-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b44b-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1b44b-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
