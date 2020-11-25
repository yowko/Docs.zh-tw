---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031989"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a>StartInfo 會針對您未啟動的進程擲回 InvalidOperationException

讀取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動之進程的屬性會擲回 <xref:System.InvalidOperationException> 。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，存取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動之進程的屬性會傳回虛擬 <xref:System.Diagnostics.ProcessStartInfo> 物件。 除了以外，虛擬物件會包含其所有屬性的預設值 <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> 。

從 .NET Core 1.0 開始，如果您 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 針對未啟動的進程讀取屬性 (也就是呼叫 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>) ， <xref:System.InvalidOperationException> 則會擲回。

#### <a name="version-introduced"></a>引進的版本

1.0

#### <a name="recommended-action"></a>建議的動作

請勿存取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動的進程屬性。 例如，請勿針對所傳回的進程讀取這個屬性 <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
