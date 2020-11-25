---
title: 中斷性變更： MulticastOption。群組不接受 null 值
description: 瞭解 .NET 5.0 中的重大變更，其中 MulticastOption 已不再接受 null 值。
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760622"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>MulticastOption。群組不接受 null 值

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 不再接受的值 `null` 。 如果您將屬性設定為 `null` ， <xref:System.ArgumentNullException> 就會擲回。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="change-description"></a>變更描述

在舊版的 .NET 中，您可以將 <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 屬性設定為 `null` 。 如果 <xref:System.Net.Sockets.MulticastOption> 稍後傳遞至 <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> ，則執行時間會擲回 <xref:System.NullReferenceException> 。

在 .NET 5.0 和更新版本中， <xref:System.ArgumentNullException> 如果您將屬性設定為，就會擲回 `null` 。

## <a name="reason-for-change"></a>變更的原因

為了與架構設計指導方針一致，屬性已更新為如果值為，則會擲回 <xref:System.ArgumentNullException> `null` 。

## <a name="recommended-action"></a>建議的動作

請確定您未將設定 <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 為 `null` 。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
