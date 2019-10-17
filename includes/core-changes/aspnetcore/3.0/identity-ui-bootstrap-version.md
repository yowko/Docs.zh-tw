---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394344"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>身分識別： UI 的預設啟動程式版本已變更

從 ASP.NET Core 3.0 開始，身分識別 UI 預設為使用第4版的啟動程式。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

@No__t-0 方法呼叫等同于 `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>新的行為

@No__t-0 方法呼叫等同于 `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>變更的原因

啟動程式4是在 ASP.NET Core 3.0 時間範圍內發行。

#### <a name="recommended-action"></a>建議的動作

如果您使用預設身分識別 UI，並已將其新增至 `Startup.ConfigureServices`，則會受到這項變更的影響，如下列範例所示：

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

採取下列其中一個動作：

- 使用其[遷移指南](https://getbootstrap.com/docs/4.0/migration)，將您的應用程式遷移至使用啟動程式4。
- 更新 `Startup.ConfigureServices`，以強制使用啟動程式3。 例如:

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
