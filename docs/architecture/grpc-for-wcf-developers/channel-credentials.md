---
title: 通道憑據 - 適用于 WCF 開發人員的 gRPC
description: 如何在ASP.NET酷睿3.0中實現和使用gRPC通道憑據。
ms.date: 09/02/2019
ms.openlocfilehash: 9ebe0aecb517e4cc2fe280632c4ecb593da9871c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148201"
---
# <a name="channel-credentials"></a><span data-ttu-id="815d7-103">通道認證</span><span class="sxs-lookup"><span data-stu-id="815d7-103">Channel credentials</span></span>

<span data-ttu-id="815d7-104">顧名思義，通道憑據附加到基礎 gRPC 通道。</span><span class="sxs-lookup"><span data-stu-id="815d7-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="815d7-105">通道憑據的標準形式使用用戶端憑證身份驗證。</span><span class="sxs-lookup"><span data-stu-id="815d7-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="815d7-106">在此過程中，用戶端在進行連接時提供 TLS 證書，然後伺服器在允許進行任何調用之前驗證此證書。</span><span class="sxs-lookup"><span data-stu-id="815d7-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this before allowing any calls to be made.</span></span>

<span data-ttu-id="815d7-107">您可以將通道憑據與呼叫憑據相結合，為 gRPC 服務提供全面的安全性。</span><span class="sxs-lookup"><span data-stu-id="815d7-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="815d7-108">通道憑據證明允許用戶端應用程式訪問服務，並且調用憑據提供有關使用用戶端應用程式的人員的資訊。</span><span class="sxs-lookup"><span data-stu-id="815d7-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="815d7-109">用戶端憑證身份驗證適用于 gRPC，就像它適用于ASP.NET酷睿一樣。</span><span class="sxs-lookup"><span data-stu-id="815d7-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="815d7-110">有關詳細資訊，請參閱在[ASP.NET 酷中配置證書身份驗證](/aspnet/core/security/authentication/certauth)。</span><span class="sxs-lookup"><span data-stu-id="815d7-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="815d7-111">出於開發目的，可以使用自簽章憑證，但對於生產，應使用由受信任的機構簽名的適當 HTTPS 證書。</span><span class="sxs-lookup"><span data-stu-id="815d7-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="815d7-112">向伺服器添加證書身份驗證</span><span class="sxs-lookup"><span data-stu-id="815d7-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="815d7-113">在主機分級（例如，在 Kestrel 伺服器上）和 ASP.NET核心管道中配置證書身份驗證。</span><span class="sxs-lookup"><span data-stu-id="815d7-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="815d7-114">在 Kestrel 上配置證書驗證</span><span class="sxs-lookup"><span data-stu-id="815d7-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="815d7-115">您可以配置 Kestrel（ASP.NET酷睿 HTTP 伺服器）以需要用戶端憑證，並可以選擇在接受傳入連接之前對提供的證書執行某些驗證。</span><span class="sxs-lookup"><span data-stu-id="815d7-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="815d7-116">在 類的方法中`CreateWebHostBuilder`執行此操作，`Program`而不是在 中`Startup`執行此操作。</span><span class="sxs-lookup"><span data-stu-id="815d7-116">You do this in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

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

<span data-ttu-id="815d7-117">此設置`ClientCertificateMode.RequireCertificate`導致 Kestrel 立即拒絕任何不提供用戶端憑證的連接請求，但此設置本身不會驗證提供的證書。</span><span class="sxs-lookup"><span data-stu-id="815d7-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="815d7-118">添加`ClientCertificateValidation`回檔，使 Kestrel 能夠在連接時驗證用戶端憑證，然後ASP.NET核心管道進行。</span><span class="sxs-lookup"><span data-stu-id="815d7-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="815d7-119">（在這種情況下，回檔可確保它由與伺服器憑證相同的*憑證發行*。</span><span class="sxs-lookup"><span data-stu-id="815d7-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="815d7-120">添加ASP.NET核心證書身份驗證</span><span class="sxs-lookup"><span data-stu-id="815d7-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="815d7-121">[Microsoft.AspNetCore.身份驗證.證書](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate)NuGet 包提供證書身份驗證。</span><span class="sxs-lookup"><span data-stu-id="815d7-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="815d7-122">在`ConfigureServices`方法中添加證書身份驗證服務，並將身份驗證和授權添加到`Configure`方法中的ASP.NET核心管道。</span><span class="sxs-lookup"><span data-stu-id="815d7-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

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

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="815d7-123">在用戶端應用程式中提供通道憑據</span><span class="sxs-lookup"><span data-stu-id="815d7-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="815d7-124">使用`Grpc.Net.Client`包，您可以在提供給用於連接的<xref:System.Net.Http.HttpClient>`GrpcChannel`實例上配置證書。</span><span class="sxs-lookup"><span data-stu-id="815d7-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

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

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="815d7-125">組合通道憑據和呼叫憑據</span><span class="sxs-lookup"><span data-stu-id="815d7-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="815d7-126">您可以將伺服器配置為同時使用證書和權杖身份驗證。</span><span class="sxs-lookup"><span data-stu-id="815d7-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="815d7-127">為此，將證書更改應用於 Kestrel 伺服器，並使用 ASP.NET Core 中的 JWT 承載中介軟體。</span><span class="sxs-lookup"><span data-stu-id="815d7-127">Do this by applying the certificate changes to the Kestrel server, and using the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="815d7-128">要提供用戶端`ChannelCredentials`和`CallCredentials`用戶端，請使用`ChannelCredentials.Create`方法應用調用憑據。</span><span class="sxs-lookup"><span data-stu-id="815d7-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="815d7-129">您仍然需要使用<xref:System.Net.Http.HttpClient>實例應用證書身份驗證。</span><span class="sxs-lookup"><span data-stu-id="815d7-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="815d7-130">如果將任何參數傳遞給`SslCredentials`建構函式，則內部用戶端代碼將引發異常。</span><span class="sxs-lookup"><span data-stu-id="815d7-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="815d7-131">該`SslCredentials`參數僅包含在包`Grpc.Net.Client``Create`的方法中，以保持與包的`Grpc.Core`相容性。</span><span class="sxs-lookup"><span data-stu-id="815d7-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

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
> <span data-ttu-id="815d7-132">您可以將 方法`ChannelCredentials.Create`用於沒有證書身份驗證的用戶端。</span><span class="sxs-lookup"><span data-stu-id="815d7-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="815d7-133">這是將權杖憑據與通道上所做的每個調用傳遞的有用方法。</span><span class="sxs-lookup"><span data-stu-id="815d7-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="815d7-134">在 GitHub 上添加了[證書身份驗證的 FullStockTicker 示例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker)的版本。</span><span class="sxs-lookup"><span data-stu-id="815d7-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="815d7-135">[上一個](call-credentials.md)
>[下一個](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="815d7-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
