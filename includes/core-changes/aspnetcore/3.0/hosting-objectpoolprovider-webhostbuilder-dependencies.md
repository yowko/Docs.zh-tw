---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901641"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>託管：從 WebHostBuilder 依賴項中刪除物件集區提供程式

作為使ASP.NET核心遊戲支付更多費用的一部分，`ObjectPoolProvider`從主依賴項集中刪除了 。 依賴于特定元件`ObjectPoolProvider`現在自行添加。

有關討論，請參閱[點網/阿斯平核心#5944](https://github.com/dotnet/aspnetcore/issues/5944)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`WebHostBuilder`預設情況下`ObjectPoolProvider`在 DI 容器中提供。

#### <a name="new-behavior"></a>新的行為

`WebHostBuilder`預設情況下，DI`ObjectPoolProvider`容器中不再提供。

#### <a name="reason-for-change"></a>更改原因

這一改變是為了使ASP.NET核心公司為遊戲支付更多報酬。

#### <a name="recommended-action"></a>建議的動作

如果需要`ObjectPoolProvider`，則需要通過 將其添加到依賴項中`IServiceCollection`。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
