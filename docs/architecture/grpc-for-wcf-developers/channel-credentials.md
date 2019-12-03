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
# <a name="channel-credentials"></a><span data-ttu-id="7d138-103">通道認證</span><span class="sxs-lookup"><span data-stu-id="7d138-103">Channel credentials</span></span>

<span data-ttu-id="7d138-104">如其名稱所示，通道認證會附加至基礎 gRPC 通道。</span><span class="sxs-lookup"><span data-stu-id="7d138-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="7d138-105">通道認證的標準形式會使用用戶端憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="7d138-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="7d138-106">在此程式中，用戶端會在進行連線時提供 TLS 憑證，然後伺服器會在允許進行任何呼叫之前先驗證。</span><span class="sxs-lookup"><span data-stu-id="7d138-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="7d138-107">您可以結合通道認證與呼叫認證，為 gRPC 服務提供全面的安全性。</span><span class="sxs-lookup"><span data-stu-id="7d138-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="7d138-108">通道認證會證明用戶端應用程式可以存取服務，而呼叫認證會提供使用用戶端應用程式之人員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7d138-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="7d138-109">用戶端憑證驗證適用于 gRPC，其運作方式與 ASP.NET Core 的相同。</span><span class="sxs-lookup"><span data-stu-id="7d138-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="7d138-110">如需詳細資訊，請參閱[在 ASP.NET Core 中設定憑證驗證](/aspnet/core/security/authentication/certauth)。</span><span class="sxs-lookup"><span data-stu-id="7d138-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="7d138-111">基於開發目的，您可以使用自我簽署的憑證，但在生產環境中，您應該使用由受信任的授權單位所簽署的適當 HTTPS 憑證。</span><span class="sxs-lookup"><span data-stu-id="7d138-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="7d138-112">將憑證驗證新增至伺服器</span><span class="sxs-lookup"><span data-stu-id="7d138-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="7d138-113">在主機層級（例如，在 Kestrel 伺服器上），以及在 ASP.NET Core 管線中設定憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="7d138-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="7d138-114">在 Kestrel 上設定憑證驗證</span><span class="sxs-lookup"><span data-stu-id="7d138-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="7d138-115">您可以將 Kestrel （ASP.NET Core HTTP 伺服器）設定為需要用戶端憑證，並選擇性地執行提供的憑證驗證，然後再接受連入連線。</span><span class="sxs-lookup"><span data-stu-id="7d138-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="7d138-116">您可以在 `Program` 類別的 `CreateWebHostBuilder` 方法中執行這項操作，而不是 `Startup`中。</span><span class="sxs-lookup"><span data-stu-id="7d138-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="7d138-117">`ClientCertificateMode.RequireCertificate` 設定會導致 Kestrel 立即拒絕未提供用戶端憑證的任何連線要求，但此設定本身不會驗證所提供的憑證。</span><span class="sxs-lookup"><span data-stu-id="7d138-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="7d138-118">新增 `ClientCertificateValidation` 回呼，讓 Kestrel 在進行連線時驗證用戶端憑證，然後才參與 ASP.NET Core 管線。</span><span class="sxs-lookup"><span data-stu-id="7d138-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="7d138-119">（在此情況下，回呼會確保它是由與伺服器憑證相同的*憑證授權單位*單位所發行）。</span><span class="sxs-lookup"><span data-stu-id="7d138-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span> 

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="7d138-120">新增 ASP.NET Core 憑證驗證</span><span class="sxs-lookup"><span data-stu-id="7d138-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="7d138-121">[AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet 套件提供憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="7d138-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="7d138-122">在 `ConfigureServices` 方法中新增憑證驗證服務，然後在 `Configure` 方法中，將驗證和授權新增至 ASP.NET Core 管線。</span><span class="sxs-lookup"><span data-stu-id="7d138-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="7d138-123">在用戶端應用程式中提供通道認證</span><span class="sxs-lookup"><span data-stu-id="7d138-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="7d138-124">使用 `Grpc.Net.Client` 封裝，您可以在提供給用於連線之 `GrpcChannel` 的 <xref:System.Net.Http.HttpClient> 實例上設定憑證。</span><span class="sxs-lookup"><span data-stu-id="7d138-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="7d138-125">結合 ChannelCredentials 和 CallCredentials</span><span class="sxs-lookup"><span data-stu-id="7d138-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="7d138-126">您可以將伺服器設定為同時使用憑證和權杖驗證。</span><span class="sxs-lookup"><span data-stu-id="7d138-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="7d138-127">若要這麼做，請將憑證變更套用至 Kestrel 伺服器，並在 ASP.NET Core 中使用 JWT 持有人中介軟體。</span><span class="sxs-lookup"><span data-stu-id="7d138-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="7d138-128">若要在用戶端上提供 `ChannelCredentials` 和 `CallCredentials`，請使用 `ChannelCredentials.Create` 方法來套用呼叫認證。</span><span class="sxs-lookup"><span data-stu-id="7d138-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="7d138-129">您仍然需要使用 <xref:System.Net.Http.HttpClient> 實例來套用憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="7d138-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="7d138-130">如果您將任何引數傳遞至 `SslCredentials` 的函式，內部用戶端程式代碼就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7d138-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="7d138-131">`SslCredentials` 參數只會包含在 `Grpc.Net.Client` 套件的 `Create` 方法中，以維持與 `Grpc.Core` 套件的相容性。</span><span class="sxs-lookup"><span data-stu-id="7d138-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="7d138-132">您可以在沒有憑證驗證的情況下，對用戶端使用 `ChannelCredentials.Create` 方法。</span><span class="sxs-lookup"><span data-stu-id="7d138-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="7d138-133">這是在通道上每次呼叫時傳遞權杖認證的實用方式。</span><span class="sxs-lookup"><span data-stu-id="7d138-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="7d138-134">GitHub 上已[加入憑證驗證的 FullStockTicker 範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker)版本。</span><span class="sxs-lookup"><span data-stu-id="7d138-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7d138-135">[上一頁](call-credentials.md)
>[下一頁](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="7d138-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
