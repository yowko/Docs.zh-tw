---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420420"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a>StartInfo 會針對您未啟動的進程擲回 InvalidOperationException

讀取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動之進程的屬性會擲回 <xref:System.InvalidOperationException> 。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，存取程式 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 代碼未啟動之進程的屬性會傳回虛擬 <xref:System.Diagnostics.ProcessStartInfo> 物件。 虛擬物件包含其所有屬性的預設值，但除外 <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> 。

從 .NET Core 1.0 開始，如果您讀取 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 未啟動之進程的屬性（也就是藉由呼叫 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ）， <xref:System.InvalidOperationException> 則會擲回。

#### <a name="version-introduced"></a>引進的版本

1.0

#### <a name="recommended-action"></a>建議的動作

請勿存取 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 程式碼未啟動之進程的屬性。 例如，請勿讀取所傳回之進程的這個屬性 <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
