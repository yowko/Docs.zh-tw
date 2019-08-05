---
title: 關於 .NET 微服務和 Web 應用程式中的授權
description: .NET 微服務和 Web 應用程式中的安全性 - 取得 ASP.NET Core 應用程式中主要授權選項 (以角色為基礎和以原則為基礎) 的概觀。
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675655"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="f61aa-103">關於 .NET 微服務和 Web 應用程式中的授權</span><span class="sxs-lookup"><span data-stu-id="f61aa-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="f61aa-104">在驗證之後，ASP.NET Core Web API 需要授與存取權。</span><span class="sxs-lookup"><span data-stu-id="f61aa-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="f61aa-105">這個程序允許服務向某些已驗證的使用者提供 API，但不是所有使用者。</span><span class="sxs-lookup"><span data-stu-id="f61aa-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="f61aa-106">[授權](/aspnet/core/security/authorization/introduction)可以根據使用者的角色或自訂原則來完成，這可能包含檢查宣告或其他啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="f61aa-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="f61aa-107">限制對 ASP.NET Core MVC 路由的存取，就像將 Authorize 屬性套用至動作方法一樣簡單 (或套用至控制器類別，如果所有控制器動作都需要授權)，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="f61aa-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

<span data-ttu-id="f61aa-108">根據預設，新增不含參數的 Authorize 屬性會限制已驗證使用者對該控制器或動作的存取權。</span><span class="sxs-lookup"><span data-stu-id="f61aa-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="f61aa-109">為進一步限制 API 僅供特定使用者使用，您可以擴充屬性，指定使用者必須滿足的必要角色或原則。</span><span class="sxs-lookup"><span data-stu-id="f61aa-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="f61aa-110">實作以角色為基礎的授權</span><span class="sxs-lookup"><span data-stu-id="f61aa-110">Implement role-based authorization</span></span>

<span data-ttu-id="f61aa-111">ASP.NET Core 身分識別具有內建的角色概念。</span><span class="sxs-lookup"><span data-stu-id="f61aa-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="f61aa-112">除使用者之外，ASP.NET Core 身分識別還會儲存應用程式所用之不同角色的資訊，並追蹤哪些使用者獲指派哪些角色。</span><span class="sxs-lookup"><span data-stu-id="f61aa-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="f61aa-113">您可以使用 `RoleManager` 型別 (它會更新持續性儲存體中的角色) 和 `UserManager` 型別 (它可授與或撤銷使用者角色)，以程式設計方式來變更這些指派。</span><span class="sxs-lookup"><span data-stu-id="f61aa-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="f61aa-114">如果您要使用 JWT 持有人權杖進行驗證，ASP.NET Core JWT 持有人驗證中介軟體會根據權杖中找到的角色宣告，填入使用者的角色。</span><span class="sxs-lookup"><span data-stu-id="f61aa-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="f61aa-115">若要限制僅有特定角色的使用者可以存取 MVC 動作或控制器，您可以在授權註解 (屬性) 中包含 Roles 參數，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="f61aa-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

<span data-ttu-id="f61aa-116">在本例中，只有系統管理員或 PowerUser 角色的使用者可以存取 ControlPanel 控制器中的 API (例如執行 SetTime 動作)。</span><span class="sxs-lookup"><span data-stu-id="f61aa-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="f61aa-117">關機 API 進一步限制僅限系統管理員角色存取。</span><span class="sxs-lookup"><span data-stu-id="f61aa-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="f61aa-118">為要求使用者具備多種角色，您要使用多個 Authorize 屬性，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="f61aa-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="f61aa-119">在本例中，若要呼叫 API1，使用者必須：</span><span class="sxs-lookup"><span data-stu-id="f61aa-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="f61aa-120">為系統管理員或  PowerUser 角色，且 </span><span class="sxs-lookup"><span data-stu-id="f61aa-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="f61aa-121">為 RemoteEmployee 角色，「並」 </span><span class="sxs-lookup"><span data-stu-id="f61aa-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="f61aa-122">滿足 CustomPolicy 授權的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="f61aa-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="f61aa-123">實作以原則為基礎的授權</span><span class="sxs-lookup"><span data-stu-id="f61aa-123">Implement policy-based authorization</span></span>

<span data-ttu-id="f61aa-124">您也可以使用[授權原則](https://docs.asp.net/en/latest/security/authorization/policies.html)撰寫自訂授權規則。</span><span class="sxs-lookup"><span data-stu-id="f61aa-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="f61aa-125">此節提供摡觀。</span><span class="sxs-lookup"><span data-stu-id="f61aa-125">This section provides an overview.</span></span> <span data-ttu-id="f61aa-126">如需詳細資訊，請參閱 [ASP.NET 授權工作坊](https://github.com/blowdart/AspNetAuthorizationWorkshop) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f61aa-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="f61aa-127">自訂授權原則會使用 service.AddAuthorization 方法在 Startup.ConfigureServices 方法中註冊。</span><span class="sxs-lookup"><span data-stu-id="f61aa-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="f61aa-128">這個方法採用委派來設定 AuthorizationOptions 引數。</span><span class="sxs-lookup"><span data-stu-id="f61aa-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));
    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));
    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

<span data-ttu-id="f61aa-129">如範例所示，原則可與不同類型的需求建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="f61aa-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="f61aa-130">註冊原則之後，即可套用到動作或控制器，只要將原則的名稱傳遞為 Authorize 屬性的 Policy 引數 (例如，`[Authorize(Policy="EmployeesOnly")]`)。原則可有多個需求，不是只有一個 (如這些範例所示)。</span><span class="sxs-lookup"><span data-stu-id="f61aa-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="f61aa-131">在前例中，第一個 AddPolicy 呼叫只是根據角色授權的替代方式。</span><span class="sxs-lookup"><span data-stu-id="f61aa-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="f61aa-132">若 `[Authorize(Policy="AdministratorsOnly")]` 已套用至 API，只有系統管理員角色的使用者才能夠存取它。</span><span class="sxs-lookup"><span data-stu-id="f61aa-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="f61aa-133">第二個 <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> 呼叫示範的簡單方法，要求應該向使用者顯示特定的宣告。</span><span class="sxs-lookup"><span data-stu-id="f61aa-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="f61aa-134"><xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> 方法也會選擇性使用宣告的預期值。</span><span class="sxs-lookup"><span data-stu-id="f61aa-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="f61aa-135">如已指定值，只有當使用者同時具有正確的類型宣告以及其中一個指定的值時，才會滿足此需求。</span><span class="sxs-lookup"><span data-stu-id="f61aa-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="f61aa-136">如果您使用 JWT 持有人驗證中介軟體，則所有的 JWT 屬性都可作為使用者宣告。</span><span class="sxs-lookup"><span data-stu-id="f61aa-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="f61aa-137">本文最有趣的原則是第三個 `AddPolicy` 方法，因為它會使用自訂的授權需求。</span><span class="sxs-lookup"><span data-stu-id="f61aa-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="f61aa-138">藉由使用自訂的授權需求，您對授權的執行方式可有更大的掌控力。</span><span class="sxs-lookup"><span data-stu-id="f61aa-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="f61aa-139">您必須實作這些類型，此操作才會生效：</span><span class="sxs-lookup"><span data-stu-id="f61aa-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="f61aa-140">Requirements 型別衍生自 <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> 並包含指定需求詳細資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="f61aa-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="f61aa-141">在範例中，這是範例 `MinimumAgeRequirement` 型別的一個存留期欄位。</span><span class="sxs-lookup"><span data-stu-id="f61aa-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="f61aa-142">實作 <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601> 的處理常式，其中 T 是處理常式可滿足的 <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> 的型別。</span><span class="sxs-lookup"><span data-stu-id="f61aa-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="f61aa-143">此處理常式必須實作 <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> 方法，檢查指定的內容是否包含使用者滿足需求的資訊。</span><span class="sxs-lookup"><span data-stu-id="f61aa-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="f61aa-144">如果使用者滿足需求，則 `context.Succeed` 呼叫會指出使用者已獲得授權。</span><span class="sxs-lookup"><span data-stu-id="f61aa-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="f61aa-145">如果使用者有多種方式滿足授權需求，就可以建立多個處理常式。</span><span class="sxs-lookup"><span data-stu-id="f61aa-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="f61aa-146">除了使用 `AddPolicy` 呼叫來註冊自訂原則需求，您也需要透過相依性插入 (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`) 來註冊自訂需求處理常式。</span><span class="sxs-lookup"><span data-stu-id="f61aa-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="f61aa-147">自訂授權需求和檢查使用者存留期處理常式 (以 `DateOfBirth` 宣告為基礎) 的範例，可自 ASP.NET Core [授權文件](https://docs.asp.net/en/latest/security/authorization/policies.html)取得。</span><span class="sxs-lookup"><span data-stu-id="f61aa-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f61aa-148">其他資源</span><span class="sxs-lookup"><span data-stu-id="f61aa-148">Additional resources</span></span>

- <span data-ttu-id="f61aa-149">**ASP.NET Core 驗證** </span><span class="sxs-lookup"><span data-stu-id="f61aa-149">**ASP.NET Core Authentication** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="f61aa-150">**ASP.NET Core 授權** </span><span class="sxs-lookup"><span data-stu-id="f61aa-150">**ASP.NET Core Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="f61aa-151">**以角色為基礎的授權** </span><span class="sxs-lookup"><span data-stu-id="f61aa-151">**Role-based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="f61aa-152">**自訂以原則為基礎的授權** </span><span class="sxs-lookup"><span data-stu-id="f61aa-152">**Custom Policy-Based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="f61aa-153">[上一頁](index.md)
>[下一頁](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="f61aa-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
