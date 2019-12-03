---
title: 呼叫認證-WCF 開發人員的 gRPC
description: 如何在 ASP.NET Core 3.0 中執行和使用 gRPC 呼叫認證。
ms.date: 09/02/2019
ms.openlocfilehash: 01f21f58ed4235f45509c948c84653cd99d35618
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711528"
---
# <a name="call-credentials"></a><span data-ttu-id="2bbc2-103">呼叫認證</span><span class="sxs-lookup"><span data-stu-id="2bbc2-103">Call credentials</span></span>

<span data-ttu-id="2bbc2-104">呼叫認證全都是根據每個要求傳入中繼資料的權杖。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-104">Call credentials are all based on a token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="2bbc2-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="2bbc2-105">WS-Federation</span></span>

<span data-ttu-id="2bbc2-106">ASP.NET Core 使用[WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet 套件來支援 WS-同盟。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="2bbc2-107">WS-同盟是 Windows 驗證最接近的可用替代方法，不支援透過 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-107">WS-Federation is the closest available alternative to Windows Authentication, which isn't supported over HTTP/2.</span></span> <span data-ttu-id="2bbc2-108">系統會使用 Active Directory 同盟服務（AD FS）來驗證使用者，其提供可用來向 ASP.NET Core 進行驗證的權杖。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-108">Users are authenticated by using Active Directory Federation Services (AD FS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="2bbc2-109">如需如何開始使用此驗證方法的詳細資訊，請參閱[在 ASP.NET Core 中使用 WS-同盟來驗證使用者](/aspnet/core/security/authentication/ws-federation)。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-109">For more information on how to get started with this authentication method, see [Authenticate users with WS-Federation in ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="2bbc2-110">JWT 持有人權杖</span><span class="sxs-lookup"><span data-stu-id="2bbc2-110">JWT Bearer tokens</span></span>

<span data-ttu-id="2bbc2-111">[JSON Web 權杖](https://jwt.io)（JWT）標準提供了一種方式，可將使用者的相關資訊及其在編碼字串中的宣告編碼。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-111">The [JSON Web Token](https://jwt.io) (JWT) standard provides a way to encode information about a user and their claims in an encoded string.</span></span> <span data-ttu-id="2bbc2-112">它也提供簽署該權杖的方法，讓取用者可以使用公開金鑰加密來驗證權杖的完整性。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-112">It also provides a way to sign that token, so that the consumer can verify the integrity of the token by using public key cryptography.</span></span> <span data-ttu-id="2bbc2-113">您可以使用各種服務（例如 IdentityServer4）來驗證使用者，並產生 OpenID Connect （OIDC）權杖以搭配 gRPC 和 HTTP Api 使用。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-113">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="2bbc2-114">ASP.NET Core 3.0 可以使用 JWT 持有人套件來處理 Jwt。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-114">ASP.NET Core 3.0 can handle JWTs by using the JWT Bearer package.</span></span> <span data-ttu-id="2bbc2-115">GRPC 應用程式的設定與 ASP.NET Core MVC 應用程式的設定完全相同。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-115">The configuration is exactly the same for a gRPC application as it is for an ASP.NET Core MVC application.</span></span> <span data-ttu-id="2bbc2-116">在此，我們會將焦點放在 JWT 持有人權杖，因為使用 WS-同盟比進行開發更容易。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-116">Here, we'll focus on JWT Bearer tokens, because they're easier to develop with than WS-Federation.</span></span>

## <a name="add-authentication-and-authorization-to-the-server"></a><span data-ttu-id="2bbc2-117">將驗證和授權新增至伺服器</span><span class="sxs-lookup"><span data-stu-id="2bbc2-117">Add authentication and authorization to the server</span></span>

<span data-ttu-id="2bbc2-118">根據預設，JWT 持有人套件不包含在 ASP.NET Core 3.0 中。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-118">The JWT Bearer package isn't included in ASP.NET Core 3.0 by default.</span></span> <span data-ttu-id="2bbc2-119">在您的應用程式中安裝[AspNetCore Microsoft.aspnetcore.authentication.jwtbearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-119">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="2bbc2-120">在 Startup 類別中新增驗證服務，並設定 JWT 持有人處理常式：</span><span class="sxs-lookup"><span data-stu-id="2bbc2-120">Add the Authentication service in the Startup class, and configure the JWT Bearer handler:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

<span data-ttu-id="2bbc2-121">`IssuerSigningKey` 屬性需要使用驗證已簽署權杖所需的密碼編譯資料來執行 `Microsoft.IdentityModels.Tokens.SecurityKey`。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-121">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="2bbc2-122">將此權杖安全地儲存在*秘密伺服器*中，例如 Azure Key Vault。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-122">Store this token securely in a *secrets server*, like Azure Key Vault.</span></span>

<span data-ttu-id="2bbc2-123">接下來，新增授權服務，以控制對系統的存取：</span><span class="sxs-lookup"><span data-stu-id="2bbc2-123">Next, add the Authorization service, which controls access to the system:</span></span>

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> <span data-ttu-id="2bbc2-124">驗證和授權是兩個不同的步驟。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-124">Authentication and authorization are two separate steps.</span></span> <span data-ttu-id="2bbc2-125">您可以使用驗證來判斷使用者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-125">You use authentication to determine the user's identity.</span></span> <span data-ttu-id="2bbc2-126">您可以使用授權來決定是否允許該使用者存取系統的各個部分。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-126">You use authorization to decide whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="2bbc2-127">現在，在 `Configure` 方法中，將驗證和授權中介軟體新增至 ASP.NET Core 管線：</span><span class="sxs-lookup"><span data-stu-id="2bbc2-127">Now add the authentication and authorization middleware to the ASP.NET Core pipeline in the `Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="2bbc2-128">最後，將 `[Authorize]` 屬性套用至要保護的任何服務或方法，並使用基礎 `HttpContext` 的 `User` 屬性來確認許可權。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-128">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="provide-call-credentials-in-the-client-application"></a><span data-ttu-id="2bbc2-129">在用戶端應用程式中提供呼叫認證</span><span class="sxs-lookup"><span data-stu-id="2bbc2-129">Provide call credentials in the client application</span></span>

<span data-ttu-id="2bbc2-130">從身分識別伺服器取得 JWT 權杖之後，您可以使用它來驗證來自用戶端的 gRPC 呼叫，方法是將它新增為呼叫上的中繼資料標頭，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2bbc2-130">After you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

<span data-ttu-id="2bbc2-131">現在您已使用 JWT 持有人權杖做為呼叫認證來保護您的 gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-131">Now you've secured your gRPC service by using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="2bbc2-132">已[新增驗證和授權的組合範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth)版本位於 GitHub。</span><span class="sxs-lookup"><span data-stu-id="2bbc2-132">A version of the [portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2bbc2-133">[上一頁](security.md)
>[下一頁](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="2bbc2-133">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
