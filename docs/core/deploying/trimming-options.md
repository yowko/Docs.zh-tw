---
title: 修剪選項
description: 瞭解如何控制獨立應用程式的修剪。
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: e36aca3aadb6968f73a439ca985dc410d1bc88d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704652"
---
# <a name="trimming-options"></a><span data-ttu-id="1e765-103">修剪選項</span><span class="sxs-lookup"><span data-stu-id="1e765-103">Trimming options</span></span>

<span data-ttu-id="1e765-104">下列 MSBuild 屬性和專案會影響已修剪的 [獨立部署](trim-self-contained.md)行為。</span><span class="sxs-lookup"><span data-stu-id="1e765-104">The following MSBuild properties and items influence the behavior of [trimmed self-contained deployments](trim-self-contained.md).</span></span> <span data-ttu-id="1e765-105">有些選項 `ILLink` 會提及，也就是執行修剪的基礎工具名稱。</span><span class="sxs-lookup"><span data-stu-id="1e765-105">Some of the options mention `ILLink`, which is the name of the underlying tool that implements trimming.</span></span> <span data-ttu-id="1e765-106">如需基礎工具的詳細資訊，請參閱 [連結器檔](https://github.com/mono/linker/tree/master/docs)。</span><span class="sxs-lookup"><span data-stu-id="1e765-106">More information about the underlying tool can be found at the [Linker documentation](https://github.com/mono/linker/tree/master/docs).</span></span>

## <a name="enable-trimming"></a><span data-ttu-id="1e765-107">啟用修剪</span><span class="sxs-lookup"><span data-stu-id="1e765-107">Enable trimming</span></span>

- `<PublishTrimmed>true</PublishTrimmed>`

   <span data-ttu-id="1e765-108">使用 SDK 所定義的預設設定，在發佈期間啟用修剪。</span><span class="sxs-lookup"><span data-stu-id="1e765-108">Enable trimming during publish, with the default settings defined by the SDK.</span></span>

<span data-ttu-id="1e765-109">使用時 `Microsoft.NET.Sdk` ，會從 netcoreapp 執行時間套件執行架構元件的元件層級修剪。</span><span class="sxs-lookup"><span data-stu-id="1e765-109">When using `Microsoft.NET.Sdk`, this will perform assembly-level trimming of the framework assemblies from the netcoreapp runtime pack.</span></span> <span data-ttu-id="1e765-110">應用程式程式碼和非架構程式庫不會被修剪。</span><span class="sxs-lookup"><span data-stu-id="1e765-110">Application code and non-framework libraries are not trimmed.</span></span> <span data-ttu-id="1e765-111">其他 Sdk 可能會定義不同的預設值。</span><span class="sxs-lookup"><span data-stu-id="1e765-111">Other SDKs may define different defaults.</span></span>

## <a name="trimming-granularity"></a><span data-ttu-id="1e765-112">修剪細微性</span><span class="sxs-lookup"><span data-stu-id="1e765-112">Trimming granularity</span></span>

<span data-ttu-id="1e765-113">下列資料細微性設定可控制如何捨棄未使用的 IL。</span><span class="sxs-lookup"><span data-stu-id="1e765-113">The following granularity settings control how aggressively unused IL is discarded.</span></span> <span data-ttu-id="1e765-114">這可以設定為屬性，或做為 [個別元件](#trimmed-assemblies)上的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1e765-114">This can be set as a property, or as metadata on an [individual assembly](#trimmed-assemblies).</span></span>

- `<TrimMode>copyused</TrimMode>`

   <span data-ttu-id="1e765-115">啟用元件層級的修剪，如果使用任何部分的元件，則會以靜態瞭解的方式) ，以保持整個元件的 (。</span><span class="sxs-lookup"><span data-stu-id="1e765-115">Enable assembly-level trimming, which will keep an entire assembly if any part of it is used (in a statically understood way).</span></span>

- `<TrimMode>link</TrimMode>`

    <span data-ttu-id="1e765-116">啟用成員層級修剪，以從類型中移除未使用的成員。</span><span class="sxs-lookup"><span data-stu-id="1e765-116">Enable member-level trimming, which removes unused members from types.</span></span>

<span data-ttu-id="1e765-117">具有 `<IsTrimmable>true</IsTrimmable>` 中繼資料但沒有明確的元件 `TrimMode` 會使用全域 `TrimMode` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-117">Assemblies with `<IsTrimmable>true</IsTrimmable>` metadata but no explicit `TrimMode` will use the global `TrimMode`.</span></span> <span data-ttu-id="1e765-118">的預設值為 `TrimMode` `Microsoft.NET.Sdk` `copyused` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-118">The default `TrimMode` for `Microsoft.NET.Sdk` is `copyused`.</span></span>

## <a name="trimmed-assemblies"></a><span data-ttu-id="1e765-119">修剪的元件</span><span class="sxs-lookup"><span data-stu-id="1e765-119">Trimmed assemblies</span></span>

<span data-ttu-id="1e765-120">發佈已修剪的應用程式時，SDK `ItemGroup` 會計算呼叫 `ManagedAssemblyToLink` ，以代表要處理的一組檔案進行修剪。</span><span class="sxs-lookup"><span data-stu-id="1e765-120">When publishing a trimmed app, the SDK computes an `ItemGroup` called `ManagedAssemblyToLink` that represents the set of files to be processed for trimming.</span></span> <span data-ttu-id="1e765-121">`ManagedAssemblyToLink` 可能有可控制每個元件之修剪行為的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1e765-121">`ManagedAssemblyToLink` may have metadata that controls the trimming behavior per assembly.</span></span> <span data-ttu-id="1e765-122">若要設定此中繼資料，請建立在內建目標之前執行的目標 `PrepareForILLink` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-122">To set this metadata, create a target that runs before the built-in `PrepareForILLink` target.</span></span> <span data-ttu-id="1e765-123">下列範例顯示如何啟用的修剪 `MyAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-123">The following example shows how to enable trimming of `MyAssembly`.</span></span>

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

<span data-ttu-id="1e765-124">請勿在中加入或移除專案 `ManagedAssemblyToLink` ，因為 SDK 會在發行期間計算此集合，並預期不會變更。</span><span class="sxs-lookup"><span data-stu-id="1e765-124">Do not add or remove items to/from `ManagedAssemblyToLink`, because the SDK computes this set during publish and expects it not to change.</span></span> <span data-ttu-id="1e765-125">支援的中繼資料為：</span><span class="sxs-lookup"><span data-stu-id="1e765-125">The supported metadata is:</span></span>

- `<IsTrimmable>true</IsTrimmable>`

  <span data-ttu-id="1e765-126">控制是否修剪指定的元件。</span><span class="sxs-lookup"><span data-stu-id="1e765-126">Control whether the given assembly is trimmed.</span></span>

- <span data-ttu-id="1e765-127">`<TrimMode>copyused</TrimMode>` 或 `<TrimMode>link</TrimMode>`</span><span class="sxs-lookup"><span data-stu-id="1e765-127">`<TrimMode>copyused</TrimMode>` or `<TrimMode>link</TrimMode>`</span></span>

  <span data-ttu-id="1e765-128">控制這個元件的 [修剪資料細微性](#trimming-granularity) 。</span><span class="sxs-lookup"><span data-stu-id="1e765-128">Control the [trimming granularity](#trimming-granularity) of this assembly.</span></span> <span data-ttu-id="1e765-129">這優先于全域 `TrimMode` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-129">This takes precedence over the global `TrimMode`.</span></span> <span data-ttu-id="1e765-130">`TrimMode`元件上的設定暗示 `<IsTrimmable>true</IsTrimmable>` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-130">Setting `TrimMode` on an assembly implies `<IsTrimmable>true</IsTrimmable>`.</span></span>

## <a name="root-assemblies"></a><span data-ttu-id="1e765-131">根元件</span><span class="sxs-lookup"><span data-stu-id="1e765-131">Root assemblies</span></span>

<span data-ttu-id="1e765-132">所有不具有的元件 `<IsTrimmable>true</IsTrimmable>` 都會被視為分析的根目錄，這表示會保留它們及其所有靜態瞭解的相依性。</span><span class="sxs-lookup"><span data-stu-id="1e765-132">All assemblies that do not have `<IsTrimmable>true</IsTrimmable>` are considered roots for the analysis, which means that they and all of their statically understood dependencies will be kept.</span></span> <span data-ttu-id="1e765-133">其他元件可能會以名稱「根目錄」 (沒有 `.dll` 副檔名) ：</span><span class="sxs-lookup"><span data-stu-id="1e765-133">Additional assemblies may be "rooted" by name (without the `.dll` extension):</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a><span data-ttu-id="1e765-134">根描述元</span><span class="sxs-lookup"><span data-stu-id="1e765-134">Root descriptors</span></span>

<span data-ttu-id="1e765-135">另一種指定根以進行分析的方式，就是使用使用連結器 [描述元格式](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="1e765-135">Another way to specify roots for analysis is using an XML file that uses the linker [descriptor format](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format).</span></span> <span data-ttu-id="1e765-136">這可讓您指定根特定的成員，而不是整個元件。</span><span class="sxs-lookup"><span data-stu-id="1e765-136">This lets you root specific members instead of a whole assembly.</span></span>

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

<span data-ttu-id="1e765-137">例如， `MyRoots.xml` 可能是應用程式動態存取的特定方法的根：</span><span class="sxs-lookup"><span data-stu-id="1e765-137">For example, `MyRoots.xml` might root a specific method that is dynamically accessed by the application:</span></span>

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a><span data-ttu-id="1e765-138">分析警告</span><span class="sxs-lookup"><span data-stu-id="1e765-138">Analysis warnings</span></span>

<span data-ttu-id="1e765-139">修剪將會移除無法以靜態方式連線的 IL。</span><span class="sxs-lookup"><span data-stu-id="1e765-139">Trimming will remove IL that is not statically reachable.</span></span> <span data-ttu-id="1e765-140">使用反映的應用程式或其他建立動態相依性的模式，可能會藉由修剪來中斷。</span><span class="sxs-lookup"><span data-stu-id="1e765-140">Apps that use reflection or other patterns that create dynamic dependencies may be broken by trimming.</span></span> <span data-ttu-id="1e765-141">若要對這類模式發出警告：</span><span class="sxs-lookup"><span data-stu-id="1e765-141">To warn about such patterns:</span></span>

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    <span data-ttu-id="1e765-142">啟用 trim 分析警告。</span><span class="sxs-lookup"><span data-stu-id="1e765-142">Enable trim analysis warnings.</span></span>

<span data-ttu-id="1e765-143">這會包含整個應用程式的相關警告，包括您自己的程式碼、程式庫程式碼和架構程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e765-143">This will include warnings about the entire app, including your own code, library code, and framework code.</span></span>

## <a name="warning-versions"></a><span data-ttu-id="1e765-144">警告版本</span><span class="sxs-lookup"><span data-stu-id="1e765-144">Warning versions</span></span>

<span data-ttu-id="1e765-145">Trim 分析採用 [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) 控制 SDK 之間分析警告版本的屬性。</span><span class="sxs-lookup"><span data-stu-id="1e765-145">Trim analysis respects the [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) property that controls the version of analysis warnings across the SDK.</span></span> <span data-ttu-id="1e765-146">另外還有另一個屬性，可控制個別的 trim 分析警告版本， (類似于 `WarningLevel` 編譯器) ：</span><span class="sxs-lookup"><span data-stu-id="1e765-146">There is another property that controls the version of trim analysis warnings independently (similar to `WarningLevel` for the compiler):</span></span>

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    <span data-ttu-id="1e765-147">只發出指定層級或更低的警告。</span><span class="sxs-lookup"><span data-stu-id="1e765-147">Emit only warnings of the given level or lower.</span></span> <span data-ttu-id="1e765-148">這可以 `9999` 包含所有警告版本。</span><span class="sxs-lookup"><span data-stu-id="1e765-148">This can be `9999` to include all warning versions.</span></span>

## <a name="suppressing-warnings"></a><span data-ttu-id="1e765-149">隱藏警告</span><span class="sxs-lookup"><span data-stu-id="1e765-149">Suppressing warnings</span></span>

<span data-ttu-id="1e765-150">您可以使用工具鏈所遵守的一般 MSBuild 屬性來隱藏個別的 [警告碼](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) ，包括 `NoWarn` 、、 `WarningsAsErrors` `WarningsNotAsErrors` 和 `TreatWarningsAsErrors` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-150">Individual [warning codes](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) can be suppressed using the usual MSBuild properties respected by the toolchain, including `NoWarn`, `WarningsAsErrors`, `WarningsNotAsErrors`, and `TreatWarningsAsErrors`.</span></span> <span data-ttu-id="1e765-151">另外還有另一個選項，可個別控制 ILLink 警告錯誤行為：</span><span class="sxs-lookup"><span data-stu-id="1e765-151">There is an additional option that controls the ILLink warn-as-error behavior independently:</span></span>

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    <span data-ttu-id="1e765-152">請勿將 ILLink 警告視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e765-152">Don't treat ILLink warnings as errors.</span></span> <span data-ttu-id="1e765-153">這有助於避免在全域將編譯器警告視為錯誤時，將 trim 分析警告轉換成錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e765-153">This may be useful to avoid turning trim analysis warnings into errors when treating compiler warnings as errors globally.</span></span>

## <a name="removing-symbols"></a><span data-ttu-id="1e765-154">移除符號</span><span class="sxs-lookup"><span data-stu-id="1e765-154">Removing symbols</span></span>

<span data-ttu-id="1e765-155">通常會修剪符號以符合修剪的元件。</span><span class="sxs-lookup"><span data-stu-id="1e765-155">Symbols will normally be trimmed to match the trimmed assemblies.</span></span> <span data-ttu-id="1e765-156">您也可以移除所有符號：</span><span class="sxs-lookup"><span data-stu-id="1e765-156">You can also remove all symbols:</span></span>

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    <span data-ttu-id="1e765-157">從修剪的應用程式中移除符號，包括內嵌的 Pdb 和個別的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="1e765-157">Remove symbols from the trimmed application, including embedded PDBs and separate PDB files.</span></span> <span data-ttu-id="1e765-158">這同時適用于應用程式程式碼和符號隨附的任何相依性。</span><span class="sxs-lookup"><span data-stu-id="1e765-158">This applies to both the application code and any dependencies that come with symbols.</span></span>

<span data-ttu-id="1e765-159">SDK 也可以使用屬性來停用偵錯工具支援 `DebuggerSupport` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-159">The SDK also makes it possible to disable debugger support using the property `DebuggerSupport`.</span></span> <span data-ttu-id="1e765-160">停用偵錯工具支援時，修剪會自動移除符號 (`TrimmerRemoveSymbols` 預設為 true) 。</span><span class="sxs-lookup"><span data-stu-id="1e765-160">When debugger support is disabled, trimming will remove symbols automatically (`TrimmerRemoveSymbols` will default to true).</span></span>

## <a name="trimming-framework-library-features"></a><span data-ttu-id="1e765-161">修剪架構程式庫功能</span><span class="sxs-lookup"><span data-stu-id="1e765-161">Trimming framework library features</span></span>

<span data-ttu-id="1e765-162">架構程式庫的數個功能區域隨附連結器指示詞，可讓您移除停用功能的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e765-162">Several feature areas of the framework libraries come with linker directives that make it possible to remove the code for disabled features.</span></span>

- `<DebuggerSupport>false</DebuggerSupport>`

    <span data-ttu-id="1e765-163">移除可進行更佳的偵錯工具的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e765-163">Remove code that enables better debugging experiences.</span></span> <span data-ttu-id="1e765-164">這也會 [移除符號](#removing-symbols)。</span><span class="sxs-lookup"><span data-stu-id="1e765-164">This will also [remove symbols](#removing-symbols).</span></span>

- `<EnableUnsafeBinaryFormatterSerialization>false</EnableUnsafeBinaryFormatterSerialization>`

    <span data-ttu-id="1e765-165">移除 BinaryFormatter 序列化支援。</span><span class="sxs-lookup"><span data-stu-id="1e765-165">Remove BinaryFormatter serialization support.</span></span> <span data-ttu-id="1e765-166">如需詳細資訊，請參閱 [BinaryFormatter 序列化方法已過時](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md)。</span><span class="sxs-lookup"><span data-stu-id="1e765-166">For more information, see [BinaryFormatter serialization methods are obsolete](../compatibility/core-libraries/5.0/binaryformatter-serialization-obsolete.md).</span></span>

- `<EnableUnsafeUTF7Encoding>false</EnableUnsafeUTF7Encoding>`

    <span data-ttu-id="1e765-167">移除不安全的 UTF-7 編碼程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e765-167">Remove insecure UTF-7 encoding code.</span></span> <span data-ttu-id="1e765-168">如需詳細資訊，請參閱 [utf-7 程式碼路徑已淘汰](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md)。</span><span class="sxs-lookup"><span data-stu-id="1e765-168">For more information, see [UTF-7 code paths are obsolete](../compatibility/core-libraries/5.0/utf-7-code-paths-obsolete.md).</span></span>

- `<EventSourceSupport>false</EventSourceSupport>`

    <span data-ttu-id="1e765-169">移除 EventSource 相關的程式碼或邏輯。</span><span class="sxs-lookup"><span data-stu-id="1e765-169">Remove EventSource related code or logic.</span></span>

- `<HttpActivityPropagationSupport>false</HttpActivityPropagationSupport>`

    <span data-ttu-id="1e765-170">移除與系統 .Net 的診斷支援相關的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1e765-170">Remove code related to diagnostics support for System.Net.Http.</span></span>

- `<InvariantGlobalization>true</InvariantGlobalization>`

    <span data-ttu-id="1e765-171">移除全球化的特定程式碼和資料。</span><span class="sxs-lookup"><span data-stu-id="1e765-171">Remove globalization specific code and data.</span></span> <span data-ttu-id="1e765-172">如需詳細資訊，請參閱不 [變模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="1e765-172">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

- `<UseSystemResourceKeys>true</UseSystemResourceKeys>`

    <span data-ttu-id="1e765-173">去除元件的例外狀況訊息 `System.*` 。</span><span class="sxs-lookup"><span data-stu-id="1e765-173">Strip exception messages for `System.*` assemblies.</span></span> <span data-ttu-id="1e765-174">從元件擲回例外狀況時 `System.*` ，訊息會是簡化的資源識別碼，而不是完整的訊息。</span><span class="sxs-lookup"><span data-stu-id="1e765-174">When an exception is thrown from a `System.*` assembly, the message will be a simplified resource ID instead of the full message.</span></span>

 <span data-ttu-id="1e765-175">這些屬性會造成相關的程式碼遭到修剪，也會透過 [>.runtimeconfig.json](../run-time-config/index.md) 檔停用功能。</span><span class="sxs-lookup"><span data-stu-id="1e765-175">These properties will cause the related code to be trimmed and will also disable features via the [runtimeconfig](../run-time-config/index.md) file.</span></span> <span data-ttu-id="1e765-176">如需這些屬性的詳細資訊，包括對應的 >.runtimeconfig.json 選項，請參閱 [功能參數](https://github.com/dotnet/runtime/blob/master/docs/workflow/trimming/feature-switches.md)。</span><span class="sxs-lookup"><span data-stu-id="1e765-176">For more information about these properties, including the corresponding runtimeconfig options, see [feature switches](https://github.com/dotnet/runtime/blob/master/docs/workflow/trimming/feature-switches.md).</span></span> <span data-ttu-id="1e765-177">某些 Sdk 可能會有這些屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="1e765-177">Some SDKs may have default values for these properties.</span></span>
