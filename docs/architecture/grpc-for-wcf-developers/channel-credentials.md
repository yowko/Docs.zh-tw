---
title: 通道認證-適用于 WCF 開發人員的 gRPC
description: 如何在 ASP.NET Core 3.0 中執行和使用 gRPC 通道認證。
ms.date: 12/15/2020
ms.openlocfilehash: 3663bbf061156db957241e2a32dbb9c64562ade2
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938633"
---
# <a name="channel-credentials"></a><span data-ttu-id="adfac-103">通道認證</span><span class="sxs-lookup"><span data-stu-id="adfac-103">Channel credentials</span></span>

<span data-ttu-id="adfac-104">顧名思義，通道認證會附加至基礎 gRPC 通道。</span><span class="sxs-lookup"><span data-stu-id="adfac-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="adfac-105">通道認證的標準形式會使用用戶端憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="adfac-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="adfac-106">在此程式中，用戶端會在建立連線時提供 TLS 憑證，然後伺服器會在允許進行任何呼叫之前驗證此憑證。</span><span class="sxs-lookup"><span data-stu-id="adfac-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this certificate before allowing any calls to be made.</span></span>

<span data-ttu-id="adfac-107">您可以將通道認證與呼叫認證結合，以提供 gRPC 服務的完整安全性。</span><span class="sxs-lookup"><span data-stu-id="adfac-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="adfac-108">通道認證證明用戶端應用程式可以存取服務，而呼叫認證則提供使用用戶端應用程式之人員的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="adfac-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="adfac-109">用戶端憑證驗證的 gRPC 方式與 ASP.NET Core 的方式相同。</span><span class="sxs-lookup"><span data-stu-id="adfac-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="adfac-110">如需詳細資訊，請參閱 [ASP.NET Core 中的設定憑證驗證](/aspnet/core/security/authentication/certauth)。</span><span class="sxs-lookup"><span data-stu-id="adfac-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="adfac-111">針對開發用途，您可以使用自我簽署憑證，但在生產環境中，您應該使用由受信任的授權單位所簽署的正確 HTTPS 憑證。</span><span class="sxs-lookup"><span data-stu-id="adfac-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="adfac-112">將憑證驗證新增至伺服器</span><span class="sxs-lookup"><span data-stu-id="adfac-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="adfac-113">在主機層級設定憑證驗證 (例如，在 Kestrel 伺服器) 和 ASP.NET Core 管線中。</span><span class="sxs-lookup"><span data-stu-id="adfac-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="adfac-114">在 Kestrel 上設定憑證驗證</span><span class="sxs-lookup"><span data-stu-id="adfac-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="adfac-115">您可以設定 Kestrel (ASP.NET Core 的 HTTP 伺服器) 要求用戶端憑證，並選擇性地在接受連入連線之前，先執行一些提供的憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="adfac-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="adfac-116">您可以在類別的方法中指定這項設定 `CreateWebHostBuilder` `Program` ，而不是在中指定 `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="adfac-116">You specify this configuration in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="adfac-117">此 `ClientCertificateMode.RequireCertificate` 設定會使 Kestrel 立即拒絕任何未提供用戶端憑證的連線要求，但這項設定本身不會驗證所提供的憑證。</span><span class="sxs-lookup"><span data-stu-id="adfac-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="adfac-118">新增 `ClientCertificateValidation` 回呼，以在 ASP.NET Core 管線參與之前，讓 Kestrel 驗證用戶端憑證的連接點。</span><span class="sxs-lookup"><span data-stu-id="adfac-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="adfac-119"> (在這種情況下，回呼可確保它是由與伺服器憑證相同的 *憑證授權單位* 單位所發出。 ) </span><span class="sxs-lookup"><span data-stu-id="adfac-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="adfac-120">新增 ASP.NET Core 憑證驗證</span><span class="sxs-lookup"><span data-stu-id="adfac-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="adfac-121">[AspNetCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet 套件提供憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="adfac-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="adfac-122">在方法中新增憑證驗證服務 `ConfigureServices` ，並在方法中將驗證和授權新增至 ASP.NET Core 管線 `Configure` 。</span><span class="sxs-lookup"><span data-stu-id="adfac-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="adfac-123">在用戶端應用程式中提供通道認證</span><span class="sxs-lookup"><span data-stu-id="adfac-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="adfac-124">使用 `Grpc.Net.Client` 封裝，您可以在 <xref:System.Net.Http.HttpClient> 提供給用於連接的實例上設定憑證 `GrpcChannel` 。</span><span class="sxs-lookup"><span data-stu-id="adfac-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="adfac-125">結合 ChannelCredentials 和 CallCredentials</span><span class="sxs-lookup"><span data-stu-id="adfac-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="adfac-126">您可以將伺服器設定為使用憑證和權杖驗證。</span><span class="sxs-lookup"><span data-stu-id="adfac-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="adfac-127">若要這樣做，請將憑證變更套用至 Kestrel 伺服器，並在 ASP.NET Core 中使用 JWT 持有人中介軟體。</span><span class="sxs-lookup"><span data-stu-id="adfac-127">To do this, apply the certificate changes to the Kestrel server, and use the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="adfac-128">若要 `ChannelCredentials` `CallCredentials` 在用戶端上提供和，請使用 `ChannelCredentials.Create` 方法來套用通話認證。</span><span class="sxs-lookup"><span data-stu-id="adfac-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="adfac-129">您仍然需要使用實例來套用憑證驗證 <xref:System.Net.Http.HttpClient> 。</span><span class="sxs-lookup"><span data-stu-id="adfac-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="adfac-130">如果您將任何引數傳遞至函 `SslCredentials` 式，內部用戶端程式代碼會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="adfac-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="adfac-131">`SslCredentials`參數只會包含在 `Grpc.Net.Client` 封裝的方法中 `Create` ，以維持與封裝的相容性 `Grpc.Core` 。</span><span class="sxs-lookup"><span data-stu-id="adfac-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="adfac-132">您可以 `ChannelCredentials.Create` 針對沒有憑證驗證的用戶端使用方法。</span><span class="sxs-lookup"><span data-stu-id="adfac-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="adfac-133">這是在通道上進行每次呼叫時傳遞權杖認證的實用方式。</span><span class="sxs-lookup"><span data-stu-id="adfac-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="adfac-134">已 [新增憑證驗證的 FullStockTicker 範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) 版本位於 GitHub 上。</span><span class="sxs-lookup"><span data-stu-id="adfac-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="adfac-135">[上一個](call-credentials.md) 
>[下一步](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="adfac-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
