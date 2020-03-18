---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901915"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel：連接配接器已移除

作為將"公共"API 移動到移動的一部分`public`，從 Kestrel 中刪除`IConnectionAdapter`了 a 的概念。 連接配接器正在被連接中介軟體替換（類似于 ASP.NET核心管道中的 HTTP 中介軟體，但對於較低級別的連接）。 HTTPS 和連接日誌記錄已經從連接配接器移動到連接中介軟體。 這些擴充方法應繼續無縫工作，但實現細節已更改。

有關詳細資訊，請參閱[點網/阿斯平核心#11412](https://github.com/dotnet/aspnetcore/pull/11412)。 有關討論，請參閱[點網/阿斯平核心#11475](https://github.com/dotnet/aspnetcore/issues/11475)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

Kestrel 擴充性元件是使用`IConnectionAdapter`創建的。

#### <a name="new-behavior"></a>新的行為

Kestrel 擴充性元件創建為[中介軟體](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)。

#### <a name="reason-for-change"></a>更改原因

此更改旨在提供更靈活的擴充性體系結構。

#### <a name="recommended-action"></a>建議的動作

轉換的任何`IConnectionAdapter`實現，以使用新的中介軟體模式，[如下所示](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
