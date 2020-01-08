---
ms.openlocfilehash: 7c0930f6606aa96d2863dc740aef8e9cab724b37
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344890"
---
### <a name="change-in-default-value-of-useshellexecute"></a>預設值為 UseShellExecute 的變更

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 在 .NET Core 上有 `false` 的預設值。 在 .NET Framework 上，其預設值為 `true`。

#### <a name="change-description"></a>變更描述

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 可讓您直接啟動應用程式（例如，使用啟動油漆的 `Process.Start("mspaint.exe")` 這類程式碼）。 如果 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 設定為 `true`，它也可讓您間接啟動相關聯的應用程式。 在 .NET Framework 上，<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值是 `true`，這表示如果您已將 *.txt*檔案與該編輯器建立關聯，`Process.Start("mytextfile.txt")` 之類的程式碼就會啟動「記事本」。 若要防止在 .NET Framework 上間接啟動應用程式，您必須明確地將 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 設定為 [`false`]。 在 .NET Core 上，<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值是 `false`。 這表示，當您呼叫 `Process.Start`時，預設不會啟動相關聯的應用程式。

基於效能考慮，這項變更是在 .NET Core 中引進。 一般來說，<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 是用來直接啟動應用程式。 直接啟動應用程式不需要包含 Windows shell，而且會產生相關聯的效能成本。 為了讓此預設案例更快速，.NET Core 會將 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值變更為 `false`。 您可以視需要選擇較慢的路徑。

#### <a name="version-introduced"></a>引進的版本

2.1

> [!NOTE]
> 在舊版的 .NET Core 中，不會為 Windows 執行 `UseShellExecute`。

#### <a name="recommended-action"></a>建議的動作

如果您的應用程式依賴舊的行為，請呼叫 <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType>，並 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> 設定為 <xref:System.Diagnostics.ProcessStartInfo> 物件上的 `true`。

#### <a name="category"></a>分類

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
