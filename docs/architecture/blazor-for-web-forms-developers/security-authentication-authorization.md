---
title: 安全性： ASP.NET Web Forms 和中的驗證和授權 Blazor
description: 瞭解如何在 ASP.NET Web Forms 和中處理驗證和授權 Blazor 。
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 1cc82b14a940465c26377f9181a2e20b46b0783f
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267822"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a><span data-ttu-id="dfad9-103">安全性： ASP.NET Web Forms 和中的驗證和授權 Blazor</span><span class="sxs-lookup"><span data-stu-id="dfad9-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="dfad9-104">Blazor假設應用程式已設定驗證，則從 ASP.NET Web Forms 應用程式遷移到幾乎都需要更新驗證和授權的執行方式。</span><span class="sxs-lookup"><span data-stu-id="dfad9-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization is performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="dfad9-105">本章將說明如何) 成員資格、角色和使用者設定檔的 ASP.NET Web Forms 通用提供者模型 (遷移，以及如何從應用程式使用 ASP.NET Core 身分識別 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="dfad9-106">雖然本章將涵蓋高階步驟和考慮，但您可以在參考的檔中找到詳細的步驟和腳本。</span><span class="sxs-lookup"><span data-stu-id="dfad9-106">While this chapter will cover the high level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="dfad9-107">ASP.NET 通用提供者</span><span class="sxs-lookup"><span data-stu-id="dfad9-107">ASP.NET universal providers</span></span>

<span data-ttu-id="dfad9-108">自 ASP.NET 2.0 起，ASP.NET Web Forms 平臺支援各種功能的提供者模型，包括成員資格。</span><span class="sxs-lookup"><span data-stu-id="dfad9-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="dfad9-109">通用成員資格提供者以及選用的角色提供者，通常會與 ASP.NET Web Forms 的應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="dfad9-109">The universal membership provider, along with the optional role provider, is very commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="dfad9-110">它提供一種健全且安全的方式來管理驗證和授權，以持續正常運作。</span><span class="sxs-lookup"><span data-stu-id="dfad9-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="dfad9-111">這些通用提供者的最新供應專案是以 NuGet[套件的形式提供。](https://www.nuget.org/packages/Microsoft.AspNet.Providers)</span><span class="sxs-lookup"><span data-stu-id="dfad9-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="dfad9-112">Universal Providers 使用包含 `aspnet_Applications` 、、和等資料表的 SQL database 架構 `aspnet_Membership` `aspnet_Roles` `aspnet_Users` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="dfad9-113">藉由執行 [aspnet_regsql.exe 命令](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140))來設定時，提供者會安裝資料表和預存程式，以提供使用基礎資料所需的所有必要查詢和命令。</span><span class="sxs-lookup"><span data-stu-id="dfad9-113">When configured by running the [aspnet_regsql.exe command](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands necessary to work with the underlying data.</span></span> <span data-ttu-id="dfad9-114">資料庫架構與這些預存程式與較新的 ASP.NET Identity 和 ASP.NET Core 的身分識別系統不相容，因此必須將現有的資料移轉到新系統中。</span><span class="sxs-lookup"><span data-stu-id="dfad9-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="dfad9-115">[圖 1] 顯示針對通用提供者設定的範例資料表架構。</span><span class="sxs-lookup"><span data-stu-id="dfad9-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![通用提供者架構](./media/security/membership-tables.png)

<span data-ttu-id="dfad9-117">通用提供者會處理使用者、成員資格、角色和設定檔。</span><span class="sxs-lookup"><span data-stu-id="dfad9-117">The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id="dfad9-118">系統會將全域唯一識別碼和非常基本的資訊指派給使用者， (userId、userName) 儲存在 `aspnet_Users` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="dfad9-118">Users are assigned globally unique identifiers and very basic information (userId, userName) is stored in the `aspnet_Users` table.</span></span> <span data-ttu-id="dfad9-119">系統會將驗證資訊（例如密碼、密碼格式、密碼 salt、鎖定計數器和詳細資料等）儲存在 `aspnet_Membership` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="dfad9-119">Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id="dfad9-120">角色只包含名稱和唯一識別碼，可透過關聯資料表指派給使用者 `aspnet_UsersInRoles` ，並提供多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="dfad9-120">Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id="dfad9-121">如果您現有的系統除了成員資格之外還在使用角色，您必須將使用者帳戶、相關聯的密碼、角色和角色成員資格遷移至 ASP.NET Core 身分識別。</span><span class="sxs-lookup"><span data-stu-id="dfad9-121">If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id="dfad9-122">您也可能需要使用 if 語句來更新您目前正在執行角色檢查的程式碼，以改用宣告式篩選、屬性和/或標記協助程式。</span><span class="sxs-lookup"><span data-stu-id="dfad9-122">You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id="dfad9-123">我們將在這一章的結尾更詳細地探討遷移考慮。</span><span class="sxs-lookup"><span data-stu-id="dfad9-123">We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name="authorization-configuration-in-web-forms"></a><span data-ttu-id="dfad9-124">Web Form 中的授權設定</span><span class="sxs-lookup"><span data-stu-id="dfad9-124">Authorization configuration in Web Forms</span></span>

<span data-ttu-id="dfad9-125">若要在 ASP.NET Web Forms 應用程式中設定特定頁面的授權存取，您通常會指定匿名使用者無法存取特定頁面或資料夾。</span><span class="sxs-lookup"><span data-stu-id="dfad9-125">To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id="dfad9-126">這是在 web.config 檔案中完成：</span><span class="sxs-lookup"><span data-stu-id="dfad9-126">This is done in the web.config file:</span></span>

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

<span data-ttu-id="dfad9-127">`authentication`設定區段會設定應用程式的表單驗證。</span><span class="sxs-lookup"><span data-stu-id="dfad9-127">The `authentication` configuration section sets up forms authentication for the application.</span></span> <span data-ttu-id="dfad9-128">`authorization`區段是用來禁止整個應用程式的匿名使用者。</span><span class="sxs-lookup"><span data-stu-id="dfad9-128">The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id="dfad9-129">不過，您可以針對每個位置提供更細微的授權規則，以及套用以角色為基礎的授權檢查。</span><span class="sxs-lookup"><span data-stu-id="dfad9-129">However, you can provide more granular authorization rules on a per-location basis as well as apply role based authorization checks.</span></span>

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="dfad9-130">上述設定與第一個設定合併時，會允許匿名使用者存取登入頁面，以覆寫非驗證使用者的全網站限制。</span><span class="sxs-lookup"><span data-stu-id="dfad9-130">The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="dfad9-131">上述設定與其他設定合併時， `/admin` 會將資料夾和其內所有資源的存取限制為「系統管理員」角色的成員。</span><span class="sxs-lookup"><span data-stu-id="dfad9-131">The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the "Administrators" role.</span></span> <span data-ttu-id="dfad9-132">也可以藉由將個別檔案放 `web.config` 在資料夾根目錄中來套用 `/admin` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-132">This could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name="authorization-code-in-web-forms"></a><span data-ttu-id="dfad9-133">Web Form 中的授權碼</span><span class="sxs-lookup"><span data-stu-id="dfad9-133">Authorization code in Web Forms</span></span>

<span data-ttu-id="dfad9-134">除了使用設定存取之外 `web.config` ，您也可以在 Web Form 應用程式中，以程式設計方式設定存取和行為。</span><span class="sxs-lookup"><span data-stu-id="dfad9-134">In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id="dfad9-135">例如，您可以限制執行特定作業或根據使用者角色來查看特定資料的能力。</span><span class="sxs-lookup"><span data-stu-id="dfad9-135">For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id="dfad9-136">這段程式碼可用於程式碼後置邏輯和頁面本身：</span><span class="sxs-lookup"><span data-stu-id="dfad9-136">This code can be used both in codebehind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="dfad9-137">除了檢查使用者角色成員資格，您也可以判斷這些成員資格是否經過驗證 (但使用上述) 所涵蓋的位置型設定，通常是較好的做法。</span><span class="sxs-lookup"><span data-stu-id="dfad9-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="dfad9-138">以下是此方法的範例。</span><span class="sxs-lookup"><span data-stu-id="dfad9-138">Below is an example of this approach.</span></span>

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

<span data-ttu-id="dfad9-139">在上述程式碼中， (RBAC) 的角色型存取控制會用來判斷是否 `SecretPanel` 會根據目前使用者的角色來顯示頁面的某些專案，例如。</span><span class="sxs-lookup"><span data-stu-id="dfad9-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="dfad9-140">一般來說，ASP.NET Web Forms 的應用程式會在檔案中設定安全性 `web.config` ，然後再于 `.aspx` 頁面及其相關的程式碼後置檔案中新增其他檢查 `.aspx.cs` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` codebehind files.</span></span> <span data-ttu-id="dfad9-141">大部分的應用程式會利用通用的成員資格提供者，通常會有額外的角色提供者。</span><span class="sxs-lookup"><span data-stu-id="dfad9-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="dfad9-142">ASP.NET Core 身分識別</span><span class="sxs-lookup"><span data-stu-id="dfad9-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="dfad9-143">雖然仍然負責驗證和授權，但在與通用提供者相較之下，ASP.NET Core 身分識別會使用一組不同的抽象概念和假設。</span><span class="sxs-lookup"><span data-stu-id="dfad9-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="dfad9-144">例如，新的身分識別模型支援協力廠商驗證，可讓使用者使用社交媒體帳戶或其他受信任的驗證提供者進行驗證。</span><span class="sxs-lookup"><span data-stu-id="dfad9-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="dfad9-145">ASP.NET Core 身分識別支援使用者介面，可用於通常需要的頁面，例如登入、登出及註冊。</span><span class="sxs-lookup"><span data-stu-id="dfad9-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="dfad9-146">它會利用 EF Core 來存取資料，並使用 EF Core 的遷移來產生支援其資料模型所需的架構。</span><span class="sxs-lookup"><span data-stu-id="dfad9-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to supports its data model.</span></span> <span data-ttu-id="dfad9-147">本 [ASP.NET Core 的身分識別簡介](https://docs.microsoft.com/aspnet/core/security/authentication/identity) 提供了 ASP.NET Core 身分識別所包含的內容，以及如何開始使用它的良好總覽。</span><span class="sxs-lookup"><span data-stu-id="dfad9-147">This [introduction to Identity on ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="dfad9-148">如果您尚未在您的應用程式及其資料庫中設定 ASP.NET Core 身分識別，它會協助您開始使用。</span><span class="sxs-lookup"><span data-stu-id="dfad9-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="dfad9-149">角色、宣告和原則</span><span class="sxs-lookup"><span data-stu-id="dfad9-149">Roles, claims, and policies</span></span>

<span data-ttu-id="dfad9-150">通用提供者和 ASP.NET Core 身分識別都支援角色的概念。</span><span class="sxs-lookup"><span data-stu-id="dfad9-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="dfad9-151">您可以為使用者建立角色，並將使用者指派給角色。</span><span class="sxs-lookup"><span data-stu-id="dfad9-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="dfad9-152">使用者可以屬於任意數量的角色，而且您可以驗證角色成員資格作為授權實施的一部分。</span><span class="sxs-lookup"><span data-stu-id="dfad9-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="dfad9-153">除了角色之外，ASP.NET Core 身分識別也支援宣告和原則的概念。</span><span class="sxs-lookup"><span data-stu-id="dfad9-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="dfad9-154">角色應特別對應到一組資源，而該角色的使用者應該能夠存取，而宣告只是使用者身分識別的一部分。</span><span class="sxs-lookup"><span data-stu-id="dfad9-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="dfad9-155">宣告是一組名稱值組，代表主體是什麼，而不是主體可做的動作。</span><span class="sxs-lookup"><span data-stu-id="dfad9-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="dfad9-156">您可以直接檢查使用者的宣告，並根據這些使用者是否應該獲得資源的存取權來決定。</span><span class="sxs-lookup"><span data-stu-id="dfad9-156">It is possible to directly inspect a user's claims and determine based on these whether a user should be given access to a resource.</span></span> <span data-ttu-id="dfad9-157">不過，這類檢查通常會在整個系統中重複和散佈。</span><span class="sxs-lookup"><span data-stu-id="dfad9-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="dfad9-158">更好的方法是定義 *原則*。</span><span class="sxs-lookup"><span data-stu-id="dfad9-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="dfad9-159">授權原則包含一個或多個需求。</span><span class="sxs-lookup"><span data-stu-id="dfad9-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="dfad9-160">原則會在的方法中註冊為授權服務設定的一部分 `ConfigureServices` `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="dfad9-161">例如，下列程式碼片段會設定名為 "CanadiansOnly" 的原則，其要求使用者的國家/地區宣告值為 "加拿大"。</span><span class="sxs-lookup"><span data-stu-id="dfad9-161">For example, the following code snippet configures a policy called "CanadiansOnly" which has the requirement that the user have the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="dfad9-162">您可以 [在檔中深入瞭解如何建立自訂原則](https://docs.microsoft.com/aspnet/core/security/authorization/policies)。</span><span class="sxs-lookup"><span data-stu-id="dfad9-162">You can [learn more about how to create custom policies in the documentation](https://docs.microsoft.com/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="dfad9-163">無論您使用的是原則或角色，都可以指定應用程式中的特定頁面， Blazor 要求該角色或具有 `[Authorize]` 屬性（attribute）的原則套用於指示詞 `@attribute` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application require that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="dfad9-164">需要角色：</span><span class="sxs-lookup"><span data-stu-id="dfad9-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="dfad9-165">需要滿足原則：</span><span class="sxs-lookup"><span data-stu-id="dfad9-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="dfad9-166">如果您需要存取使用者的驗證狀態、角色或程式碼中的宣告，有兩種主要方式可以達成此目的。</span><span class="sxs-lookup"><span data-stu-id="dfad9-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this.</span></span> <span data-ttu-id="dfad9-167">第一個是以串聯參數形式接收驗證狀態。</span><span class="sxs-lookup"><span data-stu-id="dfad9-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="dfad9-168">第二個是使用插入的來存取狀態 `AuthenticationStateProvider` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="dfad9-169">這些方法的詳細資料將在[ Blazor 安全性檔案](https://docs.microsoft.com/aspnet/core/blazor/security/)中說明。</span><span class="sxs-lookup"><span data-stu-id="dfad9-169">The details of each of these approaches are described in the [Blazor Security documentation](https://docs.microsoft.com/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="dfad9-170">下列程式碼示範如何以串聯 `AuthenticationState` 參數的形式接收：</span><span class="sxs-lookup"><span data-stu-id="dfad9-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="dfad9-171">使用這個參數時，您可以使用下列程式碼來取得使用者：</span><span class="sxs-lookup"><span data-stu-id="dfad9-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="dfad9-172">下列程式碼顯示如何插入 `AuthenticationStateProvider` ：</span><span class="sxs-lookup"><span data-stu-id="dfad9-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="dfad9-173">有了提供者之後，您就可以使用下列程式碼來取得使用者的存取權：</span><span class="sxs-lookup"><span data-stu-id="dfad9-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="dfad9-174">**注意：**`AuthorizeView`本章節稍後所涵蓋的元件提供了一種宣告方式，可控制使用者在頁面或元件上看到的內容。</span><span class="sxs-lookup"><span data-stu-id="dfad9-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="dfad9-175">若要在伺服器應用程式中使用使用者和宣告 (Blazor) 您可能也需要插入 `UserManager<T>` 預設) 的 (用法， `IdentityUser` 您可以用來列舉和修改使用者的宣告。</span><span class="sxs-lookup"><span data-stu-id="dfad9-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="dfad9-176">先插入類型，並將它指派給屬性：</span><span class="sxs-lookup"><span data-stu-id="dfad9-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="dfad9-177">然後使用它來處理使用者的宣告。</span><span class="sxs-lookup"><span data-stu-id="dfad9-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="dfad9-178">下列範例顯示如何在使用者上新增和保存宣告：</span><span class="sxs-lookup"><span data-stu-id="dfad9-178">The following sample shows how to add and persist a claim on a user:</span></span>

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

<span data-ttu-id="dfad9-179">如果您需要使用角色，請遵循相同的方法。</span><span class="sxs-lookup"><span data-stu-id="dfad9-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="dfad9-180">您可能需要插入 (用於 `RoleManager<T>` `IdentityRole` 預設類型) ，以列出和管理角色本身。</span><span class="sxs-lookup"><span data-stu-id="dfad9-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="dfad9-181">**注意：** 在 Blazor WebAssembly 專案中，您將需要提供伺服器 api 來執行這些作業 (而不是使用 `UserManager<T>` 或 `RoleManager<T>` 直接) 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="dfad9-182">BlazorWebAssembly 用戶端應用程式會藉由安全地呼叫針對此目的公開的 API 端點來管理宣告和/或角色。</span><span class="sxs-lookup"><span data-stu-id="dfad9-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="dfad9-183">移轉指南</span><span class="sxs-lookup"><span data-stu-id="dfad9-183">Migration guide</span></span>

<span data-ttu-id="dfad9-184">從 ASP.NET Web Forms 和通用提供者遷移到 ASP.NET Core 身分識別需要幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="dfad9-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="dfad9-185">在目的地資料庫中建立 ASP.NET Core 身分識別資料庫架構</span><span class="sxs-lookup"><span data-stu-id="dfad9-185">Create ASP.NET Core Identity database schema in destination database</span></span>
2. <span data-ttu-id="dfad9-186">將資料從通用提供者架構遷移至 ASP.NET Core 的身分識別架構</span><span class="sxs-lookup"><span data-stu-id="dfad9-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="dfad9-187">將 configuration 從 web.config 遷移至中介軟體和服務，通常位於 `Startup.cs`</span><span class="sxs-lookup"><span data-stu-id="dfad9-187">Migrate configuration from web.config to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="dfad9-188">使用控制項和條件更新個別頁面，以使用標記協助程式和新的身分識別 Api。</span><span class="sxs-lookup"><span data-stu-id="dfad9-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="dfad9-189">下列各節將詳細討論這其中每個步驟。</span><span class="sxs-lookup"><span data-stu-id="dfad9-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="dfad9-190">建立 ASP.NET Core 身分識別架構</span><span class="sxs-lookup"><span data-stu-id="dfad9-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="dfad9-191">有幾種方式可以建立用於 ASP.NET Core 身分識別的必要資料表結構。</span><span class="sxs-lookup"><span data-stu-id="dfad9-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="dfad9-192">最簡單的方式是建立新的 ASP.NET Core Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dfad9-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="dfad9-193">選擇 [Web 應用程式]，然後將驗證變更為使用個別的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="dfad9-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![具有個別使用者帳戶的新專案](./media/security/individual-user-accounts.png)

<span data-ttu-id="dfad9-195">您可以從命令列執行相同的動作 `dotnet new webapp -au Individual` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="dfad9-196">建立應用程式之後，請在該網站上執行並註冊。</span><span class="sxs-lookup"><span data-stu-id="dfad9-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="dfad9-197">您應該會觸發如下所示的頁面：</span><span class="sxs-lookup"><span data-stu-id="dfad9-197">You should trigger a page like the one shown below:</span></span>

![套用遷移頁面](./media/security/apply-migrations-page.png)

<span data-ttu-id="dfad9-199">按一下 [套用遷移] 按鈕，就應該為您建立必要的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="dfad9-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="dfad9-200">此外，遷移檔應該會出現在您的專案中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dfad9-200">In addition, the migration files should appear in your project, as shown:</span></span>

![遷移檔](./media/security/migration-files.png)

<span data-ttu-id="dfad9-202">您可以使用下列命令列工具，自行執行遷移，而不需要執行 web 應用程式：</span><span class="sxs-lookup"><span data-stu-id="dfad9-202">You can run the migration yourself, without running the web application, using this command line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="dfad9-203">如果您想要執行腳本，以將新的架構套用至現有的資料庫，您可以從命令列編寫這些遷移的腳本。</span><span class="sxs-lookup"><span data-stu-id="dfad9-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command line.</span></span> <span data-ttu-id="dfad9-204">執行此命令以產生腳本：</span><span class="sxs-lookup"><span data-stu-id="dfad9-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="dfad9-205">這將會在輸出檔案中產生 SQL 腳本， `auth.sql` 然後針對您想要的任何資料庫來執行。</span><span class="sxs-lookup"><span data-stu-id="dfad9-205">This will produce a SQL script in the output file `auth.sql` which can then be run against whatever database you like.</span></span> <span data-ttu-id="dfad9-206">如果您在執行命令時遇到任何問題 `dotnet ef` ， [請確定您已在系統上安裝 EF Core 工具](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="dfad9-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="dfad9-207">如果您的來源資料表有額外的資料行，您必須在新的架構中找出這些資料行的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="dfad9-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="dfad9-208">一般而言，資料表上的資料行 `aspnet_Membership` 應該對應至 `AspNetUsers` 資料表。</span><span class="sxs-lookup"><span data-stu-id="dfad9-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="dfad9-209">上的資料行 `aspnet_Roles` 應該對應至 `AspNetRoles` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="dfad9-210">資料表上的任何其他資料行 `aspnet_UsersInRoles` 都會加入至 `AspNetUserRoles` 資料表。</span><span class="sxs-lookup"><span data-stu-id="dfad9-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="dfad9-211">也值得考慮將任何額外的資料行放在不同的資料表上，以便未來的遷移不需要考慮預設身分識別架構的自訂。</span><span class="sxs-lookup"><span data-stu-id="dfad9-211">It's also worth considering putting any additional columns on separate tables, so that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="dfad9-212">將資料從通用提供者遷移至 ASP.NET Core 身分識別</span><span class="sxs-lookup"><span data-stu-id="dfad9-212">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="dfad9-213">當您備妥目的地資料表架構後，下一個步驟是將您的使用者和角色記錄遷移至新的架構。</span><span class="sxs-lookup"><span data-stu-id="dfad9-213">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="dfad9-214">您可以在 [這裡](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)找到架構差異的完整清單，包括哪些資料行對應到哪些新資料行。</span><span class="sxs-lookup"><span data-stu-id="dfad9-214">A complete list of the schema differences, including which columns map to which new columns, can be found [here](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="dfad9-215">若要將使用者的成員資格遷移至新的身分識別資料表，您應 [遵循檔中所述的步驟](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)。</span><span class="sxs-lookup"><span data-stu-id="dfad9-215">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="dfad9-216">遵循這些步驟和提供的腳本之後，您的使用者將需要在下次登入時變更其密碼。</span><span class="sxs-lookup"><span data-stu-id="dfad9-216">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="dfad9-217">您可以遷移使用者密碼，但程式更牽涉到更多。</span><span class="sxs-lookup"><span data-stu-id="dfad9-217">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="dfad9-218">要求使用者在遷移過程中更新其密碼，並鼓勵他們使用新的唯一密碼，可能會增強應用程式的整體安全性。</span><span class="sxs-lookup"><span data-stu-id="dfad9-218">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="dfad9-219">將安全性設定從 web.config 遷移至 Startup.cs</span><span class="sxs-lookup"><span data-stu-id="dfad9-219">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="dfad9-220">如先前所述，ASP.NET 成員資格和角色提供者會在應用程式的 web.config 檔中設定。</span><span class="sxs-lookup"><span data-stu-id="dfad9-220">As noted above, ASP.NET membership and role providers are configured in the application's web.config file.</span></span> <span data-ttu-id="dfad9-221">由於 ASP.NET Core 的應用程式不會系結至 IIS，並且使用個別的系統進行設定，因此必須在其他地方設定這些設定。</span><span class="sxs-lookup"><span data-stu-id="dfad9-221">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="dfad9-222">在大部分的情況下，會在檔案中設定 ASP.NET Core 身分識別 `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-222">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="dfad9-223">開啟稍早建立的 Web 專案 (，以產生識別資料表架構) 並檢查其檔案 `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-223">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="dfad9-224">預設的 ConfigureServices 方法會新增 EF Core 和身分識別的支援：</span><span class="sxs-lookup"><span data-stu-id="dfad9-224">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

<span data-ttu-id="dfad9-225">`AddDefaultIdentity`擴充方法是用來設定身分識別，以使用預設值 `ApplicationDbContext` 和架構的 `IdentityUser` 類型。</span><span class="sxs-lookup"><span data-stu-id="dfad9-225">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="dfad9-226">如果您是使用自訂 `IdentityUser` ，請務必在此指定它的類型。</span><span class="sxs-lookup"><span data-stu-id="dfad9-226">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="dfad9-227">如果這些擴充方法無法在您的應用程式中運作，請檢查您是否有適當的 using 語句，以及您是否有必要的 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="dfad9-227">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="dfad9-228">例如，您的專案應該已參考某些版本的 `Microsoft.AspNetCore.Identity.EntityFrameworkCore` 和 `Microsoft.AspNetCore.Identity.UI` 套件。</span><span class="sxs-lookup"><span data-stu-id="dfad9-228">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="dfad9-229">此外 `Startup.cs` ，您應該會看到為網站設定的必要中介軟體。</span><span class="sxs-lookup"><span data-stu-id="dfad9-229">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="dfad9-230">具體來說 `UseAuthentication` ， `UseAuthorization` 應該在適當的位置進行設定。</span><span class="sxs-lookup"><span data-stu-id="dfad9-230">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

<span data-ttu-id="dfad9-231">ASP.NET Identity 不會將匿名或以角色為基礎的存取設定至的位置 `Startup.cs` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-231">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="dfad9-232">您必須將任何位置特定的授權設定資料移轉至 ASP.NET Core 中的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="dfad9-232">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="dfad9-233">請記下哪些資料夾和頁面需要這類更新。</span><span class="sxs-lookup"><span data-stu-id="dfad9-233">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="dfad9-234">您將在下一節中進行這些變更。</span><span class="sxs-lookup"><span data-stu-id="dfad9-234">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="dfad9-235">更新個別頁面以使用 ASP.NET Core 身分識別抽象</span><span class="sxs-lookup"><span data-stu-id="dfad9-235">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="dfad9-236">在您的 ASP.NET Web Forms 應用程式中，如果您有 web.config 設定來拒絕匿名使用者的特定頁面或資料夾的存取權，您只要將此 `[Authorize]` 屬性新增至這類頁面，即可進行遷移：</span><span class="sxs-lookup"><span data-stu-id="dfad9-236">In your ASP.NET Web Forms application, if you had web.config settings to deny access to certain pages or folders to anonymous users, you would migrate these by simply adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="dfad9-237">如果您對屬於某個角色的使用者進一步拒絕存取，您也可以藉由新增指定角色的屬性來進行遷移：</span><span class="sxs-lookup"><span data-stu-id="dfad9-237">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="dfad9-238">請注意，此 `[Authorize]` 屬性只適用于透過 `@page` 路由器達成的元件 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-238">Note that the `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="dfad9-239">屬性無法與子元件搭配使用，而應該改用 `AuthorizeView` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-239">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="dfad9-240">如果您在頁面標記內有邏輯來判斷是否要對特定使用者顯示某些程式碼，您可以將此取代為 `AuthorizeView` 元件。</span><span class="sxs-lookup"><span data-stu-id="dfad9-240">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="dfad9-241">[AuthorizeView 元件](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component)會選擇性地顯示 UI，取決於使用者是否已獲授權查看。</span><span class="sxs-lookup"><span data-stu-id="dfad9-241">The [AuthorizeView component](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="dfad9-242">它也會公開 `context` 可以用來存取使用者資訊的變數。</span><span class="sxs-lookup"><span data-stu-id="dfad9-242">It also exposes a `context` variable that can be used to access user information.</span></span>

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

<span data-ttu-id="dfad9-243">您可以使用屬性設定的，存取程式邏輯內的驗證狀態 `Task<AuthenticationState` `[CascadingParameter]` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-243">You can access authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="dfad9-244">這可讓您存取使用者，這可讓您判斷它們是否經過驗證，以及是否屬於特定的角色。</span><span class="sxs-lookup"><span data-stu-id="dfad9-244">This will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="dfad9-245">如果您需要評估原則 cti，您可以插入的實例， `IAuthorizationService` 並 `AuthorizeAsync` 在其上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="dfad9-245">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="dfad9-246">下列範例程式碼示範如何取得使用者資訊，並允許授權的使用者執行原則所限制的工作 `content-editor` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-246">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

<span data-ttu-id="dfad9-247">`AuthenticationState`首先需要將設定為串聯值，才能系結至像這樣的串聯參數。</span><span class="sxs-lookup"><span data-stu-id="dfad9-247">The `AuthenticationState` does first need to be setup as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="dfad9-248">這通常是使用元件來完成 `CascadingAuthenticationState` 。</span><span class="sxs-lookup"><span data-stu-id="dfad9-248">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="dfad9-249">這通常是在中完成 `App.razor` ：</span><span class="sxs-lookup"><span data-stu-id="dfad9-249">This is typically done in `App.razor`:</span></span>

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a><span data-ttu-id="dfad9-250">摘要</span><span class="sxs-lookup"><span data-stu-id="dfad9-250">Summary</span></span>

<span data-ttu-id="dfad9-251">Blazor 使用與 ASP.NET Core 相同的安全性模型，這是 ASP.NET Core 身分識別。</span><span class="sxs-lookup"><span data-stu-id="dfad9-251">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="dfad9-252">從通用提供者遷移到 ASP.NET Core 身分識別相當簡單，但前提是不太太多自訂套用至原始資料架構。</span><span class="sxs-lookup"><span data-stu-id="dfad9-252">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="dfad9-253">一旦資料移轉之後，在應用程式中使用驗證和授權的 Blazor 記錄就會有完整的記錄，並可進行設定，以及針對大部分的安全性需求進行程式設計支援。</span><span class="sxs-lookup"><span data-stu-id="dfad9-253">Once the data has been migrated, working with authentication and authorization in Blazor apps is well-documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="dfad9-254">參考</span><span class="sxs-lookup"><span data-stu-id="dfad9-254">References</span></span>

- [<span data-ttu-id="dfad9-255">ASP.NET Core 上的身分識別簡介</span><span class="sxs-lookup"><span data-stu-id="dfad9-255">Introduction to Identity on ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="dfad9-256">從 ASP.NET 成員資格驗證遷移至 ASP.NET Core 2.0 身分識別</span><span class="sxs-lookup"><span data-stu-id="dfad9-256">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="dfad9-257">將驗證和身分識別遷移至 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dfad9-257">Migrate Authentication and Identity to ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/migration/identity)
- [<span data-ttu-id="dfad9-258">ASP.NET Core Blazor 驗證與授權</span><span class="sxs-lookup"><span data-stu-id="dfad9-258">ASP.NET Core Blazor authentication and authorization</span></span>](https://docs.microsoft.com/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="dfad9-259">[上一個](config.md) 
>[下一步](migration.md)</span><span class="sxs-lookup"><span data-stu-id="dfad9-259">[Previous](config.md)
[Next](migration.md)</span></span>
