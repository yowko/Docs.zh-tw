---
title: 從 ASP.NET Web Forms 遷移至 Blazor
description: 瞭解如何將現有的 ASP.NET Web Forms 應用程式遷移至 Blazor 。
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: ca3d8747b02602c89aec187ea0826e658fb0cbc4
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267798"
---
# <a name="migrate-from-aspnet-web-forms-to-no-locblazor"></a><span data-ttu-id="6ab5c-103">從 ASP.NET Web Forms 遷移至 Blazor</span><span class="sxs-lookup"><span data-stu-id="6ab5c-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

<span data-ttu-id="6ab5c-104">從 ASP.NET Web Forms 將程式碼基底遷移至 Blazor 需要規劃的耗時工作。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="6ab5c-105">本章概述此程式。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-105">This chapter outlines the process.</span></span> <span data-ttu-id="6ab5c-106">可以簡化轉換的工作，是確保應用程式遵守多 *層式* 架構，在此案例中，應用程式模型 (，Web Form) 與商務邏輯不同。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="6ab5c-107">圖層的這種邏輯分隔可讓您清楚瞭解需要移至 .NET Core 和 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="6ab5c-108">在此範例中，會使用 [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) 上提供的 eShop 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="6ab5c-109">eShop 是一種目錄服務，可透過表單輸入和驗證提供 CRUD 功能。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="6ab5c-110">為何要將工作中的應用程式遷移至 Blazor ？</span><span class="sxs-lookup"><span data-stu-id="6ab5c-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="6ab5c-111">很多時候都不需要。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-111">Many times, there's no need.</span></span> <span data-ttu-id="6ab5c-112">ASP.NET Web Forms 將持續支援許多年。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="6ab5c-113">不過， Blazor 只有已遷移的應用程式才支援所提供的許多功能。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="6ab5c-114">這類功能包括：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-114">Such features include:</span></span>

- <span data-ttu-id="6ab5c-115">架構中的效能改進，例如 `Span<T>`</span><span class="sxs-lookup"><span data-stu-id="6ab5c-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="6ab5c-116">執行 as 的能力 WebAssembly</span><span class="sxs-lookup"><span data-stu-id="6ab5c-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="6ab5c-117">Linux 和 macOS 的跨平臺支援</span><span class="sxs-lookup"><span data-stu-id="6ab5c-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="6ab5c-118">應用程式本機部署或共用架構部署，而不影響其他應用程式</span><span class="sxs-lookup"><span data-stu-id="6ab5c-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="6ab5c-119">如果這些或其他新功能的吸引力夠大，則遷移應用程式可能會有價值。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="6ab5c-120">遷移可採用不同的圖形;它可以是整個應用程式，或只是需要變更的特定端點。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="6ab5c-121">遷移決策最終是以開發人員要解決的商務問題為基礎。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="6ab5c-122">伺服器端與用戶端裝載</span><span class="sxs-lookup"><span data-stu-id="6ab5c-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="6ab5c-123">如 [裝載模型](hosting-models.md) 一章所述， Blazor 應用程式可以用兩種不同的方式裝載：伺服器端和用戶端。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="6ab5c-124">伺服器端模型會在執行伺服器上的任何實際程式碼時，使用 ASP.NET Core SignalR 連接來管理 DOM 更新。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="6ab5c-125">用戶端模型會在 WebAssembly 瀏覽器中執行，而不需要伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="6ab5c-126">有一些差異會影響，最適合特定的應用程式：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="6ab5c-127">執行時 WebAssembly 仍在開發中，而且可能不支援所有功能 (例如目前時間的執行緒) </span><span class="sxs-lookup"><span data-stu-id="6ab5c-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="6ab5c-128">用戶端與伺服器之間的多對話通訊可能會導致伺服器端模式的延遲問題</span><span class="sxs-lookup"><span data-stu-id="6ab5c-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="6ab5c-129">存取資料庫和內部或受保護的服務時，需要使用用戶端裝載的個別服務</span><span class="sxs-lookup"><span data-stu-id="6ab5c-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="6ab5c-130">在撰寫本文時，伺服器端模型更為類似 Web Form。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="6ab5c-131">本章大多著重于伺服器端裝載模型，因為它已準備好用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="6ab5c-132">建立新專案</span><span class="sxs-lookup"><span data-stu-id="6ab5c-132">Create a new project</span></span>

<span data-ttu-id="6ab5c-133">此初始遷移步驟是建立新專案。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="6ab5c-134">此專案類型是以 .NET Core 的 SDK 樣式專案為基礎，並且簡化了先前專案格式所使用的大部分重複專案。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="6ab5c-135">如需詳細資訊，請參閱 [專案結構](project-structure.md)的章節。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="6ab5c-136">建立專案之後，請安裝先前專案中使用的程式庫。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="6ab5c-137">在較舊的 Web Form 專案中，您可能已使用 *packages.config* 檔案來列出所需的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="6ab5c-138">在新的 SDK 樣式專案中， *packages.config* 已取代為 `<PackageReference>` 專案檔中的元素。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="6ab5c-139">這種方法的優點是所有相依性都是以可轉移的方式安裝的。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="6ab5c-140">您只會列出您感興趣的最上層相依性。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="6ab5c-141">您所使用的許多相依性都適用于 .NET Core，包括 Entity Framework 6 和 log4net。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="6ab5c-142">如果沒有可用的 .NET Core 或 .NET Standard 版本，則通常可以使用 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="6ab5c-143">您的里程可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-143">Your mileage may vary.</span></span> <span data-ttu-id="6ab5c-144">任何在 .NET Core 中無法使用的 API 都會導致執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="6ab5c-145">Visual Studio 會通知您這類套件。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="6ab5c-146">**方案總管**中專案的 [**參考**] 節點上會出現黃色圖示。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="6ab5c-147">在以 Blazor eShop 為基礎的專案中，您可以看到已安裝的封裝。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="6ab5c-148">先前， *packages.config* 檔案會列出專案中使用的每個套件，而導致檔案的長度大約是50行。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="6ab5c-149">*packages.config*的程式碼片段為：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-149">A snippet of *packages.config* is:</span></span>

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

<span data-ttu-id="6ab5c-150">`<packages>`元素包含所有必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="6ab5c-151">因為您需要這些封裝，所以很難找出其中包含哪些套件。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="6ab5c-152">有些 `<package>` 元素只是為了滿足您需要的相依性需求而列出的。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="6ab5c-153">Blazor專案會在專案檔的專案中列出您需要的相依性 `<ItemGroup>` ：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="6ab5c-154">其中一個可簡化 Web Form 開發人員生命週期的 NuGet 套件是 [Windows 相容性套件](../../core/porting/windows-compat-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="6ab5c-155">雖然 .NET Core 是跨平臺的，但某些功能只能在 Windows 上使用。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="6ab5c-156">藉由安裝相容性套件，可取得 Windows 特定功能。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="6ab5c-157">這類功能的範例包括登錄、WMI 和目錄服務。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="6ab5c-158">套件會新增 20000 Api，並啟用您可能已經熟悉的許多服務。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="6ab5c-159">EShop 專案不需要相容性套件;但是，如果您的專案使用 Windows 特定功能，則套件會簡化遷移工作。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="6ab5c-160">啟用啟動進程</span><span class="sxs-lookup"><span data-stu-id="6ab5c-160">Enable startup process</span></span>

<span data-ttu-id="6ab5c-161">的啟動程式 Blazor 從 Web Form 變更，並遵循其他 ASP.NET Core 服務的類似設定。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="6ab5c-162">裝載伺服器端時， Blazor 元件會作為一般 ASP.NET Core 應用程式的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="6ab5c-163">當裝載于瀏覽器時 WebAssembly ， Blazor 元件會使用類似的裝載模型。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="6ab5c-164">不同之處在于元件是以不同于任何後端進程的服務來執行。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="6ab5c-165">無論何種方式，啟動都很類似。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="6ab5c-166">*Global.asax.cs*檔案是 Web Form 專案的預設啟動頁面。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="6ab5c-167">在 eShop 專案中，此檔案會設定反轉 (IoC) 容器的控制權，並處理應用程式或要求的各種生命週期事件。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="6ab5c-168">其中有些事件是使用中介軟體 (（例如) ）來處理 `Application_BeginRequest` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="6ab5c-169">其他事件則需要透過相依性插入 (DI) 覆寫特定的服務。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="6ab5c-170">例如，eShop 的 *Global.asax.cs* 檔案包含下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

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
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
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

<span data-ttu-id="6ab5c-171">先前的檔案會變成 `Startup` 伺服器端中的類別 Blazor ：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

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

<span data-ttu-id="6ab5c-172">您可能會注意到 Web Form 的一項重大變更，就是 DI 的優點。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="6ab5c-173">DI 是 ASP.NET Core 設計中的指導準則。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="6ab5c-174">它支援 ASP.NET Core framework 幾乎所有層面的自訂。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="6ab5c-175">甚至有內建的服務提供者可以用於許多案例。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="6ab5c-176">如果需要更多自訂，許多的社區專案都可以支援。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="6ab5c-177">例如，您可以將協力廠商 DI 程式庫投資轉寄。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="6ab5c-178">在原始的 eShop 應用程式中，有一些會話管理的設定。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="6ab5c-179">由於伺服器端 Blazor 使用 ASP.NET Core SignalR 進行通訊，因此不支援會話狀態，因為連接可能會因 HTTP 內容而發生。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="6ab5c-180">使用會話狀態的應用程式必須先重新架構，才能以 Blazor 應用程式的形式執行。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="6ab5c-181">如需應用程式啟動的詳細資訊，請參閱 [應用程式啟動](app-startup.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="6ab5c-182">將 HTTP 模組和處理常式遷移至中介軟體</span><span class="sxs-lookup"><span data-stu-id="6ab5c-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="6ab5c-183">HTTP 模組和處理常式是 Web Form 中常見的模式，可控制 HTTP 要求管線。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="6ab5c-184">實 `IHttpModule` `IHttpHandler` 作為或可註冊並處理傳入要求的類別。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="6ab5c-185">Web Form 設定 *web.config* 檔案中的模組和處理常式。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="6ab5c-186">Web Form 也會隨著應用程式生命週期事件處理而有很大的依據。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="6ab5c-187">ASP.NET Core 會改為使用中介軟體。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="6ab5c-188">中介軟體是在類別的方法中註冊 `Configure` `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="6ab5c-189">中介軟體執行順序取決於註冊順序。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="6ab5c-190">在 [ [啟用啟動進程](#enable-startup-process) ] 區段中，Web Form 引發生命週期事件做為 `Application_BeginRequest` 方法。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="6ab5c-191">ASP.NET Core 中無法使用此事件。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="6ab5c-192">達成此行為的其中一種方式是執行中介軟體，如 *Startup.cs* 檔範例所示。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="6ab5c-193">此中介軟體會執行相同的邏輯，然後將控制權傳輸至中介軟體管線中的下一個處理常式。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="6ab5c-194">如需有關遷移模組和處理常式的詳細資訊，請參閱 [將 HTTP 處理常式和模組遷移至 ASP.NET Core 中介軟體](/aspnet/core/migration/http-modules)。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="6ab5c-195">遷移靜態檔案</span><span class="sxs-lookup"><span data-stu-id="6ab5c-195">Migrate static files</span></span>

<span data-ttu-id="6ab5c-196">為了提供靜態檔案 (例如 HTML、CSS、影像和 JavaScript) ，檔案必須由中介軟體公開。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="6ab5c-197">呼叫 `UseStaticFiles` 方法可從 web 根路徑提供靜態檔案。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="6ab5c-198">預設的 web 根目錄是 *wwwroot*，但可以自訂。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="6ab5c-199">如同 `Configure` eShop 類別的方法所包含 `Startup` ：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="6ab5c-200">EShop 專案會啟用基本的靜態檔案存取。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="6ab5c-201">有許多自訂可用於靜態檔案存取。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="6ab5c-202">如需啟用預設檔案或檔案瀏覽器的詳細資訊，請參閱 [ASP.NET Core 中的靜態](/aspnet/core/fundamentals/static-files)檔案。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="6ab5c-203">遷移執行時間包裝和縮制設定</span><span class="sxs-lookup"><span data-stu-id="6ab5c-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="6ab5c-204">組合和縮制是一種效能優化技術，可減少伺服器要求的數目和大小，以抓取特定檔案類型。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="6ab5c-205">JavaScript 和 CSS 通常會在傳送至用戶端之前，先進行某種形式的組合或縮制。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="6ab5c-206">在 ASP.NET Web Forms 中，會在執行時間處理這些優化。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="6ab5c-207">優化慣例是定義 *App_Start/bundleconfig.cs* 檔。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="6ab5c-208">在 ASP.NET Core 中，採用了更宣告的方法。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="6ab5c-209">檔案會列出要縮減的檔案，以及特定的縮制設定。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="6ab5c-210">如需有關組合和縮制的詳細資訊，請參閱 [ASP.NET Core 中的配套和縮短靜態資產](/aspnet/core/client-side/bundling-and-minification)。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="6ab5c-211">遷移 ASPX 頁面</span><span class="sxs-lookup"><span data-stu-id="6ab5c-211">Migrate ASPX pages</span></span>

<span data-ttu-id="6ab5c-212">Web Form 應用程式中的頁面是具有 *.aspx* 副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="6ab5c-213">Web Form 頁面通常可以對應到中的元件 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="6ab5c-214">Blazor元件是以*razor*副檔名的檔案撰寫的。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="6ab5c-215">針對 eShop 專案，會將五個頁面轉換成 Razor 頁面。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="6ab5c-216">例如，詳細資料檢視包含 Web Form 專案中的三個檔案： *default.aspx*、 *Details.aspx.cs*和 *Details.aspx.designer.cs*。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-216">For example, the details view comprises three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="6ab5c-217">轉換為時 Blazor ，程式碼後端和標記會合並成 *詳細資料。 razor*。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="6ab5c-218">Razor 編譯 (相當於 *designer.cs* 檔案) 儲存在 *obj* 目錄中，而且預設不會在 **方案總管**中看到。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and isn't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="6ab5c-219">Web Form] 頁面包含下列標記：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-219">The Web Forms page consists of the following markup:</span></span>

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

<span data-ttu-id="6ab5c-220">上述標記的程式碼後端包含下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-220">The preceding markup's code-behind includes the following code:</span></span>

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

<span data-ttu-id="6ab5c-221">當轉換為時 Blazor ，Web Form 頁面會轉譯成下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

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

<span data-ttu-id="6ab5c-222">請注意，程式碼和標記都在相同的檔案中。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="6ab5c-223">所有必要的服務都可透過屬性來存取 `@inject` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="6ab5c-224">每個指示詞 `@page` 可以在路由存取此頁面 `Catalog/Details/{id}` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="6ab5c-225">路由的預留位置值已 `{id}` 限制為整數。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="6ab5c-226">如 [路由](pages-routing-layouts.md) 區段中所述，與 Web Form 不同的是，Razor 元件會明確指出其路由和包含的任何參數。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="6ab5c-227">許多 Web Form 控制項在中可能沒有確切的對應專案 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="6ab5c-228">通常會有同等的 HTML 程式碼片段，以提供相同的用途。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="6ab5c-229">例如， `<asp:Label />` 控制項可以取代為 HTML 專案 `<label>` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-no-locblazor"></a><span data-ttu-id="6ab5c-230">中的模型驗證 Blazor</span><span class="sxs-lookup"><span data-stu-id="6ab5c-230">Model validation in Blazor</span></span>

<span data-ttu-id="6ab5c-231">如果您的 Web Form 程式碼包含驗證，您可以傳輸大部分的內容，而且幾乎不會有任何變更。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="6ab5c-232">在中執行的好處在於，您 Blazor 可以在不需要自訂 JavaScript 的情況下執行相同的驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="6ab5c-233">資料批註可讓您輕鬆地驗證模型。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="6ab5c-234">例如， *建立 .aspx* 頁面的資料輸入表單具有驗證。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="6ab5c-235">範例程式碼片段看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-235">An example snippet would look like this:</span></span>

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

<span data-ttu-id="6ab5c-236">在中 Blazor ，會在 *Create razor* 檔案中提供對等的標記：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

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

<span data-ttu-id="6ab5c-237">`EditForm`內容包含驗證支援，而且可以包裝在輸入周圍。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="6ab5c-238">資料批註是新增驗證的常見方式。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="6ab5c-239">這類驗證支援可透過元件加入 `DataAnnotationsValidator` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="6ab5c-240">如需此機制的詳細資訊，請參閱 [ASP.NET Core Blazor 表單和驗證](/aspnet/core/blazor/forms-validation)。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="6ab5c-241">遷移內建的 Web Form 控制項</span><span class="sxs-lookup"><span data-stu-id="6ab5c-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="6ab5c-242">*此內容即將推出。*</span><span class="sxs-lookup"><span data-stu-id="6ab5c-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="6ab5c-243">移轉組態</span><span class="sxs-lookup"><span data-stu-id="6ab5c-243">Migrate configuration</span></span>

<span data-ttu-id="6ab5c-244">在 Web Form 專案中，設定資料最常儲存在 *web.config* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="6ab5c-245">使用存取設定資料 `ConfigurationManager` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="6ab5c-246">服務通常需要剖析物件。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-246">Services were often required to parse objects.</span></span> <span data-ttu-id="6ab5c-247">在 .NET Framework 4.7.2 中，可組合性是透過來新增至 configuration `ConfigurationBuilders` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="6ab5c-248">這些產生器可讓開發人員加入不同的設定來源，然後在執行時間撰寫這些來源以取得必要的值。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="6ab5c-249">ASP.NET Core 引進了彈性的設定系統，可讓您定義應用程式和部署所使用的設定來源或來源。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="6ab5c-250">`ConfigurationBuilder`您可能會在 Web Form 應用程式中使用的基礎結構，是在 ASP.NET Core 設定系統中使用的概念之後進行模型化。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="6ab5c-251">下列程式碼片段示範 Web Form eShop 專案如何使用 *web.config* 來儲存設定值：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

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

<span data-ttu-id="6ab5c-252">在 *web.config*中儲存秘密（例如資料庫連接字串）是很常見的。秘密可避免保存在不安全的位置，例如原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="6ab5c-253">Blazor在 ASP.NET Core 上，上述以 XML 為基礎的設定會以下列 JSON 取代：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="6ab5c-254">JSON 是預設的設定格式;不過，ASP.NET Core 支援許多其他格式，包括 XML。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="6ab5c-255">另外還有數個支援社區的格式。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="6ab5c-256">專案類別中的函 Blazor 式會 `Startup` 透過稱為「函式插入」 `IConfiguration` 的 DI 技術來接受實例：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

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

<span data-ttu-id="6ab5c-257">根據預設，環境變數、JSON 檔案 (*appsettings.json* 和 *appsettings。環境}. json*) ，而且命令列選項會在設定物件中註冊為有效的設定來源。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="6ab5c-258">您可以透過存取設定來源 `Configuration[key]` 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="6ab5c-259">更先進的技術是使用選項模式將設定資料系結至物件。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="6ab5c-260">如需設定和選項模式的詳細資訊，請分別參閱 ASP.NET Core 中的 [ASP.NET Core](/aspnet/core/fundamentals/configuration/) 和 [選項模式](/aspnet/core/fundamentals/configuration/options)設定。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="6ab5c-261">遷移資料存取</span><span class="sxs-lookup"><span data-stu-id="6ab5c-261">Migrate data access</span></span>

<span data-ttu-id="6ab5c-262">資料存取是任何應用程式的重要層面。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="6ab5c-263">EShop 專案會將目錄資訊儲存在資料庫中，並使用 Entity Framework (EF) 6 來抓取資料。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="6ab5c-264">由於 .NET Core 3.0 支援 EF 6，因此專案可以繼續使用。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="6ab5c-265">EShop 需要下列 EF 相關變更：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="6ab5c-266">在 .NET Framework 中， `DbContext` 物件會接受表單 *Name = ConnectionString* 的字串，並使用中的連接字串 `ConfigurationManager.AppSettings[ConnectionString]` 來連接。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="6ab5c-267">在 .NET Core 中不支援此功能。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="6ab5c-268">必須提供連接字串。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="6ab5c-269">資料庫是以同步方式存取。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="6ab5c-270">雖然這是可行的，但是擴充性可能會受到影響。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="6ab5c-271">此邏輯應移至非同步模式。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="6ab5c-272">雖然資料集系結沒有相同的原生支援，但 Blazor 在 Razor 頁面中提供其 c # 支援的彈性和能力。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="6ab5c-273">例如，您可以執行計算並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="6ab5c-274">如需有關中資料模式的詳細資訊 Blazor ，請參閱 [資料存取](data.md) 章節。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="6ab5c-275">架構變更</span><span class="sxs-lookup"><span data-stu-id="6ab5c-275">Architectural changes</span></span>

<span data-ttu-id="6ab5c-276">最後，在遷移至時，需要考慮一些重要的架構差異 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="6ab5c-277">其中許多變更都適用于以 .NET Core 或 ASP.NET Core 為基礎的任何變更。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="6ab5c-278">因為 Blazor 是以 .Net core 為基礎，所以在確定 .Net core 支援時有一些考慮。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="6ab5c-279">部分主要變更包括移除下列功能：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="6ab5c-280">多個 Appdomain</span><span class="sxs-lookup"><span data-stu-id="6ab5c-280">Multiple AppDomains</span></span>
- <span data-ttu-id="6ab5c-281">遠端</span><span class="sxs-lookup"><span data-stu-id="6ab5c-281">Remoting</span></span>
- <span data-ttu-id="6ab5c-282">程式碼存取安全性 (CAS)</span><span class="sxs-lookup"><span data-stu-id="6ab5c-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="6ab5c-283">安全性透明度</span><span class="sxs-lookup"><span data-stu-id="6ab5c-283">Security Transparency</span></span>

<span data-ttu-id="6ab5c-284">如需有關可在 .NET Core 上執行的支援所需變更之技術的詳細資訊，請參閱將 [您的程式碼從 .NET Framework 移植到 .Net core](/dotnet/core/porting)。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="6ab5c-285">ASP.NET Core 是 ASP.NET 的重新發想版本，而且有一些可能不會很明顯的變更。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="6ab5c-286">主要變更如下：</span><span class="sxs-lookup"><span data-stu-id="6ab5c-286">The main changes are:</span></span>

- <span data-ttu-id="6ab5c-287">沒有同步處理內容，這表示沒有 `HttpContext.Current` 、 `Thread.CurrentPrincipal` 或其他靜態存取子</span><span class="sxs-lookup"><span data-stu-id="6ab5c-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="6ab5c-288">無陰影複製</span><span class="sxs-lookup"><span data-stu-id="6ab5c-288">No shadow copying</span></span>
- <span data-ttu-id="6ab5c-289">沒有要求佇列</span><span class="sxs-lookup"><span data-stu-id="6ab5c-289">No request queue</span></span>

<span data-ttu-id="6ab5c-290">ASP.NET Core 中的許多作業都是非同步，可讓您更輕鬆地關閉 i/o 系結工作的載入作業。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="6ab5c-291">絕對不要使用或來封鎖 `Task.Wait()` `Task.GetResult()` ，這樣可以快速耗盡執行緒集區資源。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="6ab5c-292">遷移結論</span><span class="sxs-lookup"><span data-stu-id="6ab5c-292">Migration conclusion</span></span>

<span data-ttu-id="6ab5c-293">到目前為止，您已瞭解將 Web Form 專案移至的許多範例 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="6ab5c-294">如需完整範例，請參閱[eShopOn Blazor ](https://github.com/dotnet-architecture/eShopOnBlazor)專案。</span><span class="sxs-lookup"><span data-stu-id="6ab5c-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6ab5c-295">[[上一步]](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="6ab5c-295">[Previous](security-authentication-authorization.md)</span></span>
