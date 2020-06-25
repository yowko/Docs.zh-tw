---
ms.openlocfilehash: d85fb8df7afdc5f4c3faecebcd24d11677798bc9
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365607"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a>已移除 DotNet PlatformAbstractions 套件

將不會產生任何新版本的[DotNet PlatformAbstractions NuGet 套件](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/)。

#### <a name="change-description"></a>變更描述

之前，新版本的連結 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 庫是與新版的 .Net Core 一起產生的。 未來，程式庫不會新增任何新功能，也不會發行任何新的主要版本。 不過，現有的程式庫版本仍可繼續使用並提供服務。

連結 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 庫與已在系統命名空間中建立的 api 重迭 \* 。 此外，某些 <xref:Microsoft.DotNet.PlatformAbstractions> api 的設計並不是以相同層級的審查和長期可支援性做為系統的其餘部分。 \*Api. 例如，會 <xref:Microsoft.DotNet.PlatformAbstractions> 使用 `Platform` 列舉來描述目前的作業系統平臺。 設計 API 時，已明確拒絕此列舉設計 <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> ，以允許新的平臺和未來的彈性。

程式庫所啟用的案例 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 現在不會發生。 即使在 .NET 5.0 和更新版本中，現有的版本仍可繼續作用，而且將會與舊版的 .NET Core 一起提供服務。 不過，新功能不會新增至程式庫。 相反地，新功能將會新增至其他程式庫和 Api。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 6

#### <a name="recommended-action"></a>建議的動作

- 如果符合您的需求，您可以繼續使用較舊版本的程式庫。

- 如果較舊的版本不符合您的需求，請將 api 的使用方式取代為 `PlatformAbstractions` 建議的替代專案。

  | `PlatformAbstractions`API | 建議取代 |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> 和 <xref:System.Environment.OSVersion?displayProperty=nameWithType> |

  > [!NOTE]
  > 和的大部分使用 `RuntimeEnvironment.OperatingSystem` 案例 `RuntimeEnvironment.OperatingSystemVersion` 都是為了顯示用途，例如，顯示給使用者、記錄和遙測。 不建議根據作業系統（OS）版本來進行執行時間決策。 <xref:System.Environment.OSVersion?displayProperty=nameWithType>現在會傳回 Windows 和 macOS 作業系統的正確版本。 不過，對於大部分的 Unix 散發套件而言，視為「作業系統版本」並不簡單。 例如，它可能是 Linux 核心版本，也可能是散發版本版本。 適用于大部分的 Unix 平臺， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 並 <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> 傳回所傳回的版本 `uname` 。 若要取得 Linux 散發版本名稱和版本資訊，建議的方法是讀取 */etc/os-release*檔案。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

#### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
