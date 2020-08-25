---
ms.openlocfilehash: f1129500c9b779256b2650fe6fa855152cb3ae80
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811253"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="ba9c5-101">中介軟體：資料庫錯誤頁面標示為已淘汰</span><span class="sxs-lookup"><span data-stu-id="ba9c5-101">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="ba9c5-102">[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)及其相關聯的擴充方法在 ASP.NET Core 5.0 中標示為過時。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-102">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="ba9c5-103">中介軟體和擴充方法將會在 ASP.NET Core 6.0 中移除。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-103">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="ba9c5-104">這項功能將改由 `DatabaseDeveloperPageExceptionFilter` 和其擴充方法提供。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-104">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="ba9c5-105">如需相關討論，請參閱 GitHub 問題，網址為 [dotnet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987)。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-105">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ba9c5-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ba9c5-106">Version introduced</span></span>

<span data-ttu-id="ba9c5-107">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="ba9c5-107">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ba9c5-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="ba9c5-108">Old behavior</span></span>

<span data-ttu-id="ba9c5-109">`DatabaseErrorPageMiddleware` 與其相關聯的擴充方法尚未淘汰。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-109">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ba9c5-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="ba9c5-110">New behavior</span></span>

<span data-ttu-id="ba9c5-111">`DatabaseErrorPageMiddleware` 與其相關聯的擴充方法已過時。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-111">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ba9c5-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ba9c5-112">Reason for change</span></span>

<span data-ttu-id="ba9c5-113">`DatabaseErrorPageMiddleware` 已遷移至 [開發人員例外狀況頁面](/aspnet/core/fundamentals/error-handling#developer-exception-page)的可延伸 API。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-113">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="ba9c5-114">如需可延伸 API 的詳細資訊，請參閱 GitHub issue [dotnet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536)。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-114">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ba9c5-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ba9c5-115">Recommended action</span></span>

<span data-ttu-id="ba9c5-116">完成以下步驟：</span><span class="sxs-lookup"><span data-stu-id="ba9c5-116">Complete the following steps:</span></span>

1. <span data-ttu-id="ba9c5-117">停止 `DatabaseErrorPageMiddleware` 在您的專案中使用。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-117">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="ba9c5-118">例如， `UseDatabaseErrorPage` 從移除方法呼叫 `Startup.Configure` ：</span><span class="sxs-lookup"><span data-stu-id="ba9c5-118">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="ba9c5-119">將開發人員例外狀況頁面新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-119">Add the developer exception page to your project.</span></span> <span data-ttu-id="ba9c5-120">例如， <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> 在中呼叫方法 `Startup.Configure` ：</span><span class="sxs-lookup"><span data-stu-id="ba9c5-120">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="ba9c5-121">將資料庫開發人員頁面例外狀況篩選加入至服務集合。</span><span class="sxs-lookup"><span data-stu-id="ba9c5-121">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="ba9c5-122">例如， `AddDatabaseDeveloperPageExceptionFilter` 在中呼叫方法 `Startup.ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="ba9c5-122">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a><span data-ttu-id="ba9c5-123">類別</span><span class="sxs-lookup"><span data-stu-id="ba9c5-123">Category</span></span>

<span data-ttu-id="ba9c5-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba9c5-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ba9c5-125">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ba9c5-125">Affected APIs</span></span>

- [<span data-ttu-id="ba9c5-126">AspNetCore. DatabaseErrorPageExtensions. UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="ba9c5-126">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="ba9c5-127">AspNetCore. Microsoft.entityframeworkcore. DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="ba9c5-127">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
