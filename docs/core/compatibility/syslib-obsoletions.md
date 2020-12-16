---
title: .NET 5 + 中已淘汰的功能
description: 瞭解在 .NET 5.0 和更新版本中標示為過時的 Api，這些 Api 會產生 SYSLIB 編譯器警告。
ms.date: 10/20/2020
ms.openlocfilehash: 336958c93e3db8f66cfbec89476a666e5e103b70
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593301"
---
# <a name="obsolete-features-in-net-5"></a><span data-ttu-id="c7e85-103">.NET 5 中已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="c7e85-103">Obsolete features in .NET 5</span></span>

<span data-ttu-id="c7e85-104">從 .NET 5.0 開始，某些新標記為過時的 Api 會使用上的兩個新屬性 <xref:System.ObsoleteAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="c7e85-104">Starting in .NET 5.0, some APIs that are newly marked as obsolete make use of two new properties on <xref:System.ObsoleteAttribute>.</span></span>

- <span data-ttu-id="c7e85-105"><xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType>屬性會指示編譯器使用自訂診斷識別碼產生組建警告。</span><span class="sxs-lookup"><span data-stu-id="c7e85-105">The <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> property tells the compiler to generate build warnings using a custom diagnostic ID.</span></span> <span data-ttu-id="c7e85-106">自訂識別碼可讓您明確地隱藏 obsoletion 警告，以及彼此分開隱藏。</span><span class="sxs-lookup"><span data-stu-id="c7e85-106">The custom ID allows for obsoletion warning to be suppressed specifically and separately from one another.</span></span> <span data-ttu-id="c7e85-107">在 .NET 5 + obsoletions 的情況下，自訂診斷識別碼的格式為 `SYSLIBxxxx` 。</span><span class="sxs-lookup"><span data-stu-id="c7e85-107">In the case of the .NET 5+ obsoletions, the format for the custom diagnostic ID is `SYSLIBxxxx`.</span></span>

- <span data-ttu-id="c7e85-108"><xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType>屬性會指示編譯器包含 URL 連結，以深入瞭解 obsoletion。</span><span class="sxs-lookup"><span data-stu-id="c7e85-108">The <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> property tells the compiler to include a URL link to learn more about the obsoletion.</span></span>

<span data-ttu-id="c7e85-109">如果您因為使用過時的 API 而遇到組建警告或錯誤，請遵循 [參考](#reference) 一節中所列的診斷識別碼所提供的特定指導方針。</span><span class="sxs-lookup"><span data-stu-id="c7e85-109">If you encounter build warnings or errors due to usage of an obsolete API, follow the specific guidance provided for the diagnostic ID listed in the [Reference](#reference) section.</span></span> <span data-ttu-id="c7e85-110">針對過時的類型或成員， *無法* 使用 [標準診斷識別碼 (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) 來抑制這些 obsoletions 的警告或錯誤;請改用自訂 `SYSLIBxxxx` 診斷識別碼值。</span><span class="sxs-lookup"><span data-stu-id="c7e85-110">Warnings or errors for these obsoletions *can't* be suppressed using the [standard diagnostic ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID values instead.</span></span> <span data-ttu-id="c7e85-111">如需詳細資訊，請參閱 [隱藏警告](#suppress-warnings)。</span><span class="sxs-lookup"><span data-stu-id="c7e85-111">For more information, see [Suppress warnings](#suppress-warnings).</span></span>

## <a name="reference"></a><span data-ttu-id="c7e85-112">參考</span><span class="sxs-lookup"><span data-stu-id="c7e85-112">Reference</span></span>

<span data-ttu-id="c7e85-113">下表提供 `SYSLIBxxxx` .net 5 + 中 obsoletions 的索引。</span><span class="sxs-lookup"><span data-stu-id="c7e85-113">The following table provides an index to the `SYSLIBxxxx` obsoletions in .NET 5+.</span></span>

| <span data-ttu-id="c7e85-114">診斷識別碼</span><span class="sxs-lookup"><span data-stu-id="c7e85-114">Diagnostic ID</span></span> | <span data-ttu-id="c7e85-115">描述</span><span class="sxs-lookup"><span data-stu-id="c7e85-115">Description</span></span> |
| - | - |
| [<span data-ttu-id="c7e85-116">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="c7e85-116">SYSLIB0001</span></span>](syslib-warnings/syslib0001.md) | <span data-ttu-id="c7e85-117">UTF-7 編碼並不安全，因此不應該使用。</span><span class="sxs-lookup"><span data-stu-id="c7e85-117">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="c7e85-118">請考慮改為使用 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="c7e85-118">Consider using UTF-8 instead.</span></span> |
| [<span data-ttu-id="c7e85-119">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="c7e85-119">SYSLIB0002</span></span>](syslib-warnings/syslib0002.md) | <span data-ttu-id="c7e85-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 執行時間不接受，而且不得使用。</span><span class="sxs-lookup"><span data-stu-id="c7e85-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> |
| [<span data-ttu-id="c7e85-121">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="c7e85-121">SYSLIB0003</span></span>](syslib-warnings/syslib0003.md) | <span data-ttu-id="c7e85-122">執行時間不支援或不接受代碼啟用安全性 (CAS) 。</span><span class="sxs-lookup"><span data-stu-id="c7e85-122">Code access security (CAS) is not supported or honored by the runtime.</span></span> |
| [<span data-ttu-id="c7e85-123">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="c7e85-123">SYSLIB0004</span></span>](syslib-warnings/syslib0004.md) | <span data-ttu-id="c7e85-124">不支援 (CER) 功能的限制執列區域。</span><span class="sxs-lookup"><span data-stu-id="c7e85-124">The constrained execution region (CER) feature is not supported.</span></span> |
| [<span data-ttu-id="c7e85-125">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="c7e85-125">SYSLIB0005</span></span>](syslib-warnings/syslib0005.md) | <span data-ttu-id="c7e85-126">不支援全域組件快取 (GAC) 。</span><span class="sxs-lookup"><span data-stu-id="c7e85-126">The global assembly cache (GAC) is not supported.</span></span> |
| [<span data-ttu-id="c7e85-127">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="c7e85-127">SYSLIB0006</span></span>](syslib-warnings/syslib0006.md) | <span data-ttu-id="c7e85-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> 不受支援，而且會擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="c7e85-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="c7e85-129">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="c7e85-129">SYSLIB0007</span></span>](syslib-warnings/syslib0007.md) | <span data-ttu-id="c7e85-130">不支援此密碼編譯演算法的預設執行。</span><span class="sxs-lookup"><span data-stu-id="c7e85-130">The default implementation of this cryptography algorithm is not supported.</span></span> |
| [<span data-ttu-id="c7e85-131">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="c7e85-131">SYSLIB0008</span></span>](syslib-warnings/syslib0008.md) | <span data-ttu-id="c7e85-132"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator>不支援並擲回 API <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="c7e85-132">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="c7e85-133">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="c7e85-133">SYSLIB0009</span></span>](syslib-warnings/syslib0009.md) | <span data-ttu-id="c7e85-134"><xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>和 <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> 方法不受支援，而且會擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="c7e85-134">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="c7e85-135">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="c7e85-135">SYSLIB0010</span></span>](syslib-warnings/syslib0010.md) | <span data-ttu-id="c7e85-136">某些遠端 Api 不受支援且會擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="c7e85-136">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="c7e85-137">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="c7e85-137">SYSLIB0011</span></span>](syslib-warnings/syslib0011.md) | <span data-ttu-id="c7e85-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 序列化已過時，不應該使用。</span><span class="sxs-lookup"><span data-stu-id="c7e85-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> |
| [<span data-ttu-id="c7e85-139">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="c7e85-139">SYSLIB0012</span></span>](syslib-warnings/syslib0012.md) | <span data-ttu-id="c7e85-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> 和 <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> 只包含 .NET Framework 相容性。</span><span class="sxs-lookup"><span data-stu-id="c7e85-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="c7e85-141">請改用 <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c7e85-141">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> |

## <a name="suppress-warnings"></a><span data-ttu-id="c7e85-142">隱藏警告</span><span class="sxs-lookup"><span data-stu-id="c7e85-142">Suppress warnings</span></span>

<span data-ttu-id="c7e85-143">如果您必須使用已淘汰的 Api，且 `SYSLIBxxxx` 診斷未顯示為錯誤，您可以在程式碼或專案檔中隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="c7e85-143">If you must use the obsolete APIs and the `SYSLIBxxxx` diagnostic does not surface as an error, you can suppress the warning in code or in your project file.</span></span>

<span data-ttu-id="c7e85-144">在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="c7e85-144">In code:</span></span>

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

<span data-ttu-id="c7e85-145">專案檔：</span><span class="sxs-lookup"><span data-stu-id="c7e85-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> <span data-ttu-id="c7e85-146">以這種方式隱藏警告只會停用您指定的 obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="c7e85-146">Suppressing warnings in this way only disables the obsoletion warnings you specify.</span></span> <span data-ttu-id="c7e85-147">它不會停用任何其他警告，包括具有不同診斷識別碼的 obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="c7e85-147">It doesn't disable any other warnings, including obsoletion warnings with different diagnostic IDs.</span></span>
