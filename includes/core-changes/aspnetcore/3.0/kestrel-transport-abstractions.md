---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394414"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel：已移除並設為公用的傳輸抽象概念

在離開「pubternal」 Api 的過程中，Kestrel 傳輸層 Api 會公開為 @no__t 0 程式庫中的公用介面。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

- @No__t-0 程式庫中提供傳輸相關的抽象概念。
- @No__t-0 屬性可供使用。

#### <a name="new-behavior"></a>新的行為

- @No__t-0 介面是在 @no__t 1 程式庫中引進，用以公開 @no__t 2 程式庫中最常用的功能。
- @No__t-0 現在可用於傳輸選項（`LibuvTransportOptions` 和 `SocketTransportOptions`）。
- `SchedulingMode` 已無法再使用。

#### <a name="reason-for-change"></a>變更的原因

ASP.NET Core 3.0 已從 "pubternal" Api 中移除。

#### <a name="recommended-action"></a>建議的動作

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

### Affected APIs

Not detectable via API analysis

-->
