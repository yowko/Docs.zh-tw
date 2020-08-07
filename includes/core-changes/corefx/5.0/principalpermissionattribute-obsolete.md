---
ms.openlocfilehash: 2c8a5c1ec87918a91600a3557c679a42cae74896
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556321"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="fa323-101">PrincipalPermissionAttribute 已淘汰為錯誤</span><span class="sxs-lookup"><span data-stu-id="fa323-101">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="fa323-102">此函式 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 已過時，並會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="fa323-102">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="fa323-103">您無法具現化此屬性，或將它套用至方法。</span><span class="sxs-lookup"><span data-stu-id="fa323-103">You cannot instantiate this attribute or apply it to a method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fa323-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="fa323-104">Change description</span></span>

<span data-ttu-id="fa323-105">在 .NET Framework 和 .NET Core 上，您可以使用屬性來標注方法 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="fa323-105">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="fa323-106">例如：</span><span class="sxs-lookup"><span data-stu-id="fa323-106">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="fa323-107">從 .NET 5.0 開始，您無法將 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性套用至方法。</span><span class="sxs-lookup"><span data-stu-id="fa323-107">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="fa323-108">屬性的構造函式已過時，並產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="fa323-108">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="fa323-109">不同于其他 obsoletion 警告，您無法隱藏此錯誤。</span><span class="sxs-lookup"><span data-stu-id="fa323-109">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fa323-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="fa323-110">Reason for change</span></span>

<span data-ttu-id="fa323-111">類型與子 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 類別的其他類型一樣， <xref:System.Security.Permissions.SecurityAttribute> 是的一部分。NET 的代碼啟用安全性 (CAS) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="fa323-111">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="fa323-112">在 .NET Framework 2.x-4.x 中， <xref:System.Security.Permissions.PrincipalPermissionAttribute> 即使應用程式是在完全信任的情況下執行，執行時間還是會在方法專案上強制執行注釋。</span><span class="sxs-lookup"><span data-stu-id="fa323-112">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="fa323-113">.NET Core 和 .NET 5.0 和更新版本不支援 CAS 屬性，而執行時間會忽略它們。</span><span class="sxs-lookup"><span data-stu-id="fa323-113">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="fa323-114">從 .NET Framework 到 .NET Core 和 .NET 5.0 的行為差異，可能會導致「失敗開啟」案例，其中的存取權應該已被封鎖，但改為允許。</span><span class="sxs-lookup"><span data-stu-id="fa323-114">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="fa323-115">若要避免「失敗開啟」案例，您無法再于以 .NET 5.0 或更新版本為目標的程式碼中套用屬性。</span><span class="sxs-lookup"><span data-stu-id="fa323-115">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fa323-116">引進的版本</span><span class="sxs-lookup"><span data-stu-id="fa323-116">Version introduced</span></span>

<span data-ttu-id="fa323-117">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="fa323-117">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fa323-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="fa323-118">Recommended action</span></span>

<span data-ttu-id="fa323-119">如果您遇到 obsoletion 錯誤，則必須採取動作。</span><span class="sxs-lookup"><span data-stu-id="fa323-119">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="fa323-120">**如果您要將屬性套用至 ASP.NET MVC 動作方法：**</span><span class="sxs-lookup"><span data-stu-id="fa323-120">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="fa323-121">請考慮使用 ASP。NET 的內建授權基礎結構。</span><span class="sxs-lookup"><span data-stu-id="fa323-121">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="fa323-122">下列程式碼示範如何使用屬性標注控制器 <xref:System.Web.Mvc.AuthorizeAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="fa323-122">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="fa323-123">ASP.NET 執行時間會先授權使用者，然後再執行此動作。</span><span class="sxs-lookup"><span data-stu-id="fa323-123">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="fa323-124">如需詳細資訊，請參閱[ASP.NET Core 中以角色為基礎的授權](/aspnet/core/security/authorization/roles)和[ASP.NET Core 中的授權簡介](/aspnet/core/security/authorization/introduction)。</span><span class="sxs-lookup"><span data-stu-id="fa323-124">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="fa323-125">**如果您要將屬性套用至 web 應用程式內容外部的程式庫程式碼：**</span><span class="sxs-lookup"><span data-stu-id="fa323-125">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="fa323-126">在方法的開頭手動執行檢查。</span><span class="sxs-lookup"><span data-stu-id="fa323-126">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="fa323-127">這可以藉由使用方法來完成 <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="fa323-127">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

#### <a name="category"></a><span data-ttu-id="fa323-128">類別</span><span class="sxs-lookup"><span data-stu-id="fa323-128">Category</span></span>

- <span data-ttu-id="fa323-129">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="fa323-129">Core .NET libraries</span></span>
- <span data-ttu-id="fa323-130">安全性</span><span class="sxs-lookup"><span data-stu-id="fa323-130">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fa323-131">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fa323-131">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->