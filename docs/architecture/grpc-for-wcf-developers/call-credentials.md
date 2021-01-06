---
title: 呼叫認證-WCF 開發人員的 gRPC
description: 如何在 ASP.NET Core 3.0 中執行和使用 gRPC 呼叫認證。
ms.date: 12/15/2020
ms.openlocfilehash: 66394c75929bf068f83d631e022b467386e59ec5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938438"
---
# <a name="call-credentials"></a><span data-ttu-id="a31ea-103">呼叫認證</span><span class="sxs-lookup"><span data-stu-id="a31ea-103">Call credentials</span></span>

<span data-ttu-id="a31ea-104">呼叫認證全都是以每個要求在中繼資料中傳遞的權杖為基礎。</span><span class="sxs-lookup"><span data-stu-id="a31ea-104">Call credentials are all based on a token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="a31ea-105">WS-同盟</span><span class="sxs-lookup"><span data-stu-id="a31ea-105">WS-Federation</span></span>

<span data-ttu-id="a31ea-106">ASP.NET Core 支援使用 [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet 套件的 WS-Federation。</span><span class="sxs-lookup"><span data-stu-id="a31ea-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="a31ea-107">WS-Federation 是 Windows 驗證最接近的可用替代方案，不支援透過 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="a31ea-107">WS-Federation is the closest available alternative to Windows Authentication, which isn't supported over HTTP/2.</span></span> <span data-ttu-id="a31ea-108">使用者會使用 Active Directory 同盟服務 (AD FS) 進行驗證，這會提供可用於向 ASP.NET Core 進行驗證的權杖。</span><span class="sxs-lookup"><span data-stu-id="a31ea-108">Users are authenticated by using Active Directory Federation Services (AD FS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="a31ea-109">如需如何開始使用此驗證方法的詳細資訊，請參閱 [ASP.NET Core 中的使用 WS-Federation 驗證使用者](/aspnet/core/security/authentication/ws-federation)。</span><span class="sxs-lookup"><span data-stu-id="a31ea-109">For more information on how to get started with this authentication method, see [Authenticate users with WS-Federation in ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="a31ea-110">JWT 持有人權杖</span><span class="sxs-lookup"><span data-stu-id="a31ea-110">JWT Bearer tokens</span></span>

<span data-ttu-id="a31ea-111"> (JWT) standard 的 [JSON Web 權杖](https://jwt.io) 提供一種方式，可讓您在編碼字串中將使用者及其宣告的相關資訊編碼。</span><span class="sxs-lookup"><span data-stu-id="a31ea-111">The [JSON Web Token](https://jwt.io) (JWT) standard provides a way to encode information about a user and their claims in an encoded string.</span></span> <span data-ttu-id="a31ea-112">它也提供簽署該權杖的方法，讓取用者可以使用公開金鑰加密來確認權杖的完整性。</span><span class="sxs-lookup"><span data-stu-id="a31ea-112">It also provides a way to sign that token, so that the consumer can verify the integrity of the token by using public key cryptography.</span></span> <span data-ttu-id="a31ea-113">您可以使用各種服務（例如 IdentityServer4）來驗證使用者，並產生 OpenID Connect (OIDC) 權杖，以搭配 gRPC 和 HTTP Api 使用。</span><span class="sxs-lookup"><span data-stu-id="a31ea-113">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="a31ea-114">ASP.NET Core 5.0 可以使用 JWT 持有人套件來處理 Jwt。</span><span class="sxs-lookup"><span data-stu-id="a31ea-114">ASP.NET Core 5.0 can handle JWTs by using the JWT Bearer package.</span></span> <span data-ttu-id="a31ea-115">GRPC 應用程式的設定完全相同，因為它適用于 ASP.NET Core MVC 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a31ea-115">The configuration is exactly the same for a gRPC application as it is for an ASP.NET Core MVC application.</span></span> <span data-ttu-id="a31ea-116">在這裡，我們將著重于 JWT 持有人權杖，因為它們比 WS-同盟更容易開發。</span><span class="sxs-lookup"><span data-stu-id="a31ea-116">Here, we'll focus on JWT Bearer tokens, because they're easier to develop with than WS-Federation.</span></span>

## <a name="add-authentication-and-authorization-to-the-server"></a><span data-ttu-id="a31ea-117">將驗證和授權新增至伺服器</span><span class="sxs-lookup"><span data-stu-id="a31ea-117">Add authentication and authorization to the server</span></span>

<span data-ttu-id="a31ea-118">預設不會在 ASP.NET Core 5.0 中包含 JWT 持有人套件。</span><span class="sxs-lookup"><span data-stu-id="a31ea-118">The JWT Bearer package isn't included in ASP.NET Core 5.0 by default.</span></span> <span data-ttu-id="a31ea-119">在您的應用程式中安裝 [AspNetCore JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="a31ea-119">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="a31ea-120">在 Startup 類別中新增驗證服務，並設定 JWT 持有人處理常式：</span><span class="sxs-lookup"><span data-stu-id="a31ea-120">Add the Authentication service in the Startup class, and configure the JWT Bearer handler:</span></span>

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

<span data-ttu-id="a31ea-121">`IssuerSigningKey`屬性需要 `Microsoft.IdentityModels.Tokens.SecurityKey` 使用驗證簽署權杖所需的密碼編譯資料來執行。</span><span class="sxs-lookup"><span data-stu-id="a31ea-121">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="a31ea-122">將此權杖安全地儲存在 *秘密伺服器* 中，例如 Azure Key Vault。</span><span class="sxs-lookup"><span data-stu-id="a31ea-122">Store this token securely in a *secrets server*, like Azure Key Vault.</span></span>

<span data-ttu-id="a31ea-123">接下來，新增授權服務，以控制對系統的存取：</span><span class="sxs-lookup"><span data-stu-id="a31ea-123">Next, add the Authorization service, which controls access to the system:</span></span>

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
> <span data-ttu-id="a31ea-124">驗證和授權分為兩個不同的步驟。</span><span class="sxs-lookup"><span data-stu-id="a31ea-124">Authentication and authorization are two separate steps.</span></span> <span data-ttu-id="a31ea-125">您可以使用驗證來判斷使用者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="a31ea-125">You use authentication to determine the user's identity.</span></span> <span data-ttu-id="a31ea-126">您可以使用授權來決定是否允許該使用者存取系統的各個部分。</span><span class="sxs-lookup"><span data-stu-id="a31ea-126">You use authorization to decide whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="a31ea-127">現在將驗證和授權中介軟體新增至方法中的 ASP.NET Core 管線 `Configure` ：</span><span class="sxs-lookup"><span data-stu-id="a31ea-127">Now add the authentication and authorization middleware to the ASP.NET Core pipeline in the `Configure` method:</span></span>

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

<span data-ttu-id="a31ea-128">最後，將 `[Authorize]` 屬性套用至任何要保護的服務或方法，並使用 `User` 來自基礎的屬性 `HttpContext` 來驗證許可權。</span><span class="sxs-lookup"><span data-stu-id="a31ea-128">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

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

## <a name="provide-call-credentials-in-the-client-application"></a><span data-ttu-id="a31ea-129">在用戶端應用程式中提供通話認證</span><span class="sxs-lookup"><span data-stu-id="a31ea-129">Provide call credentials in the client application</span></span>

<span data-ttu-id="a31ea-130">從身分識別伺服器取得 JWT 權杖之後，您可以使用它來驗證用戶端的 gRPC 呼叫，方法是將它新增為呼叫的中繼資料標頭，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a31ea-130">After you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

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

<span data-ttu-id="a31ea-131">現在您已使用 JWT 持有人權杖作為呼叫認證，來保護您的 gRPC 服務。</span><span class="sxs-lookup"><span data-stu-id="a31ea-131">Now you've secured your gRPC service by using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="a31ea-132">在 GitHub 上，已 [新增驗證和授權的組合範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) 版本。</span><span class="sxs-lookup"><span data-stu-id="a31ea-132">A version of the [portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a31ea-133">[上一個](security.md) 
>[下一步](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="a31ea-133">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
