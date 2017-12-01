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
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>關於.NET microservices 及 web 應用程式中的授權

在驗證之後，ASP.NET Core Web Api 需要授權存取。 這個程序在可驗證的使用者，但不是為所有允許的服務，讓應用程式開發介面。 [授權](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)可以根據使用者的角色來完成，或可能包含宣告或其他啟發學習法所檢查的自訂原則為基礎。

限制對 ASP.NET Core MVC 路由的存取是簡單，只要將套用 Authorize 屬性至動作方法 （或如果在控制器的所有動作都需要授權的控制站的類別），下列範例中所示：

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

根據預設，加入不含參數的授權屬性會限制該控制器或動作的存取權已驗證的使用者。 若要進一步限制只有特定使用者的可用應用程式開發介面，可以擴充屬性，來指定必要的角色或使用者必須滿足的原則。

## <a name="implementing-role-based-authorization"></a>實作以角色為基礎的授權

ASP.NET Core 識別具有內建角色的概念。 除了使用者，ASP.NET Core 識別儲存應用程式所使用的不同角色的相關資訊並追蹤哪些使用者已指派給哪些角色。 以 RoleManager 型別 （更新持續性儲存體中的角色） 和 UserManager 型別 （可指派，或取消指派使用者角色） 來以程式設計方式變更這些指派。

如果您要進行驗證的 JWT bearer 權杖，ASP.NET Core JWT 承載驗證中介軟體將會填入使用者的角色根據權杖中找到的角色宣告。 若要限制存取的 MVC 動作或控制器中特定角色的使用者，您可以授權標頭中包含的角色參數，如下列範例所示：

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

在此範例中，只有系統管理員或 PowerUser 角色中的使用者可以在 [控制台] 的控制器 （例如執行 SetTime 動作） 中存取應用程式開發介面。 關閉應用程式開發介面進一步限制為只允許存取使用者的系統管理員角色中。

若要要求使用者是多個角色中，您會使用多個授權屬性，如下列範例所示：

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

在此範例中，若要呼叫 API1，使用者必須：

-   系統管理員在*或*PowerUser 角色*和*

-   RemoteEmployee 角色時，會*和*

-   滿足 CustomPolicy 授權的自訂處理常式。

## <a name="implementing-policy-based-authorization"></a>實作以原則為基礎的授權

自訂授權規則也可以寫入使用[授權原則](https://docs.asp.net/en/latest/security/authorization/policies.html)。 本節中，我們會提供概觀。 更多詳細資料位於線上[ASP.NET 授權 Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop)。

Startup.ConfigureServices 方法使用服務中註冊自訂授權原則。AddAuthorization 方法。 這個方法會採用設定 AuthorizationOptions 引數的委派。

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

此範例所示，原則可以是不同類型的需求與相關聯。 註冊原則之後，它們可以套用到某個動作或控制器的傳遞原則屬性的引數授權原則的名稱 (例如， \[Authorize(Policy="EmployeesOnly")\]) 可以有原則多個需求，不是只有一個 （如這些範例中所示）。

在上述範例中，第一次 AddPolicy 呼叫是只根據角色來授權的替代方式。 如果\[Authorize(Policy="AdministratorsOnly")\]套用至應用程式開發介面，只有系統管理員角色中的使用者，才能夠存取它。

第二個 AddPolicy 呼叫示範需要特定的宣告，應該會顯示使用者的簡單方法。 RequireClaim 方法也會使用宣告的預期值。 如果指定的值，只有當使用者具有都正確的型別宣告，以及其中一個指定的值，是為了滿足此需求。 如果您使用 JWT 承載驗證中介軟體，所有的 JWT 屬性可做為使用者宣告。

最有趣如下所示的原則是在第三個 AddPolicy 方法中，因為它會使用自訂的授權需求。 藉由使用自訂的授權需求，您可以有更多的控制如何執行授權。 針對此目的，您必須實作這些型別：

-   需求類型衍生自 IAuthorizationRequirement 並包含指定之需求的詳細資料的欄位。 在範例中，這是範例 MinimumAgeRequirement 類型的一個時間欄位。

-   處理常式實作 AuthorizationHandler&lt;T&gt;，其中 T 是 IAuthorizationRequirement，可滿足此處理常式的類型。 此處理常式必須實作 HandleRequirementAsync 方法，這個方法會檢查指定的內容，其中包含使用者的資訊是否滿足需求。

如果使用者符合需求，也就是內容的呼叫。將會成功，表示使用者已授權。 如果有多個使用者可能符合授權需求的方式，就可以建立多個處理常式。

除了向 AddPolicy 呼叫的自訂原則的需求，您也需要註冊自訂需求的處理常式透過相依性插入 （服務。AddTransient&lt;IAuthorizationHandler、 MinimumAgeHandler&gt;（)）。

自訂授權需求和檢查 （根據 DateOfBirth 宣告） 的使用者的年齡的處理常式的範例可用於 ASP.NET Core[授權文件](https://docs.asp.net/en/latest/security/authorization/policies.html)。

## <a name="additional-resources"></a>其他資源

-   **ASP.NET Core 驗證**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **ASP.NET Core 授權**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **角色型授權**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **以原則為基礎的自訂授權**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[上一個](index.md) [下一步] (開發人員為應用程式-機密-storage.md)
