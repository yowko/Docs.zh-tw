---
ms.openlocfilehash: dcc64fe651b219ff1416c0afcdb4c6d275160f4b
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97911651"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="f7fba-101">UseShellExecute 預設值的變更</span><span class="sxs-lookup"><span data-stu-id="f7fba-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="f7fba-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值是 `false` 在 .Net Core 上。</span><span class="sxs-lookup"><span data-stu-id="f7fba-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="f7fba-103">在 .NET Framework 上，其預設值為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f7fba-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f7fba-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="f7fba-104">Change description</span></span>

<span data-ttu-id="f7fba-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 可讓您直接啟動應用程式（例如，使用 `Process.Start("mspaint.exe")` 啟動油漆的程式碼）。</span><span class="sxs-lookup"><span data-stu-id="f7fba-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="f7fba-106">如果設定為，它也可讓您間接啟動相關聯的應用程式 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` 。</span><span class="sxs-lookup"><span data-stu-id="f7fba-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="f7fba-107">在 .NET Framework 上，的預設值 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 是 `true` ，這表示 `Process.Start("mytextfile.txt")` 如果您已使用該編輯器將 *.txt* 檔案相關聯，像這樣的程式碼將會啟動 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="f7fba-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="f7fba-108">若要避免在 .NET Framework 上間接啟動應用程式，您必須明確地將設定 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f7fba-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="f7fba-109">在 .NET Core 上，的預設值 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f7fba-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="f7fba-110">這表示當您呼叫時，關聯的應用程式預設不會啟動 `Process.Start` 。</span><span class="sxs-lookup"><span data-stu-id="f7fba-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="f7fba-111">上的下列屬性 <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> 只有在為時才能正常運作 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` ：</span><span class="sxs-lookup"><span data-stu-id="f7fba-111">The following properties on <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> are only functional when <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`:</span></span>

- <xref:System.Diagnostics.ProcessStartInfo.CreateNoWindow?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.ErrorDialog?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.Verb?displayProperty=nameWithType>
- <span data-ttu-id="f7fba-112"><xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7fba-112"><xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f7fba-113">基於效能考慮，.NET Core 引進了這項變更。</span><span class="sxs-lookup"><span data-stu-id="f7fba-113">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="f7fba-114">通常 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 是用來直接啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="f7fba-114">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="f7fba-115">直接啟動應用程式並不需要包含 Windows shell，並產生相關聯的效能成本。</span><span class="sxs-lookup"><span data-stu-id="f7fba-115">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="f7fba-116">為了讓此預設案例更快，.NET Core 會將的預設值變更 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f7fba-116">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="f7fba-117">您可以視需要加入宣告較慢的路徑。</span><span class="sxs-lookup"><span data-stu-id="f7fba-117">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f7fba-118">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f7fba-118">Version introduced</span></span>

<span data-ttu-id="f7fba-119">2.1</span><span class="sxs-lookup"><span data-stu-id="f7fba-119">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="f7fba-120">在舊版的 .NET Core 中， `UseShellExecute` 並未針對 Windows 執行。</span><span class="sxs-lookup"><span data-stu-id="f7fba-120">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f7fba-121">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f7fba-121">Recommended action</span></span>

<span data-ttu-id="f7fba-122">如果您的應用程式依賴舊的行為， <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> 請 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> 在物件上呼叫並將設定為 `true` <xref:System.Diagnostics.ProcessStartInfo> 。</span><span class="sxs-lookup"><span data-stu-id="f7fba-122">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="f7fba-123">類別</span><span class="sxs-lookup"><span data-stu-id="f7fba-123">Category</span></span>

<span data-ttu-id="f7fba-124">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="f7fba-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f7fba-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f7fba-125">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
