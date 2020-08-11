---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062417"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a>非 Windows 平臺上沒有 A/W 尾碼探查

在 `A` `W` 非 Windows 平臺上進行 P/invoke 的探查期間，.net 執行時間不再為函式匯出名稱新增或尾碼。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 4

#### <a name="change-description"></a>變更描述

[Windows 具有](/windows/win32/intl/conventions-for-function-prototypes)將 `A` 或尾碼新增至 Windows SDK 函式名稱的慣例 `W` ，分別對應至 Windows 字碼頁和 Unicode 版本。

在舊版的 .NET 中，CoreCLR 和 Mono 執行時間會在 `A` `W` *所有平臺上*的 P/invoke 的匯出探索期間，為匯出名稱新增或尾碼。

在 .NET 5.0 和更新版本中， `A` `W` *只有在 Windows 上*的匯出探索期間，會將或尾碼新增至匯出名稱。 在 Unix 平臺上，不會新增尾碼。 Windows 平臺上這兩個執行時間的語義會保持不變。

#### <a name="reason-for-change"></a>變更的原因

這是為了簡化跨平臺探查而進行的變更。 由於非 Windows 平臺不包含這個語義，因此不應該產生的額外負荷。

#### <a name="recommended-action"></a>建議的動作

若要減輕變更，您可以在非 Windows 平臺上手動新增所需的尾碼。 例如：

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a>類別

Interop

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
