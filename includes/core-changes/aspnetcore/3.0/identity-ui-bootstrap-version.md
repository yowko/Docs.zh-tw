---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032373"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>身分識別： UI 的預設啟動程式版本已變更

從 ASP.NET Core 3.0 開始，身分識別 UI 預設為使用第4版的啟動程式。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`方法呼叫與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>新的行為

`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`方法呼叫與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>變更的原因

啟動程式4是在 ASP.NET Core 3.0 時間範圍內發行。

#### <a name="recommended-action"></a>建議的動作

如果您使用預設身分識別 UI 並將其加入，則會受到這項變更的影響， `Startup.ConfigureServices` 如下列範例所示：

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

請採取下列其中一個動作：

- 將您的應用程式遷移至使用啟動程式4，並使用其 [遷移指南](https://getbootstrap.com/docs/4.0/migration)。
- 更新 `Startup.ConfigureServices` 以強制使用啟動程式3。 例如：

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
