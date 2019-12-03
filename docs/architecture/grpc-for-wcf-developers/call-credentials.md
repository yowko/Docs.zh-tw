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
# <a name="call-credentials"></a>呼叫認證

呼叫認證全都是根據每個要求傳入中繼資料的權杖。

## <a name="ws-federation"></a>WS-Federation

ASP.NET Core 使用[WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet 套件來支援 WS-同盟。 WS-同盟是 Windows 驗證最接近的可用替代方法，不支援透過 HTTP/2。 系統會使用 Active Directory 同盟服務（AD FS）來驗證使用者，其提供可用來向 ASP.NET Core 進行驗證的權杖。

如需如何開始使用此驗證方法的詳細資訊，請參閱[在 ASP.NET Core 中使用 WS-同盟來驗證使用者](/aspnet/core/security/authentication/ws-federation)。

## <a name="jwt-bearer-tokens"></a>JWT 持有人權杖

[JSON Web 權杖](https://jwt.io)（JWT）標準提供了一種方式，可將使用者的相關資訊及其在編碼字串中的宣告編碼。 它也提供簽署該權杖的方法，讓取用者可以使用公開金鑰加密來驗證權杖的完整性。 您可以使用各種服務（例如 IdentityServer4）來驗證使用者，並產生 OpenID Connect （OIDC）權杖以搭配 gRPC 和 HTTP Api 使用。

ASP.NET Core 3.0 可以使用 JWT 持有人套件來處理 Jwt。 GRPC 應用程式的設定與 ASP.NET Core MVC 應用程式的設定完全相同。 在此，我們會將焦點放在 JWT 持有人權杖，因為使用 WS-同盟比進行開發更容易。

## <a name="add-authentication-and-authorization-to-the-server"></a>將驗證和授權新增至伺服器

根據預設，JWT 持有人套件不包含在 ASP.NET Core 3.0 中。 在您的應用程式中安裝[AspNetCore Microsoft.aspnetcore.authentication.jwtbearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet 套件。

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

`IssuerSigningKey` 屬性需要使用驗證已簽署權杖所需的密碼編譯資料來執行 `Microsoft.IdentityModels.Tokens.SecurityKey`。 將此權杖安全地儲存在*秘密伺服器*中，例如 Azure Key Vault。

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
> 驗證和授權是兩個不同的步驟。 您可以使用驗證來判斷使用者的身分識別。 您可以使用授權來決定是否允許該使用者存取系統的各個部分。

現在，在 `Configure` 方法中，將驗證和授權中介軟體新增至 ASP.NET Core 管線：

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

最後，將 `[Authorize]` 屬性套用至要保護的任何服務或方法，並使用基礎 `HttpContext` 的 `User` 屬性來確認許可權。

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

## <a name="provide-call-credentials-in-the-client-application"></a>在用戶端應用程式中提供呼叫認證

從身分識別伺服器取得 JWT 權杖之後，您可以使用它來驗證來自用戶端的 gRPC 呼叫，方法是將它新增為呼叫上的中繼資料標頭，如下所示：

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

現在您已使用 JWT 持有人權杖做為呼叫認證來保護您的 gRPC 服務。 已[新增驗證和授權的組合範例 gRPC 應用程式](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth)版本位於 GitHub。

>[!div class="step-by-step"]
>[上一頁](security.md)
>[下一頁](channel-credentials.md)
