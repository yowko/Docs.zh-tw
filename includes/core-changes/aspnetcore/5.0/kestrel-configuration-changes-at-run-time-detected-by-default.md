---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803243"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a>Kestrel：預設偵測到執行時間的設定變更

Kestrel 現在會回應 `Kestrel` 在執行時間對專案實例之區段進行的變更 `IConfiguration` （例如， *appsettings.js*）。 若要深入瞭解如何使用*appsettings.js*來設定 Kestrel，請參閱[端點](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration)設定中的*appsettings.js*範例。

Kestrel 會視需要系結、解除系結和重新系結端點，以回應這些設定變更。

如需討論，請參閱 issue [dotnet/aspnetcore # 22807](https://github.com/dotnet/aspnetcore/issues/22807)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 7

#### <a name="old-behavior"></a>舊的行為

在 ASP.NET Core 5.0 Preview 6 之前，Kestrel 不支援在執行時間變更設定。

在 ASP.NET Core 5.0 Preview 6 中，您可以選擇在執行時間回應設定變更的立即預設行為。 手動選擇 [必要的系結 Kestrel] 設定：

```csharp
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
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a>新的行為

Kestrel 預設會回應執行時間的設定變更。 為了支援這項變更 <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> ， `KestrelServerOptions.Configure(IConfiguration, bool)` 預設會呼叫 `reloadOnChange: true` 。

#### <a name="reason-for-change"></a>變更的原因

已進行變更，以支援在執行時間重新設定端點，而不需完全重新開機伺服器。 與完整伺服器重新開機不同的是，未變更的端點也不會暫時解除系結。

#### <a name="recommended-action"></a>建議的動作

* 在大多數情況下，Kestrel 的預設設定區段不會在執行時間變更，這項變更不會有任何影響，也不需要採取任何動作。
* 對於 Kestrel 的預設設定區段在執行時間變更的情況，Kestrel 應該對其做出反應，這現在是預設行為。
* 對於 Kestrel 的預設設定區段在執行時間變更，而 Kestrel 不應對其做出反應的案例，您可以退出宣告，如下所示：

    ```csharp
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
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

**注意：**

這項變更不會修改多載的行為 `KestrelServerOptions.Configure(IConfiguration)` ，這仍然會預設為 `reloadOnChange: false` 行為。

也請務必確定設定來源支援重載。 針對 JSON 來源，重載是藉由呼叫來設定 `AddJsonFile(path, reloadOnChange: true)` 。 在和 appsettings 上，預設已針對*appsettings.js*設定重載 *。 {環境}. json*。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
