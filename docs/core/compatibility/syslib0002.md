---
title: SYSLIB0002 錯誤
description: 瞭解產生編譯時期錯誤 SYSLIB0002 的 obsoletion。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 36ecde3c52845a6594c4d04e167df48142038654
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437509"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a><span data-ttu-id="6d441-103">SYSLIB0002： PrincipalPermissionAttribute 已淘汰</span><span class="sxs-lookup"><span data-stu-id="6d441-103">SYSLIB0002: PrincipalPermissionAttribute is obsolete</span></span>

<span data-ttu-id="6d441-104"><xref:System.Security.Permissions.PrincipalPermissionAttribute> `SYSLIB0002` 從 .net 5.0 開始，此函式已淘汰並產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d441-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces compile-time error `SYSLIB0002`, starting in .NET 5.0.</span></span> <span data-ttu-id="6d441-105">您無法具現化此屬性，或將它套用至方法。</span><span class="sxs-lookup"><span data-stu-id="6d441-105">You cannot instantiate this attribute or apply it to a method.</span></span>

<span data-ttu-id="6d441-106">與其他 obsoletion 警告不同的是，您無法隱藏錯誤。</span><span class="sxs-lookup"><span data-stu-id="6d441-106">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="6d441-107">因應措施</span><span class="sxs-lookup"><span data-stu-id="6d441-107">Workarounds</span></span>

- <span data-ttu-id="6d441-108">如果您要將屬性套用至 ASP.NET MVC 動作方法：</span><span class="sxs-lookup"><span data-stu-id="6d441-108">If you're applying the attribute to an ASP.NET MVC action method:</span></span>

  <span data-ttu-id="6d441-109">請考慮使用 ASP。NET 的內建授權基礎結構。</span><span class="sxs-lookup"><span data-stu-id="6d441-109">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="6d441-110">下列程式碼示範如何使用屬性來標注控制器 <xref:System.Web.Mvc.AuthorizeAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="6d441-110">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="6d441-111">ASP.NET 執行時間會在執行動作之前授權使用者。</span><span class="sxs-lookup"><span data-stu-id="6d441-111">The ASP.NET runtime will authorize the user before performing the action.</span></span>

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

  <span data-ttu-id="6d441-112">如需詳細資訊，請參閱 [ASP.NET Core 中以角色為基礎的授權](/aspnet/core/security/authorization/roles) ，以及 [ASP.NET Core 中的授權簡介](/aspnet/core/security/authorization/introduction)。</span><span class="sxs-lookup"><span data-stu-id="6d441-112">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="6d441-113">如果您要將屬性套用至 web 應用程式內容之外的程式庫程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d441-113">If you're applying the attribute to library code outside the context of a web app:</span></span>

  <span data-ttu-id="6d441-114">藉由呼叫方法，在方法的開頭手動執行檢查 <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6d441-114">Perform the checks manually at the beginning of your method by calling the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

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

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="6d441-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d441-115">See also</span></span>

- [<span data-ttu-id="6d441-116">PrincipalPermissionAttribute 已淘汰為錯誤</span><span class="sxs-lookup"><span data-stu-id="6d441-116">PrincipalPermissionAttribute is obsolete as error</span></span>](core-libraries/5.0/principalpermissionattribute-obsolete.md)
