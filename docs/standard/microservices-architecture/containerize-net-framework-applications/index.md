---
title: "將舊版整合型 .NET Framework 應用程式移轉至 Windows 容器"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 將舊版整合型 .NET Framework 應用程式移轉至 Windows 容器"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 1756ff0f49d9bb243fa561ba760418eba79de1f0
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="migrating-legacy-monolithic-net-framework-applications-to-windows-containers"></a>將舊版整合型 .NET Framework 應用程式移轉至 Windows 容器

*Windows 容器可用來改善開發和測試環境，並可用來部署以舊版 .NET Framework 技術 (例如 Web* *Form) 為基礎的應用程式。以這種方式將容器用於舊版應用程式稱為「隨即轉移」案例。*

本指南稍早章節已探討微服務架構，其中商務應用程式會分散到不同的容器，且每個容器會執行很小的集中式服務。 該目標有許多好處。 在新的程式開發中，強烈建議使用該方法。 企業關鍵應用程式也能從中受益，而且所獲得的好處足以彌補重新架構和重新實作的成本。

但是，並非所有應用程式所獲得的好處都足以彌補成本。 這並不表示這些應用程式不能用在容器案例。

在本節中，我們將探討 eShopOnContainers 應用程式，如圖 7-1 所示。 eShopOnContainers 企業小組成員會使用此應用程式來檢視及編輯產品目錄。

![](./media/image1.png)

**圖 7-1**. Windows 容器上的 ASP.NET Web Form 應用程式 (舊版技術)

這是用來瀏覽及修改目錄項目的 Web Form 應用程式。 Web Form 相依性表示此應用程式不會在 .NET Core 上執行，除非經過重寫不使用 Web Form 而改用 ASP.NET Core MVC。 您會看到如何在容器中執行這類應用程式，而不進行任何變更。 您也會看到如何進行微幅變更，以便在混合模式中運作，其中某些功能已移至不同的微服務，但大部分功能仍然保留在整合型應用程式中。

## <a name="benefits-of-containerizing-a-monolithic-application"></a>容器化整合型應用程式的好處

Catalog.WebForms 應用程式位於 eShopOnContainers GitHub 存放庫 (<https://github.com/dotnet/eShopOnContainers>) 中。 此應用程式是獨立 Web 應用程式，可存取高可用性資料存放區。 即便如此，在容器中執行此應用程式還是有些優點。 您會建立應用程式的映像。 之後，每個部署會在相同的環境中執行。 每個容器會使用相同的 OS 版本、安裝相同版本的相依性、使用相同的架構，並使用相同的程序來建置。 您可以在圖 7-2 中看到載入 Visual Studio 2017 的應用程式。

![](./media/image2.png)

**圖 7-2**. Visual Studio 2017 中的目錄管理 Web Form 應用程式

此外，所有開發人員都可以在此一致的環境中執行應用程式。 特定版本才有的問題會立即對開發人員顯示，而不是出現在預備環境或生產環境中。 一旦應用程式在容器中執行，不同開發環境之間的差異對開發小組而言就不再那麼重要。

最後，容器化應用程式的向外延展曲線較平坦。 您已了解容器化應用程式如何在 VM 中啟用更多容器，或在實體機器中啟用更多容器。 這會導致密度增加且所需的資源減少。

基於上述所有原因，請考慮在 Docker 容器中使用「隨即轉移」作業來執行舊版整合型應用程式。 「隨即轉移」一詞描述工作範圍：您從實體或虛擬機器「取出」(lift)整個應用程式，然後將它「移位」(shift) 到容器中。 在理想的情況下，您不需要對應用程式程式碼進行任何變更，就能在容器中執行。

## <a name="possible-migration-paths"></a>可能的移轉路徑

如同整合型應用程式，Catalog.Webforms 應用程式是一個包含所有程式碼的 Web 應用程式，包括資料存取程式庫。 資料庫會在不同的高可用性機器上執行。 該設定會在範例程式碼中透過模擬目錄服務來模擬：您可以對假的資料執行 Catalog.WebForms 應用程式，以模擬純粹的隨即轉移案例。 這會展示最簡單的移轉路徑，其中您會移動現有的資產以在容器中執行，完全不需要變更任何程式碼。 此路徑適用於完整且與移至微服務的功能有最少互動的應用程式。

不過，eShopOnContainers 網站已針對不同案例使用微服務來存取資料存放區。 您可以對目錄編輯器進行一些額外的微幅變更，有效率的調控目錄微服務，而不是直接存取目錄資料存放區。

這些變更有助於讓您自己的應用程式持續運作。 您可以進行任何變更，從將現有應用程式保持不變地移至容器中、進行微幅變更讓現有應用程式存取部分新的微服務，到完全重寫應用程式以完全參與新的微服務架構。 正確的路徑取決於移轉成本及任何移轉的好處。

## <a name="application-tour"></a>應用程式導覽

您可以載入 Catalog.WebForms 方案，並將應用程式當作獨立應用程式來執行。 在此設定中，應用程式使用假的服務傳回資料，而不是永續性儲存體資料庫。 應用程式使用 Autofac (<https://autofac.org/>) 作為控制反轉 (Inversion of Control，IOC) 容器。 透過相依性插入 (DI)，您可以設定應用程式來使用假的資料或即時目錄資料服務 (稍後我們將進一步說明 DI)。啟始程式碼會從 web.config 檔案讀取 useFake 設定，並設定 Autofac 容器以插入假的資料服務或即時目錄服務。 如果您執行應用程式並將 web.config 檔案中的 useFake 設定為 false，您會看到 Web Form 應用程式顯示目錄資料。

使用過 Web Form 的所有人應該都很熟悉此應用程式中所使用的大部分技術。 不過，目錄微服務引進兩項可能不熟悉的技術：稍早所述的相依性插入 (DI)，以及在 Web Form 中使用非同步資料存放區。

DI 會將撰寫類別以配置所有必要資源的典型物件導向策略反轉。 讓類別改為從服務容器要求其相依性。 DI 的優點是您可以將外部服務取代為假的 (模擬) 服務，以支援測試或其他環境。

DI 容器使用 web.config appSettings 設定，來控制要使用假的目錄資料或執行中服務的即時資料。 應用程式會註冊 HttpModule 物件以建置容器，並註冊前置要求處理常式以插入相依性。 您會看到 Modules/AutoFacHttpModule.cs 檔案中的程式碼，如下列範例所示：

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

應用程式的頁面 (Default.aspx.cs 和 EditPage.aspx.cs) 會定義接受這些相依性的建構函式。 請注意，預設建構函式仍然存在且可供存取。 此基礎結構需要下列程式碼。

```cs
protected _Default() { }

public _Default(ICatalogService catalog) => this.catalog = catalog;
```

所有目錄 API 都是非同步方法。 Web Form 現在為所有資料控制項提供這些支援。 Catalog.WebForms 應用程式使用清單和編輯頁面的模型繫結；頁面上的控制項會定義指定 Task-returning 非同步作業的 SelectMethod、UpdateMethod、InsertMethod 和 DeleteMethod 屬性。 Web Form 控制項了解繫結至控制項的方法何時非同步。 使用非同步 Select 方法的唯一限制是您無法支援分頁。 分頁簽章需要 out 參數，而非同步方法不可有 out 參數。 此相同技術可用於從目錄服務要求資料的其他頁面。

目錄 Web Form 應用程式的預設設定使用 catalog.api 服務的模擬實作。 此模擬針對其資料使用硬式編碼資料集，藉由移除開發環境中 catalog.api 服務上的相依性來簡化一些工作。

## <a name="lifting-and-shifting"></a>隨即轉移

Visual Studio 提供容器化應用程式的絕佳支援。 您以滑鼠右鍵按一下專案節點，然後選取 [新增] 和 [Docker 支援]。 Docker 專案範本會將名為 **docker-compose** 的專案新增至方案。 此專案包含由您需要的映像所組成 (或建置) 的 Docker 資產，並會開始執行必要的容器，如圖 7-3 所示。

在最簡單的隨即轉移案例中，應用程式會是您用於 Web Form 應用程式的單一服務。 此範本也會變更您的啟始專案，以指向 **docker-compose** 專案。 按下 Ctrl+F5 或 F5 現在會建立 Docker 映像並啟動 Docker 容器。

![](./media/image3.png)

**圖 7-3**. Web Form 方案中的 **docker-compose** 專案

執行方案之前，您必須確定設定 Docker 以使用 Windows 容器。 若要這樣做，請以滑鼠右鍵按一下 Windows 中的 Docker 工作列圖示，然後選取 [切換至 Windows 容器]，如圖 7-4 所示。

![](./media/image4.png)

**圖 7-4**. 從 Windows 的 Docker 工作列圖示切換至 Windows 容器

如果功能表項目顯示 [切換至 Linux 容器]，則表示您已使用 Windows 容器執行 Docker。

執行方案會重新啟動 Docker 主機。 當您建置時，您會建置應用程式和 Web Form 專案的 Docker 映像。 第一次這樣做需要相當長的時間。 這是因為建置流程會下拉基底 Windows Server 映像和 ASP.NET 的額外映像。 後續建置和執行循環會更快。

讓我們進一步查看由 Docker 專案範本新增的檔案。 它已為您建立數個檔案。 Visual Studio 會使用這些檔案來建立 Docker 映像並啟動容器。 您可以使用相同的檔案從 CLI 手動執行 Docker 命令。

下列 Dockerfile 範例顯示基本設定，以根據執行 ASP.NET 網站的 Windows ASP.NET 映像建置 Docker 映像。

```
FROM microsoft/aspnet

ARG source

WORKDIR /inetpub/wwwroot

COPY ${source:-obj/Docker/publish} .
```

此 Dockerfile 看起來非常類似為了在 Linux 容器中執行 ASP.NET Core 應用程式所建立的檔案。 不過，有幾個重要的差異。 最重要的差異是基底映像為 microsoft/aspnet，也就是包含 .NET Framework 的目前 Windows Server 映像。 其他差異是從來源目錄複製的目錄會不同。

**docker-compose** 專案中的其他檔案包括建置及設定容器所需的 Docker 資產。 Visual Studio 會將各種 docker-compose.yml 檔案放在一個節點下，以醒目提示其使用方式。 基底 docker-compose 檔案包含所有設定通用的指示詞。 docker-compose.override.yml 檔案包含環境變數和開發人員設定的相關覆寫。 副檔名為 .vs.debug 和 .vs.release 的變數提供環境設定，讓 Visual Studio 可以附加及管理執行中的容器。

雖然 Visual Studio 整合是對您的方案新增 Docker 支援的一部分，但您也可以使用 docker-compose up 命令從命令列建置及執行，如您在先前章節中所見。

## <a name="getting-data-from-the-existing-catalog-net-core-microservice"></a>從現有的目錄 .NET Core 微服務取得資料

您可以設定 Web Form 應用程式使用 eShopOnContainers 目錄微服務取得資料，而不是使用假的資料。 若要這樣做，您可以編輯 web.config 檔案，並將 useFake 索引鍵的值設定為 false。 DI 容器將會使用存取即時目錄微服務的類別，而不是傳回硬式編碼資料的類別。 不需要其他程式碼變更。

存取即時目錄服務並不表示您需要更新 **docker-compose** 專案，才能建置目錄服務映像並啟動目錄服務容器。 Docker CE for Windows 支援 Linux 容器和 Windows 容器，但不會同時支援。 若要執行目錄微服務，您需要建置一個映像，以在 Windows 容器上執行目錄微服務。 此方法需要不同於您在稍早章節中所看到之微服務專案的 Dockerfile。 Dockerfile.windows 檔案包含組態設定，可建置目錄 API 容器映像以便在 Windows 容器上執行；例如，若要使用 Windows Nano Docker 映像。

目錄微服務依賴 SQL Server 資料庫。 因此，您也需要使用以 Windows 為基礎的 SQL Server Docker 映像。

在這些變更之後，docker-compose 專案除了啟動應用程式，還會執行其他作業。 此專案現在會使用以 Windows 為基礎的 SQL Server 映像來啟動 SQL Server。 它會在 Windows 容器中啟動目錄微服務。 此外，它也會在 Windows 容器中啟動 Web Form 目錄編輯器容器。 如果任何映像需要建置，則會先建立映像。

## <a name="development-and-production-environments"></a>開發和生產環境

開發設定和生產設定之間有兩項差異。 在開發環境中，您會將 Web Form 應用程式、目錄微服務和 Windows 容器中的 SQL Server 當作相同 Docker 主機的一部分來執行。 在稍早章節中，我們提到 SQL Server 映像是部署在相同的 Docker 主機中，如同其他 .NET Core 服務是在 Linux 架構的 Docker 主機上。 在相同 Docker 主機 (或叢集) 中執行多個微服務的優點是，網路通訊較少且容器之間的通訊延遲較低。

在開發環境中，您必須在相同的 OS 中執行所有容器。 Docker CE for Windows 不支援同時執行 Windows 和 Linux 容器。 在生產環境中，您可以決定要在單一 Docker 主機 (或叢集) 的 Windows 容器中執行目錄微服務，還是要讓 Web Form 應用程式與不同 Docker 主機之 Linux 容器中執行的目錄微服務執行個體通訊。 這會視您要如何最佳化網路延遲而定。 在大多數情況下，您會想要讓應用程式相依的微服務在相同的 Docker 主機 (或群集) 中執行，以方便部署並降低通訊延遲。 在這些設定中，只有在微服務執行個體與高可用性伺服器之間為了永續性資料儲存的通訊才會有很高的成本。

>[!div class="step-by-step"]
[上一個] (../net-core-single-containers-linux-windows-server-hosts/index.md) [下一個] (../multi-container-microservice-net-applications/index.md)

