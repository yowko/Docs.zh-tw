---
title: 重大變更：中介軟體：資料庫錯誤頁面標示為已淘汰
description: 瞭解 ASP.NET Core 5.0 中的重大變更，標題為中介軟體：資料庫錯誤頁面標示為已淘汰
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f828b5e20c2a9a709d675e435caa99727aebd5b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760743"
---
# <a name="middleware-database-error-page-marked-as-obsolete"></a>中介軟體：資料庫錯誤頁面標示為已淘汰

[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)及其相關聯的擴充方法在 ASP.NET Core 5.0 中標示為過時。 中介軟體和擴充方法將會在 ASP.NET Core 6.0 中移除。 這項功能將改由 `DatabaseDeveloperPageExceptionFilter` 和其擴充方法提供。

如需相關討論，請參閱 GitHub 問題，網址為 [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987)。

## <a name="version-introduced"></a>引進的版本

5.0 RC 1

## <a name="old-behavior"></a>舊的行為

`DatabaseErrorPageMiddleware` 與其相關聯的擴充方法尚未淘汰。

## <a name="new-behavior"></a>新的行為

`DatabaseErrorPageMiddleware` 與其相關聯的擴充方法已過時。

## <a name="reason-for-change"></a>變更的原因

`DatabaseErrorPageMiddleware` 已遷移至 [開發人員例外狀況頁面](/aspnet/core/fundamentals/error-handling#developer-exception-page)的可延伸 API。 如需可延伸 API 的詳細資訊，請參閱 GitHub issue [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536)。

## <a name="recommended-action"></a>建議的動作

完成以下步驟：

1. 停止 `DatabaseErrorPageMiddleware` 在您的專案中使用。 例如， `UseDatabaseErrorPage` 從移除方法呼叫 `Startup.Configure` ：

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. 將開發人員例外狀況頁面新增至您的專案。 例如， <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> 在中呼叫方法 `Startup.Configure` ：

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. 將 [AspNetCore Microsoft.entityframeworkcore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet 套件新增至專案檔。

1. 將資料庫開發人員頁面例外狀況篩選加入至服務集合。 例如， `AddDatabaseDeveloperPageExceptionFilter` 在中呼叫方法 `Startup.ConfigureServices` ：

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a>受影響的 API

- [AspNetCore. DatabaseErrorPageExtensions. UseDatabaseErrorPage](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [AspNetCore. Microsoft.entityframeworkcore. DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
