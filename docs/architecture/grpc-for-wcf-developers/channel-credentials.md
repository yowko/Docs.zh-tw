---
title: 通道認證-適用于 WCF 開發人員的 gRPC
description: 如何在 ASP.NET Core 3.0 中執行和使用 gRPC 通道認證。
ms.date: 09/02/2019
ms.openlocfilehash: 133de2c732e72844f249f11bfe22b5980b828b89
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711496"
---
# <a name="channel-credentials"></a>通道認證

如其名稱所示，通道認證會附加至基礎 gRPC 通道。 通道認證的標準形式會使用用戶端憑證驗證。 在此程式中，用戶端會在進行連線時提供 TLS 憑證，然後伺服器會在允許進行任何呼叫之前先驗證。

您可以結合通道認證與呼叫認證，為 gRPC 服務提供全面的安全性。 通道認證會證明用戶端應用程式可以存取服務，而呼叫認證會提供使用用戶端應用程式之人員的相關資訊。

用戶端憑證驗證適用于 gRPC，其運作方式與 ASP.NET Core 的相同。 如需詳細資訊，請參閱[在 ASP.NET Core 中設定憑證驗證](/aspnet/core/security/authentication/certauth)。

基於開發目的，您可以使用自我簽署的憑證，但在生產環境中，您應該使用由受信任的授權單位所簽署的適當 HTTPS 憑證。

## <a name="add-certificate-authentication-to-the-server"></a>將憑證驗證新增至伺服器

在主機層級（例如，在 Kestrel 伺服器上），以及在 ASP.NET Core 管線中設定憑證驗證。

### <a name="configure-certificate-validation-on-kestrel"></a>在 Kestrel 上設定憑證驗證

您可以將 Kestrel （ASP.NET Core HTTP 伺服器）設定為需要用戶端憑證，並選擇性地執行提供的憑證驗證，然後再接受連入連線。 您可以在 `Program` 類別的 `CreateWebHostBuilder` 方法中執行這項操作，而不是 `Startup`中。

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

`ClientCertificateMode.RequireCertificate` 設定會導致 Kestrel 立即拒絕未提供用戶端憑證的任何連線要求，但此設定本身不會驗證所提供的憑證。 新增 `ClientCertificateValidation` 回呼，讓 Kestrel 在進行連線時驗證用戶端憑證，然後才參與 ASP.NET Core 管線。 （在此情況下，回呼會確保它是由與伺服器憑證相同的*憑證授權單位*單位所發行）。 

### <a name="add-aspnet-core-certificate-authentication"></a>新增 ASP.NET Core 憑證驗證

[AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet 套件提供憑證驗證。

在 `ConfigureServices` 方法中新增憑證驗證服務，然後在 `Configure` 方法中，將驗證和授權新增至 ASP.NET Core 管線。

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="provide-channel-credentials-in-the-client-application"></a>在用戶端應用程式中提供通道認證

使用 `Grpc.Net.Client` 封裝，您可以在提供給用於連線之 `GrpcChannel` 的 <xref:System.Net.Http.HttpClient> 實例上設定憑證。

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combine-channelcredentials-and-callcredentials"></a>結合 ChannelCredentials 和 CallCredentials

您可以將伺服器設定為同時使用憑證和權杖驗證。 若要這麼做，請將憑證變更套用至 Kestrel 伺服器，並在 ASP.NET Core 中使用 JWT 持有人中介軟體。

若要在用戶端上提供 `ChannelCredentials` 和 `CallCredentials`，請使用 `ChannelCredentials.Create` 方法來套用呼叫認證。 您仍然需要使用 <xref:System.Net.Http.HttpClient> 實例來套用憑證驗證。 如果您將任何引數傳遞至 `SslCredentials` 的函式，內部用戶端程式代碼就會擲回例外狀況。 `SslCredentials` 參數只會包含在 `Grpc.Net.Client` 套件的 `Create` 方法中，以維持與 `Grpc.Core` 套件的相容性。

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> 您可以在沒有憑證驗證的情況下，對用戶端使用 `ChannelCredentials.Create` 方法。 這是在通道上每次呼叫時傳遞權杖認證的實用方式。

GitHub 上已[加入憑證驗證的 FullStockTicker 範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker)版本。

>[!div class="step-by-step"]
>[上一頁](call-credentials.md)
>[下一頁](encryption.md)
