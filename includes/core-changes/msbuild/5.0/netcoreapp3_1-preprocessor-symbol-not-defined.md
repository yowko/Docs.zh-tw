---
ms.openlocfilehash: de35df21d1887bc95a3106edba312c53daad8b68
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654730"
---
### <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a>以 .NET 5 為目標時，未定義 NETCOREAPP3_1 預處理器符號

在 .NET 5.0 RC2 和更新版本中，專案不再定義舊版的預處理器符號，而是僅針對其目標版本。 這與 .NET Core 1.0-3.1 的行為相同。

#### <a name="version-introduced"></a>引進的版本

5.0 RC2

#### <a name="change-description"></a>變更描述

在 .NET 5.0 preview 7 到 RC1 中，目標專案會 `net5.0` 定義 `NETCOREAPP3_1` 和 `NET5_0` 預處理器符號。 此行為變更背後的目的在於從 .NET 5.0 開始，條件式編譯 [符號會是累計](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols)的。

在 .NET 5.0 RC2 和更新版本中，專案只會定義目標 framework 標記的符號 (TFM 它的目標) ，而不是任何較早的版本。

#### <a name="reason-for-change"></a>變更的原因

因為客戶的意見反應，已還原 preview 7 的變更。 針對較舊的版本定義符號，讓客戶感到驚訝及混淆，並假設它是 c # 編譯器中的 bug。

#### <a name="recommended-action"></a>建議的動作

請確定您的 `#if` 邏輯不會假設在 `NETCOREAPP3_1` 專案目標 `net5.0` 或更高版本時定義。 相反地，假設 `NETCOREAPP3_1` 只有在專案明確設定為目標時才會定義 `netcoreapp3.1` 。

例如，如果您的專案是針對 .NET core 2.1 和 .NET Core 3.1 所 multitargets，而且您呼叫 .NET Core 3.1 中引進的 Api，則您的 `#if` 邏輯看起來應該如下所示：

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

#### <a name="category"></a>類別

MSBuild

#### <a name="affected-apis"></a>受影響的 API

N/A

<!--

#### Affected APIs

Not detectable via API analysis.

-->
