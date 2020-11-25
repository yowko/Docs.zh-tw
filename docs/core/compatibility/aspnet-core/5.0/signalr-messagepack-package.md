---
title: 重大變更： SignalR： MessagePack Hub 通訊協定已移至 MessagePack 2.x 套件
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 SignalR： MessagePack Hub Protocol 已移至 MessagePack 2.x 套件
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1e666c40d7046233c9fb06af819b901fd1251b06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760785"
---
# <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>SignalR： MessagePack Hub 通訊協定已移至 MessagePack 2.x 套件

ASP.NET Core SignalR [MessagePack Hub 通訊協定](/aspnet/core/signalr/messagepackhubprotocol) 會使用 [MessagePack NuGet 套件](https://www.nuget.org/packages/MessagePack) 進行 MessagePack 序列化。 ASP.NET Core 5.0 會將套件從1.x 升級到最新的2.x 套件版本。

如需此問題的討論，請參閱 [dotnet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 1

## <a name="old-behavior"></a>舊的行為

ASP.NET Core SignalR 使用 MessagePack 1.x 套件來序列化和還原序列化 MessagePack 訊息。

## <a name="new-behavior"></a>新的行為

ASP.NET Core SignalR 會使用 MessagePack 2.x 套件來序列化和還原序列化 MessagePack 訊息。

## <a name="reason-for-change"></a>變更的原因

MessagePack 2.x 套件中的最新改良功能可新增有用的功能。

## <a name="recommended-action"></a>建議的動作

此重大變更適用于：

* 設定或設定上的值 <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> 。
* 直接使用 MessagePack Api，並在相同專案中使用 ASP.NET Core SignalR MessagePack Hub 通訊協定。 將會載入較新的版本，而不是先前的版本。

如需封裝作者的遷移指導方針，請參閱 [從 MessagePack v1. x 遷移至 MessagePack v2. x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)。 訊息序列化和還原序列化的某些層面會受到影響。 具體而言， [日期時間值的序列化方式有一些行為變更](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)。

## <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
