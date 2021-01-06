---
ms.openlocfilehash: dcc64fe651b219ff1416c0afcdb4c6d275160f4b
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97911651"
---
### <a name="change-in-default-value-of-useshellexecute"></a>UseShellExecute 預設值的變更

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 的預設值是 `false` 在 .Net Core 上。 在 .NET Framework 上，其預設值為 `true` 。

#### <a name="change-description"></a>變更描述

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 可讓您直接啟動應用程式（例如，使用 `Process.Start("mspaint.exe")` 啟動油漆的程式碼）。 如果設定為，它也可讓您間接啟動相關聯的應用程式 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` 。 在 .NET Framework 上，的預設值 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 是 `true` ，這表示 `Process.Start("mytextfile.txt")` 如果您已使用該編輯器將 *.txt* 檔案相關聯，像這樣的程式碼將會啟動 [記事本]。 若要避免在 .NET Framework 上間接啟動應用程式，您必須明確地將設定 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。 在 .NET Core 上，的預設值 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。 這表示當您呼叫時，關聯的應用程式預設不會啟動 `Process.Start` 。

上的下列屬性 <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> 只有在為時才能正常運作 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` ：

- <xref:System.Diagnostics.ProcessStartInfo.CreateNoWindow?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.ErrorDialog?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.Verb?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.

基於效能考慮，.NET Core 引進了這項變更。 通常 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> 是用來直接啟動應用程式。 直接啟動應用程式並不需要包含 Windows shell，並產生相關聯的效能成本。 為了讓此預設案例更快，.NET Core 會將的預設值變更 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> 為 `false` 。 您可以視需要加入宣告較慢的路徑。

#### <a name="version-introduced"></a>引進的版本

2.1

> [!NOTE]
> 在舊版的 .NET Core 中， `UseShellExecute` 並未針對 Windows 執行。

#### <a name="recommended-action"></a>建議的動作

如果您的應用程式依賴舊的行為， <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> 請 <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> 在物件上呼叫並將設定為 `true` <xref:System.Diagnostics.ProcessStartInfo> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
