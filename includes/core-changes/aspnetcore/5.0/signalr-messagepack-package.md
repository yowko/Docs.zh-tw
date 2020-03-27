---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345231"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>信號R：MessagePack集線器協定移動到消息包 2.x 包

ASP.NET核心信號R[消息包集線器協定](/aspnet/core/signalr/messagepackhubprotocol)使用[MessagePack NuGet 包](https://www.nuget.org/packages/MessagePack)進行消息包序列化。 ASP.NET Core 5.0 將包從 1.x 升級到最新的 2.x 包版本。

有關此問題的討論，請參閱[dotnet/aspnetcore_18692](https://github.com/dotnet/aspnetcore/issues/18692)。

#### <a name="version-introduced"></a>介紹的版本

5.0 預覽 1

#### <a name="old-behavior"></a>舊的行為

ASP.NET核心信號R使用 MessagePack 1.x 包對消息包進行序列化和反序列化。

#### <a name="new-behavior"></a>新的行為

ASP.NET核心信號R使用 MessagePack 2.x 包對消息包進行序列化和反序列化。

#### <a name="reason-for-change"></a>更改原因

MessagePack 2.x 包中的最新改進增加了有用的功能。

#### <a name="recommended-action"></a>建議的動作

此重大更改適用于：

* 設置或配置 上<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>的值。
* 直接使用 MessagePack API，並在同一專案中使用ASP.NET核心信號R 消息包集線器協定。 將載入較新版本，而不是以前的版本。

有關包作者的遷移指南，請參閱[從 MessagePack v1.x 遷移到 MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)。 消息序列化和反序列化的某些方面受到影響。 具體來說，[日期時間值的序列化方式存在行為變化](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
