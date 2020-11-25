---
title: 重大變更： WinHttpHandler 已從 .NET 執行時間移除
description: 瞭解 .NET 5.0 中從 .NET 執行時間移除 WinHttpHandler 的重大變更。
ms.date: 10/18/2020
ms.openlocfilehash: f8b9910ade8d459133791a23704d624a91cc5dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760618"
---
# <a name="winhttphandler-removed-from-net-runtime"></a>WinHttpHandler 已從 .NET 執行時間移除

`WinHttpHandler`類別已從 *System.Net.Http.dll* 元件中移除。 它現在僅適用于頻外 (OOB) [NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="change-description"></a>變更描述

在先前的 .NET 版本中， <xref:System.Net.Http.WinHttpHandler> 類別可作為核心 .net 程式庫的一部分。 從 .NET 5.0 開始， <xref:System.Net.Http.WinHttpHandler> 類別僅可作為個別安裝的 [NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。

## <a name="recommended-action"></a>建議的動作

安裝 [WinHttpHandler NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。 或者，如果您不需要 WinHTTP 特定功能，請改用 <xref:System.Net.Http.SocketsHttpHandler> 。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->
