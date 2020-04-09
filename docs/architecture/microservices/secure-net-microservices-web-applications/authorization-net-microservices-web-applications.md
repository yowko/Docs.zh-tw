---
title: 關於 .NET 微服務和 Web 應用程式中的授權
description: .NET 微服務和 Web 應用程式中的安全性 - 取得 ASP.NET Core 應用程式中主要授權選項 (以角色為基礎和以原則為基礎) 的概觀。
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 27936a33ea2bb46cedb9d10ee47a2117e1843e14
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988202"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>關於 .NET 微服務和 Web 應用程式中的授權

在驗證之後，ASP.NET Core Web API 需要授與存取權。 這個程序允許服務讓 API 可供某些已驗證的使用者使用，而不是所有使用者都可使用。 [授權](/aspnet/core/security/authorization/introduction)可以基於使用者的角色或自定義策略完成,其中可能包括檢查聲明或其他啟發式。

限制對ASP.NET酷睿 MVC 路由的訪問與將授權屬性應用於操作方法(如果控制器的所有操作都需要授權)一樣簡單,如以下範例所示:

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

根據預設，新增不含參數的 Authorize 屬性會限制已驗證使用者對該控制器或動作的存取權。 為進一步限制 API 僅供特定使用者使用，您可以擴充屬性，指定使用者必須滿足的必要角色或原則。

## <a name="implement-role-based-authorization"></a>實作以角色為基礎的授權

ASP.NET Core 身分識別具有內建的角色概念。 除使用者之外，ASP.NET Core 身分識別還會儲存應用程式所用之不同角色的資訊，並追蹤哪些使用者獲指派哪些角色。 您可以使用 `RoleManager` 型別 (它會更新持續性儲存體中的角色) 和 `UserManager` 型別 (它可授與或撤銷使用者角色)，以程式設計方式來變更這些指派。

如果使用 JWT 承載權杖進行身份驗證,則 ASP.NET 酷睿 JWT 承載身份驗證中間件將根據權杖中找到的角色聲明填充使用者的角色。 若要限制僅有特定角色的使用者可以存取 MVC 動作或控制器，您可以在授權註解 (屬性) 中包含 Roles 參數，如下列程式碼片段所示：

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

在本例中，只有系統管理員或 PowerUser 角色的使用者可以存取 ControlPanel 控制器中的 API (例如執行 SetTime 動作)。 關機 API 進一步限制僅限系統管理員角色存取。

為要求使用者具備多種角色，您要使用多個 Authorize 屬性，如下例所示：

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

在本例中，若要呼叫 API1，使用者必須：

- 為系統管理員或** PowerUser 角色，且**

- 為 RemoteEmployee 角色，「並」**

- 滿足 CustomPolicy 授權的自訂處理常式。

## <a name="implement-policy-based-authorization"></a>實作以原則為基礎的授權

您也可以使用[授權原則](https://docs.asp.net/en/latest/security/authorization/policies.html)撰寫自訂授權規則。 此節提供摡觀。 如需詳細資訊，請參閱 [ASP.NET 授權工作坊](https://github.com/blowdart/AspNetAuthorizationWorkshop) \(英文\)。

自訂授權原則會使用 service.AddAuthorization 方法在 Startup.ConfigureServices 方法中註冊。 這個方法採用委派來設定 AuthorizationOptions 引數。

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

如範例所示，原則可與不同類型的需求建立關聯性。 註冊策略後,可以通過將策略的名稱傳遞給"授權"屬性(`[Authorize(Policy="EmployeesOnly")]`例如 )策略參數,從而將其應用於操作或控制器,例如,策略可以有多個要求,而不僅僅是一個要求(如這些示例所示)。

在前例中，第一個 AddPolicy 呼叫只是根據角色授權的替代方式。 若 `[Authorize(Policy="AdministratorsOnly")]` 已套用至 API，只有系統管理員角色的使用者才能夠存取它。

第二個 <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> 呼叫示範的簡單方法，要求應該向使用者顯示特定的宣告。 <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> 方法也會選擇性使用宣告的預期值。 如已指定值，只有當使用者同時具有正確的類型宣告以及其中一個指定的值時，才會滿足此需求。 如果您使用 JWT 持有人驗證中介軟體，則所有的 JWT 屬性都可作為使用者宣告。

本文最有趣的原則是第三個 `AddPolicy` 方法，因為它會使用自訂的授權需求。 藉由使用自訂的授權需求，您對授權的執行方式可有更大的掌控力。 您必須實作這些類型，此操作才會生效：

- Requirements 型別衍生自 <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> 並包含指定需求詳細資料的欄位。 在範例中，這是範例 `MinimumAgeRequirement` 型別的一個存留期欄位。

- 實作 <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601> 的處理常式，其中 T 是處理常式可滿足的 <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> 的型別。 此處理常式必須實作 <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> 方法，檢查指定的內容是否包含使用者滿足需求的資訊。

如果使用者滿足需求，則 `context.Succeed` 呼叫會指出使用者已獲得授權。 如果使用者有多種方式滿足授權需求，就可以建立多個處理常式。

除了使用 `AddPolicy` 呼叫來註冊自訂原則需求，您也需要透過相依性插入 (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`) 來註冊自訂需求處理常式。

檢查使用者的使用者的使用者`DateOfBirth`的使用者的使用者的使用者的使用者的使用者授權要求與處理程式的範例ASP.NET Core[授權文件](https://docs.asp.net/en/latest/security/authorization/policies.html)中提供 。

## <a name="additional-resources"></a>其他資源

- **ASP.NET核心身份驗證** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **ASP.NET核心授權** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **基於角色的授權** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **基於策略的自訂授權** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[前一個](index.md)
>[下一個](developer-app-secrets-storage.md)
