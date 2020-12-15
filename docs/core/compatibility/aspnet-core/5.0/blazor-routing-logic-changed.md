---
title: 重大變更： Blazor： Blazor apps 中的路由邏輯變更
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor： Blazor apps 中的路由邏輯變更
author: scottaddie
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: 4ab8289565c88b17eb204a11724bb12a09b033c2
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513518"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a>Blazor： Blazor apps 中的路由優先順序邏輯已變更

Blazor 路由執行中的錯誤會影響路由的優先順序決定方式。 此錯誤會在您的 Blazor 應用程式內使用選擇性參數來影響全部攔截路由或路由。

## <a name="version-introduced"></a>引進的版本

5.0.1

## <a name="old-behavior"></a>舊的行為

使用錯誤的行為時，會考慮優先順序較低的路由，並透過優先順序較高的路由進行比對。 例如， `{*slug}` 路由會先符合 `/customer/{id}` 。

## <a name="new-behavior"></a>新的行為

目前的行為更緊密符合 ASP.NET Core apps 中定義的路由行為。 架構會先判斷每個區段的路由優先順序。 路由的長度只會用來做為中斷系結的第二個準則。

## <a name="reason-for-change"></a>變更的原因

原始行為在執行時視為錯誤。 作為目標，Blazor apps 中的路由系統在 ASP.NET Core 的其餘部分應該與路由系統的行為方式相同。

## <a name="recommended-action"></a>建議的動作

如果從舊版 Blazor 升級為5.x，請使用 `PreferExactMatches` 元件上的屬性 `Router` 。 這個屬性可用來選擇使用正確的行為。 例如︰

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

當 `PreferExactMatches` 設定為時 `true` ，路由比對會優先于萬用字元的完全相符專案。

## <a name="affected-apis"></a>受影響的 API

無

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
