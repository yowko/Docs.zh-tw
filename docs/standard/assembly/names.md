---
title: 組件名稱
description: 瞭解 .NET 元件名稱及其對元件範圍的影響，以及應用程式的使用方式，並瞭解 FullName 屬性。
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET], assemblies
- assemblies [.NET], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 9aa94b4ee54c0a663c9f38392d37369af9f27e48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731445"
---
# <a name="assembly-names"></a><span data-ttu-id="cb9cd-103">組件名稱</span><span class="sxs-lookup"><span data-stu-id="cb9cd-103">Assembly names</span></span>

<span data-ttu-id="cb9cd-104">組件的名稱儲存在中繼資料內，而且對組件範圍具有重大影響，並供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-104">An assembly's name is stored in metadata and has a significant impact on the assembly's scope and use by an application.</span></span> <span data-ttu-id="cb9cd-105">強式名稱元件具有完整名稱，其中包含元件的名稱、文化特性、公開金鑰、版本號碼，以及選擇性的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-105">A strong-named assembly has a fully qualified name that includes the assembly's name, culture, public key, version number, and, optionally, processor architecture.</span></span> <span data-ttu-id="cb9cd-106">您 <xref:System.Reflection.Assembly.FullName%2A> 可以使用屬性來取得已載入元件的完整名稱，通常稱為顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-106">Use the <xref:System.Reflection.Assembly.FullName%2A> property to obtain the fully qualified name, frequently referred to as the display name, for loaded assemblies.</span></span>

<span data-ttu-id="cb9cd-107">執行時間會使用名稱資訊來找出元件，並將它與具有相同名稱的其他元件區別。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-107">The runtime uses the name information to locate the assembly and differentiate it from other assemblies with the same name.</span></span> <span data-ttu-id="cb9cd-108">例如，稱為 `myTypes` 的強式名稱組件的完整名稱可能如下：</span><span class="sxs-lookup"><span data-stu-id="cb9cd-108">For example, a strong-named assembly called `myTypes` could have the following fully qualified name:</span></span>

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

<span data-ttu-id="cb9cd-109">在此範例中，完整名稱表示 `myTypes` 元件具有具有公開金鑰 token 的強式名稱、具有適用于美國英文的文化特性值，且具有1.0.1234.0 的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-109">In this example, the fully qualified name indicates that the `myTypes` assembly has a strong name with a public key token, has the culture value for United States English, and has a version number of 1.0.1234.0.</span></span> <span data-ttu-id="cb9cd-110">它的處理器架構是 `msil` ，這表示它會及時 (JIT) 編譯成32位程式碼或64位程式碼，視作業系統和處理器而定。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-110">Its processor architecture is `msil`, which means that it will be just-in-time (JIT)-compiled to 32-bit code or 64-bit code depending on the operating system and processor.</span></span>

> [!TIP]
> <span data-ttu-id="cb9cd-111">此 `ProcessorArchitecture` 資訊允許處理器特定版本的元件。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-111">The `ProcessorArchitecture` information allows processor-specific versions of assemblies.</span></span> <span data-ttu-id="cb9cd-112">您可以建立組件的版本，其身分識別只有處理器架構不同，例如 32 位元和 64 位元處理器特定版本。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-112">You can create versions of an assembly whose identity differs only by processor architecture, for example 32-bit and 64-bit processor-specific versions.</span></span> <span data-ttu-id="cb9cd-113">強式名稱不需要處理器架構。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-113">Processor architecture is not required for strong names.</span></span> <span data-ttu-id="cb9cd-114">如需詳細資訊，請參閱<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-114">For more information, see <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="cb9cd-115">要求組件中類型的程式碼必須使用完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-115">Code that requests types in an assembly must use a fully qualified assembly name.</span></span> <span data-ttu-id="cb9cd-116">這稱為完整繫結。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-116">This is called fully qualified binding.</span></span> <span data-ttu-id="cb9cd-117">參考 .NET Framework 中的元件時，不允許只指定元件名稱的部分系結。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-117">Partial binding, which specifies only an assembly name, is not permitted when referencing assemblies in .NET Framework.</span></span>

 <span data-ttu-id="cb9cd-118">組成 .NET Framework 之元件的所有元件參考也必須包含元件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-118">All assembly references to assemblies that make up .NET Framework must also contain the fully qualified name of the assembly.</span></span> <span data-ttu-id="cb9cd-119">例如，版本1.0 的資料 .NET Framework 元件的參考包括：</span><span class="sxs-lookup"><span data-stu-id="cb9cd-119">For example, a reference to the System.Data .NET Framework assembly for version 1.0 would include:</span></span>

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

<span data-ttu-id="cb9cd-120">版本會對應至 .NET Framework 1.0 版隨附的所有 .NET Framework 元件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-120">The version corresponds to the version number of all .NET Framework assemblies that shipped with .NET Framework version 1.0.</span></span> <span data-ttu-id="cb9cd-121">針對 .NET Framework 組件，文化特性值一律為中性，而且公開金鑰與上述範例所示相同。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-121">For .NET Framework assemblies, the culture value is always neutral, and the public key is the same as shown in the above example.</span></span>

 <span data-ttu-id="cb9cd-122">例如，若要在組態檔中新增組件參考來設定追蹤接聽程式，您將包括系統 .NET Framework 組件的完整名稱：</span><span class="sxs-lookup"><span data-stu-id="cb9cd-122">For example, to add an assembly reference in a configuration file to set up a trace listener, you would include the fully qualified name of the system .NET Framework assembly:</span></span>

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> <span data-ttu-id="cb9cd-123">繫結至組件時，執行階段會將組件名稱視為不區分大小寫，但會保留組件名稱中所使用的大小寫。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-123">The runtime treats assembly names as case-insensitive when binding to an assembly, but preserves whatever case is used in an assembly name.</span></span> <span data-ttu-id="cb9cd-124">Windows SDK 中的數個工具會以區分大小寫的方式處理組件名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-124">Several tools in the Windows SDK handle assembly names as case-sensitive.</span></span> <span data-ttu-id="cb9cd-125">為了獲得最佳結果，請如同其區分大小寫一樣地管理組件名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-125">For best results, manage assembly names as though they were case-sensitive.</span></span>

## <a name="name-application-components"></a><span data-ttu-id="cb9cd-126">命名應用程式元件</span><span class="sxs-lookup"><span data-stu-id="cb9cd-126">Name application components</span></span>

 <span data-ttu-id="cb9cd-127">判斷組件的身分識別時，執行階段不會考慮檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-127">The runtime does not consider the file name when determining an assembly's identity.</span></span> <span data-ttu-id="cb9cd-128">執行階段必須知道包含組件名稱、版本、文化特性和強式名稱的組件身分識別。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-128">The assembly identity, which consists of the assembly name, version, culture, and strong name, must be clear to the runtime.</span></span>

 <span data-ttu-id="cb9cd-129">例如，如果您有一個稱為 *myAssembly.exe* 的元件，而該元件參考稱為 *myAssembly.dll* 的元件，則系結會在您執行 *myAssembly.exe* 時正確進行。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-129">For example, if you have an assembly called *myAssembly.exe* that references an assembly called *myAssembly.dll*, binding occurs correctly if you execute *myAssembly.exe*.</span></span> <span data-ttu-id="cb9cd-130">但是，如果另一個應用程式使用方法執行 *myAssembly.exe* <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> ，則運行 `myAssembly` 時間會判斷當 *myAssembly.exe* 要求系結至時，已經載入 `myAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-130">However, if another application executes *myAssembly.exe* using the method <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, the runtime determines that `myAssembly` is already loaded when *myAssembly.exe* requests binding to `myAssembly`.</span></span> <span data-ttu-id="cb9cd-131">在此情況下，絕對不會載入 *myAssembly.dll* 。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-131">In this case, *myAssembly.dll* is never loaded.</span></span> <span data-ttu-id="cb9cd-132">因為 *myAssembly.exe* 不包含所要求的型別，所以 <xref:System.TypeLoadException> 會發生。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-132">Because *myAssembly.exe* does not contain the requested type, a <xref:System.TypeLoadException> occurs.</span></span>

 <span data-ttu-id="cb9cd-133">若要避免這個問題，請確定構成應用程式的組件沒有相同的組件名稱，或將同名的組件放在不同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-133">To avoid this problem, make sure the assemblies that make up your application do not have the same assembly name or place assemblies with the same name in different directories.</span></span>

> [!NOTE]
> <span data-ttu-id="cb9cd-134">在 .NET Framework 中，如果您將強式名稱的元件放在全域組件快取中，元件的檔案名必須符合元件名稱，而不包含副檔名，例如 *.exe* 或 *.dll*。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-134">In .NET Framework, if you put a strong-named assembly in the global assembly cache, the assembly's file name must match the assembly name, not including the file name extension, such as *.exe* or *.dll*.</span></span> <span data-ttu-id="cb9cd-135">例如，如果元件的檔案名是 *myAssembly.dll*，元件名稱必須是 `myAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-135">For example, if the file name of an assembly is *myAssembly.dll*, the assembly name must be `myAssembly`.</span></span> <span data-ttu-id="cb9cd-136">只有在根應用程式目錄中部署的私用組件才能具有與檔案名稱不同的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="cb9cd-136">Private assemblies deployed only in the root application directory can have an assembly name that is different from the file name.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb9cd-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb9cd-137">See also</span></span>

- [<span data-ttu-id="cb9cd-138">如何：決定元件的完整名稱</span><span class="sxs-lookup"><span data-stu-id="cb9cd-138">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)
- [<span data-ttu-id="cb9cd-139">建立組件</span><span class="sxs-lookup"><span data-stu-id="cb9cd-139">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="cb9cd-140">強式名稱組件</span><span class="sxs-lookup"><span data-stu-id="cb9cd-140">Strong-named assemblies</span></span>](strong-named.md)
- [<span data-ttu-id="cb9cd-141">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="cb9cd-141">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="cb9cd-142">執行時間如何找出元件</span><span class="sxs-lookup"><span data-stu-id="cb9cd-142">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
