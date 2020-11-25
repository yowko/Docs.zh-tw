---
title: 重大變更：驗證： AzureAD UI 和 AzureADB2C。 UI Api 和標記為過時的封裝
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 [驗證： AzureAD]、[UI] 和 [AzureADB2C]、[UI Api] 和 [封裝已淘汰]
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c977ba4d6e34fc5f11133bdd1446a94d54efcb63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760775"
---
# <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a><span data-ttu-id="92e64-103">驗證： AzureAD UI 和 AzureADB2C。 UI Api 和標記為過時的封裝</span><span class="sxs-lookup"><span data-stu-id="92e64-103">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>

<span data-ttu-id="92e64-104">在 ASP.NET Core 2.1 中，與 Azure Active Directory (Azure AD) 和 Azure Active Directory B2C (Azure AD B2C) 驗證的整合是由 [AzureAD](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) 提供的 AspNetCore 和 [AspNetCore。 AzureADB2C. ui](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) 套件。</span><span class="sxs-lookup"><span data-stu-id="92e64-104">In ASP.NET Core 2.1, integration with Azure Active Directory (Azure AD) and Azure Active Directory B2C (Azure AD B2C) authentication is provided by the [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) and [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) packages.</span></span> <span data-ttu-id="92e64-105">這些套件所提供的功能是以 Azure AD v1.0 端點為基礎。</span><span class="sxs-lookup"><span data-stu-id="92e64-105">The functionality provided by these packages is based on the Azure AD v1.0 endpoint.</span></span>

<span data-ttu-id="92e64-106">在 ASP.NET Core 5.0 和更新版本中，與 Azure AD 和 Azure AD B2C 驗證的整合是由 [web.config](https://www.nuget.org/packages/Microsoft.Identity.Web) 封裝提供。</span><span class="sxs-lookup"><span data-stu-id="92e64-106">In ASP.NET Core 5.0 and later, integration with Azure AD and Azure AD B2C authentication is provided by the [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) package.</span></span> <span data-ttu-id="92e64-107">此套件是以 Microsoft 身分識別平臺為基礎，先前稱為 Azure AD v2.0 端點。</span><span class="sxs-lookup"><span data-stu-id="92e64-107">This package is based on the Microsoft Identity Platform, which is formerly known as the Azure AD v2.0 endpoint.</span></span> <span data-ttu-id="92e64-108">因此，和套件中的舊 `Microsoft.AspNetCore.Authentication.AzureAD.UI` api `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` 已被取代。</span><span class="sxs-lookup"><span data-stu-id="92e64-108">Consequently, the old APIs in the `Microsoft.AspNetCore.Authentication.AzureAD.UI` and `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages were deprecated.</span></span>

<span data-ttu-id="92e64-109">如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807)。</span><span class="sxs-lookup"><span data-stu-id="92e64-109">For discussion, see GitHub issue [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="92e64-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="92e64-110">Version introduced</span></span>

<span data-ttu-id="92e64-111">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="92e64-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="92e64-112">舊的行為</span><span class="sxs-lookup"><span data-stu-id="92e64-112">Old behavior</span></span>

<span data-ttu-id="92e64-113">Api 未標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="92e64-113">The APIs weren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="92e64-114">新的行為</span><span class="sxs-lookup"><span data-stu-id="92e64-114">New behavior</span></span>

<span data-ttu-id="92e64-115">Api 會標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="92e64-115">The APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="92e64-116">變更的原因</span><span class="sxs-lookup"><span data-stu-id="92e64-116">Reason for change</span></span>

<span data-ttu-id="92e64-117">Azure AD 和 Azure AD B2C 驗證功能已遷移至所提供的 Microsoft 驗證程式庫 (MSAL) Api `Microsoft.Identity.Web` 。</span><span class="sxs-lookup"><span data-stu-id="92e64-117">The Azure AD and Azure AD B2C authentication functionality was migrated to Microsoft Authentication Library (MSAL) APIs that are provided by `Microsoft.Identity.Web`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="92e64-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="92e64-118">Recommended action</span></span>

<span data-ttu-id="92e64-119">遵循 `Microsoft.Identity.Web` 適用于 [web 應用程式](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) 和 [web api](https://github.com/azuread/microsoft-identity-web/wiki/web-apis)的 API 指引。</span><span class="sxs-lookup"><span data-stu-id="92e64-119">Follow the `Microsoft.Identity.Web` API guidance for [web apps](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) and [web APIs](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="92e64-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="92e64-120">Affected APIs</span></span>

* [<span data-ttu-id="92e64-121">AspNetCore 驗證. AzureADAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="92e64-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="92e64-122">AspNetCore. AzureAD. AzureADDefaults</span><span class="sxs-lookup"><span data-stu-id="92e64-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="92e64-123">AspNetCore. AzureAD. AzureADOptions</span><span class="sxs-lookup"><span data-stu-id="92e64-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [<span data-ttu-id="92e64-124">AspNetCore 驗證. AzureADB2CAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="92e64-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="92e64-125">AspNetCore. AzureADB2C. AzureADB2CDefaults</span><span class="sxs-lookup"><span data-stu-id="92e64-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="92e64-126">AspNetCore. AzureADB2C. AzureADB2COptions</span><span class="sxs-lookup"><span data-stu-id="92e64-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
