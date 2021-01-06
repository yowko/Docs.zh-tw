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
# <a name="call-credentials"></a>呼叫認證

呼叫認證全都是以每個要求在中繼資料中傳遞的權杖為基礎。

## <a name="ws-federation"></a>WS-同盟

ASP.NET Core 支援使用 [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet 套件的 WS-Federation。 WS-Federation 是 Windows 驗證最接近的可用替代方案，不支援透過 HTTP/2。 使用者會使用 Active Directory 同盟服務 (AD FS) 進行驗證，這會提供可用於向 ASP.NET Core 進行驗證的權杖。

如需如何開始使用此驗證方法的詳細資訊，請參閱 [ASP.NET Core 中的使用 WS-Federation 驗證使用者](/aspnet/core/security/authentication/ws-federation)。

## <a name="jwt-bearer-tokens"></a>JWT 持有人權杖

 (JWT) standard 的 [JSON Web 權杖](https://jwt.io) 提供一種方式，可讓您在編碼字串中將使用者及其宣告的相關資訊編碼。 它也提供簽署該權杖的方法，讓取用者可以使用公開金鑰加密來確認權杖的完整性。 您可以使用各種服務（例如 IdentityServer4）來驗證使用者，並產生 OpenID Connect (OIDC) 權杖，以搭配 gRPC 和 HTTP Api 使用。

ASP.NET Core 5.0 可以使用 JWT 持有人套件來處理 Jwt。 GRPC 應用程式的設定完全相同，因為它適用于 ASP.NET Core MVC 應用程式。 在這裡，我們將著重于 JWT 持有人權杖，因為它們比 WS-同盟更容易開發。

## <a name="add-authentication-and-authorization-to-the-server"></a>將驗證和授權新增至伺服器

預設不會在 ASP.NET Core 5.0 中包含 JWT 持有人套件。 在您的應用程式中安裝 [AspNetCore JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet 套件。

在 Startup 類別中新增驗證服務，並設定 JWT 持有人處理常式：

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

`IssuerSigningKey`屬性需要 `Microsoft.IdentityModels.Tokens.SecurityKey` 使用驗證簽署權杖所需的密碼編譯資料來執行。 將此權杖安全地儲存在 *秘密伺服器* 中，例如 Azure Key Vault。

接下來，新增授權服務，以控制對系統的存取：

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
> 驗證和授權分為兩個不同的步驟。 您可以使用驗證來判斷使用者的身分識別。 您可以使用授權來決定是否允許該使用者存取系統的各個部分。

現在將驗證和授權中介軟體新增至方法中的 ASP.NET Core 管線 `Configure` ：

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

最後，將 `[Authorize]` 屬性套用至任何要保護的服務或方法，並使用 `User` 來自基礎的屬性 `HttpContext` 來驗證許可權。

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

## <a name="provide-call-credentials-in-the-client-application"></a>在用戶端應用程式中提供通話認證

從身分識別伺服器取得 JWT 權杖之後，您可以使用它來驗證用戶端的 gRPC 呼叫，方法是將它新增為呼叫的中繼資料標頭，如下所示：

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

現在您已使用 JWT 持有人權杖作為呼叫認證，來保護您的 gRPC 服務。 在 GitHub 上，已 [新增驗證和授權的組合範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) 版本。

>[!div class="step-by-step"]
>[上一個](security.md) 
>[下一步](channel-credentials.md)
