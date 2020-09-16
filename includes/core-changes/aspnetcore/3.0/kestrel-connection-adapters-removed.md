---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901915"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel：已移除連接配接器

在移動 "pubternal" Api 至的過程中 `public` ， `IConnectionAdapter` 已從 Kestrel 移除的概念。 連接卡將取代為連接中介軟體 (類似 ASP.NET Core 管線中的 HTTP 中介軟體，但較低層級的連線) 。 HTTPS 和連線記錄已從連接配接器移至連接中介軟體。 這些擴充方法應該會繼續順暢地運作，但是執行的詳細資料已變更。

如需詳細資訊，請參閱 [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412)。 如需討論，請參閱 [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

Kestrel 擴充性元件是使用建立 `IConnectionAdapter` 的。

#### <a name="new-behavior"></a>新的行為

Kestrel 擴充性元件會建立為 [中介軟體](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)。

#### <a name="reason-for-change"></a>變更的原因

這項變更的目的是要提供更具彈性的擴充性架構。

#### <a name="recommended-action"></a>建議的動作

將的任何執行轉換為 `IConnectionAdapter` 使用新的中介軟體模式[here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)，如下所示。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
