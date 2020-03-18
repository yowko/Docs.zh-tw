---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449387"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="abce2-101">使用殼牌執行的預設值更改</span><span class="sxs-lookup"><span data-stu-id="abce2-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="abce2-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>在 .NET `false` Core 上具有預設值。</span><span class="sxs-lookup"><span data-stu-id="abce2-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="abce2-103">在 .NET 框架上，其`true`預設值為 。</span><span class="sxs-lookup"><span data-stu-id="abce2-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="abce2-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="abce2-104">Change description</span></span>

<span data-ttu-id="abce2-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>允許您直接啟動應用程式，例如，使用諸如啟動"畫圖"`Process.Start("mspaint.exe")`等代碼。</span><span class="sxs-lookup"><span data-stu-id="abce2-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="abce2-106">它還允許您間接啟動關聯的應用程式，如果<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="abce2-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="abce2-107">在 .NET Framework 上，<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>的`true`預設值為 ，這意味著如果`Process.Start("mytextfile.txt")`將 *.txt*檔與該編輯器關聯，則如將啟動記事本等代碼。</span><span class="sxs-lookup"><span data-stu-id="abce2-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="abce2-108">為了防止在 .NET 框架上間接啟動應用，必須顯式設置為<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>`false`。</span><span class="sxs-lookup"><span data-stu-id="abce2-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="abce2-109">在 .NET 核心上，的<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>預設值`false`為 。</span><span class="sxs-lookup"><span data-stu-id="abce2-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="abce2-110">這意味著預設情況下，在調用`Process.Start`時不會啟動關聯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="abce2-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="abce2-111">出於性能原因，在 .NET Core 中引入了此更改。</span><span class="sxs-lookup"><span data-stu-id="abce2-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="abce2-112">通常，<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>用於直接啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="abce2-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="abce2-113">直接啟動應用不需要涉及 Windows 外殼並產生相關的性能成本。</span><span class="sxs-lookup"><span data-stu-id="abce2-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="abce2-114">為了使此預設案例更快，.NET Core 將 預設值<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>更改為`false`。</span><span class="sxs-lookup"><span data-stu-id="abce2-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="abce2-115">如果需要，您可以加入宣告較慢的路徑。</span><span class="sxs-lookup"><span data-stu-id="abce2-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="abce2-116">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="abce2-116">Version introduced</span></span>

<span data-ttu-id="abce2-117">2.1</span><span class="sxs-lookup"><span data-stu-id="abce2-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="abce2-118">在早期版本的 .NET Core`UseShellExecute`中，未為 Windows 實現。</span><span class="sxs-lookup"><span data-stu-id="abce2-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="abce2-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="abce2-119">Recommended action</span></span>

<span data-ttu-id="abce2-120">如果應用依賴于舊行為，請<xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType>調用物件<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute>`true`上的<xref:System.Diagnostics.ProcessStartInfo>"設置為"調用。</span><span class="sxs-lookup"><span data-stu-id="abce2-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="abce2-121">類別</span><span class="sxs-lookup"><span data-stu-id="abce2-121">Category</span></span>

<span data-ttu-id="abce2-122">CoreFx</span><span class="sxs-lookup"><span data-stu-id="abce2-122">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abce2-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="abce2-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
