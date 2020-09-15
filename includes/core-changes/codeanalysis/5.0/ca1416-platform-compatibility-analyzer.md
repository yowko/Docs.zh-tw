---
ms.openlocfilehash: e3c9f23ca73ed9b85d09680ec15251ebe02c7f8e
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065140"
---
### <a name="ca1416-platform-compatibility"></a><span data-ttu-id="c0d94-101">CA1416：平臺相容性</span><span class="sxs-lookup"><span data-stu-id="c0d94-101">CA1416: Platform compatibility</span></span>

<span data-ttu-id="c0d94-102">預設會啟用 .NET 程式碼分析器規則 CA1416，從 .NET 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="c0d94-102">.NET code analyzer rule CA1416 is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="c0d94-103">它會從未驗證作業系統的呼叫網站，產生對平臺特定 Api 呼叫的組建警告。</span><span class="sxs-lookup"><span data-stu-id="c0d94-103">It produces a build warning for calls to platform-specific APIs from call sites that don't verify the operating system.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c0d94-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="c0d94-104">Change description</span></span>

<span data-ttu-id="c0d94-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="c0d94-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="c0d94-106">預設會啟用這些規則中的數個，包括 CA1416。</span><span class="sxs-lookup"><span data-stu-id="c0d94-106">Several of these rules are enabled, by default, including CA1416.</span></span> <span data-ttu-id="c0d94-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="c0d94-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span> <span data-ttu-id="c0d94-108">當您從平臺內容未通過驗證的位置使用平臺特定 Api 時，規則 CA1416 會通知您。</span><span class="sxs-lookup"><span data-stu-id="c0d94-108">Rule CA1416 informs you when you're using platform-specific APIs from places where the platform context isn't verified.</span></span>

<span data-ttu-id="c0d94-109">「平臺相容性分析器」規則 CA1416 與 .NET 5.0 的一些新功能搭配使用。</span><span class="sxs-lookup"><span data-stu-id="c0d94-109">Rule CA1416, the platform compatibility analyzer, works hand-in-hand with some other features that are new in .NET 5.0.</span></span> <span data-ttu-id="c0d94-110">.NET 5.0 引進 `SupportedOSPlatformAttribute` 和 `UnsupportedOSPlatformAttribute` 屬性 (<xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute> 在先前的預覽版本中) ，可讓您指定不支援 API 的平臺。 *is* *isn't*</span><span class="sxs-lookup"><span data-stu-id="c0d94-110">.NET 5.0 introduces `SupportedOSPlatformAttribute` and `UnsupportedOSPlatformAttribute` attributes (named <xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> and <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute> in an earlier preview release), which let you specify the platforms that an API *is* or *isn't* supported on.</span></span> <span data-ttu-id="c0d94-111">如果沒有這些屬性，則會假設所有平臺都支援 API。</span><span class="sxs-lookup"><span data-stu-id="c0d94-111">In the absence of these attributes, an API is assumed to be supported on all platforms.</span></span> <span data-ttu-id="c0d94-112">這些屬性已套用至核心 .NET 程式庫中的平臺特定 Api。</span><span class="sxs-lookup"><span data-stu-id="c0d94-112">These attributes have been applied to platform-specific APIs in the core .NET libraries.</span></span>

<span data-ttu-id="c0d94-113">在以無法使用其所使用之 Api 的平臺為目標的專案中，規則 CA1416 會旗標平臺特定的 API 呼叫，其中不會驗證平臺內容。</span><span class="sxs-lookup"><span data-stu-id="c0d94-113">In projects that target platforms for which APIs that they use aren't available, rule CA1416 flags any platform-specific API call where the platform context isn't verified.</span></span> <span data-ttu-id="c0d94-114">大部分現在以和屬性裝飾的 Api，在 `SupportedOSPlatformAttribute` `UnsupportedOSPlatformAttribute` 不受支援的作業系統上叫用時，會擲回 <xref:System.PlatformNotSupportedException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0d94-114">Most of the APIs that are now decorated with the `SupportedOSPlatformAttribute` and `UnsupportedOSPlatformAttribute` attributes throw <xref:System.PlatformNotSupportedException> exceptions when they're invoked on an unsupported operating system.</span></span> <span data-ttu-id="c0d94-115">既然這些 Api 已標示為平臺特定，規則 CA1416 可協助您藉 <xref:System.PlatformNotSupportedException> 由將作業系統檢查新增至呼叫位置，以防止執行時間例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0d94-115">Now that these APIs are marked as platform-specific, rule CA1416 helps you prevent run-time <xref:System.PlatformNotSupportedException> exceptions by adding OS checks to your call sites.</span></span>

#### <a name="examples"></a><span data-ttu-id="c0d94-116">範例</span><span class="sxs-lookup"><span data-stu-id="c0d94-116">Examples</span></span>

- <span data-ttu-id="c0d94-117"><xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>只有在 Windows 上才支援此方法， (它是以 `[SupportedOSPlatform("windows")]`) 裝飾。</span><span class="sxs-lookup"><span data-stu-id="c0d94-117">The <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> method is only supported on Windows (it's decorated with `[SupportedOSPlatform("windows")]`).</span></span> <span data-ttu-id="c0d94-118">如果專案的 [目標](../../../../docs/standard/frameworks.md)為 `net5.0` (但未) ，則下列程式碼會在組建階段產生 CA1416 警告 `net5.0-windows` 。</span><span class="sxs-lookup"><span data-stu-id="c0d94-118">The following code will produce a CA1416 warning at build time if the project [targets](../../../../docs/standard/frameworks.md) `net5.0` (but not `net5.0-windows`).</span></span> <span data-ttu-id="c0d94-119">您可以採取的動作來避免警告，請參閱 [建議的動作](#recommended-action)。</span><span class="sxs-lookup"><span data-stu-id="c0d94-119">For actions you can take to avoid the warning, see [Recommended action](#recommended-action).</span></span>

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <span data-ttu-id="c0d94-120">在 <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> 瀏覽器中不支援此方法 (它是以 `[UnsupportedOSPlatform("browser")]`) 裝飾。</span><span class="sxs-lookup"><span data-stu-id="c0d94-120">The <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> method is not supported in the browser (it's decorated with `[UnsupportedOSPlatform("browser")]`).</span></span> <span data-ttu-id="c0d94-121">如果專案使用 Blazor WebAssembly SDK (`<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">`) 或包含 `browser` 在專案檔中) 支援的平臺 (，則下列程式碼會在組建階段產生 CA1416 警告 `<SupportedPlatform Include="browser" />` 。</span><span class="sxs-lookup"><span data-stu-id="c0d94-121">The following code will produce a CA1416 warning at build time if the project uses the Blazor WebAssembly SDK (`<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">`) or includes `browser` as a supported platform (`<SupportedPlatform Include="browser" />`) in the project file.</span></span>

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

#### <a name="version-introduced"></a><span data-ttu-id="c0d94-122">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c0d94-122">Version introduced</span></span>

<span data-ttu-id="c0d94-123">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="c0d94-123">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c0d94-124">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c0d94-124">Recommended action</span></span>

<span data-ttu-id="c0d94-125">確定只有在程式碼在適當的平臺上執行時，才會呼叫平臺特定的 Api。</span><span class="sxs-lookup"><span data-stu-id="c0d94-125">Ensure that platform-specific APIs are only called when the code is running on an appropriate platform.</span></span> <span data-ttu-id="c0d94-126">您可以使用類別中的其中一個方法來檢查目前的作業系統 `Is<Platform>` <xref:System.OperatingSystem?displayProperty=nameWithType> ，例如，在 `System.OperatingSystem.IsWindows()` 呼叫平臺特定 API 之前。</span><span class="sxs-lookup"><span data-stu-id="c0d94-126">You can check the current operating system using one of the `Is<Platform>` methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class, for example, `System.OperatingSystem.IsWindows()`, before calling a platform-specific API.</span></span>

<span data-ttu-id="c0d94-127">您可以 `Is<Platform>` 在語句的條件中使用其中一個方法 `if` ：</span><span class="sxs-lookup"><span data-stu-id="c0d94-127">You can use one of the `Is<Platform>` methods in the condition of an `if` statement:</span></span>

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

<span data-ttu-id="c0d94-128">或者，如果您不想要在執行時間額外負荷額外的 `if` 語句，請 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> 改為呼叫：</span><span class="sxs-lookup"><span data-stu-id="c0d94-128">Or, if you don't want the overhead of an additional `if` statement at run time, call <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> instead:</span></span>

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="c0d94-129">您也可以將 API 標示為平臺特定，在這種情況下，檢查需求的負擔會落在您的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="c0d94-129">You can also mark your API as platform-specific, in which case the burden of checking requirements falls on your callers.</span></span> <span data-ttu-id="c0d94-130">您可以標記特定的方法或類型或整個元件。</span><span class="sxs-lookup"><span data-stu-id="c0d94-130">You can mark specific methods or types or an entire assembly.</span></span>

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="c0d94-131">如果您不想要修正所有的呼叫位置，可以選擇下列其中一個選項來抑制警告：</span><span class="sxs-lookup"><span data-stu-id="c0d94-131">If you don't want to fix all your call sites, you can choose one of the following options to suppress the warning:</span></span>

- <span data-ttu-id="c0d94-132">若要隱藏規則 CA1416，您可以使用 `#pragma` 或 [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) 編譯器旗標，或在 editorconfig 檔案中 [將規則的嚴重性設定](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) 為 `none` 。</span><span class="sxs-lookup"><span data-stu-id="c0d94-132">To suppress rule CA1416, you can do so using `#pragma` or the [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) compiler flag, or by [setting the rule's severity](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) to `none` in an .editorconfig file.</span></span>

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- <span data-ttu-id="c0d94-133">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="c0d94-133">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="c0d94-134">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="c0d94-134">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="c0d94-135">類別</span><span class="sxs-lookup"><span data-stu-id="c0d94-135">Category</span></span>

- <span data-ttu-id="c0d94-136">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="c0d94-136">Code analysis</span></span>
- <span data-ttu-id="c0d94-137">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="c0d94-137">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c0d94-138">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c0d94-138">Affected APIs</span></span>

<span data-ttu-id="c0d94-139">針對 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="c0d94-139">For Windows platform:</span></span>

- <span data-ttu-id="c0d94-140">所有列出的 Api <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> 。</span><span class="sxs-lookup"><span data-stu-id="c0d94-140">All APIs listed at <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>.</span></span>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

<span data-ttu-id="c0d94-141">針對 Blazor WebAssembly platform：</span><span class="sxs-lookup"><span data-stu-id="c0d94-141">For Blazor WebAssembly platform:</span></span>

- <span data-ttu-id="c0d94-142">所有列出的 Api <https://github.com/dotnet/runtime/issues/41087> 。</span><span class="sxs-lookup"><span data-stu-id="c0d94-142">All APIs listed at <https://github.com/dotnet/runtime/issues/41087>.</span></span>

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a><span data-ttu-id="c0d94-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0d94-143">See also</span></span>

- [<span data-ttu-id="c0d94-144">.NET API 分析器</span><span class="sxs-lookup"><span data-stu-id="c0d94-144">.NET API analyzer</span></span>](../../../../docs/standard/analyzers/api-analyzer.md)
