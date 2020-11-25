---
title: 重大變更： LocalEndPoint 會在呼叫 SendToAsync 之後更新
description: 瞭解 .NET 5.0 中的重大變更，SendToAsync 現在會將本機端點屬性的值更新為通訊端的本機位址。
ms.date: 10/18/2020
ms.openlocfilehash: 53d7da350eac6e65832012331044427fd90fe796
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760626"
---
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a>LocalEndPoint 會在呼叫 SendToAsync 之後更新

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> 現在會將屬性的值更新 <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> 為通訊端的本機位址。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="change-description"></a>變更描述

在先前的 .NET 版本中，不 <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> 會改變 <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> 通訊端實例上的屬性值。 從 .NET 5.0 開始，當 <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> 順利完成時，的值 <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> 會是隱含系結的通訊端本機位址。 這個新行為與和的行為一致 <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> 。

## <a name="reason-for-change"></a>變更的原因

這種變更可 [修正錯誤](https://github.com/dotnet/runtime/issues/915) ，並讓行為在不同變化之間保持一致 `SendTo` 。

## <a name="recommended-action"></a>建議的動作

改變任何假設 <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> 不會改變值的程式碼 <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> 。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
