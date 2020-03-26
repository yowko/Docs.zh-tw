---
title: 從ASP.NET Web 表單遷移到布拉佐爾
description: 瞭解如何處理將現有ASP.NET Web 表單應用遷移到 Blazor 的方法。
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134083"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="c5d47-103">從ASP.NET Web 表單遷移到布拉佐爾</span><span class="sxs-lookup"><span data-stu-id="c5d47-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="c5d47-104">將代碼庫從ASP.NET Web 表單遷移到 Blazor 是一項耗時的任務，需要規劃。</span><span class="sxs-lookup"><span data-stu-id="c5d47-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="c5d47-105">本章概述了該過程。</span><span class="sxs-lookup"><span data-stu-id="c5d47-105">This chapter outlines the process.</span></span> <span data-ttu-id="c5d47-106">可以簡化轉換的是確保應用遵循*N 層*體系結構，其中應用模型（在本例中為 Web 表單）與業務邏輯分開。</span><span class="sxs-lookup"><span data-stu-id="c5d47-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="c5d47-107">這種層的邏輯分離可以清楚地說明需要遷移到 .NET Core 和 Blazor 的內容。</span><span class="sxs-lookup"><span data-stu-id="c5d47-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="c5d47-108">在此示例中，使用[GitHub](https://github.com/dotnet-architecture/eShopOnBlazor)上可用的 eShop 應用。</span><span class="sxs-lookup"><span data-stu-id="c5d47-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="c5d47-109">eShop 是一種目錄服務，通過表單輸入和驗證提供 CRUD 功能。</span><span class="sxs-lookup"><span data-stu-id="c5d47-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="c5d47-110">為什麼工作應用應遷移到 Blazor？</span><span class="sxs-lookup"><span data-stu-id="c5d47-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="c5d47-111">很多時候，沒有必要。</span><span class="sxs-lookup"><span data-stu-id="c5d47-111">Many times, there's no need.</span></span> <span data-ttu-id="c5d47-112">ASP.NET Web 表單將繼續支援多年。</span><span class="sxs-lookup"><span data-stu-id="c5d47-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="c5d47-113">但是，Blazor 提供的許多功能僅在遷移的應用上受支援。</span><span class="sxs-lookup"><span data-stu-id="c5d47-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="c5d47-114">這些功能包括：</span><span class="sxs-lookup"><span data-stu-id="c5d47-114">Such features include:</span></span>

- <span data-ttu-id="c5d47-115">框架中的性能改進，例如`Span<T>`</span><span class="sxs-lookup"><span data-stu-id="c5d47-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="c5d47-116">能夠以 Web 程式集身份運行</span><span class="sxs-lookup"><span data-stu-id="c5d47-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="c5d47-117">對 Linux 和 macOS 的跨平臺支援</span><span class="sxs-lookup"><span data-stu-id="c5d47-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="c5d47-118">應用本地部署或共用框架部署，不影響其他應用</span><span class="sxs-lookup"><span data-stu-id="c5d47-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="c5d47-119">如果這些或其他新功能足夠吸引人，則遷移應用可能具有價值。</span><span class="sxs-lookup"><span data-stu-id="c5d47-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="c5d47-120">遷移可以採用不同的形狀;它可以是整個應用，也可以只是需要更改的某些終結點。</span><span class="sxs-lookup"><span data-stu-id="c5d47-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="c5d47-121">遷移的決定最終基於開發人員要解決的業務問題。</span><span class="sxs-lookup"><span data-stu-id="c5d47-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="c5d47-122">伺服器端與用戶端託管</span><span class="sxs-lookup"><span data-stu-id="c5d47-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="c5d47-123">如[託管模型](hosting-models.md)章節所述，Blazor 應用可以通過兩種不同的方式託管：伺服器端和用戶端。</span><span class="sxs-lookup"><span data-stu-id="c5d47-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="c5d47-124">伺服器端模型使用ASP.NET核心信號R連接來管理 DOM 更新，同時在伺服器上運行任何實際代碼。</span><span class="sxs-lookup"><span data-stu-id="c5d47-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="c5d47-125">用戶端模型在瀏覽器中作為 WebAssembly 運行，不需要伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="c5d47-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="c5d47-126">有許多差異可能會影響特定應用：</span><span class="sxs-lookup"><span data-stu-id="c5d47-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="c5d47-127">以 WebAssembly 身份運行仍處於開發階段，當前可能不支援所有功能（如執行緒）</span><span class="sxs-lookup"><span data-stu-id="c5d47-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="c5d47-128">用戶端和伺服器之間的聊天通信可能會導致伺服器端模式下的延遲問題</span><span class="sxs-lookup"><span data-stu-id="c5d47-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="c5d47-129">訪問資料庫和內部或受保護服務需要使用用戶端託管提供單獨的服務</span><span class="sxs-lookup"><span data-stu-id="c5d47-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="c5d47-130">在編寫本文時，伺服器端模型更像 Web 表單。</span><span class="sxs-lookup"><span data-stu-id="c5d47-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="c5d47-131">本章的大部分重點介紹伺服器端託管模型，因為它已做好生產準備。</span><span class="sxs-lookup"><span data-stu-id="c5d47-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="c5d47-132">建立新專案</span><span class="sxs-lookup"><span data-stu-id="c5d47-132">Create a new project</span></span>

<span data-ttu-id="c5d47-133">此初始遷移步驟是創建新專案。</span><span class="sxs-lookup"><span data-stu-id="c5d47-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="c5d47-134">此專案類型基於 .NET Core 的 SDK 樣式專案，並簡化了以前專案格式中使用的許多樣板。</span><span class="sxs-lookup"><span data-stu-id="c5d47-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="c5d47-135">有關詳細資訊，請參閱有關[專案結構](project-structure.md)的章節。</span><span class="sxs-lookup"><span data-stu-id="c5d47-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="c5d47-136">創建專案後，安裝上一個專案中使用的庫。</span><span class="sxs-lookup"><span data-stu-id="c5d47-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="c5d47-137">在較舊的 Web 表單專案中，您可能已使用*包.config*檔列出所需的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="c5d47-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="c5d47-138">在新的 SDK 樣式專案中，*包.config*已替換為`<PackageReference>`專案檔案中的元素。</span><span class="sxs-lookup"><span data-stu-id="c5d47-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="c5d47-139">此方法的一個好處是，所有依賴項都是以過渡方式安裝的。</span><span class="sxs-lookup"><span data-stu-id="c5d47-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="c5d47-140">您只列出您關心的頂級依賴項。</span><span class="sxs-lookup"><span data-stu-id="c5d47-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="c5d47-141">您正在使用的許多依賴項可用於 .NET Core，包括實體框架 6 和 log4net。</span><span class="sxs-lookup"><span data-stu-id="c5d47-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="c5d47-142">如果沒有可用的 .NET Core 或 .NET 標準版本，則經常使用 .NET 框架版本。</span><span class="sxs-lookup"><span data-stu-id="c5d47-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="c5d47-143">您的里程可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="c5d47-143">Your mileage may vary.</span></span> <span data-ttu-id="c5d47-144">.NET Core 中不可用的任何 API 都會導致執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="c5d47-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="c5d47-145">Visual Studio 會通知您此類套餐。</span><span class="sxs-lookup"><span data-stu-id="c5d47-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="c5d47-146">在**解決方案資源管理器**中的專案的**參考節點**上會出現一個黃色圖示。</span><span class="sxs-lookup"><span data-stu-id="c5d47-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="c5d47-147">在基於 Blazor 的 eShop 專案中，您可以看到已安裝的套裝軟體。</span><span class="sxs-lookup"><span data-stu-id="c5d47-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="c5d47-148">以前 *，package.config*檔列出了專案中使用的每個包，導致檔近 50 行長。</span><span class="sxs-lookup"><span data-stu-id="c5d47-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="c5d47-149">*包段. 配置*是：</span><span class="sxs-lookup"><span data-stu-id="c5d47-149">A snippet of *packages.config* is:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

<span data-ttu-id="c5d47-150">該`<packages>`元素包括所有必要的依賴項。</span><span class="sxs-lookup"><span data-stu-id="c5d47-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="c5d47-151">很難確定其中哪些包包含，因為您需要它們。</span><span class="sxs-lookup"><span data-stu-id="c5d47-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="c5d47-152">某些`<package>`元素的列出只是為了滿足您需要的依賴項的需求。</span><span class="sxs-lookup"><span data-stu-id="c5d47-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="c5d47-153">Blazor 專案列出了專案檔案中`<ItemGroup>`的元素中所需的依賴項：</span><span class="sxs-lookup"><span data-stu-id="c5d47-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="c5d47-154">一個NuGet包，簡化了Web表單開發人員的生活是[Windows相容性包](../../core/porting/windows-compat-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="c5d47-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="c5d47-155">儘管 .NET Core 是跨平臺的，但某些功能僅在 Windows 上可用。</span><span class="sxs-lookup"><span data-stu-id="c5d47-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="c5d47-156">通過安裝相容性包，可以獲得特定于 Windows 的功能。</span><span class="sxs-lookup"><span data-stu-id="c5d47-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="c5d47-157">此類功能的示例包括註冊表、WMI 和目錄服務。</span><span class="sxs-lookup"><span data-stu-id="c5d47-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="c5d47-158">該套裝軟體添加了大約 20，000 個 API，並啟動了許多您可能已經熟悉的服務。</span><span class="sxs-lookup"><span data-stu-id="c5d47-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="c5d47-159">eShop 專案不需要相容性包;因此，eShop 專案不需要相容性包。但是，如果專案使用特定于 Windows 的功能，則該包可簡化遷移工作。</span><span class="sxs-lookup"><span data-stu-id="c5d47-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="c5d47-160">啟用啟動過程</span><span class="sxs-lookup"><span data-stu-id="c5d47-160">Enable startup process</span></span>

<span data-ttu-id="c5d47-161">Blazor 的啟動過程從 Web 表單更改，並遵循其他ASP.NET核心服務的類似設置。</span><span class="sxs-lookup"><span data-stu-id="c5d47-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="c5d47-162">當託管伺服器端時，Blazor 元件作為正常ASP.NET核心應用的一部分運行。</span><span class="sxs-lookup"><span data-stu-id="c5d47-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="c5d47-163">當使用 WebAssembly 在瀏覽器中託管時，Blazor 元件使用類似的託管模型。</span><span class="sxs-lookup"><span data-stu-id="c5d47-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="c5d47-164">區別在於元件作為獨立于任何後端進程的服務運行。</span><span class="sxs-lookup"><span data-stu-id="c5d47-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="c5d47-165">無論哪種方式，啟動都是類似的。</span><span class="sxs-lookup"><span data-stu-id="c5d47-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="c5d47-166">*Global.asax.cs*檔是 Web 表單專案的預設啟動頁。</span><span class="sxs-lookup"><span data-stu-id="c5d47-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="c5d47-167">在 eShop 專案中，此檔配置"控制反轉 （IoC）"容器，並處理應用或請求的各種生命週期事件。</span><span class="sxs-lookup"><span data-stu-id="c5d47-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="c5d47-168">其中一些事件使用中介軟體（如`Application_BeginRequest`）處理。</span><span class="sxs-lookup"><span data-stu-id="c5d47-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="c5d47-169">其他事件需要通過依賴項注入 （DI） 重寫特定服務。</span><span class="sxs-lookup"><span data-stu-id="c5d47-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="c5d47-170">例如，eShop *Global.asax.cs*檔包含以下代碼：</span><span class="sxs-lookup"><span data-stu-id="c5d47-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// http://docs.autofac.org/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

<span data-ttu-id="c5d47-171">前面的檔將成為伺服器端`Startup`Blazor 中的類：</span><span class="sxs-lookup"><span data-stu-id="c5d47-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

<span data-ttu-id="c5d47-172">您可能會從 Web 表單中注意到的一個重要變化是 DI 的突出性。</span><span class="sxs-lookup"><span data-stu-id="c5d47-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="c5d47-173">DI 一直是 ASP.NET核心設計的指導原則。</span><span class="sxs-lookup"><span data-stu-id="c5d47-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="c5d47-174">它支援自訂ASP.NET核心框架的幾乎所有方面。</span><span class="sxs-lookup"><span data-stu-id="c5d47-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="c5d47-175">甚至還有一個內置的服務提供者，可用於許多方案。</span><span class="sxs-lookup"><span data-stu-id="c5d47-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="c5d47-176">如果需要更多自訂，許多社區專案可以支援它。</span><span class="sxs-lookup"><span data-stu-id="c5d47-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="c5d47-177">例如，您可以進行協力廠商 DI 庫投資。</span><span class="sxs-lookup"><span data-stu-id="c5d47-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="c5d47-178">在原始的 eShop 應用中，有一些用於會話管理的配置。</span><span class="sxs-lookup"><span data-stu-id="c5d47-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="c5d47-179">由於伺服器端 Blazor 使用ASP.NET核心信號R進行通信，因此不支援會話狀態，因為連接可能獨立于 HTTP 上下文進行。</span><span class="sxs-lookup"><span data-stu-id="c5d47-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="c5d47-180">使用會話狀態的應用需要在作為 Blazor 應用運行之前重新構建。</span><span class="sxs-lookup"><span data-stu-id="c5d47-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="c5d47-181">有關應用啟動的詳細資訊，請參閱[應用啟動](app-startup.md)。</span><span class="sxs-lookup"><span data-stu-id="c5d47-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="c5d47-182">將 HTTP 模組和處理常式遷移到中介軟體</span><span class="sxs-lookup"><span data-stu-id="c5d47-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="c5d47-183">HTTP 模組和處理常式是 Web 表單中用於控制 HTTP 要求管道的常見模式。</span><span class="sxs-lookup"><span data-stu-id="c5d47-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="c5d47-184">實現`IHttpModule`或`IHttpHandler`可以註冊和處理傳入請求的類。</span><span class="sxs-lookup"><span data-stu-id="c5d47-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="c5d47-185">Web 表單在*Web.config 檔中*配置模組和處理常式。</span><span class="sxs-lookup"><span data-stu-id="c5d47-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="c5d47-186">Web 表單還在很大程度上基於應用生命週期事件處理。</span><span class="sxs-lookup"><span data-stu-id="c5d47-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="c5d47-187">ASP.NET核心使用中介軟體代替。</span><span class="sxs-lookup"><span data-stu-id="c5d47-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="c5d47-188">中介軟體在`Configure``Startup`類的方法中註冊。</span><span class="sxs-lookup"><span data-stu-id="c5d47-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="c5d47-189">中介軟體執行順序由註冊訂單確定。</span><span class="sxs-lookup"><span data-stu-id="c5d47-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="c5d47-190">在[啟用啟動過程](#enable-startup-process)部分中，Web 表單提出了生命週期事件作為`Application_BeginRequest`方法。</span><span class="sxs-lookup"><span data-stu-id="c5d47-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="c5d47-191">此事件在 ASP.NET 酷中不可用。</span><span class="sxs-lookup"><span data-stu-id="c5d47-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="c5d47-192">實現此行為的一個方法是實現中介軟體，如*Startup.cs*檔示例中所示。</span><span class="sxs-lookup"><span data-stu-id="c5d47-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="c5d47-193">此中介軟體執行相同的邏輯，然後將控制權傳輸到中介軟體管道中的下一個處理常式。</span><span class="sxs-lookup"><span data-stu-id="c5d47-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="c5d47-194">有關遷移模組和處理常式的詳細資訊，請參閱將 HTTP[處理常式和模組遷移到ASP.NET核心中介軟體](/aspnet/core/migration/http-modules)。</span><span class="sxs-lookup"><span data-stu-id="c5d47-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="c5d47-195">遷移靜態檔</span><span class="sxs-lookup"><span data-stu-id="c5d47-195">Migrate static files</span></span>

<span data-ttu-id="c5d47-196">要提供靜態檔（例如，HTML、CSS、圖像和 JavaScript），必須通過中介軟體公開這些檔。</span><span class="sxs-lookup"><span data-stu-id="c5d47-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="c5d47-197">調用`UseStaticFiles`該方法可以從 Web 根路徑提供靜態檔。</span><span class="sxs-lookup"><span data-stu-id="c5d47-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="c5d47-198">預設 Web 根目錄是*wwwroot，* 但可以自訂。</span><span class="sxs-lookup"><span data-stu-id="c5d47-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="c5d47-199">如 eShop `Configure` `Startup`類的方法中包含的：</span><span class="sxs-lookup"><span data-stu-id="c5d47-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="c5d47-200">eShop 專案支援基本的靜態檔訪問。</span><span class="sxs-lookup"><span data-stu-id="c5d47-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="c5d47-201">有許多自訂可用於靜態檔訪問。</span><span class="sxs-lookup"><span data-stu-id="c5d47-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="c5d47-202">有關啟用預設檔或檔瀏覽器的資訊，請參閱[ASP.NET 酷睿 中的靜態檔](/aspnet/core/fundamentals/static-files)。</span><span class="sxs-lookup"><span data-stu-id="c5d47-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="c5d47-203">遷移運行時捆綁和最小化設置</span><span class="sxs-lookup"><span data-stu-id="c5d47-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="c5d47-204">捆綁和分量化是性能優化技術，用於減少檢索某些檔案類型的伺服器請求的數量和大小。</span><span class="sxs-lookup"><span data-stu-id="c5d47-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="c5d47-205">在發送到用戶端之前，JavaScript 和 CSS 通常會經歷某種形式的捆綁或小化。</span><span class="sxs-lookup"><span data-stu-id="c5d47-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="c5d47-206">在 web 表單ASP.NET，這些優化在運行時處理。</span><span class="sxs-lookup"><span data-stu-id="c5d47-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="c5d47-207">優化約定定義為*App_Start/BundleConfig.cs*檔。</span><span class="sxs-lookup"><span data-stu-id="c5d47-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="c5d47-208">在ASP.NET核心中，採用了一種更具聲明性的方法。</span><span class="sxs-lookup"><span data-stu-id="c5d47-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="c5d47-209">檔列出了要進行挖掘的檔以及特定的小化設置。</span><span class="sxs-lookup"><span data-stu-id="c5d47-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="c5d47-210">有關捆綁和最小化的詳細資訊，請參閱 ASP.NET[酷中捆綁和小化靜態資產](/aspnet/core/client-side/bundling-and-minification)。</span><span class="sxs-lookup"><span data-stu-id="c5d47-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="c5d47-211">遷移 ASPX 頁面</span><span class="sxs-lookup"><span data-stu-id="c5d47-211">Migrate ASPX pages</span></span>

<span data-ttu-id="c5d47-212">Web 表單應用中的頁面是具有 *.aspx*副檔名的檔。</span><span class="sxs-lookup"><span data-stu-id="c5d47-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="c5d47-213">Web 表單頁通常可以映射到 Blazor 中的元件。</span><span class="sxs-lookup"><span data-stu-id="c5d47-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="c5d47-214">Blazor 元件創作在具有 *.razor*副檔名的檔中。</span><span class="sxs-lookup"><span data-stu-id="c5d47-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="c5d47-215">對於 eShop 專案，五個頁面將轉換為 Razor 頁面。</span><span class="sxs-lookup"><span data-stu-id="c5d47-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="c5d47-216">例如，詳細資訊視圖由 Web 表單專案中的三個檔組成：*詳細資訊.aspx、Details.aspx.cs\*\*Details.aspx.cs*和*Details.aspx.designer.cs*。</span><span class="sxs-lookup"><span data-stu-id="c5d47-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="c5d47-217">轉換為 Blazor 時，代碼後面和標記將合併為*詳細資訊。*</span><span class="sxs-lookup"><span data-stu-id="c5d47-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="c5d47-218">Razor 編譯（等效于 *.designer.cs*檔中的內容）存儲在*obj*目錄中，預設情況下無法在**解決方案資源管理器**中查看。</span><span class="sxs-lookup"><span data-stu-id="c5d47-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="c5d47-219">"Web 表單"頁由以下標記組成：</span><span class="sxs-lookup"><span data-stu-id="c5d47-219">The Web Forms page consists of the following markup:</span></span>

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

<span data-ttu-id="c5d47-220">前面的標記代碼後面包括以下代碼：</span><span class="sxs-lookup"><span data-stu-id="c5d47-220">The preceding markup's code-behind includes the following code:</span></span>

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

<span data-ttu-id="c5d47-221">轉換為 Blazor 後，Web 表單頁將轉換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="c5d47-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

<span data-ttu-id="c5d47-222">請注意，代碼和標記位於同一檔中。</span><span class="sxs-lookup"><span data-stu-id="c5d47-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="c5d47-223">使用 屬性`@inject`可以訪問任何必需的服務。</span><span class="sxs-lookup"><span data-stu-id="c5d47-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="c5d47-224">根據`@page`指令，可以在`Catalog/Details/{id}`路由上訪問此頁面。</span><span class="sxs-lookup"><span data-stu-id="c5d47-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="c5d47-225">路由`{id}`預留位置的值已限制為整數。</span><span class="sxs-lookup"><span data-stu-id="c5d47-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="c5d47-226">如[路由](pages-routing-layouts.md)部分所述，與 Web 表單不同，Razor 元件顯式表示其路由和包含的任何參數。</span><span class="sxs-lookup"><span data-stu-id="c5d47-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="c5d47-227">許多 Web 表單控制項在 Blazor 中可能沒有確切的對應控制項。</span><span class="sxs-lookup"><span data-stu-id="c5d47-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="c5d47-228">通常有一個等效的 HTML 程式碼片段將服務于相同的目的。</span><span class="sxs-lookup"><span data-stu-id="c5d47-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="c5d47-229">例如，`<asp:Label />`控制項可以替換為 HTML`<label>`元素。</span><span class="sxs-lookup"><span data-stu-id="c5d47-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="c5d47-230">布拉佐中的模型驗證</span><span class="sxs-lookup"><span data-stu-id="c5d47-230">Model validation in Blazor</span></span>

<span data-ttu-id="c5d47-231">如果 Web 表單代碼包含驗證，則可以通過很少對無的更改傳輸大部分內容。</span><span class="sxs-lookup"><span data-stu-id="c5d47-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="c5d47-232">在 Blazor 中運行的一個好處是，無需自訂 JavaScript 即可運行相同的驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="c5d47-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="c5d47-233">資料注釋支援簡單的模型驗證。</span><span class="sxs-lookup"><span data-stu-id="c5d47-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="c5d47-234">例如 *，Create.aspx*頁具有具有驗證的資料輸入表單。</span><span class="sxs-lookup"><span data-stu-id="c5d47-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="c5d47-235">示例程式碼片段如下所示：</span><span class="sxs-lookup"><span data-stu-id="c5d47-235">An example snippet would look like this:</span></span>

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

<span data-ttu-id="c5d47-236">在 Blazor 中，等效標記在*Create.razor*檔中提供：</span><span class="sxs-lookup"><span data-stu-id="c5d47-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

<span data-ttu-id="c5d47-237">上下文`EditForm`包括驗證支援，可以環繞輸入。</span><span class="sxs-lookup"><span data-stu-id="c5d47-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="c5d47-238">資料注釋是添加驗證的常見方法。</span><span class="sxs-lookup"><span data-stu-id="c5d47-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="c5d47-239">此類驗證支援可通過`DataAnnotationsValidator`元件添加。</span><span class="sxs-lookup"><span data-stu-id="c5d47-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="c5d47-240">有關此機制的詳細資訊，請參閱[ASP.NET核心 Blazor 表單和驗證](/aspnet/core/blazor/forms-validation)。</span><span class="sxs-lookup"><span data-stu-id="c5d47-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="c5d47-241">遷移內置 Web 表單控制項</span><span class="sxs-lookup"><span data-stu-id="c5d47-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="c5d47-242">*此內容即將推出。*</span><span class="sxs-lookup"><span data-stu-id="c5d47-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="c5d47-243">移轉組態</span><span class="sxs-lookup"><span data-stu-id="c5d47-243">Migrate configuration</span></span>

<span data-ttu-id="c5d47-244">在 Web 表單專案中，配置資料通常存儲在*Web.config 檔中*。</span><span class="sxs-lookup"><span data-stu-id="c5d47-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="c5d47-245">配置資料與 訪問一起`ConfigurationManager`。</span><span class="sxs-lookup"><span data-stu-id="c5d47-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="c5d47-246">分析物件通常需要服務。</span><span class="sxs-lookup"><span data-stu-id="c5d47-246">Services were often required to parse objects.</span></span> <span data-ttu-id="c5d47-247">使用 .NET 框架 4.7.2，通過 將可組合`ConfigurationBuilders`性添加到配置中。</span><span class="sxs-lookup"><span data-stu-id="c5d47-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="c5d47-248">這些產生器允許開發人員添加各種配置源，然後在運行時組成這些源以檢索必要的值。</span><span class="sxs-lookup"><span data-stu-id="c5d47-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="c5d47-249">ASP.NET Core 引入了一個靈活的配置系統，允許您定義應用和部署使用的配置源或源。</span><span class="sxs-lookup"><span data-stu-id="c5d47-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="c5d47-250">在`ConfigurationBuilder`Web 表單應用中可能使用的基礎結構是仿ASP.NET核心配置系統中使用的概念建模的。</span><span class="sxs-lookup"><span data-stu-id="c5d47-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="c5d47-251">以下程式碼片段演示了 Web 表單 eShop 專案如何使用*Web.config*來存儲配置值：</span><span class="sxs-lookup"><span data-stu-id="c5d47-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

<span data-ttu-id="c5d47-252">機密（如資料庫連接字串）通常存儲在*Web.config*中。機密不可避免地在不安全的位置（如原始程式碼管理）中持續存在。</span><span class="sxs-lookup"><span data-stu-id="c5d47-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="c5d47-253">在ASP.NET核心上的 Blazor 上，前面基於 XML 的配置將替換為以下 JSON：</span><span class="sxs-lookup"><span data-stu-id="c5d47-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="c5d47-254">JSON 是預設配置格式;但是，ASP.NET酷睿支援許多其他格式，包括 XML。</span><span class="sxs-lookup"><span data-stu-id="c5d47-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="c5d47-255">還有幾種社區支援的格式。</span><span class="sxs-lookup"><span data-stu-id="c5d47-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="c5d47-256">Blazor 類中的建構函式通過稱為構造`Startup`函數注入的`IConfiguration`DI 技術接受實例：</span><span class="sxs-lookup"><span data-stu-id="c5d47-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

<span data-ttu-id="c5d47-257">預設情況下，環境變數、JSON 檔（*應用設置.json*和應用*設置。環境\.json*）和命令列選項在設定物件中註冊為有效的配置源。</span><span class="sxs-lookup"><span data-stu-id="c5d47-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="c5d47-258">可通過 訪問配置源`Configuration[key]`。</span><span class="sxs-lookup"><span data-stu-id="c5d47-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="c5d47-259">更高級的技術是使用選項模式將配置資料繫結到物件。</span><span class="sxs-lookup"><span data-stu-id="c5d47-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="c5d47-260">有關配置和選項模式的詳細資訊，請參閱 ASP.NET[核心中ASP.NET核心](/aspnet/core/fundamentals/configuration/)和[選項模式中的](/aspnet/core/fundamentals/configuration/options)配置。</span><span class="sxs-lookup"><span data-stu-id="c5d47-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="c5d47-261">遷移資料訪問</span><span class="sxs-lookup"><span data-stu-id="c5d47-261">Migrate data access</span></span>

<span data-ttu-id="c5d47-262">資料訪問是任何應用的一個重要方面。</span><span class="sxs-lookup"><span data-stu-id="c5d47-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="c5d47-263">eShop 專案將目錄資訊存儲在資料庫中，並使用實體框架 （EF） 6 檢索資料。</span><span class="sxs-lookup"><span data-stu-id="c5d47-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="c5d47-264">由於 .NET Core 3.0 中支援 EF 6，因此專案可以繼續使用它。</span><span class="sxs-lookup"><span data-stu-id="c5d47-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="c5d47-265">eShop 需要進行以下與 EF 相關的更改：</span><span class="sxs-lookup"><span data-stu-id="c5d47-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="c5d47-266">在 .NET 框架`DbContext`中，物件接受表單*名稱_ConnectString*的字串，並使用 中的`ConfigurationManager.AppSettings[ConnectionString]`連接字串進行連接。</span><span class="sxs-lookup"><span data-stu-id="c5d47-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="c5d47-267">在 .NET Core 中，不支援此功能。</span><span class="sxs-lookup"><span data-stu-id="c5d47-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="c5d47-268">必須提供連接字串。</span><span class="sxs-lookup"><span data-stu-id="c5d47-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="c5d47-269">以同步方式訪問資料庫。</span><span class="sxs-lookup"><span data-stu-id="c5d47-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="c5d47-270">雖然這行得通，但可擴充性可能會受到影響。</span><span class="sxs-lookup"><span data-stu-id="c5d47-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="c5d47-271">此邏輯應移動到非同步模式。</span><span class="sxs-lookup"><span data-stu-id="c5d47-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="c5d47-272">儘管對資料集綁定的本機支援不同，但 Blazor 在 Razor 頁面中提供了靈活性和功能，其 C# 支援。</span><span class="sxs-lookup"><span data-stu-id="c5d47-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="c5d47-273">例如，您可以執行計算並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="c5d47-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="c5d47-274">有關 Blazor 中資料模式的詳細資訊，請參閱[資料訪問](data.md)章節。</span><span class="sxs-lookup"><span data-stu-id="c5d47-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="c5d47-275">體系結構更改</span><span class="sxs-lookup"><span data-stu-id="c5d47-275">Architectural changes</span></span>

<span data-ttu-id="c5d47-276">最後，在遷移到 Blazor 時需要考慮一些重要的體系結構差異。</span><span class="sxs-lookup"><span data-stu-id="c5d47-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="c5d47-277">其中許多更改適用于基於 .NET Core 或 ASP.NET核心的任何更改。</span><span class="sxs-lookup"><span data-stu-id="c5d47-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="c5d47-278">由於 Blazor 建立在 .NET Core 上，因此在確保對 .NET Core 的支援時需要考慮。</span><span class="sxs-lookup"><span data-stu-id="c5d47-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="c5d47-279">一些主要更改包括刪除以下功能：</span><span class="sxs-lookup"><span data-stu-id="c5d47-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="c5d47-280">多個應用域</span><span class="sxs-lookup"><span data-stu-id="c5d47-280">Multiple AppDomains</span></span>
- <span data-ttu-id="c5d47-281">遠端</span><span class="sxs-lookup"><span data-stu-id="c5d47-281">Remoting</span></span>
- <span data-ttu-id="c5d47-282">程式碼存取安全性 (CAS)</span><span class="sxs-lookup"><span data-stu-id="c5d47-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="c5d47-283">安全性透明度</span><span class="sxs-lookup"><span data-stu-id="c5d47-283">Security Transparency</span></span>

<span data-ttu-id="c5d47-284">有關識別支援在 .NET Core 上運行的必要更改的技術的詳細資訊，請參閱[將代碼從 .NET 框架移植到 .NET Core](/dotnet/core/porting)。</span><span class="sxs-lookup"><span data-stu-id="c5d47-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="c5d47-285">ASP.NET核心是ASP.NET的重新構想版本，並且有一些最初看起來並不明顯的更改。</span><span class="sxs-lookup"><span data-stu-id="c5d47-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="c5d47-286">主要更改包括：</span><span class="sxs-lookup"><span data-stu-id="c5d47-286">The main changes are:</span></span>

- <span data-ttu-id="c5d47-287">沒有同步上下文，這意味著沒有`HttpContext.Current`、`Thread.CurrentPrincipal`或其他靜態訪問器</span><span class="sxs-lookup"><span data-stu-id="c5d47-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="c5d47-288">無陰影複製</span><span class="sxs-lookup"><span data-stu-id="c5d47-288">No shadow copying</span></span>
- <span data-ttu-id="c5d47-289">無請求佇列</span><span class="sxs-lookup"><span data-stu-id="c5d47-289">No request queue</span></span>

<span data-ttu-id="c5d47-290">ASP.NET Core 中的許多操作都是非同步，這允許更輕鬆地卸載 I/O 綁定的任務。</span><span class="sxs-lookup"><span data-stu-id="c5d47-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="c5d47-291">請務必不要使用`Task.Wait()`或`Task.GetResult()`阻止，這可以快速耗盡執行緒池資源。</span><span class="sxs-lookup"><span data-stu-id="c5d47-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="c5d47-292">遷移結論</span><span class="sxs-lookup"><span data-stu-id="c5d47-292">Migration conclusion</span></span>

<span data-ttu-id="c5d47-293">此時，您已經看到許多示例，說明將 Web 表單專案移動到 Blazor 需要什麼。</span><span class="sxs-lookup"><span data-stu-id="c5d47-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="c5d47-294">有關完整示例，請參閱[eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor)專案。</span><span class="sxs-lookup"><span data-stu-id="c5d47-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="c5d47-295">上一步</span><span class="sxs-lookup"><span data-stu-id="c5d47-295">Previous</span></span>](security-authentication-authorization.md)
