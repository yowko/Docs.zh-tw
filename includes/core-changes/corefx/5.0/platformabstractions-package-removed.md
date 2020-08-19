---
ms.openlocfilehash: a635e2ed6a735b5234c92fd8f5ffa1685fe9373e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558166"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a>已移除 DotNet PlatformAbstractions 套件

將不會產生任何新版本的 [DotNet. PlatformAbstractions NuGet 套件](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) 。

#### <a name="change-description"></a>變更描述

先前，新版本的連結 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 庫是隨著新版本的 .Net Core 一起產生。 未來，將不會在程式庫中新增任何新功能，也不會發行任何新的主要版本。 不過，現有的程式庫版本將繼續運作並提供服務。

連結 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 庫與已在 system.string 中建立的 api 重迭 \* 。 此外，有些 <xref:Microsoft.DotNet.PlatformAbstractions> api 的設計並不是使用與系統其餘部分相同的審查層級和長期可支援性。 \* Api。 例如，會 <xref:Microsoft.DotNet.PlatformAbstractions> 使用 `Platform` 列舉來描述目前的作業系統平臺。 設計 API 時，已明確拒絕此列舉設計 <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> ，以允許新的平臺和未來的彈性。

程式庫所啟用的案例 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 現在可能沒有它。 現有的版本會繼續運作，即使是在 .NET 5.0 和更新版本中，也會隨著舊版的 .NET Core 服務。 但是，不會將新功能新增至程式庫。 相反地，會將新功能新增至其他程式庫和 Api。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 6

#### <a name="recommended-action"></a>建議的動作

- 如果程式庫符合您的需求，則可以繼續使用較舊版本的程式庫。

- 如果較舊的版本不符合您的需求，請 `PlatformAbstractions` 使用建議的取代取代 api 的使用方式。

  | `PlatformAbstractions` Api | 建議取代 |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> 和 <xref:System.Environment.OSVersion?displayProperty=nameWithType> |

  > [!NOTE]
  > 和的大部分使用 `RuntimeEnvironment.OperatingSystem` 案例 `RuntimeEnvironment.OperatingSystemVersion` 都是基於顯示目的，例如顯示給使用者、記錄和遙測。 不建議您根據作業系統) 版本 (作業系統進行執行時間決策。 <xref:System.Environment.OSVersion?displayProperty=nameWithType> 現在會傳回適用于 Windows 和 macOS 作業系統 [的正確版本](../../../../docs/core/compatibility/corefx.md#environmentosversion-returns-the-correct-operating-system-version) 。 不過，對於大多數的 Unix 散發套件來說，視為「作業系統版本」的內容並不直接。 例如，它可以是 Linux 核心版本，也可以是發行版本版本。 適用于大部分的 Unix 平臺， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 並 <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> 傳回所傳回的版本 `uname` 。 若要取得 Linux 發行版本名稱和版本資訊，建議的方法是讀取 */etc/os-release* 檔案。

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
