---
ms.openlocfilehash: 203d75f5858c8ff039cf579c0539efda0c5c9f02
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474370"
---
### <a name="kestrel-libuv-transport-marked-as-obsolete"></a>Kestrel：已標記為過時的 Libuv 傳輸

舊版的 ASP.NET Core 使用 Libuv 作為非同步輸入和輸出執行方式的實作為詳細資料。 在 ASP.NET Core 2.0 中，開發了以替代為 <xref:System.Net.Sockets.Socket> 基礎的傳輸。 在 ASP.NET Core 2.1 中，Kestrel 預設會切換為使用以為 `Socket` 基礎的傳輸。 基於相容性考慮，已維護 Libuv 支援。

此時，使用以為基礎的 `Socket` 傳輸遠比 Libuv 傳輸更常見。 因此，Libuv 支援在 .NET 5.0 中標示為已淘汰，將完全在 .NET 6.0 中移除。

做為這項變更的一部分，將不會在 .NET 5.0 時間範圍內新增作業系統平臺（例如 Windows ARM64）的 Libuv 支援。

如需有關封鎖需要使用 Libuv 傳輸之問題的討論，請參閱 GitHub 問題： [dotnet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="old-behavior"></a>舊的行為

Libuv Api 不會標示為已淘汰。

#### <a name="new-behavior"></a>新的行為

Libuv Api 會標示為已淘汰。

#### <a name="reason-for-change"></a>變更的原因

以為 `Socket` 基礎的傳輸是預設值。 繼續使用 Libuv 傳輸沒有任何說服力的理由。

#### <a name="recommended-action"></a>建議的動作

停止使用[Libuv 封裝](https://www.nuget.org/packages/Libuv)和擴充方法。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- [Webhostbuilderlibuvextensions.uselibuv](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [Webhostbuilderlibuvextensions.uselibuv. Webhostbuilderlibuvextensions.uselibuv](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions. ThreadCount](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions. NoDelay](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions. MaxWriteBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [AspNetCore. Kestrel. Libuv. LibuvTransportOptions. MaxReadBufferSize](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
