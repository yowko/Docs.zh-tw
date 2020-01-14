---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901641"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>裝載：已從 WebHostBuilder 相依性移除 ObjectPoolProvider

為了讓 ASP.NET Core 擁有更多的播放費用，`ObjectPoolProvider` 已從主要的相依性集合中移除。 依賴 `ObjectPoolProvider` 的特定元件現在會自行新增。

如需討論，請參閱[dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`WebHostBuilder` 預設會在 DI 容器中提供 `ObjectPoolProvider`。

#### <a name="new-behavior"></a>新的行為

`WebHostBuilder` 不再于 DI 容器中提供 `ObjectPoolProvider`。

#### <a name="reason-for-change"></a>變更的原因

進行這種變更是為了讓 ASP.NET Core 更多的播放費用。

#### <a name="recommended-action"></a>建議的動作

如果您的元件需要 `ObjectPoolProvider`，則必須透過 `IServiceCollection`將其新增至您的相依性。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
