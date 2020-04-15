---
title: C# 保留屬性:全域屬性
ms.date: 04/09/2020
description: 屬性提供編譯器用於理解程式更多語意的中繼資料
ms.openlocfilehash: f855f32cd7349da34ffbd20fededdf42c3023938
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389853"
---
# <a name="reserved-attributes-assembly-level-attributes"></a><span data-ttu-id="e5430-103">保留屬性:程式集等級屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-103">Reserved attributes: Assembly level attributes</span></span>

<span data-ttu-id="e5430-104">大部分屬性會套用至特定語言項目 (例如類別或方法)；不過，有些屬性是全域屬性，其套用至整個組件或模組。</span><span class="sxs-lookup"><span data-stu-id="e5430-104">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="e5430-105">例如，<xref:System.Reflection.AssemblyVersionAttribute> 屬性可以用來將版本資訊內嵌到組件，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="e5430-105">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
```

<span data-ttu-id="e5430-106">全域屬性出現在任何頂級`using`指令之後的原始碼中,並在任何類型、模組或命名空間聲明之前顯示。</span><span class="sxs-lookup"><span data-stu-id="e5430-106">Global attributes appear in the source code after any top level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="e5430-107">全域屬性可以出現在多個原始程式檔中，但必須使用單一編譯階段編譯檔案。</span><span class="sxs-lookup"><span data-stu-id="e5430-107">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="e5430-108">Visual Studio 將全域屬性添加到 .NET Framework 專案中的AssemblyInfo.cs檔中。</span><span class="sxs-lookup"><span data-stu-id="e5430-108">Visual Studio adds global attributes to the AssemblyInfo.cs file in .NET Framework projects.</span></span> <span data-ttu-id="e5430-109">這些屬性不會添加到 .NET Core 專案中。</span><span class="sxs-lookup"><span data-stu-id="e5430-109">These attributes aren't added to .NET Core projects.</span></span>

<span data-ttu-id="e5430-110">組件屬性是提供組件相關資訊的值。</span><span class="sxs-lookup"><span data-stu-id="e5430-110">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="e5430-111">它們的分類如下：</span><span class="sxs-lookup"><span data-stu-id="e5430-111">They fall into the following categories:</span></span>

- <span data-ttu-id="e5430-112">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-112">Assembly identity attributes</span></span>
- <span data-ttu-id="e5430-113">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-113">Informational attributes</span></span>
- <span data-ttu-id="e5430-114">組件資訊清單屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-114">Assembly manifest attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="e5430-115">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-115">Assembly identity attributes</span></span>

<span data-ttu-id="e5430-116">三個具有強式名稱 (如果適用) 的屬性會判斷組件的識別：名稱、版本與文化特性。</span><span class="sxs-lookup"><span data-stu-id="e5430-116">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="e5430-117">這些屬性會形成組件的完整名稱，且在程式碼中參考組件時需要用到。</span><span class="sxs-lookup"><span data-stu-id="e5430-117">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="e5430-118">您可以使用屬性來設定組件的版本和文化特性。</span><span class="sxs-lookup"><span data-stu-id="e5430-118">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="e5430-119">但是,名稱值由編譯器、[程式集資訊對話框](/visualstudio/ide/reference/assembly-information-dialog-box)中的 Visual Studio IDE 或創建程式集時的程式集連結器 (Al.exe) 設置。</span><span class="sxs-lookup"><span data-stu-id="e5430-119">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created.</span></span> <span data-ttu-id="e5430-120">程式集名稱基於程式集清單。</span><span class="sxs-lookup"><span data-stu-id="e5430-120">The assembly name is based on the assembly manifest.</span></span> <span data-ttu-id="e5430-121"><xref:System.Reflection.AssemblyFlagsAttribute> 屬性指定組件的多個複本是否可以並存。</span><span class="sxs-lookup"><span data-stu-id="e5430-121">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="e5430-122">下表顯示識別屬性。</span><span class="sxs-lookup"><span data-stu-id="e5430-122">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="e5430-123">屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-123">Attribute</span></span>|<span data-ttu-id="e5430-124">目的</span><span class="sxs-lookup"><span data-stu-id="e5430-124">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="e5430-125">指定組件的版本。</span><span class="sxs-lookup"><span data-stu-id="e5430-125">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="e5430-126">指定組件所支援的文化特性。</span><span class="sxs-lookup"><span data-stu-id="e5430-126">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="e5430-127">指定是否支援在相同電腦上、相同處理程序中或相同應用程式定義域中並存執行組件。</span><span class="sxs-lookup"><span data-stu-id="e5430-127">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

## <a name="informational-attributes"></a><span data-ttu-id="e5430-128">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-128">Informational attributes</span></span>

<span data-ttu-id="e5430-129">您可以使用資訊屬性為程式集提供其他公司或產品資訊。</span><span class="sxs-lookup"><span data-stu-id="e5430-129">You use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="e5430-130">下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊屬性。</span><span class="sxs-lookup"><span data-stu-id="e5430-130">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="e5430-131">屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-131">Attribute</span></span>|<span data-ttu-id="e5430-132">目的</span><span class="sxs-lookup"><span data-stu-id="e5430-132">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="e5430-133">指定程式集清單的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="e5430-133">Specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="e5430-134">指定程式集清單的商標。</span><span class="sxs-lookup"><span data-stu-id="e5430-134">Specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="e5430-135">指定程式集清單的資訊版本。</span><span class="sxs-lookup"><span data-stu-id="e5430-135">Specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="e5430-136">指定程式集清單的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="e5430-136">Specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="e5430-137">定義自訂屬性，以指定組件資訊清單的版權。</span><span class="sxs-lookup"><span data-stu-id="e5430-137">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="e5430-138">為 Win32 檔版本資源設置特定的版本號。</span><span class="sxs-lookup"><span data-stu-id="e5430-138">Sets a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="e5430-139">表示組件是否符合 Common Language Specification (CLS) 規範。</span><span class="sxs-lookup"><span data-stu-id="e5430-139">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="e5430-140">組件資訊清單屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-140">Assembly manifest attributes</span></span>

<span data-ttu-id="e5430-141">您可以使用組件資訊清單屬性，在組件資訊清單中提供資訊。</span><span class="sxs-lookup"><span data-stu-id="e5430-141">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="e5430-142">這些屬性包括標題、說明、預設別名和配置。</span><span class="sxs-lookup"><span data-stu-id="e5430-142">The attributes include title, description, default alias, and configuration.</span></span> <span data-ttu-id="e5430-143">下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊清單屬性。</span><span class="sxs-lookup"><span data-stu-id="e5430-143">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="e5430-144">屬性</span><span class="sxs-lookup"><span data-stu-id="e5430-144">Attribute</span></span>|<span data-ttu-id="e5430-145">目的</span><span class="sxs-lookup"><span data-stu-id="e5430-145">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="e5430-146">指定程式集清單的程式集標題。</span><span class="sxs-lookup"><span data-stu-id="e5430-146">Specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="e5430-147">指定程式集清單的程式集說明。</span><span class="sxs-lookup"><span data-stu-id="e5430-147">Specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="e5430-148">為程式集清單指定程式集配置(如零售或調試)。</span><span class="sxs-lookup"><span data-stu-id="e5430-148">Specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="e5430-149">定義組件資訊清單的易記預設別名。</span><span class="sxs-lookup"><span data-stu-id="e5430-149">Defines a friendly default alias for an assembly manifest</span></span>|
