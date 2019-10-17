---
ms.openlocfilehash: a916af91670dc9c5ceb2ff759cd8ae308fb2c2dc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394371"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel：已移除連接介面卡

在移至將 "pubternal" Api 移至 `public` 的過程中，`IConnectionAdapter` 的概念已從 Kestrel 中移除。 連接介面卡會被連線中介軟體取代（類似于 ASP.NET Core 管線中的 HTTP 中介軟體，但適用于較低層級的連接）。 HTTPS 和連線記錄已從連接介面卡移至連線中介軟體。 這些擴充方法應該繼續順暢地工作，但執行詳細資料已變更。

如需詳細資訊，請參閱[aspnet/AspNetCore # 11412](https://github.com/aspnet/AspNetCore/pull/11412)。 如需討論，請參閱[aspnet/AspNetCore # 11475](https://github.com/aspnet/AspNetCore/issues/11475)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

Kestrel 擴充性元件是使用 `IConnectionAdapter` 所建立。

#### <a name="new-behavior"></a>新的行為

Kestrel 擴充性元件會建立為[中介軟體](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)。

#### <a name="reason-for-change"></a>變更的原因

這種變更的目的是要提供更具彈性的擴充性架構。

#### <a name="recommended-action"></a>建議的動作

轉換 `IConnectionAdapter` 的任何執行，以使用新的中介軟體模式[，如下所示。](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
