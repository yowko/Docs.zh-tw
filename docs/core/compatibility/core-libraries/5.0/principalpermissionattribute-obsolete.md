---
title: 重大變更： PrincipalPermissionAttribute 已淘汰為錯誤
description: 瞭解核心 .NET 程式庫中 PrincipalPermissionAttribute 的函式已淘汰並產生編譯時期錯誤的 .NET 5.0 重大變更。
ms.date: 11/01/2020
ms.openlocfilehash: 138bbf25fd493c1bb9c2b3f10b62681c735ea7b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760689"
---
# <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="abb4b-103">PrincipalPermissionAttribute 已淘汰為錯誤</span><span class="sxs-lookup"><span data-stu-id="abb4b-103">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="abb4b-104">此函 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 式已過時，並產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="abb4b-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="abb4b-105">您無法具現化此屬性，或將它套用至方法。</span><span class="sxs-lookup"><span data-stu-id="abb4b-105">You cannot instantiate this attribute or apply it to a method.</span></span>

## <a name="change-description"></a><span data-ttu-id="abb4b-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="abb4b-106">Change description</span></span>

<span data-ttu-id="abb4b-107">在 .NET Framework 和 .NET Core 上，您可以使用屬性來標注方法 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="abb4b-107">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="abb4b-108">例如：</span><span class="sxs-lookup"><span data-stu-id="abb4b-108">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="abb4b-109">從 .NET 5.0 開始，您無法將 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性套用至方法。</span><span class="sxs-lookup"><span data-stu-id="abb4b-109">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="abb4b-110">屬性的函式已過時，而且會產生編譯階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="abb4b-110">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="abb4b-111">與其他 obsoletion 警告不同的是，您無法隱藏錯誤。</span><span class="sxs-lookup"><span data-stu-id="abb4b-111">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="abb4b-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="abb4b-112">Reason for change</span></span>

<span data-ttu-id="abb4b-113"><xref:System.Security.Permissions.PrincipalPermissionAttribute>類型（如同子類別的其他類型 <xref:System.Security.Permissions.SecurityAttribute> ）屬於的一部分。NET 的代碼啟用安全性 (CAS) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="abb4b-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="abb4b-114">在 .NET Framework 2.x-4.x 中，運行 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 時間會強制執行方法專案上的批註，即使應用程式是在完全信任的情況下執行也一樣。</span><span class="sxs-lookup"><span data-stu-id="abb4b-114">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="abb4b-115">.NET Core 和 .NET 5.0 和更新版本不支援 CAS 屬性，而執行時間會忽略它們。</span><span class="sxs-lookup"><span data-stu-id="abb4b-115">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="abb4b-116">從 .NET Framework 到 .NET Core 和 .NET 5.0 的行為差異，可能會導致「開啟失敗」案例，其中應該會封鎖存取但改為允許。</span><span class="sxs-lookup"><span data-stu-id="abb4b-116">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="abb4b-117">若要防止「開啟失敗」案例，您無法再于以 .NET 5.0 或更新版本為目標的程式碼中套用屬性。</span><span class="sxs-lookup"><span data-stu-id="abb4b-117">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="abb4b-118">引進的版本</span><span class="sxs-lookup"><span data-stu-id="abb4b-118">Version introduced</span></span>

<span data-ttu-id="abb4b-119">5.0</span><span class="sxs-lookup"><span data-stu-id="abb4b-119">5.0</span></span>

## <a name=""></a><span data-ttu-id="abb4b-120"><a id="permission-action">建議的動作</a></span><span class="sxs-lookup"><span data-stu-id="abb4b-120"><a id="permission-action">Recommended action</a></span></span>

<span data-ttu-id="abb4b-121">如果您遇到 obsoletion 錯誤，您必須採取動作。</span><span class="sxs-lookup"><span data-stu-id="abb4b-121">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="abb4b-122">**如果您要將屬性套用至 ASP.NET MVC 動作方法：**</span><span class="sxs-lookup"><span data-stu-id="abb4b-122">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="abb4b-123">請考慮使用 ASP。NET 的內建授權基礎結構。</span><span class="sxs-lookup"><span data-stu-id="abb4b-123">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="abb4b-124">下列程式碼示範如何使用屬性來標注控制器 <xref:System.Web.Mvc.AuthorizeAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="abb4b-124">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="abb4b-125">ASP.NET 執行時間會在執行動作之前授權使用者。</span><span class="sxs-lookup"><span data-stu-id="abb4b-125">The ASP.NET runtime will authorize the user before performing the action.</span></span>

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

  <span data-ttu-id="abb4b-126">如需詳細資訊，請參閱 [ASP.NET Core 中以角色為基礎的授權](/aspnet/core/security/authorization/roles) ，以及 [ASP.NET Core 中的授權簡介](/aspnet/core/security/authorization/introduction)。</span><span class="sxs-lookup"><span data-stu-id="abb4b-126">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="abb4b-127">**如果您要將屬性套用至 web 應用程式內容之外的程式庫程式碼：**</span><span class="sxs-lookup"><span data-stu-id="abb4b-127">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="abb4b-128">在方法的開頭手動執行檢查。</span><span class="sxs-lookup"><span data-stu-id="abb4b-128">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="abb4b-129">這可以藉由使用方法來完成 <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="abb4b-129">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="abb4b-130">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="abb4b-130">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
