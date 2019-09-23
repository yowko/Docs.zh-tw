---
title: 通道認證-適用于 WCF 開發人員的 gRPC
description: 如何在 ASP.NET Core 3.0 中執行和使用 gRPC 通道認證。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 61305ee47a2c09a0b2a0fd866beb9b7c102ffeaa
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184579"
---
# <a name="channel-credentials"></a>通道認證

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

如其名稱所示，通道認證會附加至基礎 gRPC 通道。 通道認證的標準形式使用用戶端憑證驗證，在此情況下，用戶端會在建立連線時提供 TLS 憑證，在允許進行任何呼叫之前，伺服器會先驗證該憑證。

通道認證可以與呼叫認證結合，以提供 gRPC 服務的完整安全性。 通道認證會證明用戶端應用程式可以存取服務，而呼叫認證會提供使用用戶端應用程式之人員的相關資訊。

用戶端憑證驗證適用于 gRPC，其運作方式與 ASP.NET Core 的相同。 設定程式將在此摘要說明，但如需詳細資訊，請參閱在[ASP.NET Core 中設定憑證驗證](https://docs.microsoft.com/aspnet/core/security/authentication/certauth?view=aspnetcore-3.0)一文。

基於開發目的，您可以使用自我簽署的憑證，但在生產環境中，您應該使用由受信任的授權單位所簽署的適當 HTTPS 憑證。

## <a name="adding-certificate-authentication-to-the-server"></a>將憑證驗證新增至伺服器

您必須在主機層級設定憑證驗證，例如在 Kestrel 伺服器上，以及在 ASP.NET Core 管線中。

### <a name="configuring-certificate-validation-on-kestrel"></a>在 Kestrel 上設定憑證驗證

您可以將 Kestrel （ASP.NET Core HTTP 伺服器）設定為需要用戶端憑證，並選擇性地在接受連入連線之前，先執行所提供憑證的一些驗證。 這項設定是在`CreateWebHostBuilder` `Program`類別的方法中完成，而不是`Startup`在中。

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

此`ClientCertificateMode.RequireCertificate`設定會導致 Kestrel 立即拒絕未提供用戶端憑證的任何連線要求，但它不會驗證憑證。 新增回呼可讓 Kestrel 在連線時驗證用戶端憑證（在此案例中，確保它是由與伺服器憑證相同的*憑證授權單位*單位所發行），然後才 ASP.NET Core `ClientCertificateValidation`管線正在參與。

### <a name="adding-aspnet-core-certificate-authentication"></a>新增 ASP.NET Core 憑證驗證

憑證驗證是由 AspNetCore 所提供。[憑證](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate)NuGet 套件。

在`ConfigureServices`方法中新增憑證驗證服務，並在`Configure`方法中將驗證和授權新增至 ASP.NET Core 管線。

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

## <a name="providing-channel-credentials-in-the-client-application"></a>在用戶端應用程式中提供通道認證

使用封裝時，會<xref:System.Net.Http.HttpClient>在提供給用於連接之的`GrpcChannel`實例上設定憑證。 `Grpc.Net.Client`

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

## <a name="combining-channelcredentials-and-callcredentials"></a>結合 ChannelCredentials 和 CallCredentials

您可以將憑證變更套用至 Kestrel 伺服器，並在 ASP.NET Core 中使用 JWT 持有人中介軟體，將伺服器設定為使用憑證和權杖驗證。

若要在用戶端上同時提供 ChannelCredentials 和 CallCredentials， `ChannelCredentials.Create`請使用方法來套用呼叫認證。 您仍然需要使用<xref:System.Net.Http.HttpClient>實例來套用憑證驗證：如果您將任何引數傳遞`SslCredentials`至函式，內部用戶端程式代碼就會擲回例外狀況。 參數只會包含`Grpc.Net.Client`在封裝的`Create`方法中，以維持與`Grpc.Core`封裝的相容性。 `SslCredentials`

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
> 您可以針對沒有`ChannelCredentials.Create`憑證驗證的用戶端使用方法，這是一個實用的方法，可讓您在通道上進行每次呼叫時傳遞權杖認證。

GitHub 上已[加入憑證驗證的 FullStockTicker 範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker)版本。

>[!div class="step-by-step"]
>[上一頁](call-credentials.md)
>[下一頁](encryption.md)
