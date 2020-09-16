---
ms.openlocfilehash: 8bcd9987cb061233c8476b9c083a224fc0e25440
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539451"
---
### <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a>驗證： AzureAD UI 和 AzureADB2C。 UI Api 和標記為過時的封裝

在 ASP.NET Core 2.1 中，與 Azure Active Directory (Azure AD) 和 Azure Active Directory B2C (Azure AD B2C) 驗證的整合是由 [AzureAD](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) 提供的 AspNetCore 和 [AspNetCore。 AzureADB2C. ui](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) 套件。 這些套件所提供的功能是以 Azure AD v1.0 端點為基礎。

在 ASP.NET Core 5.0 和更新版本中，與 Azure AD 和 Azure AD B2C 驗證的整合是由 [web.config](https://www.nuget.org/packages/Microsoft.Identity.Web) 封裝提供。 此套件是以 Microsoft 身分識別平臺為基礎，先前稱為 Azure AD v2.0 端點。 因此，和套件中的舊 `Microsoft.AspNetCore.Authentication.AzureAD.UI` api `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` 已被取代。

如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="old-behavior"></a>舊的行為

Api 未標示為已淘汰。

#### <a name="new-behavior"></a>新的行為

Api 會標示為已淘汰。

#### <a name="reason-for-change"></a>變更的原因

Azure AD 和 Azure AD B2C 驗證功能已遷移至所提供的 Microsoft 驗證程式庫 (MSAL) Api `Microsoft.Identity.Web` 。

#### <a name="recommended-action"></a>建議的動作

遵循 `Microsoft.Identity.Web` 適用于 [web 應用程式](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) 和 [web api](https://github.com/azuread/microsoft-identity-web/wiki/web-apis)的 API 指引。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

* [AspNetCore 驗證. AzureADAuthenticationBuilderExtensions](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [AspNetCore. AzureAD. AzureADDefaults](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [AspNetCore. AzureAD. AzureADOptions](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [AspNetCore 驗證. AzureADB2CAuthenticationBuilderExtensions](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [AspNetCore. AzureADB2C. AzureADB2CDefaults](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [AspNetCore. AzureADB2C. AzureADB2COptions](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
