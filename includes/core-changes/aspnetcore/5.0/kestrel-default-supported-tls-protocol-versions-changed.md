---
ms.openlocfilehash: 3244a36808fb687663241e704d08775ea5c96720
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803263"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a>Kestrel：預設支援的 TLS 通訊協定版本已變更

Kestrel 現在會使用系統預設的 TLS 通訊協定版本，而不是限制與 TLS 1.1 和 TLS 1.2 通訊協定的連線，就像之前一樣。

這種變更允許：

* 在支援的環境中，預設會使用 TLS 1.3。
* 在某些環境中使用的 TLS 1.0 （預設為 Windows Server 2016），這通常[不是理想的做法](/security/engineering/solving-tls1-problem)。

如需討論，請參閱 issue [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 6

#### <a name="old-behavior"></a>舊的行為

Kestrel 需要連線預設使用 TLS 1.1 或 TLS 1.2。

#### <a name="new-behavior"></a>新的行為

Kestrel 可讓作業系統選擇使用的最佳通訊協定，並封鎖不安全的通訊協定。 <xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>現在預設為， `SslProtocols.None` 而不是 `SslProtocols.Tls12 | SslProtocols.Tls11` 。

#### <a name="reason-for-change"></a>變更的原因

根據預設，當 TLS 1.3 和未來的 TLS 版本可供使用時，就會進行變更。

#### <a name="recommended-action"></a>建議的動作

除非您的應用程式具有不適用的特定原因，否則您應該使用新的預設值。 確認您的系統已設定為只允許安全的通訊協定。

若要停用較舊的通訊協定，請採取下列其中一個動作：

* 使用[Windows 指示](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry)停用舊版的通訊協定，例如 TLS 1.0。 它目前在所有 Windows 版本上都是預設為啟用狀態。
* 手動選取您要在程式碼中支援的通訊協定，如下所示：

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

可惜的是，沒有任何 API 可以排除特定的通訊協定。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
