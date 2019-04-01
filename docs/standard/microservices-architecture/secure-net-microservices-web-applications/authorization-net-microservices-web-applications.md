---
title: 關於 .NET 微服務和 Web 應用程式中的授權
description: .NET 微服務和 Web 應用程式中的安全性 - 取得 ASP.NET Core 應用程式中主要授權選項 (以角色為基礎和以原則為基礎) 的概觀。
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466357"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>關於 .NET 微服務和 Web 應用程式中的授權

在驗證之後，ASP.NET Core Web API 需要授與存取權。 這個程序允許服務向某些已驗證的使用者提供 API，但不是所有使用者。 [授權](/aspnet/core/security/authorization/introduction)可以根據使用者的角色或自訂原則來完成，這可能包含檢查宣告或其他啟發學習法。

限制對 ASP.NET Core MVC 路由的存取，就像將 Authorize 屬性套用至動作方法一樣簡單 (或套用至控制器類別，如果所有控制器動作都需要授權)，如下例所示：

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

如果您要使用 JWT 持有人權杖進行驗證，ASP.NET Core JWT 持有人驗證中介軟體會根據權杖中找到的角色宣告，填入使用者的角色。 若要限制僅有特定角色的使用者可以存取 MVC 動作或控制器，您可以在授權註解 (屬性) 中包含 Roles 參數，如下列程式碼片段所示：

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

- 為系統管理員或 PowerUser 角色，且

- 為 RemoteEmployee 角色，「並」

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

如範例所示，原則可與不同類型的需求建立關聯性。 註冊原則之後，即可套用到動作或控制器，只要將原則的名稱傳遞為 Authorize 屬性的 Policy 引數 (例如，`[Authorize(Policy="EmployeesOnly")]`)。原則可有多個需求，不是只有一個 (如這些範例所示)。

在前例中，第一個 AddPolicy 呼叫只是根據角色授權的替代方式。 若 `[Authorize(Policy="AdministratorsOnly")]` 已套用至 API，只有系統管理員角色的使用者才能夠存取它。

第二個 <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> 呼叫示範的簡單方法，要求應該向使用者顯示特定的宣告。 <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> 方法也會選擇性使用宣告的預期值。 如已指定值，只有當使用者同時具有正確的類型宣告以及其中一個指定的值時，才會滿足此需求。 如果您使用 JWT 持有人驗證中介軟體，則所有的 JWT 屬性都可作為使用者宣告。

本文最有趣的原則是第三個 `AddPolicy` 方法，因為它會使用自訂的授權需求。 藉由使用自訂的授權需求，您對授權的執行方式可有更大的掌控力。 您必須實作這些類型，此操作才會生效：

- Requirements 型別衍生自 <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> 並包含指定需求詳細資料的欄位。 在範例中，這是範例 `MinimumAgeRequirement` 型別的一個存留期欄位。

- 實作 <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601> 的處理常式，其中 T 是處理常式可滿足的 <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> 的型別。 此處理常式必須實作 <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> 方法，檢查指定的內容是否包含使用者滿足需求的資訊。

如果使用者滿足需求，則 `context.Succeed` 呼叫會指出使用者已獲得授權。 如果使用者有多種方式滿足授權需求，就可以建立多個處理常式。

除了使用 `AddPolicy` 呼叫來註冊自訂原則需求，您也需要透過相依性插入 (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`) 來註冊自訂需求處理常式。

自訂授權需求和檢查使用者存留期處理常式 (以 `DateOfBirth` 宣告為基礎) 的範例，可自 ASP.NET Core [授權文件](https://docs.asp.net/en/latest/security/authorization/policies.html)取得。

## <a name="additional-resources"></a>其他資源

- **ASP.NET Core 驗證** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **ASP.NET Core 授權** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **以角色為基礎的授權** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **自訂以原則為基礎的授權** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](developer-app-secrets-storage.md)
