---
title: 重大變更： Blazor： JSObjectReference 和 JSInProcessObjectReference 類型已變更為內部
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor： JSObjectReference，JSInProcessObjectReference 類型已變更為內部
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 43a66d204f8309dc5afc57d099b2201c477cc3ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760666"
---
# <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Blazor： JSObjectReference 和 JSInProcessObjectReference 類型已變更為內部

`Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` ASP.NET CORE 5.0 RC1 中引進的新和類型已標示為 `internal` 。

## <a name="version-introduced"></a>引進的版本

5.0 RC2

## <a name="old-behavior"></a>舊的行為

`JSObjectReference`可以透過 JavaScript interop 呼叫來取得 `IJSRuntime` 。 例如：

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

## <a name="new-behavior"></a>新的行為

`JSObjectReference` 使用 [內部](../../../../csharp/language-reference/keywords/internal.md) 存取修飾詞。 您 `public` `IJSObjectReference` 必須改為使用介面。 例如：

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` 也標記為 `internal` ，並取代為 `IJSInProcessObjectReference` 。

## <a name="reason-for-change"></a>變更的原因

這項變更讓 JavaScript interop 功能與 Blazor 中的其他模式更一致。 `IJSObjectReference` 類似于 `IJSRuntime` ，因為它的用途類似，而且具有類似的方法和延伸模組。

## <a name="recommended-action"></a>建議的動作

`JSObjectReference`分別以和取代 and 的出現次數 `JSInProcessObjectReference` `IJSObjectReference` `IJSInProcessObjectReference` 。

## <a name="affected-apis"></a>受影響的 API

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
