---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394344"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>標識：更改了 UI 的預設引導版本

從 ASP.NET 酷 3.0 開始，標識 UI 預設使用 Bootstrap 的版本 4。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

方法`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`調用與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>新的行為

方法`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`調用與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>更改原因

引導 4 在 ASP.NET 核心 3.0 時間幀期間發佈。

#### <a name="recommended-action"></a>建議的動作

如果您使用預設標識 UI 並在 中`Startup.ConfigureServices`添加了此更改，則您受到此更改的影響，如以下示例所示：

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

請採取下列其中一個動作：

- 使用其[遷移指南](https://getbootstrap.com/docs/4.0/migration)遷移應用以使用引導 4。
- 更新`Startup.ConfigureServices`以強制使用引導 3。 例如：

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
