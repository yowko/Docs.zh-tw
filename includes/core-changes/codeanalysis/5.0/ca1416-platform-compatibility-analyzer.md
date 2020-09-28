---
ms.openlocfilehash: 4a7616d2ffaabab5279342ebc1082c93a174a52d
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406165"
---
### <a name="ca1416-platform-compatibility"></a><span data-ttu-id="d6453-101">CA1416：平臺相容性</span><span class="sxs-lookup"><span data-stu-id="d6453-101">CA1416: Platform compatibility</span></span>

<span data-ttu-id="d6453-102">預設會啟用 .NET 程式碼分析器規則 [CA1416](/visualstudio/code-quality/ca1416) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="d6453-102">.NET code analyzer rule [CA1416](/visualstudio/code-quality/ca1416) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="d6453-103">它會從未驗證作業系統的呼叫網站，產生對平臺特定 Api 呼叫的組建警告。</span><span class="sxs-lookup"><span data-stu-id="d6453-103">It produces a build warning for calls to platform-specific APIs from call sites that don't verify the operating system.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d6453-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="d6453-104">Change description</span></span>

<span data-ttu-id="d6453-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="d6453-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="d6453-106">預設會啟用這些規則中的數個，包括 [CA1416](/visualstudio/code-quality/ca1416)。</span><span class="sxs-lookup"><span data-stu-id="d6453-106">Several of these rules are enabled, by default, including [CA1416](/visualstudio/code-quality/ca1416).</span></span> <span data-ttu-id="d6453-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="d6453-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span> <span data-ttu-id="d6453-108">當您從平臺內容未通過驗證的位置使用平臺特定 Api 時，規則 CA1416 會通知您。</span><span class="sxs-lookup"><span data-stu-id="d6453-108">Rule CA1416 informs you when you're using platform-specific APIs from places where the platform context isn't verified.</span></span>

<span data-ttu-id="d6453-109">「平臺相容性分析器」規則 [CA1416](/visualstudio/code-quality/ca1416)與 .net 5.0 的一些新功能搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d6453-109">Rule [CA1416](/visualstudio/code-quality/ca1416), the platform compatibility analyzer, works hand-in-hand with some other features that are new in .NET 5.0.</span></span> <span data-ttu-id="d6453-110">.NET 5.0 引進了 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 和 <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> ，可讓您指定不支援 API 的平臺*is* 。 *isn't*</span><span class="sxs-lookup"><span data-stu-id="d6453-110">.NET 5.0 introduces the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>, which let you specify the platforms that an API *is* or *isn't* supported on.</span></span> <span data-ttu-id="d6453-111">如果沒有這些屬性，則會假設所有平臺都支援 API。</span><span class="sxs-lookup"><span data-stu-id="d6453-111">In the absence of these attributes, an API is assumed to be supported on all platforms.</span></span> <span data-ttu-id="d6453-112">這些屬性已套用至核心 .NET 程式庫中的平臺特定 Api。</span><span class="sxs-lookup"><span data-stu-id="d6453-112">These attributes have been applied to platform-specific APIs in the core .NET libraries.</span></span>

<span data-ttu-id="d6453-113">在以無法使用其所使用之 Api 的平臺為目標的專案中，規則 [CA1416](/visualstudio/code-quality/ca1416) 會旗標平臺特定的 api 呼叫，其中不會驗證平臺內容。</span><span class="sxs-lookup"><span data-stu-id="d6453-113">In projects that target platforms for which APIs that they use aren't available, rule [CA1416](/visualstudio/code-quality/ca1416) flags any platform-specific API call where the platform context isn't verified.</span></span> <span data-ttu-id="d6453-114">大部分現在以和屬性裝飾的 Api，在 <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> 不受支援的作業系統上叫用時，會擲回 <xref:System.PlatformNotSupportedException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d6453-114">Most of the APIs that are now decorated with the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> attributes throw <xref:System.PlatformNotSupportedException> exceptions when they're invoked on an unsupported operating system.</span></span> <span data-ttu-id="d6453-115">既然這些 Api 已標示為平臺特定，規則 [CA1416](/visualstudio/code-quality/ca1416) 可協助您藉 <xref:System.PlatformNotSupportedException> 由將作業系統檢查新增至呼叫位置，以防止執行時間例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d6453-115">Now that these APIs are marked as platform-specific, rule [CA1416](/visualstudio/code-quality/ca1416) helps you prevent run-time <xref:System.PlatformNotSupportedException> exceptions by adding OS checks to your call sites.</span></span>

#### <a name="examples"></a><span data-ttu-id="d6453-116">範例</span><span class="sxs-lookup"><span data-stu-id="d6453-116">Examples</span></span>

- <span data-ttu-id="d6453-117"><xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>只有在 Windows 上才支援方法，並以裝飾 `[SupportedOSPlatform("windows")]` 。</span><span class="sxs-lookup"><span data-stu-id="d6453-117">The <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> method is only supported on Windows and is decorated with `[SupportedOSPlatform("windows")]`.</span></span> <span data-ttu-id="d6453-118">如果專案的 [目標](../../../../docs/standard/frameworks.md)為 `net5.0` (但未) ，則下列程式碼會在組建階段產生 CA1416 警告 `net5.0-windows` 。</span><span class="sxs-lookup"><span data-stu-id="d6453-118">The following code will produce a CA1416 warning at build time if the project [targets](../../../../docs/standard/frameworks.md) `net5.0` (but not `net5.0-windows`).</span></span> <span data-ttu-id="d6453-119">您可以採取的動作來避免警告，請參閱 [建議的動作](#recommended-action)。</span><span class="sxs-lookup"><span data-stu-id="d6453-119">For actions you can take to avoid the warning, see [Recommended action](#recommended-action).</span></span>

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <span data-ttu-id="d6453-120">在 <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> 瀏覽器中不支援方法，並以裝飾 `[UnsupportedOSPlatform("browser")]` 。</span><span class="sxs-lookup"><span data-stu-id="d6453-120">The <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> method is not supported in the browser and is decorated with `[UnsupportedOSPlatform("browser")]`.</span></span> <span data-ttu-id="d6453-121">如果專案支援瀏覽器平臺，下列程式碼會在組建階段產生 CA1416 警告。</span><span class="sxs-lookup"><span data-stu-id="d6453-121">The following code will produce a CA1416 warning at build time if the project supports the browser platform.</span></span>

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

  > [!TIP]
  >
  > - <span data-ttu-id="d6453-122">Blazor WebAssembly projects 和 Razor 類別庫專案會自動包含瀏覽器支援。</span><span class="sxs-lookup"><span data-stu-id="d6453-122">Blazor WebAssembly projects and Razor class library projects include browser support automatically.</span></span>
  > - <span data-ttu-id="d6453-123">若要以手動方式將瀏覽器新增為專案的支援平臺，請將下列專案新增至您的專案檔：</span><span class="sxs-lookup"><span data-stu-id="d6453-123">To manually add the browser as a supported platform for your project, add the following entry to your project file:</span></span>
  >
  >  ```xml
  >  <ItemGroup>
  >    <SupportedPlatform Include="browser" />
  >  </ItemGroup>
  >  ```

#### <a name="version-introduced"></a><span data-ttu-id="d6453-124">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d6453-124">Version introduced</span></span>

<span data-ttu-id="d6453-125">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="d6453-125">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d6453-126">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d6453-126">Recommended action</span></span>

<span data-ttu-id="d6453-127">確定只有在程式碼在適當的平臺上執行時，才會呼叫平臺特定的 Api。</span><span class="sxs-lookup"><span data-stu-id="d6453-127">Ensure that platform-specific APIs are only called when the code is running on an appropriate platform.</span></span> <span data-ttu-id="d6453-128">您可以使用類別中的其中一個方法來檢查目前的作業系統 `Is<Platform>` <xref:System.OperatingSystem?displayProperty=nameWithType> ，例如，在 <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> 呼叫平臺特定 API 之前。</span><span class="sxs-lookup"><span data-stu-id="d6453-128">You can check the current operating system using one of the `Is<Platform>` methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class, for example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType>, before calling a platform-specific API.</span></span>

<span data-ttu-id="d6453-129">您可以 `Is<Platform>` 在語句的條件中使用其中一個方法 `if` ：</span><span class="sxs-lookup"><span data-stu-id="d6453-129">You can use one of the `Is<Platform>` methods in the condition of an `if` statement:</span></span>

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

<span data-ttu-id="d6453-130">或者，如果您不想要在執行時間額外負荷額外的 `if` 語句，請 <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> 改為呼叫：</span><span class="sxs-lookup"><span data-stu-id="d6453-130">Or, if you don't want the overhead of an additional `if` statement at run time, call <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> instead:</span></span>

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="d6453-131">如果您要撰寫程式庫，您可以將 API 標示為平臺特定。</span><span class="sxs-lookup"><span data-stu-id="d6453-131">If you're authoring a library, you can mark your API as platform-specific.</span></span> <span data-ttu-id="d6453-132">在此情況下，檢查需求的負擔會落在您的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="d6453-132">In this case, the burden of checking requirements falls on your callers.</span></span> <span data-ttu-id="d6453-133">您可以標記特定的方法或類型或整個元件。</span><span class="sxs-lookup"><span data-stu-id="d6453-133">You can mark specific methods or types or an entire assembly.</span></span>

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="d6453-134">如果您不想要修正所有的呼叫位置，可以選擇下列其中一個選項來抑制警告：</span><span class="sxs-lookup"><span data-stu-id="d6453-134">If you don't want to fix all your call sites, you can choose one of the following options to suppress the warning:</span></span>

- <span data-ttu-id="d6453-135">若要隱藏規則 CA1416，您可以使用 `#pragma` 或 [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) 編譯器旗標，或在 editorconfig 檔案中 [將規則的嚴重性設定](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) 為 `none` 。</span><span class="sxs-lookup"><span data-stu-id="d6453-135">To suppress rule CA1416, you can do so using `#pragma` or the [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) compiler flag, or by [setting the rule's severity](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) to `none` in an .editorconfig file.</span></span>

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- <span data-ttu-id="d6453-136">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="d6453-136">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="d6453-137">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="d6453-137">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="d6453-138">類別</span><span class="sxs-lookup"><span data-stu-id="d6453-138">Category</span></span>

- <span data-ttu-id="d6453-139">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="d6453-139">Code analysis</span></span>
- <span data-ttu-id="d6453-140">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="d6453-140">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d6453-141">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d6453-141">Affected APIs</span></span>

<span data-ttu-id="d6453-142">針對 Windows 平臺：</span><span class="sxs-lookup"><span data-stu-id="d6453-142">For Windows platform:</span></span>

- <span data-ttu-id="d6453-143">所有列出的 Api <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> 。</span><span class="sxs-lookup"><span data-stu-id="d6453-143">All APIs listed at <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>.</span></span>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

<span data-ttu-id="d6453-144">針對 Blazor WebAssembly platform：</span><span class="sxs-lookup"><span data-stu-id="d6453-144">For Blazor WebAssembly platform:</span></span>

- <span data-ttu-id="d6453-145">所有列出的 Api <https://github.com/dotnet/runtime/issues/41087> 。</span><span class="sxs-lookup"><span data-stu-id="d6453-145">All APIs listed at <https://github.com/dotnet/runtime/issues/41087>.</span></span>

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a><span data-ttu-id="d6453-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6453-146">See also</span></span>

- [<span data-ttu-id="d6453-147">CA1416：驗證平台相容性</span><span class="sxs-lookup"><span data-stu-id="d6453-147">CA1416: Validate platform compatibility</span></span>](/visualstudio/code-quality/ca1416)
- [<span data-ttu-id="d6453-148">.NET API 分析器</span><span class="sxs-lookup"><span data-stu-id="d6453-148">.NET API analyzer</span></span>](../../../../docs/standard/analyzers/api-analyzer.md)
