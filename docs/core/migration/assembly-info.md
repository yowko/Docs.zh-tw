---
title: AssemblyInfo 屬性
description: 瞭解元件屬性，以及它們如何對應至 .NET Core 2.1 和更新版本中的 MSBuild 屬性。
ms.topic: reference
ms.date: 01/08/2021
ms.openlocfilehash: a2c431b3fe3da428f21582624ca5f357887e2815
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192885"
---
# <a name="map-assemblyinfo-attributes-to-properties"></a><span data-ttu-id="cc93f-103">將 AssemblyInfo 屬性對應至屬性</span><span class="sxs-lookup"><span data-stu-id="cc93f-103">Map AssemblyInfo attributes to properties</span></span>

<span data-ttu-id="cc93f-104">通常存在於 .NET Core 2.0 和較早版本之 *AssemblyInfo* 檔中的 [元件屬性](../../standard/assembly/set-attributes.md)，會自動從 MSBuild 屬性產生，從 .net core 2.1 開始。</span><span class="sxs-lookup"><span data-stu-id="cc93f-104">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file in .NET Core 2.0 and earlier versions are automatically generated from MSBuild properties, starting in .NET Core 2.1.</span></span>

## <a name="properties-per-attribute"></a><span data-ttu-id="cc93f-105">每個屬性 (Attribute) 的屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="cc93f-105">Properties per attribute</span></span>

<span data-ttu-id="cc93f-106">如下表所示，每個屬性都有對應的屬性，可控制其內容，另一個則停用其產生：</span><span class="sxs-lookup"><span data-stu-id="cc93f-106">As shown in the following table, each attribute has a corresponding property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="cc93f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="cc93f-107">Attribute</span></span>                                                      | <span data-ttu-id="cc93f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="cc93f-108">Property</span></span>               | <span data-ttu-id="cc93f-109">要停用的屬性</span><span class="sxs-lookup"><span data-stu-id="cc93f-109">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="cc93f-110">注意：</span><span class="sxs-lookup"><span data-stu-id="cc93f-110">Notes:</span></span>

- <span data-ttu-id="cc93f-111">`AssemblyVersion` 而且 `FileVersion` 預設為 `$(Version)` 不含尾碼的值。</span><span class="sxs-lookup"><span data-stu-id="cc93f-111">`AssemblyVersion` and `FileVersion` default to the value of `$(Version)` without the suffix.</span></span> <span data-ttu-id="cc93f-112">例如，如果 `$(Version)` 是 `1.2.3-beta.4`，則此值會是 `1.2.3`。</span><span class="sxs-lookup"><span data-stu-id="cc93f-112">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="cc93f-113">`InformationalVersion` 預設為 `$(Version)` 的值。</span><span class="sxs-lookup"><span data-stu-id="cc93f-113">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="cc93f-114">如果 `$(SourceRevisionId)` 屬性存在，則會附加至 `InformationalVersion` 。</span><span class="sxs-lookup"><span data-stu-id="cc93f-114">If the `$(SourceRevisionId)` property is present, it's appended to `InformationalVersion`.</span></span> <span data-ttu-id="cc93f-115">您可以使用停用此行為 `IncludeSourceRevisionInInformationalVersion` 。</span><span class="sxs-lookup"><span data-stu-id="cc93f-115">You can disable this behavior using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="cc93f-116">也會針對 NuGet 中繼資料使用 `Copyright` 和 `Description` 屬性。</span><span class="sxs-lookup"><span data-stu-id="cc93f-116">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="cc93f-117">`Configuration`預設為的 `Debug` 會與所有 MSBuild 目標共用。</span><span class="sxs-lookup"><span data-stu-id="cc93f-117">`Configuration`, which defaults to `Debug`, is shared with all MSBuild targets.</span></span> <span data-ttu-id="cc93f-118">您可以透過 `--configuration` 命令的選項 `dotnet` （例如 [dotnet pack](../tools/dotnet-pack.md)）來設定它。</span><span class="sxs-lookup"><span data-stu-id="cc93f-118">You can set it via the `--configuration` option of `dotnet` commands, for example, [dotnet pack](../tools/dotnet-pack.md).</span></span>

## <a name="generateassemblyinfo"></a><span data-ttu-id="cc93f-119">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="cc93f-119">GenerateAssemblyInfo</span></span>

<span data-ttu-id="cc93f-120">啟用或停用 AssemblyInfo 產生的布林值。</span><span class="sxs-lookup"><span data-stu-id="cc93f-120">A Boolean that enables or disables the AssemblyInfo generation.</span></span> <span data-ttu-id="cc93f-121">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cc93f-121">The default value is `true`.</span></span>

## <a name="generatedassemblyinfofile"></a><span data-ttu-id="cc93f-122">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="cc93f-122">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="cc93f-123">產生的元件資訊檔案的相對或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="cc93f-123">The relative or absolute path of the generated assembly info file.</span></span> <span data-ttu-id="cc93f-124">預設為名為 *[專案名稱] 的檔案。AssemblyInfo.[cs | vb]* 在 `$(IntermediateOutputPath)` (*Obj*) 目錄中。</span><span class="sxs-lookup"><span data-stu-id="cc93f-124">Defaults to a file named *[project-name].AssemblyInfo.[cs|vb]* in the `$(IntermediateOutputPath)` (*obj*) directory.</span></span>
