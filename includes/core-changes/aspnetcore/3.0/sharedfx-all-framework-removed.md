---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394177"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>共用架構：已移除 AspNetCore

從 ASP.NET Core 3.0 開始， `Microsoft.AspNetCore.All` `Microsoft.AspNetCore.All` 就不會再產生中繼套件和相符的共用架構。 此封裝可在 ASP.NET Core 2.2 中取得，並將繼續在 ASP.NET Core 2.1 中接收服務更新。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

應用程式可以使用 `Microsoft.AspNetCore.All` 中繼套件將目標設為 `Microsoft.AspNetCore.All` .net Core 上的共用架構。

#### <a name="new-behavior"></a>新的行為

.NET Core 3.0 不包含 `Microsoft.AspNetCore.All` 共用架構。

#### <a name="reason-for-change"></a>變更的原因

`Microsoft.AspNetCore.All`中繼套件包含許多外部相依性。

#### <a name="recommended-action"></a>建議的動作

遷移您的專案以使用 `Microsoft.AspNetCore.App` 架構。 先前可用的元件 `Microsoft.AspNetCore.All` 仍可在 NuGet 上取得。 這些元件現在會與您的應用程式一起部署，而不會包含在共用架構中。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
