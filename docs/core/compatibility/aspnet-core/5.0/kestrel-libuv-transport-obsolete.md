---
title: 重大變更： Kestrel： Libuv 傳輸標示為已淘汰
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Kestrel： Libuv 傳輸標示為已淘汰
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f66b9b646671e07957e6d30a95333d392eb29617
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760702"
---
# <a name="kestrel-libuv-transport-marked-as-obsolete"></a>Kestrel： Libuv 傳輸標示為已淘汰

舊版 ASP.NET Core 使用 Libuv 作為非同步輸入和輸出執行方式的執行詳細資料。 在 ASP.NET Core 2.0 中，開發了替代的 <xref:System.Net.Sockets.Socket> 型傳輸。 在 ASP.NET Core 2.1 中，Kestrel 預設會切換為使用以 `Socket` 傳輸為基礎的傳輸。 基於相容性考慮，已維持 Libuv 支援。

到目前為止，使用以 `Socket` 傳輸為基礎的傳輸比 Libuv 傳輸更為普遍。 因此，Libuv 支援在 .NET 5.0 中會標示為已淘汰，而且將完全在 .NET 6.0 中移除。

作為這項變更的一部分，Libuv 支援新的作業系統平臺 (例如 Windows ARM64) 不會加入 .NET 5.0 時間範圍中。

如需封鎖需要使用 Libuv 傳輸之問題的討論，請參閱 GitHub 在 [dotnet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409)的問題。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 8

## <a name="old-behavior"></a>舊的行為

Libuv Api 未標示為已淘汰。

## <a name="new-behavior"></a>新的行為

Libuv Api 會標示為已淘汰。

## <a name="reason-for-change"></a>變更的原因

以 `Socket` 傳輸為基礎的預設值。 繼續使用 Libuv 傳輸沒有任何吸引人的理由。

## <a name="recommended-action"></a>建議的動作

不再使用 [Libuv 封裝](https://www.nuget.org/packages/Libuv) 和擴充方法。

## <a name="affected-apis"></a>受影響的 API

- [>webhostbuilderlibuvextensions.uselibuv](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [>webhostbuilderlibuvextensions.uselibuv. >webhostbuilderlibuvextensions.uselibuv](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions. ThreadCount](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions. NoDelay](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions. MaxWriteBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions. MaxReadBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
