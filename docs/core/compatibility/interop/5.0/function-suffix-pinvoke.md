---
title: 重大變更：非 Windows 平臺上沒有 A/W 尾碼探查
description: 瞭解 .NET 5.0 中的 interop 重大變更，在非 Windows 平臺上探查 P/Invoke 期間，不會再將尾碼新增至函式匯出名稱。
ms.date: 08/13/2020
ms.openlocfilehash: a4c612a81796faf80fa257df21232a54f7b95431
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760717"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a>非 Windows 平臺上沒有任何/W 尾碼探查

在 `A` `W` 非 Windows 平臺上進行 P/invoke 探查時，.net 執行時間不會再將或後置詞新增至函式匯出名稱。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="change-description"></a>變更描述

[Windows 的慣例是](/windows/win32/intl/conventions-for-function-prototypes) 將或後置詞新增 `A` 至 Windows SDK 函式 `W` 名稱，分別對應至 Windows 字碼頁和 Unicode 版本。

在舊版的 .NET 中，CoreCLR 和 Mono 執行時間會在 `A` `W` 匯出探索期間針對 *所有平臺上* 的 P/invoke，將或後置詞新增至匯出名稱。

在 .NET 5.0 和更新版本中， `A` `W` 只會在 *Windows 上* 的匯出探索期間，將或後置詞新增至匯出名稱。 在 Unix 平臺上，不會新增尾碼。 Windows 平臺上兩個執行時間的語法會保持不變。

## <a name="reason-for-change"></a>變更的原因

這是為了簡化跨平臺探查所進行的變更。 由於非 Windows 的平臺不包含此語義，因此不應該產生的額外負荷。

## <a name="recommended-action"></a>建議的動作

若要減輕變更，您可以在非 Windows 平臺上手動新增所需的尾碼。 例如：

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
