---
title: "關於.NET microservices 及 web 應用程式中的授權"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |關於.NET microservices 及 web 應用程式中的授權"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 51adda4f5bdb28154f17b9a988ee2d887bf1d461
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="a6762-104">關於.NET microservices 及 web 應用程式中的授權</span><span class="sxs-lookup"><span data-stu-id="a6762-104">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="a6762-105">在驗證之後，ASP.NET Core Web Api 需要授權存取。</span><span class="sxs-lookup"><span data-stu-id="a6762-105">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="a6762-106">這個程序在可驗證的使用者，但不是為所有允許的服務，讓應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="a6762-106">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="a6762-107">[授權](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)可以根據使用者的角色來完成，或可能包含宣告或其他啟發學習法所檢查的自訂原則為基礎。</span><span class="sxs-lookup"><span data-stu-id="a6762-107">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="a6762-108">限制對 ASP.NET Core MVC 路由的存取是簡單，只要將套用 Authorize 屬性至動作方法 （或如果在控制器的所有動作都需要授權的控制站的類別），下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="a6762-108">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="a6762-109">根據預設，加入不含參數的授權屬性會限制該控制器或動作的存取權已驗證的使用者。</span><span class="sxs-lookup"><span data-stu-id="a6762-109">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="a6762-110">若要進一步限制只有特定使用者的可用應用程式開發介面，可以擴充屬性，來指定必要的角色或使用者必須滿足的原則。</span><span class="sxs-lookup"><span data-stu-id="a6762-110">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="a6762-111">實作以角色為基礎的授權</span><span class="sxs-lookup"><span data-stu-id="a6762-111">Implementing role-based authorization</span></span>

<span data-ttu-id="a6762-112">ASP.NET Core 識別具有內建角色的概念。</span><span class="sxs-lookup"><span data-stu-id="a6762-112">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="a6762-113">除了使用者，ASP.NET Core 識別儲存應用程式所使用的不同角色的相關資訊並追蹤哪些使用者已指派給哪些角色。</span><span class="sxs-lookup"><span data-stu-id="a6762-113">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="a6762-114">以 RoleManager 型別 （更新持續性儲存體中的角色） 和 UserManager 型別 （可指派，或取消指派使用者角色） 來以程式設計方式變更這些指派。</span><span class="sxs-lookup"><span data-stu-id="a6762-114">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="a6762-115">如果您要進行驗證的 JWT bearer 權杖，ASP.NET Core JWT 承載驗證中介軟體將會填入使用者的角色根據權杖中找到的角色宣告。</span><span class="sxs-lookup"><span data-stu-id="a6762-115">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="a6762-116">若要限制存取的 MVC 動作或控制器中特定角色的使用者，您可以授權標頭中包含的角色參數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a6762-116">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

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

<span data-ttu-id="a6762-117">在此範例中，只有系統管理員或 PowerUser 角色中的使用者可以在 [控制台] 的控制器 （例如執行 SetTime 動作） 中存取應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="a6762-117">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="a6762-118">關閉應用程式開發介面進一步限制為只允許存取使用者的系統管理員角色中。</span><span class="sxs-lookup"><span data-stu-id="a6762-118">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="a6762-119">若要要求使用者是多個角色中，您會使用多個授權屬性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a6762-119">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="a6762-120">在此範例中，若要呼叫 API1，使用者必須：</span><span class="sxs-lookup"><span data-stu-id="a6762-120">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="a6762-121">系統管理員在*或*PowerUser 角色*和*</span><span class="sxs-lookup"><span data-stu-id="a6762-121">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="a6762-122">RemoteEmployee 角色時，會*和*</span><span class="sxs-lookup"><span data-stu-id="a6762-122">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="a6762-123">滿足 CustomPolicy 授權的自訂處理常式。</span><span class="sxs-lookup"><span data-stu-id="a6762-123">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="a6762-124">實作以原則為基礎的授權</span><span class="sxs-lookup"><span data-stu-id="a6762-124">Implementing policy-based authorization</span></span>

<span data-ttu-id="a6762-125">自訂授權規則也可以寫入使用[授權原則](https://docs.asp.net/en/latest/security/authorization/policies.html)。</span><span class="sxs-lookup"><span data-stu-id="a6762-125">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="a6762-126">本節中，我們會提供概觀。</span><span class="sxs-lookup"><span data-stu-id="a6762-126">In this section we provide an overview.</span></span> <span data-ttu-id="a6762-127">更多詳細資料位於線上[ASP.NET 授權 Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop)。</span><span class="sxs-lookup"><span data-stu-id="a6762-127">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="a6762-128">Startup.ConfigureServices 方法使用服務中註冊自訂授權原則。AddAuthorization 方法。</span><span class="sxs-lookup"><span data-stu-id="a6762-128">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="a6762-129">這個方法會採用設定 AuthorizationOptions 引數的委派。</span><span class="sxs-lookup"><span data-stu-id="a6762-129">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="a6762-130">此範例所示，原則可以是不同類型的需求與相關聯。</span><span class="sxs-lookup"><span data-stu-id="a6762-130">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="a6762-131">註冊原則之後，它們可以套用到某個動作或控制器的傳遞原則屬性的引數授權原則的名稱 (例如， \[Authorize(Policy="EmployeesOnly")\]) 可以有原則多個需求，不是只有一個 （如這些範例中所示）。</span><span class="sxs-lookup"><span data-stu-id="a6762-131">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="a6762-132">在上述範例中，第一次 AddPolicy 呼叫是只根據角色來授權的替代方式。</span><span class="sxs-lookup"><span data-stu-id="a6762-132">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="a6762-133">如果\[Authorize(Policy="AdministratorsOnly")\]套用至應用程式開發介面，只有系統管理員角色中的使用者，才能夠存取它。</span><span class="sxs-lookup"><span data-stu-id="a6762-133">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="a6762-134">第二個 AddPolicy 呼叫示範需要特定的宣告，應該會顯示使用者的簡單方法。</span><span class="sxs-lookup"><span data-stu-id="a6762-134">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="a6762-135">RequireClaim 方法也會使用宣告的預期值。</span><span class="sxs-lookup"><span data-stu-id="a6762-135">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="a6762-136">如果指定的值，只有當使用者具有都正確的型別宣告，以及其中一個指定的值，是為了滿足此需求。</span><span class="sxs-lookup"><span data-stu-id="a6762-136">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="a6762-137">如果您使用 JWT 承載驗證中介軟體，所有的 JWT 屬性可做為使用者宣告。</span><span class="sxs-lookup"><span data-stu-id="a6762-137">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="a6762-138">最有趣如下所示的原則是在第三個 AddPolicy 方法中，因為它會使用自訂的授權需求。</span><span class="sxs-lookup"><span data-stu-id="a6762-138">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="a6762-139">藉由使用自訂的授權需求，您可以有更多的控制如何執行授權。</span><span class="sxs-lookup"><span data-stu-id="a6762-139">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="a6762-140">針對此目的，您必須實作這些型別：</span><span class="sxs-lookup"><span data-stu-id="a6762-140">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="a6762-141">需求類型衍生自 IAuthorizationRequirement 並包含指定之需求的詳細資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="a6762-141">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="a6762-142">在範例中，這是範例 MinimumAgeRequirement 類型的一個時間欄位。</span><span class="sxs-lookup"><span data-stu-id="a6762-142">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="a6762-143">處理常式實作 AuthorizationHandler&lt;T&gt;，其中 T 是 IAuthorizationRequirement，可滿足此處理常式的類型。</span><span class="sxs-lookup"><span data-stu-id="a6762-143">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="a6762-144">此處理常式必須實作 HandleRequirementAsync 方法，這個方法會檢查指定的內容，其中包含使用者的資訊是否滿足需求。</span><span class="sxs-lookup"><span data-stu-id="a6762-144">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="a6762-145">如果使用者符合需求，也就是內容的呼叫。將會成功，表示使用者已授權。</span><span class="sxs-lookup"><span data-stu-id="a6762-145">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="a6762-146">如果有多個使用者可能符合授權需求的方式，就可以建立多個處理常式。</span><span class="sxs-lookup"><span data-stu-id="a6762-146">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="a6762-147">除了向 AddPolicy 呼叫的自訂原則的需求，您也需要註冊自訂需求的處理常式透過相依性插入 （服務。AddTransient&lt;IAuthorizationHandler、 MinimumAgeHandler&gt;（)）。</span><span class="sxs-lookup"><span data-stu-id="a6762-147">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="a6762-148">自訂授權需求和檢查 （根據 DateOfBirth 宣告） 的使用者的年齡的處理常式的範例可用於 ASP.NET Core[授權文件](https://docs.asp.net/en/latest/security/authorization/policies.html)。</span><span class="sxs-lookup"><span data-stu-id="a6762-148">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a6762-149">其他資源</span><span class="sxs-lookup"><span data-stu-id="a6762-149">Additional resources</span></span>

-   <span data-ttu-id="a6762-150">**ASP.NET Core 驗證**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="a6762-150">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="a6762-151">**ASP.NET Core 授權**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="a6762-151">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="a6762-152">**角色型授權**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="a6762-152">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="a6762-153">**以原則為基礎的自訂授權**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="a6762-153">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="a6762-154">[上一個](index.md) [下一步] (開發人員為應用程式-機密-storage.md)</span><span class="sxs-lookup"><span data-stu-id="a6762-154">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span></span>
