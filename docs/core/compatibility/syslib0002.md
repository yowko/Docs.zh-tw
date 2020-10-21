---
title: SYSLIB0002 錯誤
description: 瞭解產生編譯時期錯誤 SYSLIB0002 的 obsoletion。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 00fd42975c9286221b75c87caef8d2109b9b7100
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333250"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a>SYSLIB0002： PrincipalPermissionAttribute 已淘汰

<xref:System.Security.Permissions.PrincipalPermissionAttribute> `SYSLIB0002` 從 .net 5.0 開始，此函式已淘汰並產生編譯時期錯誤。 您無法具現化此屬性，或將它套用至方法。

與其他 obsoletion 警告不同的是，您無法隱藏錯誤。

## <a name="workarounds"></a>因應措施

- 如果您要將屬性套用至 ASP.NET MVC 動作方法：

  請考慮使用 ASP。NET 的內建授權基礎結構。 下列程式碼示範如何使用屬性來標注控制器 <xref:System.Web.Mvc.AuthorizeAttribute> 。 ASP.NET 執行時間會在執行動作之前授權使用者。

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

  如需詳細資訊，請參閱 [ASP.NET Core 中以角色為基礎的授權](/aspnet/core/security/authorization/roles) ，以及 [ASP.NET Core 中的授權簡介](/aspnet/core/security/authorization/introduction)。

- 如果您要將屬性套用至 web 應用程式內容之外的程式庫程式碼：

  藉由呼叫方法，在方法的開頭手動執行檢查 <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> 。

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

## <a name="see-also"></a>請參閱

- [PrincipalPermissionAttribute 已淘汰為錯誤](3.1-5.0.md#principalpermissionattribute-is-obsolete-as-error)
