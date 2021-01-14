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
# <a name="map-assemblyinfo-attributes-to-properties"></a>將 AssemblyInfo 屬性對應至屬性

通常存在於 .NET Core 2.0 和較早版本之 *AssemblyInfo* 檔中的 [元件屬性](../../standard/assembly/set-attributes.md)，會自動從 MSBuild 屬性產生，從 .net core 2.1 開始。

## <a name="properties-per-attribute"></a>每個屬性 (Attribute) 的屬性 (Property)

如下表所示，每個屬性都有對應的屬性，可控制其內容，另一個則停用其產生：

| 屬性                                                      | 屬性               | 要停用的屬性                             |
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

注意：

- `AssemblyVersion` 而且 `FileVersion` 預設為 `$(Version)` 不含尾碼的值。 例如，如果 `$(Version)` 是 `1.2.3-beta.4`，則此值會是 `1.2.3`。
- `InformationalVersion` 預設為 `$(Version)` 的值。
- 如果 `$(SourceRevisionId)` 屬性存在，則會附加至 `InformationalVersion` 。 您可以使用停用此行為 `IncludeSourceRevisionInInformationalVersion` 。
- 也會針對 NuGet 中繼資料使用 `Copyright` 和 `Description` 屬性。
- `Configuration`預設為的 `Debug` 會與所有 MSBuild 目標共用。 您可以透過 `--configuration` 命令的選項 `dotnet` （例如 [dotnet pack](../tools/dotnet-pack.md)）來設定它。

## <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

啟用或停用 AssemblyInfo 產生的布林值。 預設值是 `true`。

## <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

產生的元件資訊檔案的相對或絕對路徑。 預設為名為 *[專案名稱] 的檔案。AssemblyInfo.[cs | vb]* 在 `$(IntermediateOutputPath)` (*Obj*) 目錄中。
