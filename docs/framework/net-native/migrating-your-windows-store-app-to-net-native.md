---
title: 將您的 Windows 市集應用程式移轉至 .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3909855db109938794fad3e0afc99d492009b81c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461783"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="4dc98-102">將您的 Windows 市集應用程式移轉至 .NET Native</span><span class="sxs-lookup"><span data-stu-id="4dc98-102">Migrating Your Windows Store App to .NET Native</span></span>
<span data-ttu-id="4dc98-103">.NET 原生提供靜態編譯的應用程式在 Windows 市集或開發人員的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4dc98-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="4dc98-104">這不同於 just-in-time (JIT) 編譯器或裝置上的 [原生映像產生器 (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 為 Windows 市集應用程式執行的動態編譯。</span><span class="sxs-lookup"><span data-stu-id="4dc98-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="4dc98-105">儘管有所差異，.NET Native 會嘗試維持與相容性[適用於 Windows 市集應用程式](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4dc98-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span></span> <span data-ttu-id="4dc98-106">大部分的情況下，在適用於 Windows 市集應用程式運作的項目也適用於.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4dc98-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="4dc98-107">不過，在某些情況下，您可能會遇到行為上的變更。</span><span class="sxs-lookup"><span data-stu-id="4dc98-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="4dc98-108">本文將探討這些差異適用於 Windows 市集應用程式的標準和.NET Native 在下列區域：</span><span class="sxs-lookup"><span data-stu-id="4dc98-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>  
  
-   [<span data-ttu-id="4dc98-109">一般執行階段的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="4dc98-110">動態程式設計的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="4dc98-111">其他與反映相關的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="4dc98-112">不支援的案例和 API</span><span class="sxs-lookup"><span data-stu-id="4dc98-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="4dc98-113">Visual Studio 的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="4dc98-114">一般執行階段的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="4dc98-115">例外狀況，例如<xref:System.TypeLoadException>，所擲回由 JIT 編譯器是根據一般的應用程式執行時語言執行平台 (CLR) 通常會導致編譯時期錯誤時由.NET 原生處理。</span><span class="sxs-lookup"><span data-stu-id="4dc98-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>  
  
-   <span data-ttu-id="4dc98-116">請勿從應用程式的 UI 執行緒呼叫 <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4dc98-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="4dc98-117">這會導致鎖死.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4dc98-117">This can result in a deadlock on .NET Native.</span></span>  
  
-   <span data-ttu-id="4dc98-118">請不要依賴靜態類別建構函式引動過程順序。</span><span class="sxs-lookup"><span data-stu-id="4dc98-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="4dc98-119">在.NET 原生，引動過程順序是不同於標準執行階段上的順序。</span><span class="sxs-lookup"><span data-stu-id="4dc98-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="4dc98-120">(即使是使用標準執行階段，也不應該依賴靜態類別建構函式的執行順序。)</span><span class="sxs-lookup"><span data-stu-id="4dc98-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="4dc98-121">在任何執行緒上無限迴圈，而不進行呼叫 (例如 `while(true);`) 可能會導致應用程式中止。</span><span class="sxs-lookup"><span data-stu-id="4dc98-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="4dc98-122">同樣地，長時間或無限等待可能也會導致應用程式中止。</span><span class="sxs-lookup"><span data-stu-id="4dc98-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="4dc98-123">某些泛型初始化循環不會擲回例外狀況在.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4dc98-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="4dc98-124">例如，下列程式碼會在標準 CLR 上擲回 <xref:System.TypeLoadException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4dc98-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="4dc98-125">在.NET 原生，它不會。</span><span class="sxs-lookup"><span data-stu-id="4dc98-125">In .NET Native, it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="4dc98-126">在某些情況下，.NET Native，請提供不同的.NET Framework 類別庫的實作。</span><span class="sxs-lookup"><span data-stu-id="4dc98-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="4dc98-127">從方法傳回的物件一律會實作傳回類型的成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="4dc98-128">不過，由於其支援實作不同，所以您可能無法將其轉換成像在其他 .NET Framework 平台上轉換的相同類型集。</span><span class="sxs-lookup"><span data-stu-id="4dc98-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="4dc98-129">例如，在某些情況下，您可能無法將 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> 這類方法傳回的 <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> 介面物件轉換成 `T[]`。</span><span class="sxs-lookup"><span data-stu-id="4dc98-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="4dc98-130">適用於 Windows 市集應用程式，預設不啟用 WinInet 快取，但已排入.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4dc98-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="4dc98-131">這可以改善效能，但有工作集含意。</span><span class="sxs-lookup"><span data-stu-id="4dc98-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="4dc98-132">開發人員不需任何動作。</span><span class="sxs-lookup"><span data-stu-id="4dc98-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="4dc98-133">動態程式設計的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-133">Dynamic programming differences</span></span>  
 <span data-ttu-id="4dc98-134">.NET 原生靜態連結，讓程式碼的最大效能的應用程式本機的.NET Framework 的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="4dc98-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="4dc98-135">不過，二進位大小必須維持在較小的狀態，這樣才不會將整個 .NET Framework 帶進來。</span><span class="sxs-lookup"><span data-stu-id="4dc98-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="4dc98-136">.NET Native 編譯器會使用相依性縮減，以移除未使用的程式碼的參考來解析這項限制。</span><span class="sxs-lookup"><span data-stu-id="4dc98-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="4dc98-137">不過，.NET 原生可能不會維護或產生某些類型資訊和程式碼，該資訊無法在編譯時期靜態推斷，但在執行階段改為以動態方式擷取。</span><span class="sxs-lookup"><span data-stu-id="4dc98-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 <span data-ttu-id="4dc98-138">.NET native 未啟用反映和動態程式設計。</span><span class="sxs-lookup"><span data-stu-id="4dc98-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="4dc98-139">不過，並非所有類型都可以標記來進行反映，因為這樣會使所產生的程式碼大小過大 (尤其是因為可支援在 .NET Framework 中的公用 API 上反映)。</span><span class="sxs-lookup"><span data-stu-id="4dc98-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="4dc98-140">.NET Native 編譯器進行聰明的選擇，了解哪種類型應該支援反映，以及它保留中繼資料，並產生只適用於這些類型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4dc98-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="4dc98-141">例如，資料繫結會要求應用程式能夠將屬性名稱對應至函式。</span><span class="sxs-lookup"><span data-stu-id="4dc98-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="4dc98-142">在適用於 Windows 市集應用程式的 .NET 中，通用語言執行平台會自動使用反映來提供這項功能給 Managed 類型和可公開取得的原生類型。</span><span class="sxs-lookup"><span data-stu-id="4dc98-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="4dc98-143">在.NET Native 編譯器會自動包含您要繫結資料類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4dc98-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="4dc98-144">.NET Native 編譯器也可以處理通常使用泛型型別這類<xref:System.Collections.Generic.List%601>和<xref:System.Collections.Generic.Dictionary%602>、 哪些工作，而不需要任何提示或指示詞。</span><span class="sxs-lookup"><span data-stu-id="4dc98-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="4dc98-145">在某些限制下，也可支援 [動態](~/docs/csharp/language-reference/keywords/dynamic.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4dc98-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc98-146">移植至.NET Native 應用程式時，您應該徹底測試所有動態程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="4dc98-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>  
  
 <span data-ttu-id="4dc98-147">.NET 原生的預設組態已足以應付大部分的開發人員，但有些開發人員可能想要微調其組態使用執行階段指示詞 (。 rd.xml) 檔案。</span><span class="sxs-lookup"><span data-stu-id="4dc98-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="4dc98-148">此外，在某些情況下，.NET Native 編譯器會無法判斷中繼資料必須可供反映，而依賴提示，特別是在下列情況下：</span><span class="sxs-lookup"><span data-stu-id="4dc98-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="4dc98-149">無法以靜態方式判斷某些結構，例如 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="4dc98-150">由於編譯器無法判斷具現化，所以必須以執行階段指示詞來指定您想要反映的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="4dc98-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="4dc98-151">這不只是因為所有的程式碼必須包含在內，也因為反映在泛型類型上會形成無限循環 (例如，在泛型類型上叫用泛型方法時)。</span><span class="sxs-lookup"><span data-stu-id="4dc98-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dc98-152">執行階段指示詞中定義在執行階段指示詞 (.rd.xml) 檔案中。</span><span class="sxs-lookup"><span data-stu-id="4dc98-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="4dc98-153">如需使用此檔案的一般資訊，請參閱[使用者入門](../../../docs/framework/net-native/getting-started-with-net-native.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc98-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="4dc98-154">如需執行階段指示詞的詳細資訊，請參閱 [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc98-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 <span data-ttu-id="4dc98-155">.NET 原生也包含程式碼剖析工具，可協助開發人員決定預設集之外的哪些類型應該支援反映。</span><span class="sxs-lookup"><span data-stu-id="4dc98-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="4dc98-156">其他與反映相關的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="4dc98-157">有幾個其他個別反映相關的行為之間差異的適用於 Windows 市集應用程式 」 和 「.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4dc98-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>  
  
 <span data-ttu-id="4dc98-158">在.NET 原生：</span><span class="sxs-lookup"><span data-stu-id="4dc98-158">In .NET Native:</span></span>  
  
-   <span data-ttu-id="4dc98-159">不支援 .NET Framework 類別庫中，透過類型和成員的私用反映。</span><span class="sxs-lookup"><span data-stu-id="4dc98-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="4dc98-160">不過，您可以透過自己的私用類型和成員，以及協力廠商程式庫中的類型和成員來進行反映。</span><span class="sxs-lookup"><span data-stu-id="4dc98-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="4dc98-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> 屬性針對表示傳回值的 `false` 物件，正確地傳回 <xref:System.Reflection.ParameterInfo>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="4dc98-162">在適用於 Windows 市集應用程式的 .NET 中，它會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="4dc98-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="4dc98-163">中繼語言 (IL) 不會直接支援此作業，而是將解譯工作留給語言。</span><span class="sxs-lookup"><span data-stu-id="4dc98-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="4dc98-164">不支援 <xref:System.RuntimeFieldHandle> 和 <xref:System.RuntimeMethodHandle> 結構上的公用成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="4dc98-165">只有針對 LINQ、運算式樹狀架構和靜態陣列初始設定，才會支援這些類型。</span><span class="sxs-lookup"><span data-stu-id="4dc98-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="4dc98-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> 將隱藏的成員包含基底類別中，因此可能會在非明確覆寫的情況下被覆寫。</span><span class="sxs-lookup"><span data-stu-id="4dc98-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="4dc98-167">這也是如此另[runtimereflectionextensions.getruntime \*](https://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="4dc98-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](https://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) methods.</span></span>  
  
-   <span data-ttu-id="4dc98-168">當您嘗試建立特定的組合 (例如 byref 的陣列) 時，<xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 和 <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> 不會失敗。</span><span class="sxs-lookup"><span data-stu-id="4dc98-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="4dc98-169">您不能使用反映來叫用具有指標參數的成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="4dc98-170">您不能使用反映來取得或設定指標欄位。</span><span class="sxs-lookup"><span data-stu-id="4dc98-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="4dc98-171">當引數計數是錯誤的其中一個引數類型不正確，.NET Native 會擲回<xref:System.ArgumentException>而不是<xref:System.Reflection.TargetParameterCountException>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="4dc98-172">通常不支援例外狀況的二進位序列化。</span><span class="sxs-lookup"><span data-stu-id="4dc98-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="4dc98-173">因此，可以將不可序列化的物件加入 <xref:System.Exception.Data%2A?displayProperty=nameWithType> 字典。</span><span class="sxs-lookup"><span data-stu-id="4dc98-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="4dc98-174">不支援的案例和 API</span><span class="sxs-lookup"><span data-stu-id="4dc98-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="4dc98-175">下列各節會針對一般開發、interop 以及 HTTPClient 和 Windows Communication Foundation (WCF) 等技術，列出不支援的案例和 API：</span><span class="sxs-lookup"><span data-stu-id="4dc98-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="4dc98-176">一般開發</span><span class="sxs-lookup"><span data-stu-id="4dc98-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="4dc98-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="4dc98-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="4dc98-178">Interop</span><span class="sxs-lookup"><span data-stu-id="4dc98-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="4dc98-179">不支援的 API</span><span class="sxs-lookup"><span data-stu-id="4dc98-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="4dc98-180">一般開發的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-180">General development differences</span></span>  
 <span data-ttu-id="4dc98-181">**值類型**</span><span class="sxs-lookup"><span data-stu-id="4dc98-181">**Value types**</span></span>  
  
-   <span data-ttu-id="4dc98-182">如果您覆寫 <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> 和 <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> 方法的值類型，請勿呼叫基底類別實作。</span><span class="sxs-lookup"><span data-stu-id="4dc98-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="4dc98-183">在適用於 Windows 市集應用程式的 .NET 中，這些方法會依賴反映。</span><span class="sxs-lookup"><span data-stu-id="4dc98-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="4dc98-184">在編譯時期，.NET Native 會產生不依賴執行階段反映的實作。</span><span class="sxs-lookup"><span data-stu-id="4dc98-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="4dc98-185">這表示，如果您不覆寫這兩種方法，它們會如預期般運作，因為.NET Native 會產生編譯時期的實作。</span><span class="sxs-lookup"><span data-stu-id="4dc98-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="4dc98-186">不過，覆寫這些方法，但又呼叫基底類別實作，將會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4dc98-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="4dc98-187">不支援大於 1 MB 的值類型。</span><span class="sxs-lookup"><span data-stu-id="4dc98-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="4dc98-188">實值型別不能有預設建構函式，在.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4dc98-188">Value types can't have a default constructor in .NET Native.</span></span> <span data-ttu-id="4dc98-189">(C# 和 Visual Basic 禁止值類型上有預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="4dc98-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="4dc98-190">不過，可以在 IL 中建立這些預設建構函式)。</span><span class="sxs-lookup"><span data-stu-id="4dc98-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="4dc98-191">**陣列**</span><span class="sxs-lookup"><span data-stu-id="4dc98-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="4dc98-192">不支援下限不是零的陣列。</span><span class="sxs-lookup"><span data-stu-id="4dc98-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="4dc98-193">一般而言，可以呼叫 <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> 多載來建立這些陣列。</span><span class="sxs-lookup"><span data-stu-id="4dc98-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="4dc98-194">不支援動態建立多維陣列。</span><span class="sxs-lookup"><span data-stu-id="4dc98-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="4dc98-195">這類陣列的建立，通常是藉由呼叫包含 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 參數之 `lengths` 方法的多載，或是呼叫 <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4dc98-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="4dc98-196">不支援具有 4 個 (含) 以上維度的多維陣列，意即，其 <xref:System.Array.Rank%2A?displayProperty=nameWithType> 屬性值為 4 (含) 以上。</span><span class="sxs-lookup"><span data-stu-id="4dc98-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="4dc98-197">請改用 [不規則陣列](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (陣列的陣列)。</span><span class="sxs-lookup"><span data-stu-id="4dc98-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="4dc98-198">例如， `array[x,y,z]` 無效，但 `array[x][y][z]` 有效。</span><span class="sxs-lookup"><span data-stu-id="4dc98-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="4dc98-199">不支援多維陣列的變異數，它會在執行階段導致 <xref:System.InvalidCastException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4dc98-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="4dc98-200">**泛型**</span><span class="sxs-lookup"><span data-stu-id="4dc98-200">**Generics**</span></span>  
  
-   <span data-ttu-id="4dc98-201">無限的泛型類型擴充會導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4dc98-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="4dc98-202">例如，此程式碼無法編譯：</span><span class="sxs-lookup"><span data-stu-id="4dc98-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="4dc98-203">**Pointers**</span><span class="sxs-lookup"><span data-stu-id="4dc98-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="4dc98-204">不支援指標的陣列。</span><span class="sxs-lookup"><span data-stu-id="4dc98-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="4dc98-205">您不能使用反映來取得或設定指標欄位。</span><span class="sxs-lookup"><span data-stu-id="4dc98-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="4dc98-206">**序列化**</span><span class="sxs-lookup"><span data-stu-id="4dc98-206">**Serialization**</span></span>  
  
 <span data-ttu-id="4dc98-207">不支援 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4dc98-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="4dc98-208">請改用 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4dc98-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="4dc98-209">**資源**</span><span class="sxs-lookup"><span data-stu-id="4dc98-209">**Resources**</span></span>  
  
 <span data-ttu-id="4dc98-210">不支援將當地語系化的資源與 <xref:System.Diagnostics.Tracing.EventSource> 類別搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4dc98-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="4dc98-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> 屬性不會定義當地語系化的資源。</span><span class="sxs-lookup"><span data-stu-id="4dc98-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="4dc98-212">**委派**</span><span class="sxs-lookup"><span data-stu-id="4dc98-212">**Delegates**</span></span>  
  
 <span data-ttu-id="4dc98-213">不支援`Delegate.BeginInvoke` 和 `Delegate.EndInvoke` 。</span><span class="sxs-lookup"><span data-stu-id="4dc98-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="4dc98-214">**其他 API**</span><span class="sxs-lookup"><span data-stu-id="4dc98-214">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="4dc98-215">如果沒有將 <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> 屬性 (attribute) 套用至類型，則 <xref:System.PlatformNotSupportedException> 屬性 (property) 會擲回 <xref:System.Runtime.InteropServices.GuidAttribute> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4dc98-215">The <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="4dc98-216">GUID 主要用於 COM 支援。</span><span class="sxs-lookup"><span data-stu-id="4dc98-216">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="4dc98-217"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType>方法正確地剖析包含在.NET 原生的簡短日期的字串。</span><span class="sxs-lookup"><span data-stu-id="4dc98-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="4dc98-218">不過，它不會變更的相容性維護中的日期和時間剖析 Microsoft Knowledge Base 文章所述[KB2803771](https://support.microsoft.com/kb/2803771)並[KB2803755](https://support.microsoft.com/kb/2803755)。</span><span class="sxs-lookup"><span data-stu-id="4dc98-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="4dc98-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` 正確地在.NET 原生四捨五入。</span><span class="sxs-lookup"><span data-stu-id="4dc98-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="4dc98-220">在某些版本的 CLR 中，會將結果字串無條件捨去，而不是四捨五入。</span><span class="sxs-lookup"><span data-stu-id="4dc98-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="4dc98-221">HttpClient 差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-221">HttpClient differences</span></span>  
 <span data-ttu-id="4dc98-222">在.NET Native<xref:System.Net.Http.HttpClientHandler>類別在內部使用 WinINet (透過[HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx)類別) 而非<xref:System.Net.WebRequest>和<xref:System.Net.WebResponse>標準適用於 Windows 市集應用程式中使用的類別。</span><span class="sxs-lookup"><span data-stu-id="4dc98-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the [HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="4dc98-223">WinINet 並未支援 <xref:System.Net.Http.HttpClientHandler> 類別支援的所有組態選項。</span><span class="sxs-lookup"><span data-stu-id="4dc98-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="4dc98-224">因此：</span><span class="sxs-lookup"><span data-stu-id="4dc98-224">As a result:</span></span>  
  
-   <span data-ttu-id="4dc98-225">部分功能屬性會在<xref:System.Net.Http.HttpClientHandler>會傳回`false`.NET native，則會傳回`true`適用於 Windows 市集應用程式的標準。</span><span class="sxs-lookup"><span data-stu-id="4dc98-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="4dc98-226">某些組態屬性`get`存取子一律會傳回固定的值在.NET Native 上將會不同於適用於 Windows 市集應用程式中的預設設定值。</span><span class="sxs-lookup"><span data-stu-id="4dc98-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="4dc98-227">下列各小節會說明一些其他的行為差異。</span><span class="sxs-lookup"><span data-stu-id="4dc98-227">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="4dc98-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="4dc98-228">**Proxy**</span></span>  
  
 <span data-ttu-id="4dc98-229">[HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx)類別不支援設定或覆寫個別要求上的 proxy。</span><span class="sxs-lookup"><span data-stu-id="4dc98-229">The [HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="4dc98-230">這表示在.NET 原生的所有要求都使用系統設定的 proxy 伺服器或未使用 proxy 伺服器，根據的值<xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="4dc98-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="4dc98-231">在適用於 Windows 市集應用程式的 .NET 中，是由 <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> 屬性來定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="4dc98-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="4dc98-232">在.NET Native 上，設定<xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType>以外的值來`null`就會擲回<xref:System.PlatformNotSupportedException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4dc98-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="4dc98-233"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType>屬性會傳回`false`.NET native，則會傳回`true`適用於 Windows 市集.NET Framework 應用程式的標準。</span><span class="sxs-lookup"><span data-stu-id="4dc98-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="4dc98-234">**自動重新導向**</span><span class="sxs-lookup"><span data-stu-id="4dc98-234">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="4dc98-235">[HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx)類別不允許設定自動重新導向的最大數目。</span><span class="sxs-lookup"><span data-stu-id="4dc98-235">The [HttpBaseProtocolFilter](https://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="4dc98-236">在適用於 Windows 市集應用程式的標準 .NET 中，<xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> 屬性的值預設為 50，而且可以修改。</span><span class="sxs-lookup"><span data-stu-id="4dc98-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="4dc98-237">.NET native，這個屬性的值會是 10，而且嘗試修改它會擲回<xref:System.PlatformNotSupportedException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4dc98-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="4dc98-238"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType>屬性會傳回`false`.NET native，則會傳回`true`適用於 Windows 市集應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4dc98-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="4dc98-239">**自動解壓縮**</span><span class="sxs-lookup"><span data-stu-id="4dc98-239">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="4dc98-240">適用於 Windows 市集應用程式的 .NET 可讓您將 <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> 屬性設為 <xref:System.Net.DecompressionMethods.Deflate>、<xref:System.Net.DecompressionMethods.GZip>、<xref:System.Net.DecompressionMethods.Deflate> 和 <xref:System.Net.DecompressionMethods.GZip> 同時設定，或是設為 <xref:System.Net.DecompressionMethods.None>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="4dc98-241">.NET 原生只支援<xref:System.Net.DecompressionMethods.Deflate>連同<xref:System.Net.DecompressionMethods.GZip>，或<xref:System.Net.DecompressionMethods.None>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="4dc98-242">嘗試以無訊息模式將 <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> 屬性單獨設為 <xref:System.Net.DecompressionMethods.Deflate> 或 <xref:System.Net.DecompressionMethods.GZip> ，會將其設為同時使用 <xref:System.Net.DecompressionMethods.Deflate> 和 <xref:System.Net.DecompressionMethods.GZip>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="4dc98-243">**Cookie**</span><span class="sxs-lookup"><span data-stu-id="4dc98-243">**Cookies**</span></span>  
  
 <span data-ttu-id="4dc98-244"><xref:System.Net.Http.HttpClient> 和 WinINet 會同時執行 Cookie 處理作業。</span><span class="sxs-lookup"><span data-stu-id="4dc98-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="4dc98-245"><xref:System.Net.CookieContainer> 所產生的 Cookie 會與 WinINet Cookie 快取中的 Cookie 合併。</span><span class="sxs-lookup"><span data-stu-id="4dc98-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="4dc98-246">從 <xref:System.Net.CookieContainer> 移除 Cookie 會防止 <xref:System.Net.Http.HttpClient> 傳送 Cookie，但如果 WinINet 已經看到 Cookie，而且使用者沒有刪除 Cookie，WinINet 就會加以傳送。</span><span class="sxs-lookup"><span data-stu-id="4dc98-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="4dc98-247">若要使用 <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>或 <xref:System.Net.CookieContainer> API，以程式設計方式將 Cookie 從 WinINet 移除是不可能的。</span><span class="sxs-lookup"><span data-stu-id="4dc98-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="4dc98-248">將 <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> 屬性設為 `false` 只會導致 <xref:System.Net.Http.HttpClient> 停止傳送 Cookie，WinINet 還是會在要求中包含其 Cookie。</span><span class="sxs-lookup"><span data-stu-id="4dc98-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="4dc98-249">**認證**</span><span class="sxs-lookup"><span data-stu-id="4dc98-249">**Credentials**</span></span>  
  
 <span data-ttu-id="4dc98-250">在適用於 Windows 市集應用程式的 .NET 中，<xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> 屬性會獨立運作。</span><span class="sxs-lookup"><span data-stu-id="4dc98-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="4dc98-251">此外， <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性會接受實作 <xref:System.Net.ICredentials> 介面的任何物件。</span><span class="sxs-lookup"><span data-stu-id="4dc98-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="4dc98-252">在.NET 原生，設定<xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A>屬性，以`true`會導致<xref:System.Net.Http.HttpClientHandler.Credentials%2A>屬性變成`null`。</span><span class="sxs-lookup"><span data-stu-id="4dc98-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="4dc98-253">此外， <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性只能設為 `null`、 <xref:System.Net.CredentialCache.DefaultCredentials%2A>，或是 <xref:System.Net.NetworkCredential>類型的物件。</span><span class="sxs-lookup"><span data-stu-id="4dc98-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="4dc98-254">將任何其他 <xref:System.Net.ICredentials> 物件 (最常用的是 <xref:System.Net.CredentialCache>) 指派給 <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性會擲回 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="4dc98-255">**其他不受支援或不可設定的功能**</span><span class="sxs-lookup"><span data-stu-id="4dc98-255">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="4dc98-256">在.NET 原生：</span><span class="sxs-lookup"><span data-stu-id="4dc98-256">In .NET Native:</span></span>  
  
-   <span data-ttu-id="4dc98-257"><xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> 屬性的值一律為 <xref:System.Net.Http.ClientCertificateOption.Automatic>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="4dc98-258">在適用於 Windows 市集應用程式的 .NET 中，預設值為 <xref:System.Net.Http.ClientCertificateOption.Manual>。</span><span class="sxs-lookup"><span data-stu-id="4dc98-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="4dc98-259"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> 屬性不可設定。</span><span class="sxs-lookup"><span data-stu-id="4dc98-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="4dc98-260"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> 屬性一律為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4dc98-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="4dc98-261">在適用於 Windows 市集應用程式的 .NET 中，預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4dc98-261">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="4dc98-262">系統會將回應中的 `SetCookie2` 標頭視為過時而將它忽略。</span><span class="sxs-lookup"><span data-stu-id="4dc98-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="4dc98-263">Interop 的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-263">Interop differences</span></span>  
 <span data-ttu-id="4dc98-264">**已被取代的 API**</span><span class="sxs-lookup"><span data-stu-id="4dc98-264">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="4dc98-265">有些與 Managed 程式碼交互操作的不常用 API 已被取代。</span><span class="sxs-lookup"><span data-stu-id="4dc98-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="4dc98-266">這些 Api 與.NET 原生使用時，可能會擲回<xref:System.NotImplementedException>或<xref:System.PlatformNotSupportedException>例外狀況或導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4dc98-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="4dc98-267">在適用於 Windows 市集應用程式的 .NET 中，這些 API 會標示為已過時，但是呼叫這些 API 會產生編譯器警告，而不是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4dc98-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="4dc98-268">用於 `VARIANT` 封送處理的被取代 API：</span><span class="sxs-lookup"><span data-stu-id="4dc98-268">Deprecated APIs for `VARIANT` marshaling:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <span data-ttu-id="4dc98-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> 支援，但在它擲回例外狀況，請在某些情況下，例如當它搭配[IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)或 byref 變異數。</span><span class="sxs-lookup"><span data-stu-id="4dc98-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or byref variants.</span></span>  
  
 <span data-ttu-id="4dc98-270">已被取代的 Api [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)支援：</span><span class="sxs-lookup"><span data-stu-id="4dc98-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support:</span></span>  
  
|<span data-ttu-id="4dc98-271">類型</span><span class="sxs-lookup"><span data-stu-id="4dc98-271">Type</span></span>|<span data-ttu-id="4dc98-272">成員</span><span class="sxs-lookup"><span data-stu-id="4dc98-272">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|<span data-ttu-id="4dc98-273">不支援屬性</span><span class="sxs-lookup"><span data-stu-id="4dc98-273">Attribute isn't supported</span></span>|  
  
 <span data-ttu-id="4dc98-274">用於傳統 COM 事件的被取代 API：</span><span class="sxs-lookup"><span data-stu-id="4dc98-274">Deprecated APIs for classic COM events:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 <span data-ttu-id="4dc98-275">中的 Api 已被取代<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>介面，在.NET 原生不支援：</span><span class="sxs-lookup"><span data-stu-id="4dc98-275">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native:</span></span>  
  
|<span data-ttu-id="4dc98-276">類型</span><span class="sxs-lookup"><span data-stu-id="4dc98-276">Type</span></span>|<span data-ttu-id="4dc98-277">成員</span><span class="sxs-lookup"><span data-stu-id="4dc98-277">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|<span data-ttu-id="4dc98-278">所有成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-278">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|<span data-ttu-id="4dc98-279">所有成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-279">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|<span data-ttu-id="4dc98-280">所有成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-280">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 <span data-ttu-id="4dc98-281">其他不受支援的 interop 功能：</span><span class="sxs-lookup"><span data-stu-id="4dc98-281">Other unsupported interop features:</span></span>  
  
|<span data-ttu-id="4dc98-282">類型</span><span class="sxs-lookup"><span data-stu-id="4dc98-282">Type</span></span>|<span data-ttu-id="4dc98-283">成員</span><span class="sxs-lookup"><span data-stu-id="4dc98-283">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|<span data-ttu-id="4dc98-284">所有成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-284">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|<span data-ttu-id="4dc98-285">所有成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-285">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 <span data-ttu-id="4dc98-286">很少使用的封送處理 API：</span><span class="sxs-lookup"><span data-stu-id="4dc98-286">Rarely used marshalling APIs:</span></span>  
  
|<span data-ttu-id="4dc98-287">類型</span><span class="sxs-lookup"><span data-stu-id="4dc98-287">Type</span></span>|<span data-ttu-id="4dc98-288">成員</span><span class="sxs-lookup"><span data-stu-id="4dc98-288">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 <span data-ttu-id="4dc98-289">**平台叫用和 COM interop 相容性**</span><span class="sxs-lookup"><span data-stu-id="4dc98-289">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="4dc98-290">大部分的平台叫用和 COM interop 案例仍在.NET 原生支援。</span><span class="sxs-lookup"><span data-stu-id="4dc98-290">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="4dc98-291">特別是仍支援與 Windows 執行階段 (WinRT) API 的所有交互操作性，以及 Windows 執行階段需要的所有封送處理。</span><span class="sxs-lookup"><span data-stu-id="4dc98-291">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="4dc98-292">其中包括對下列項目的封送處理支援：</span><span class="sxs-lookup"><span data-stu-id="4dc98-292">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="4dc98-293">陣列 (包括<xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="4dc98-293">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="4dc98-294">委派</span><span class="sxs-lookup"><span data-stu-id="4dc98-294">Delegates</span></span>  
  
-   <span data-ttu-id="4dc98-295">字串 (Unicode、Ansi 和 HSTRING)</span><span class="sxs-lookup"><span data-stu-id="4dc98-295">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="4dc98-296">結構 (`byref` 和 `byval`)</span><span class="sxs-lookup"><span data-stu-id="4dc98-296">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="4dc98-297">等位</span><span class="sxs-lookup"><span data-stu-id="4dc98-297">Unions</span></span>  
  
-   <span data-ttu-id="4dc98-298">Win32 控制代碼</span><span class="sxs-lookup"><span data-stu-id="4dc98-298">Win32 handles</span></span>  
  
-   <span data-ttu-id="4dc98-299">所有 WinRT 結構</span><span class="sxs-lookup"><span data-stu-id="4dc98-299">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="4dc98-300">部分支援封送處理變異數類型。</span><span class="sxs-lookup"><span data-stu-id="4dc98-300">Partial support for marshaling variant types.</span></span> <span data-ttu-id="4dc98-301">支援的項目如下：</span><span class="sxs-lookup"><span data-stu-id="4dc98-301">The following are supported:</span></span>  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [<span data-ttu-id="4dc98-302">IUnknown</span><span class="sxs-lookup"><span data-stu-id="4dc98-302">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)  
  
 <span data-ttu-id="4dc98-303">不過，.NET 原生不支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="4dc98-303">However, .NET Native doesn't support the following:</span></span>  
  
-   <span data-ttu-id="4dc98-304">使用傳統 COM 事件</span><span class="sxs-lookup"><span data-stu-id="4dc98-304">Using classic COM events</span></span>  
  
-   <span data-ttu-id="4dc98-305">在 Managed 類型上實作 <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> 介面</span><span class="sxs-lookup"><span data-stu-id="4dc98-305">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="4dc98-306">實作[IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)介面，透過在 managed 類型上的<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="4dc98-306">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="4dc98-307">不過，請注意您不能透過 `IDispatch`來呼叫 COM 物件，而且您的 Managed 物件不能實作 `IDispatch`。</span><span class="sxs-lookup"><span data-stu-id="4dc98-307">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="4dc98-308">不支援使用反映來叫用平台叫用方法。</span><span class="sxs-lookup"><span data-stu-id="4dc98-308">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="4dc98-309">若要解除決這項限制，您可以將此方法呼叫包裝在另一個方法中，並改用反映來呼叫包裝函式。</span><span class="sxs-lookup"><span data-stu-id="4dc98-309">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="4dc98-310">其他與適用於 Windows 市集應用程式的 .NET API 的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-310">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="4dc98-311">此區段會列出不支援在.NET 原生的其餘 Api。</span><span class="sxs-lookup"><span data-stu-id="4dc98-311">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="4dc98-312">不受支援的的最大 API 集是 Windows Communication Foundation (WCF) API。</span><span class="sxs-lookup"><span data-stu-id="4dc98-312">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="4dc98-313">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="4dc98-313">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="4dc98-314">中的型別<xref:System.ComponentModel.DataAnnotations>和<xref:System.ComponentModel.DataAnnotations.Schema>命名空間不在.NET 原生支援。</span><span class="sxs-lookup"><span data-stu-id="4dc98-314">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="4dc98-315">其中包括適用於 Windows 8.1 之 Windows 市集應用程式的 .NET 中存在的下列類型：</span><span class="sxs-lookup"><span data-stu-id="4dc98-315">These include the following types that are present in the .NET for Windows Store apps for Windows 8:</span></span>  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 <span data-ttu-id="4dc98-316">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="4dc98-316">**Visual Basic**</span></span>  
  
 <span data-ttu-id="4dc98-317">Visual Basic 目前不在.NET 原生支援。</span><span class="sxs-lookup"><span data-stu-id="4dc98-317">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="4dc98-318">中的下列型別<xref:Microsoft.VisualBasic>和<xref:Microsoft.VisualBasic.CompilerServices>命名空間無法在.NET 原生：</span><span class="sxs-lookup"><span data-stu-id="4dc98-318">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 <span data-ttu-id="4dc98-319">**反映內容 (System.Reflection.Context 命名空間)**</span><span class="sxs-lookup"><span data-stu-id="4dc98-319">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="4dc98-320"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType>類別不支援在.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4dc98-320">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="4dc98-321">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="4dc98-321">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="4dc98-322"><xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType>類別不支援在.NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4dc98-322">The <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="4dc98-323">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="4dc98-323">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="4dc98-324">中的型別[system.servicemodel.\* 命名空間](https://msdn.microsoft.com/library/gg145010.aspx)不在.NET 原生支援。</span><span class="sxs-lookup"><span data-stu-id="4dc98-324">The types in the [System.ServiceModel.\* namespaces](https://msdn.microsoft.com/library/gg145010.aspx) aren't supported in .NET Native.</span></span> <span data-ttu-id="4dc98-325">其中包括下列類型：</span><span class="sxs-lookup"><span data-stu-id="4dc98-325">These includes the following types:</span></span>  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a><span data-ttu-id="4dc98-326">序列化程式的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-326">Differences in serializers</span></span>  
 <span data-ttu-id="4dc98-327">下列差異與使用 <xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和 <xref:System.Xml.Serialization.XmlSerializer> 類別來進行序列化和還原序列化有關。</span><span class="sxs-lookup"><span data-stu-id="4dc98-327">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="4dc98-328">在.NET Native<xref:System.Runtime.Serialization.DataContractSerializer>和<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>無法序列化或還原序列化衍生的類別具有其類型不是根序列化類型的基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-328">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="4dc98-329">例如，在下列程式碼中，嘗試序列化或還原序列化 `Y` 會產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="4dc98-329">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="4dc98-330">序列化程式無法識別 `InnerType` 類型，因為在序列化期間，並未周遊基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="4dc98-330">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="4dc98-331"><xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 無法將實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的類別或結構序列化。</span><span class="sxs-lookup"><span data-stu-id="4dc98-331"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="4dc98-332">例如，下列的類型無法序列化或還原序列化：</span><span class="sxs-lookup"><span data-stu-id="4dc98-332">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="4dc98-333"><xref:System.Xml.Serialization.XmlSerializer> 無法將下列物件值序列化，因為它不知道要序列化之物件的確切類型：</span><span class="sxs-lookup"><span data-stu-id="4dc98-333"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="4dc98-334">如果已序列化物件的類型是<xref:System.Xml.Serialization.XmlSerializer> ，則 <xref:System.Xml.XmlQualifiedName>無法序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="4dc98-334"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="4dc98-335">所有序列化程式 (<xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer>) 都無法為 <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> 類型或是包含 <xref:System.Xml.Linq.XElement> 的類型產生序列化程式碼，</span><span class="sxs-lookup"><span data-stu-id="4dc98-335">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="4dc98-336">而會顯示建置時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="4dc98-336">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="4dc98-337">無法保證序列化類型的下列建構函式能夠如預期般運作：</span><span class="sxs-lookup"><span data-stu-id="4dc98-337">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <span data-ttu-id="4dc98-338">如果類型中有使用下列任何屬性的方法，則<xref:System.Xml.Serialization.XmlSerializer> 無法為該類型產生程式碼：</span><span class="sxs-lookup"><span data-stu-id="4dc98-338"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="4dc98-339"><xref:System.Xml.Serialization.XmlSerializer> 不接受 <xref:System.Xml.Serialization.IXmlSerializable> 自訂序列化介面。</span><span class="sxs-lookup"><span data-stu-id="4dc98-339"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="4dc98-340">如果您有實作這個介面的類別， <xref:System.Xml.Serialization.XmlSerializer> 會將該類型視為簡單的 CLR 物件 (POCO) 類型，並且只將其公開屬性序列化。</span><span class="sxs-lookup"><span data-stu-id="4dc98-340">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="4dc98-341">使用 <xref:System.Exception> 和 <xref:System.Runtime.Serialization.DataContractSerializer> 來將純 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>物件 (例如下列物件) 序列化的效果不佳：</span><span class="sxs-lookup"><span data-stu-id="4dc98-341">Serializing a plain <xref:System.Exception> object, such as the following, doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="4dc98-342">Visual Studio 的差異</span><span class="sxs-lookup"><span data-stu-id="4dc98-342">Visual Studio differences</span></span>  
 <span data-ttu-id="4dc98-343">**例外狀況和偵錯**</span><span class="sxs-lookup"><span data-stu-id="4dc98-343">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="4dc98-344">當您執行偵錯工具中使用.NET 原生編譯的應用程式時，如下列的例外狀況類型啟用 first-chance 例外狀況：</span><span class="sxs-lookup"><span data-stu-id="4dc98-344">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="4dc98-345">**建置應用程式**</span><span class="sxs-lookup"><span data-stu-id="4dc98-345">**Building apps**</span></span>  
  
 <span data-ttu-id="4dc98-346">使用 Visual Studio 預設使用的 x86 建置工具。</span><span class="sxs-lookup"><span data-stu-id="4dc98-346">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="4dc98-347">我們不建議使用 AMD64 MSBuild 工具 (可以在 C:\Program Files (x86)\MSBuild\12.0\bin\amd64 中找到)；這些工具可能會造成組建問題。</span><span class="sxs-lookup"><span data-stu-id="4dc98-347">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="4dc98-348">**分析工具**</span><span class="sxs-lookup"><span data-stu-id="4dc98-348">**Profilers**</span></span>  
  
-   <span data-ttu-id="4dc98-349">Visual Studio CPU 分析工具和 XAML 記憶體分析工具不會正確顯示 Just-My-Code。</span><span class="sxs-lookup"><span data-stu-id="4dc98-349">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="4dc98-350">XAML 記憶體分析工具不會準確地顯示 Managed 堆積資料。</span><span class="sxs-lookup"><span data-stu-id="4dc98-350">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="4dc98-351">CPU 分析工具不會正確地識別模組，並且會顯示具有前置詞的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="4dc98-351">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="4dc98-352">**單元測試程式庫專案**</span><span class="sxs-lookup"><span data-stu-id="4dc98-352">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="4dc98-353">啟用.NET Native 上針對 Windows 市集應用程式專案的單元測試程式庫不支援，並造成無法建置專案。</span><span class="sxs-lookup"><span data-stu-id="4dc98-353">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc98-354">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dc98-354">See Also</span></span>  
 [<span data-ttu-id="4dc98-355">快速入門</span><span class="sxs-lookup"><span data-stu-id="4dc98-355">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="4dc98-356">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="4dc98-356">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="4dc98-357">適用於 Windows 市集應用程式的概觀</span><span class="sxs-lookup"><span data-stu-id="4dc98-357">.NET For Windows Store apps overview</span></span>](https://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [<span data-ttu-id="4dc98-358">Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援</span><span class="sxs-lookup"><span data-stu-id="4dc98-358">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
