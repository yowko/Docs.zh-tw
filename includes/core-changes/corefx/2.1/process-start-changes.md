---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031988"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="f93b9-101">UseShellExecute 預設值的變更</span><span class="sxs-lookup"><span data-stu-id="f93b9-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="f93b9-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值是 `false` 在 .Net Core 上。</span><span class="sxs-lookup"><span data-stu-id="f93b9-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="f93b9-103">在 .NET Framework 上，其預設值為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="f93b9-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f93b9-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="f93b9-104">Change description</span></span>

<span data-ttu-id="f93b9-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 可讓您直接啟動應用程式（例如，使用 `Process.Start("mspaint.exe")` 啟動油漆的程式碼）。</span><span class="sxs-lookup"><span data-stu-id="f93b9-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="f93b9-106">如果設定為，它也可讓您間接啟動相關聯的應用程式 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` 。</span><span class="sxs-lookup"><span data-stu-id="f93b9-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="f93b9-107">在 .NET Framework 上，的預設值 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 是 `true` ，這表示 `Process.Start("mytextfile.txt")` 如果您已使用該編輯器將 *.txt* 檔案相關聯，像這樣的程式碼將會啟動 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="f93b9-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="f93b9-108">若要避免在 .NET Framework 上間接啟動應用程式，您必須明確地將設定 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f93b9-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="f93b9-109">在 .NET Core 上，的預設值 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f93b9-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="f93b9-110">這表示當您呼叫時，關聯的應用程式預設不會啟動 `Process.Start` 。</span><span class="sxs-lookup"><span data-stu-id="f93b9-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="f93b9-111">基於效能考慮，.NET Core 引進了這項變更。</span><span class="sxs-lookup"><span data-stu-id="f93b9-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="f93b9-112">通常 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 是用來直接啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="f93b9-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="f93b9-113">直接啟動應用程式並不需要包含 Windows shell，並產生相關聯的效能成本。</span><span class="sxs-lookup"><span data-stu-id="f93b9-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="f93b9-114">為了讓此預設案例更快，.NET Core 會將的預設值變更 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f93b9-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="f93b9-115">您可以視需要加入宣告較慢的路徑。</span><span class="sxs-lookup"><span data-stu-id="f93b9-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f93b9-116">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f93b9-116">Version introduced</span></span>

<span data-ttu-id="f93b9-117">2.1</span><span class="sxs-lookup"><span data-stu-id="f93b9-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="f93b9-118">在舊版的 .NET Core 中， `UseShellExecute` 並未針對 Windows 執行。</span><span class="sxs-lookup"><span data-stu-id="f93b9-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f93b9-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f93b9-119">Recommended action</span></span>

<span data-ttu-id="f93b9-120">如果您的應用程式依賴舊的行為， <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> 請 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> 在物件上呼叫並將設定為 `true` <xref:System.Diagnostics.ProcessStartInfo> 。</span><span class="sxs-lookup"><span data-stu-id="f93b9-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="f93b9-121">類別</span><span class="sxs-lookup"><span data-stu-id="f93b9-121">Category</span></span>

<span data-ttu-id="f93b9-122">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="f93b9-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f93b9-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f93b9-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
