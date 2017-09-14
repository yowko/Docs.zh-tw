---
title: "將舊版整合型 .NET Framework 應用程式移轉至 Windows 容器"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 將舊版整合型 .NET Framework 應用程式移轉至 Windows 容器"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 1756ff0f49d9bb243fa561ba760418eba79de1f0
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="migrating-legacy-monolithic-net-framework-applications-to-windows-containers"></a><span data-ttu-id="45107-104">將舊版整合型 .NET Framework 應用程式移轉至 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="45107-104">Migrating Legacy Monolithic .NET Framework Applications to Windows Containers</span></span>

<span data-ttu-id="45107-105">*Windows 容器可用來改善開發和測試環境，並可用來部署以舊版 .NET Framework 技術 (例如 Web* *Form) 為基礎的應用程式。以這種方式將容器用於舊版應用程式稱為「隨即轉移」案例。*</span><span class="sxs-lookup"><span data-stu-id="45107-105">*Windows Containers can be used as a way to improve development and test environments, and to deploy applications that are based on legacy .NET Framework technologies like Web* *Forms. Using containers for legacy applications in this way is referred to as a “lift and shift” scenario.*</span></span>

<span data-ttu-id="45107-106">本指南稍早章節已探討微服務架構，其中商務應用程式會分散到不同的容器，且每個容器會執行很小的集中式服務。</span><span class="sxs-lookup"><span data-stu-id="45107-106">Earlier sections of this guide have championed a microservices architecture where business applications are distributed among different containers, each running a small, focused service.</span></span> <span data-ttu-id="45107-107">該目標有許多好處。</span><span class="sxs-lookup"><span data-stu-id="45107-107">That goal has many benefits.</span></span> <span data-ttu-id="45107-108">在新的程式開發中，強烈建議使用該方法。</span><span class="sxs-lookup"><span data-stu-id="45107-108">In new development, that approach is strongly recommended.</span></span> <span data-ttu-id="45107-109">企業關鍵應用程式也能從中受益，而且所獲得的好處足以彌補重新架構和重新實作的成本。</span><span class="sxs-lookup"><span data-stu-id="45107-109">Enterprise-critical applications will also benefit enough to justify the cost of a rearchitecture and reimplementation.</span></span>

<span data-ttu-id="45107-110">但是，並非所有應用程式所獲得的好處都足以彌補成本。</span><span class="sxs-lookup"><span data-stu-id="45107-110">But not every application will benefit enough to justify the cost.</span></span> <span data-ttu-id="45107-111">這並不表示這些應用程式不能用在容器案例。</span><span class="sxs-lookup"><span data-stu-id="45107-111">That does not mean that those applications cannot be used in container scenarios.</span></span>

<span data-ttu-id="45107-112">在本節中，我們將探討 eShopOnContainers 應用程式，如圖 7-1 所示。</span><span class="sxs-lookup"><span data-stu-id="45107-112">In this section, we will explore an application for eShopOnContainers, shown in Figure 7-1.</span></span> <span data-ttu-id="45107-113">eShopOnContainers 企業小組成員會使用此應用程式來檢視及編輯產品目錄。</span><span class="sxs-lookup"><span data-stu-id="45107-113">This application would be used by members of the eShopOnContainers enterprise team to view and edit the product catalog.</span></span>

![](./media/image1.png)

<span data-ttu-id="45107-114">**圖 7-1**.</span><span class="sxs-lookup"><span data-stu-id="45107-114">**Figure 7-1**.</span></span> <span data-ttu-id="45107-115">Windows 容器上的 ASP.NET Web Form 應用程式 (舊版技術)</span><span class="sxs-lookup"><span data-stu-id="45107-115">ASP.NET Web Forms application (legacy technology) on a Windows Container</span></span>

<span data-ttu-id="45107-116">這是用來瀏覽及修改目錄項目的 Web Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="45107-116">This is a Web Forms application that is used to browse and modify the catalog entries.</span></span> <span data-ttu-id="45107-117">Web Form 相依性表示此應用程式不會在 .NET Core 上執行，除非經過重寫不使用 Web Form 而改用 ASP.NET Core MVC。</span><span class="sxs-lookup"><span data-stu-id="45107-117">The Web Forms dependency means this application will not run on .NET Core unless it is rewritten without Web Forms and instead uses ASP.NET Core MVC.</span></span> <span data-ttu-id="45107-118">您會看到如何在容器中執行這類應用程式，而不進行任何變更。</span><span class="sxs-lookup"><span data-stu-id="45107-118">You will see how you can run applications like these in containers without changes.</span></span> <span data-ttu-id="45107-119">您也會看到如何進行微幅變更，以便在混合模式中運作，其中某些功能已移至不同的微服務，但大部分功能仍然保留在整合型應用程式中。</span><span class="sxs-lookup"><span data-stu-id="45107-119">You will also see how you can make minimal changes to work in a hybrid mode where some functionality has been moved into a separate microservice, but most functionality remains in the monolithic application.</span></span>

## <a name="benefits-of-containerizing-a-monolithic-application"></a><span data-ttu-id="45107-120">容器化整合型應用程式的好處</span><span class="sxs-lookup"><span data-stu-id="45107-120">Benefits of containerizing a monolithic application</span></span>

<span data-ttu-id="45107-121">Catalog.WebForms 應用程式位於 eShopOnContainers GitHub 存放庫 (<https://github.com/dotnet/eShopOnContainers>) 中。</span><span class="sxs-lookup"><span data-stu-id="45107-121">The Catalog.WebForms application is available in the eShopOnContainers GitHub repository (<https://github.com/dotnet/eShopOnContainers>).</span></span> <span data-ttu-id="45107-122">此應用程式是獨立 Web 應用程式，可存取高可用性資料存放區。</span><span class="sxs-lookup"><span data-stu-id="45107-122">This application is a standalone web application accessing a high-availability data store.</span></span> <span data-ttu-id="45107-123">即便如此，在容器中執行此應用程式還是有些優點。</span><span class="sxs-lookup"><span data-stu-id="45107-123">Even so, there are advantages to running the application in a container.</span></span> <span data-ttu-id="45107-124">您會建立應用程式的映像。</span><span class="sxs-lookup"><span data-stu-id="45107-124">You create an image for the application.</span></span> <span data-ttu-id="45107-125">之後，每個部署會在相同的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="45107-125">From that point forward, every deployment runs in the same environment.</span></span> <span data-ttu-id="45107-126">每個容器會使用相同的 OS 版本、安裝相同版本的相依性、使用相同的架構，並使用相同的程序來建置。</span><span class="sxs-lookup"><span data-stu-id="45107-126">Every container uses the same OS version, has the same version of dependencies installed, uses the same framework, and is built using the same process.</span></span> <span data-ttu-id="45107-127">您可以在圖 7-2 中看到載入 Visual Studio 2017 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="45107-127">You can see the application loaded in Visual Studio 2017 in Figure 7-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="45107-128">**圖 7-2**.</span><span class="sxs-lookup"><span data-stu-id="45107-128">**Figure 7-2**.</span></span> <span data-ttu-id="45107-129">Visual Studio 2017 中的目錄管理 Web Form 應用程式</span><span class="sxs-lookup"><span data-stu-id="45107-129">Catalog management Web Forms application in Visual Studio 2017</span></span>

<span data-ttu-id="45107-130">此外，所有開發人員都可以在此一致的環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="45107-130">In addition, developers can all run the application in this consistent environment.</span></span> <span data-ttu-id="45107-131">特定版本才有的問題會立即對開發人員顯示，而不是出現在預備環境或生產環境中。</span><span class="sxs-lookup"><span data-stu-id="45107-131">Issues that only appear with certain versions will appear immediately for developers rather than surfacing in a staging or production environment.</span></span> <span data-ttu-id="45107-132">一旦應用程式在容器中執行，不同開發環境之間的差異對開發小組而言就不再那麼重要。</span><span class="sxs-lookup"><span data-stu-id="45107-132">Differences between the development environments among the development team matter less once applications run in containers.</span></span>

<span data-ttu-id="45107-133">最後，容器化應用程式的向外延展曲線較平坦。</span><span class="sxs-lookup"><span data-stu-id="45107-133">Finally, containerized applications have a flatter scale-out curve.</span></span> <span data-ttu-id="45107-134">您已了解容器化應用程式如何在 VM 中啟用更多容器，或在實體機器中啟用更多容器。</span><span class="sxs-lookup"><span data-stu-id="45107-134">You have learned how containerized apps enable more containers in a VM or more containers in a physical machine.</span></span> <span data-ttu-id="45107-135">這會導致密度增加且所需的資源減少。</span><span class="sxs-lookup"><span data-stu-id="45107-135">This translates to higher density and fewer required resources.</span></span>

<span data-ttu-id="45107-136">基於上述所有原因，請考慮在 Docker 容器中使用「隨即轉移」作業來執行舊版整合型應用程式。</span><span class="sxs-lookup"><span data-stu-id="45107-136">For all these reasons, consider running legacy monolithic apps in a Docker container using a “lift-and-shift” operation.</span></span> <span data-ttu-id="45107-137">「隨即轉移」一詞描述工作範圍：您從實體或虛擬機器「取出」(lift)整個應用程式，然後將它「移位」(shift) 到容器中。</span><span class="sxs-lookup"><span data-stu-id="45107-137">The phrase “lift and shift” describes the scope of the task: you *lift* the entire application from a physical or virtual machine, and *shift* it into a container.</span></span> <span data-ttu-id="45107-138">在理想的情況下，您不需要對應用程式程式碼進行任何變更，就能在容器中執行。</span><span class="sxs-lookup"><span data-stu-id="45107-138">In ideal situations, you do not need to make any changes to the application code to run it in a container.</span></span>

## <a name="possible-migration-paths"></a><span data-ttu-id="45107-139">可能的移轉路徑</span><span class="sxs-lookup"><span data-stu-id="45107-139">Possible migration paths</span></span>

<span data-ttu-id="45107-140">如同整合型應用程式，Catalog.Webforms 應用程式是一個包含所有程式碼的 Web 應用程式，包括資料存取程式庫。</span><span class="sxs-lookup"><span data-stu-id="45107-140">As a monolithic application, the Catalog.Webforms application is one web application containing all the code, including the data access libraries.</span></span> <span data-ttu-id="45107-141">資料庫會在不同的高可用性機器上執行。</span><span class="sxs-lookup"><span data-stu-id="45107-141">The database runs on a separate high-availability machine.</span></span> <span data-ttu-id="45107-142">該設定會在範例程式碼中透過模擬目錄服務來模擬：您可以對假的資料執行 Catalog.WebForms 應用程式，以模擬純粹的隨即轉移案例。</span><span class="sxs-lookup"><span data-stu-id="45107-142">That configuration is simulated in the sample code by using a mock catalog service: you can run the Catalog.WebForms application against that fake data to simulate a pure lift-and-shift scenario.</span></span> <span data-ttu-id="45107-143">這會展示最簡單的移轉路徑，其中您會移動現有的資產以在容器中執行，完全不需要變更任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="45107-143">This demonstrates the simplest migration path, where you move existing assets to run in a container without any code changes at all.</span></span> <span data-ttu-id="45107-144">此路徑適用於完整且與移至微服務的功能有最少互動的應用程式。</span><span class="sxs-lookup"><span data-stu-id="45107-144">This path is appropriate for applications that are complete and that have minimal interaction with functionality that you are moving to microservices.</span></span>

<span data-ttu-id="45107-145">不過，eShopOnContainers 網站已針對不同案例使用微服務來存取資料存放區。</span><span class="sxs-lookup"><span data-stu-id="45107-145">However, the eShopOnContainers website is already accessing the data storage using microservices for different scenarios.</span></span> <span data-ttu-id="45107-146">您可以對目錄編輯器進行一些額外的微幅變更，有效率的調控目錄微服務，而不是直接存取目錄資料存放區。</span><span class="sxs-lookup"><span data-stu-id="45107-146">Some small additional changes can be made to the catalog editor to leverage the catalog microservice instead of accessing the catalog data storage directly.</span></span>

<span data-ttu-id="45107-147">這些變更有助於讓您自己的應用程式持續運作。</span><span class="sxs-lookup"><span data-stu-id="45107-147">These changes demonstrate the continuum for your own applications.</span></span> <span data-ttu-id="45107-148">您可以進行任何變更，從將現有應用程式保持不變地移至容器中、進行微幅變更讓現有應用程式存取部分新的微服務，到完全重寫應用程式以完全參與新的微服務架構。</span><span class="sxs-lookup"><span data-stu-id="45107-148">You can do anything from moving an existing application without change into containers, to making small changes that enable existing applications to access some of the new microservices, to completely rewriting an application to fully participate in a new microservice-based architecture.</span></span> <span data-ttu-id="45107-149">正確的路徑取決於移轉成本及任何移轉的好處。</span><span class="sxs-lookup"><span data-stu-id="45107-149">The right path depends on both the cost of the migration and the benefits from any migration.</span></span>

## <a name="application-tour"></a><span data-ttu-id="45107-150">應用程式導覽</span><span class="sxs-lookup"><span data-stu-id="45107-150">Application tour</span></span>

<span data-ttu-id="45107-151">您可以載入 Catalog.WebForms 方案，並將應用程式當作獨立應用程式來執行。</span><span class="sxs-lookup"><span data-stu-id="45107-151">You can load the Catalog.WebForms solution and run the application as a standalone application.</span></span> <span data-ttu-id="45107-152">在此設定中，應用程式使用假的服務傳回資料，而不是永續性儲存體資料庫。</span><span class="sxs-lookup"><span data-stu-id="45107-152">In this configuration, instead of a persistent storage database, the application uses a fake service to return data.</span></span> <span data-ttu-id="45107-153">應用程式使用 Autofac (<https://autofac.org/>) 作為控制反轉 (Inversion of Control，IOC) 容器。</span><span class="sxs-lookup"><span data-stu-id="45107-153">The application uses Autofac (<https://autofac.org/>) as an inversion of control (IOC) container.</span></span> <span data-ttu-id="45107-154">透過相依性插入 (DI)，您可以設定應用程式來使用假的資料或即時目錄資料服務</span><span class="sxs-lookup"><span data-stu-id="45107-154">Using Dependency Injection (DI), you can configure the application to use the fake data or the live catalog data service.</span></span> <span data-ttu-id="45107-155">(稍後我們將進一步說明 DI)。啟始程式碼會從 web.config 檔案讀取 useFake 設定，並設定 Autofac 容器以插入假的資料服務或即時目錄服務。</span><span class="sxs-lookup"><span data-stu-id="45107-155">(We will explain more about DI shortly.) The startup code reads a useFake setting from the web.config files, and configures the Autofac container to inject either the fake data service or the live catalog service.</span></span> <span data-ttu-id="45107-156">如果您執行應用程式並將 web.config 檔案中的 useFake 設定為 false，您會看到 Web Form 應用程式顯示目錄資料。</span><span class="sxs-lookup"><span data-stu-id="45107-156">If you run the application with useFake set to false in the web.config file, you see the Web Forms application displaying the catalog data.</span></span>

<span data-ttu-id="45107-157">使用過 Web Form 的所有人應該都很熟悉此應用程式中所使用的大部分技術。</span><span class="sxs-lookup"><span data-stu-id="45107-157">Most of the techniques used in this application should be very familiar to anyone who has used Web Forms.</span></span> <span data-ttu-id="45107-158">不過，目錄微服務引進兩項可能不熟悉的技術：稍早所述的相依性插入 (DI)，以及在 Web Form 中使用非同步資料存放區。</span><span class="sxs-lookup"><span data-stu-id="45107-158">However, the catalog microservice introduces two techniques that might be unfamiliar: Dependency Injection (DI), which was mentioned earlier, and working with asynchronous data stores in Web Forms.</span></span>

<span data-ttu-id="45107-159">DI 會將撰寫類別以配置所有必要資源的典型物件導向策略反轉。</span><span class="sxs-lookup"><span data-stu-id="45107-159">DI inverts the typical object-oriented strategy of writing classes that allocate all needed resources.</span></span> <span data-ttu-id="45107-160">讓類別改為從服務容器要求其相依性。</span><span class="sxs-lookup"><span data-stu-id="45107-160">Instead, classes request their dependencies from a service container.</span></span> <span data-ttu-id="45107-161">DI 的優點是您可以將外部服務取代為假的 (模擬) 服務，以支援測試或其他環境。</span><span class="sxs-lookup"><span data-stu-id="45107-161">The advantage of DI is that you can replace external services with fakes (mocks) to support testing or other environments.</span></span>

<span data-ttu-id="45107-162">DI 容器使用 web.config appSettings 設定，來控制要使用假的目錄資料或執行中服務的即時資料。</span><span class="sxs-lookup"><span data-stu-id="45107-162">The DI container uses the web.config appSettings configuration to control whether to use the fake catalog data or the live data from the running service.</span></span> <span data-ttu-id="45107-163">應用程式會註冊 HttpModule 物件以建置容器，並註冊前置要求處理常式以插入相依性。</span><span class="sxs-lookup"><span data-stu-id="45107-163">The application registers an HttpModule object that builds the container and registers a pre-request handler to inject dependencies.</span></span> <span data-ttu-id="45107-164">您會看到 Modules/AutoFacHttpModule.cs 檔案中的程式碼，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="45107-164">You can see that code in the Modules/AutoFacHttpModule.cs file, which looks like the following example:</span></span>

```cs
private static IContainer CreateContainer()
{
  // Configure AutoFac:
  // Register Containers:

  var settings = WebConfigurationManager.AppSettings;
  var useFake = settings["usefake"];
  bool fake = useFake == "true";
  var builder = new ContainerBuilder();

  if (fake)
  {
    builder.RegisterType<CatalogMockService>()
    .As<ICatalogService>();
  }
  else
  {
    builder.RegisterType<CatalogService>()
    .As<ICatalogService>();
    builder.RegisterType<RequestProvider>()
    .As<IRequestProvider>();
  }

  var container = builder.Build();
  return container;
}

private void InjectDependencies()
{
  if (HttpContext.Current.CurrentHandler is Page page)
  {
    // Get the code-behind class that we may have written
    var pageType = page.GetType().BaseType;

    // Determine if there is a constructor to inject, and grab it
    var ctor = (from c in pageType.GetConstructors()
                where c.GetParameters().Length > 0
                select c).FirstOrDefault();

    if (ctor != null)
    {
      // Resolve the parameters for the constructor
      var args = (from parm in ctor.GetParameters()
                  select Container.Resolve(parm.ParameterType))
                  .ToArray();

      // Execute the constructor method with the arguments resolved
      ctor.Invoke(page, args);
    }

    // Use the Autofac method to inject any
    // properties that can be filled by Autofac
    Container.InjectProperties(page);
  }
}
```

<span data-ttu-id="45107-165">應用程式的頁面 (Default.aspx.cs 和 EditPage.aspx.cs) 會定義接受這些相依性的建構函式。</span><span class="sxs-lookup"><span data-stu-id="45107-165">The application’s pages (Default.aspx.cs and EditPage.aspx.cs) define constructors that take these dependencies.</span></span> <span data-ttu-id="45107-166">請注意，預設建構函式仍然存在且可供存取。</span><span class="sxs-lookup"><span data-stu-id="45107-166">Note that the default constructor is still present and accessible.</span></span> <span data-ttu-id="45107-167">此基礎結構需要下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="45107-167">The infrastructure needs the following code.</span></span>

```cs
protected _Default() { }

public _Default(ICatalogService catalog) => this.catalog = catalog;
```

<span data-ttu-id="45107-168">所有目錄 API 都是非同步方法。</span><span class="sxs-lookup"><span data-stu-id="45107-168">The catalog APIs are all asynchronous methods.</span></span> <span data-ttu-id="45107-169">Web Form 現在為所有資料控制項提供這些支援。</span><span class="sxs-lookup"><span data-stu-id="45107-169">Web Forms now supports these for all data controls.</span></span> <span data-ttu-id="45107-170">Catalog.WebForms 應用程式使用清單和編輯頁面的模型繫結；頁面上的控制項會定義指定 Task-returning 非同步作業的 SelectMethod、UpdateMethod、InsertMethod 和 DeleteMethod 屬性。</span><span class="sxs-lookup"><span data-stu-id="45107-170">The Catalog.WebForms application uses model binding for the list and edit pages; controls on the pages define SelectMethod, UpdateMethod, InsertMethod, and DeleteMethod properties that specify Task-returning asynchronous operations.</span></span> <span data-ttu-id="45107-171">Web Form 控制項了解繫結至控制項的方法何時非同步。</span><span class="sxs-lookup"><span data-stu-id="45107-171">Web Forms controls understand when the methods bound to a control are asynchronous.</span></span> <span data-ttu-id="45107-172">使用非同步 Select 方法的唯一限制是您無法支援分頁。</span><span class="sxs-lookup"><span data-stu-id="45107-172">The only restriction you encounter when using asynchronous select methods is that you cannot support paging.</span></span> <span data-ttu-id="45107-173">分頁簽章需要 out 參數，而非同步方法不可有 out 參數。</span><span class="sxs-lookup"><span data-stu-id="45107-173">The paging signature requires an out parameter, and asynchronous methods cannot have out parameters.</span></span> <span data-ttu-id="45107-174">此相同技術可用於從目錄服務要求資料的其他頁面。</span><span class="sxs-lookup"><span data-stu-id="45107-174">This same technique is used on other pages that require data from the catalog service.</span></span>

<span data-ttu-id="45107-175">目錄 Web Form 應用程式的預設設定使用 catalog.api 服務的模擬實作。</span><span class="sxs-lookup"><span data-stu-id="45107-175">The default configuration for the catalog Web Forms application uses a mock implementation of the catalog.api service.</span></span> <span data-ttu-id="45107-176">此模擬針對其資料使用硬式編碼資料集，藉由移除開發環境中 catalog.api 服務上的相依性來簡化一些工作。</span><span class="sxs-lookup"><span data-stu-id="45107-176">This mock uses a hard-coded dataset for its data, which simplifies some tasks by removing the dependency on the catalog.api service in development environments.</span></span>

## <a name="lifting-and-shifting"></a><span data-ttu-id="45107-177">隨即轉移</span><span class="sxs-lookup"><span data-stu-id="45107-177">Lifting and shifting</span></span>

<span data-ttu-id="45107-178">Visual Studio 提供容器化應用程式的絕佳支援。</span><span class="sxs-lookup"><span data-stu-id="45107-178">Visual Studio provides great support for containerizing an application.</span></span> <span data-ttu-id="45107-179">您以滑鼠右鍵按一下專案節點，然後選取 [新增] 和 [Docker 支援]。</span><span class="sxs-lookup"><span data-stu-id="45107-179">You right-click the project node and then select **Add** and **Docker Support**.</span></span> <span data-ttu-id="45107-180">Docker 專案範本會將名為 **docker-compose** 的專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="45107-180">The Docker project template adds a new project to the solution called **docker-compose**.</span></span> <span data-ttu-id="45107-181">此專案包含由您需要的映像所組成 (或建置) 的 Docker 資產，並會開始執行必要的容器，如圖 7-3 所示。</span><span class="sxs-lookup"><span data-stu-id="45107-181">The project contains the Docker assets that compose (or build) the images you need, and starts running the necessary containers, as shown in Figure 7-3.</span></span>

<span data-ttu-id="45107-182">在最簡單的隨即轉移案例中，應用程式會是您用於 Web Form 應用程式的單一服務。</span><span class="sxs-lookup"><span data-stu-id="45107-182">In the simplest lift-and-shift scenarios, the application will be the single service that you use for the Web Forms application.</span></span> <span data-ttu-id="45107-183">此範本也會變更您的啟始專案，以指向 **docker-compose** 專案。</span><span class="sxs-lookup"><span data-stu-id="45107-183">The template also changes your startup project to point to the **docker-compose** project.</span></span> <span data-ttu-id="45107-184">按下 Ctrl+F5 或 F5 現在會建立 Docker 映像並啟動 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="45107-184">Pressing Ctrl+F5 or F5 now creates the Docker image and launches the Docker container.</span></span>

![](./media/image3.png)

<span data-ttu-id="45107-185">**圖 7-3**.</span><span class="sxs-lookup"><span data-stu-id="45107-185">**Figure 7-3**.</span></span> <span data-ttu-id="45107-186">Web Form 方案中的 **docker-compose** 專案</span><span class="sxs-lookup"><span data-stu-id="45107-186">The **docker-compose** project in the Web Forms solution</span></span>

<span data-ttu-id="45107-187">執行方案之前，您必須確定設定 Docker 以使用 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="45107-187">Before you run the solution, you must make sure that you configure Docker to use Windows Containers.</span></span> <span data-ttu-id="45107-188">若要這樣做，請以滑鼠右鍵按一下 Windows 中的 Docker 工作列圖示，然後選取 [切換至 Windows 容器]，如圖 7-4 所示。</span><span class="sxs-lookup"><span data-stu-id="45107-188">To do that, you right-click the Docker taskbar icon in Windows and select **Switch to Windows Containers**, as shown in Figure 7-4.</span></span>

![](./media/image4.png)

<span data-ttu-id="45107-189">**圖 7-4**.</span><span class="sxs-lookup"><span data-stu-id="45107-189">**Figure 7-4**.</span></span> <span data-ttu-id="45107-190">從 Windows 的 Docker 工作列圖示切換至 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="45107-190">Switching to Windows Containers from the Docker taskbar icon in Windows</span></span>

<span data-ttu-id="45107-191">如果功能表項目顯示 [切換至 Linux 容器]，則表示您已使用 Windows 容器執行 Docker。</span><span class="sxs-lookup"><span data-stu-id="45107-191">If the menu item says **Switch to Linux containers**, you are already running Docker with Windows Containers.</span></span>

<span data-ttu-id="45107-192">執行方案會重新啟動 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="45107-192">Running the solution restarts the Docker host.</span></span> <span data-ttu-id="45107-193">當您建置時，您會建置應用程式和 Web Form 專案的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="45107-193">When you build, you build the application and the Docker image for the Web Forms project.</span></span> <span data-ttu-id="45107-194">第一次這樣做需要相當長的時間。</span><span class="sxs-lookup"><span data-stu-id="45107-194">The first time you do this, it takes considerable time.</span></span> <span data-ttu-id="45107-195">這是因為建置流程會下拉基底 Windows Server 映像和 ASP.NET 的額外映像。</span><span class="sxs-lookup"><span data-stu-id="45107-195">This is because the build process pulls down the base Windows Server image and the additional image for ASP.NET.</span></span> <span data-ttu-id="45107-196">後續建置和執行循環會更快。</span><span class="sxs-lookup"><span data-stu-id="45107-196">Subsequent build and run cycles will be much faster.</span></span>

<span data-ttu-id="45107-197">讓我們進一步查看由 Docker 專案範本新增的檔案。</span><span class="sxs-lookup"><span data-stu-id="45107-197">Let’s take a deeper look at the files added by the Docker project template.</span></span> <span data-ttu-id="45107-198">它已為您建立數個檔案。</span><span class="sxs-lookup"><span data-stu-id="45107-198">It created several files for you.</span></span> <span data-ttu-id="45107-199">Visual Studio 會使用這些檔案來建立 Docker 映像並啟動容器。</span><span class="sxs-lookup"><span data-stu-id="45107-199">Visual Studio uses these files to create the Docker image and launch a container.</span></span> <span data-ttu-id="45107-200">您可以使用相同的檔案從 CLI 手動執行 Docker 命令。</span><span class="sxs-lookup"><span data-stu-id="45107-200">You can use the same files from the CLI to run Docker commands manually.</span></span>

<span data-ttu-id="45107-201">下列 Dockerfile 範例顯示基本設定，以根據執行 ASP.NET 網站的 Windows ASP.NET 映像建置 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="45107-201">The following Dockerfile example shows the basic settings for building a Docker image based on the Windows ASP.NET image that runs an ASP.NET site.</span></span>

```
FROM microsoft/aspnet

ARG source

WORKDIR /inetpub/wwwroot

COPY ${source:-obj/Docker/publish} .
```

<span data-ttu-id="45107-202">此 Dockerfile 看起來非常類似為了在 Linux 容器中執行 ASP.NET Core 應用程式所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="45107-202">This Dockerfile will look very similar to those created for running an ASP.NET Core application in Linux containers.</span></span> <span data-ttu-id="45107-203">不過，有幾個重要的差異。</span><span class="sxs-lookup"><span data-stu-id="45107-203">However, there are a few important differences.</span></span> <span data-ttu-id="45107-204">最重要的差異是基底映像為 microsoft/aspnet，也就是包含 .NET Framework 的目前 Windows Server 映像。</span><span class="sxs-lookup"><span data-stu-id="45107-204">The most important difference is that the base image is microsoft/aspnet, which is the current Windows Server image that includes the .NET Framework.</span></span> <span data-ttu-id="45107-205">其他差異是從來源目錄複製的目錄會不同。</span><span class="sxs-lookup"><span data-stu-id="45107-205">Other differences are that the directories copied from your source directory are different.</span></span>

<span data-ttu-id="45107-206">**docker-compose** 專案中的其他檔案包括建置及設定容器所需的 Docker 資產。</span><span class="sxs-lookup"><span data-stu-id="45107-206">The other files in the **docker-compose** project are the Docker assets needed to build and configure the containers.</span></span> <span data-ttu-id="45107-207">Visual Studio 會將各種 docker-compose.yml 檔案放在一個節點下，以醒目提示其使用方式。</span><span class="sxs-lookup"><span data-stu-id="45107-207">Visual Studio puts the various docker-compose.yml files under one node to highlight how they are used.</span></span> <span data-ttu-id="45107-208">基底 docker-compose 檔案包含所有設定通用的指示詞。</span><span class="sxs-lookup"><span data-stu-id="45107-208">The base docker-compose file contains the directives that are common to all configurations.</span></span> <span data-ttu-id="45107-209">docker-compose.override.yml 檔案包含環境變數和開發人員設定的相關覆寫。</span><span class="sxs-lookup"><span data-stu-id="45107-209">The docker-compose.override.yml file contains environment variables and related overrides for a developer configuration.</span></span> <span data-ttu-id="45107-210">副檔名為 .vs.debug 和 .vs.release 的變數提供環境設定，讓 Visual Studio 可以附加及管理執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="45107-210">The variants with .vs.debug and .vs.release provide environment settings that enable Visual Studio to attach to and manage the running container.</span></span>

<span data-ttu-id="45107-211">雖然 Visual Studio 整合是對您的方案新增 Docker 支援的一部分，但您也可以使用 docker-compose up 命令從命令列建置及執行，如您在先前章節中所見。</span><span class="sxs-lookup"><span data-stu-id="45107-211">While Visual Studio integration is part of adding Docker support to your solution, you can also build and run from the command line, using the docker-compose up command, as you saw in previous sections.</span></span>

## <a name="getting-data-from-the-existing-catalog-net-core-microservice"></a><span data-ttu-id="45107-212">從現有的目錄 .NET Core 微服務取得資料</span><span class="sxs-lookup"><span data-stu-id="45107-212">Getting data from the existing catalog .NET Core microservice</span></span>

<span data-ttu-id="45107-213">您可以設定 Web Form 應用程式使用 eShopOnContainers 目錄微服務取得資料，而不是使用假的資料。</span><span class="sxs-lookup"><span data-stu-id="45107-213">You can configure the Web Forms application to use the eShopOnContainers catalog microservice to get data instead of using fake data.</span></span> <span data-ttu-id="45107-214">若要這樣做，您可以編輯 web.config 檔案，並將 useFake 索引鍵的值設定為 false。</span><span class="sxs-lookup"><span data-stu-id="45107-214">To do this, you edit the web.config file and set the value of the useFake key to false.</span></span> <span data-ttu-id="45107-215">DI 容器將會使用存取即時目錄微服務的類別，而不是傳回硬式編碼資料的類別。</span><span class="sxs-lookup"><span data-stu-id="45107-215">The DI container will use the class that accesses the live catalog microservice instead of the class that returns the hard-coded data.</span></span> <span data-ttu-id="45107-216">不需要其他程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="45107-216">No other code changes are needed.</span></span>

<span data-ttu-id="45107-217">存取即時目錄服務並不表示您需要更新 **docker-compose** 專案，才能建置目錄服務映像並啟動目錄服務容器。</span><span class="sxs-lookup"><span data-stu-id="45107-217">Accessing the live catalog service does mean you need to update the **docker-compose** project to build the catalog service image and launch the catalog service container.</span></span> <span data-ttu-id="45107-218">Docker CE for Windows 支援 Linux 容器和 Windows 容器，但不會同時支援。</span><span class="sxs-lookup"><span data-stu-id="45107-218">Docker CE for Windows supports both Linux containers and Windows Containers, but not at the same time.</span></span> <span data-ttu-id="45107-219">若要執行目錄微服務，您需要建置一個映像，以在 Windows 容器上執行目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="45107-219">To run the catalog microservice, you need to build an image that runs the catalog microservice on top of a Windows-based container.</span></span> <span data-ttu-id="45107-220">此方法需要不同於您在稍早章節中所看到之微服務專案的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="45107-220">This approach requires a different Dockerfile for the microservices project than you have seen in earlier sections.</span></span> <span data-ttu-id="45107-221">Dockerfile.windows 檔案包含組態設定，可建置目錄 API 容器映像以便在 Windows 容器上執行；例如，若要使用 Windows Nano Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="45107-221">The Dockerfile.windows file contains the configuration settings to build the catalog API container image so that it runs on a Windows container—for example, to use a Windows Nano Docker image.</span></span>

<span data-ttu-id="45107-222">目錄微服務依賴 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="45107-222">The catalog microservice relies on the SQL Server database.</span></span> <span data-ttu-id="45107-223">因此，您也需要使用以 Windows 為基礎的 SQL Server Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="45107-223">Therefore, you need to use a Windows-based SQL Server Docker image as well.</span></span>

<span data-ttu-id="45107-224">在這些變更之後，docker-compose 專案除了啟動應用程式，還會執行其他作業。</span><span class="sxs-lookup"><span data-stu-id="45107-224">After these changes, the docker-compose project does more to start the application.</span></span> <span data-ttu-id="45107-225">此專案現在會使用以 Windows 為基礎的 SQL Server 映像來啟動 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="45107-225">The project now starts the SQL Server using the Windows based SQL Server image.</span></span> <span data-ttu-id="45107-226">它會在 Windows 容器中啟動目錄微服務。</span><span class="sxs-lookup"><span data-stu-id="45107-226">It starts the catalog microservice in a Windows container.</span></span> <span data-ttu-id="45107-227">此外，它也會在 Windows 容器中啟動 Web Form 目錄編輯器容器。</span><span class="sxs-lookup"><span data-stu-id="45107-227">And it starts the Web Forms catalog editor container, also in a Windows container.</span></span> <span data-ttu-id="45107-228">如果任何映像需要建置，則會先建立映像。</span><span class="sxs-lookup"><span data-stu-id="45107-228">If any of the images need building, the images are created first.</span></span>

## <a name="development-and-production-environments"></a><span data-ttu-id="45107-229">開發和生產環境</span><span class="sxs-lookup"><span data-stu-id="45107-229">Development and production environments</span></span>

<span data-ttu-id="45107-230">開發設定和生產設定之間有兩項差異。</span><span class="sxs-lookup"><span data-stu-id="45107-230">There are a couple of differences between the development configuration and a production configuration.</span></span> <span data-ttu-id="45107-231">在開發環境中，您會將 Web Form 應用程式、目錄微服務和 Windows 容器中的 SQL Server 當作相同 Docker 主機的一部分來執行。</span><span class="sxs-lookup"><span data-stu-id="45107-231">In the development environment, you run the Web Forms application, the catalog microservice, and SQL Server in Windows Containers, as part of the same Docker host.</span></span> <span data-ttu-id="45107-232">在稍早章節中，我們提到 SQL Server 映像是部署在相同的 Docker 主機中，如同其他 .NET Core 服務是在 Linux 架構的 Docker 主機上。</span><span class="sxs-lookup"><span data-stu-id="45107-232">In earlier sections, we mentioned SQL Server images deployed in the same Docker host as the other .NET Core-based services on a Linux-based Docker host.</span></span> <span data-ttu-id="45107-233">在相同 Docker 主機 (或叢集) 中執行多個微服務的優點是，網路通訊較少且容器之間的通訊延遲較低。</span><span class="sxs-lookup"><span data-stu-id="45107-233">The advantage of running the multiple microservices in the same Docker host (or cluster) is that there is less network communication and the communication between containers has lower latency.</span></span>

<span data-ttu-id="45107-234">在開發環境中，您必須在相同的 OS 中執行所有容器。</span><span class="sxs-lookup"><span data-stu-id="45107-234">In the development environment, you must run all the containers in the same OS.</span></span> <span data-ttu-id="45107-235">Docker CE for Windows 不支援同時執行 Windows 和 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="45107-235">Docker CE for Windows does not support running Windows- and Linux-based containers at the same time.</span></span> <span data-ttu-id="45107-236">在生產環境中，您可以決定要在單一 Docker 主機 (或叢集) 的 Windows 容器中執行目錄微服務，還是要讓 Web Form 應用程式與不同 Docker 主機之 Linux 容器中執行的目錄微服務執行個體通訊。</span><span class="sxs-lookup"><span data-stu-id="45107-236">In production, you can decide if you want to run the catalog microservice in a Windows container in a single Docker host (or cluster), or have the Web Forms application communicate with an instance of the catalog microservice running in a Linux container on a different Docker host.</span></span> <span data-ttu-id="45107-237">這會視您要如何最佳化網路延遲而定。</span><span class="sxs-lookup"><span data-stu-id="45107-237">It depends on how you want to optimize for network latency.</span></span> <span data-ttu-id="45107-238">在大多數情況下，您會想要讓應用程式相依的微服務在相同的 Docker 主機 (或群集) 中執行，以方便部署並降低通訊延遲。</span><span class="sxs-lookup"><span data-stu-id="45107-238">In most cases, you want the microservices that your applications depend on running in the same Docker host (or swarm) for ease of deployment and lower communication latency.</span></span> <span data-ttu-id="45107-239">在這些設定中，只有在微服務執行個體與高可用性伺服器之間為了永續性資料儲存的通訊才會有很高的成本。</span><span class="sxs-lookup"><span data-stu-id="45107-239">In those configurations, the only costly communications is between the microservice instances and the high-availability servers for the persistent data storage.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="45107-240">[上一個] (../net-core-single-containers-linux-windows-server-hosts/index.md) [下一個] (../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="45107-240">[Previous] (../net-core-single-containers-linux-windows-server-hosts/index.md) [Next] (../multi-container-microservice-net-applications/index.md)</span></span>

