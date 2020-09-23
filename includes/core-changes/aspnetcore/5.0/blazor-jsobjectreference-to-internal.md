---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077588"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Blazor： JSObjectReference 和 JSInProcessObjectReference 類型已變更為內部

`Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` ASP.NET CORE 5.0 RC1 中引進的新和類型已標示為 `internal` 。

#### <a name="version-introduced"></a>引進的版本

5.0 RC2

#### <a name="old-behavior"></a>舊的行為

`JSObjectReference`可以透過 JavaScript interop 呼叫來取得 `IJSRuntime` 。 例如：

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a>新的行為

`JSObjectReference` 使用 [內部](../../../../docs/csharp/language-reference/keywords/internal.md) 存取修飾詞。 您 `public` `IJSObjectReference` 必須改為使用介面。 例如：

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` 也標記為 `internal` ，並取代為 `IJSInProcessObjectReference` 。

#### <a name="reason-for-change"></a>變更的原因

這項變更讓 JavaScript interop 功能與 Blazor 中的其他模式更一致。 `IJSObjectReference` 類似于 `IJSRuntime` ，因為它的用途類似，而且具有類似的方法和延伸模組。

#### <a name="recommended-action"></a>建議的動作

`JSObjectReference`分別以和取代 and 的出現次數 `JSInProcessObjectReference` `IJSObjectReference` `IJSInProcessObjectReference` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
