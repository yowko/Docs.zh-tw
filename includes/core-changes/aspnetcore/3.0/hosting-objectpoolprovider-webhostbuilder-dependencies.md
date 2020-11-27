---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032356"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>裝載： ObjectPoolProvider 已從 >webhostbuilder 相依性中移除

在讓 ASP.NET Core 更多付費的情況下， `ObjectPoolProvider` 已從主要的相依性集合中移除。 依賴的特定元件 `ObjectPoolProvider` 現在會自行新增。

如需討論，請參閱 [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`WebHostBuilder``ObjectPoolProvider`預設會在 DI 容器中提供。

#### <a name="new-behavior"></a>新的行為

`WebHostBuilder``ObjectPoolProvider`在 DI 容器中，預設不再提供。

#### <a name="reason-for-change"></a>變更的原因

這是為了讓 ASP.NET Core 更多的播放付費所做的變更。

#### <a name="recommended-action"></a>建議的動作

如果您的元件需要 `ObjectPoolProvider` ，則必須透過將其新增至您的相依性 `IServiceCollection` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
