---
title: Docker 應用程式的開發工作流程
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 應用程式的開發工作流程
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: b7115530c44321dc2a10be3996c14429591b611f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401976"
---
# <a name="development-workflow-for-docker-apps"></a>Docker 應用程式的開發工作流程

應用程式開發生命週期從每位開發人員的電腦開始，開發人員在此使用其偏好的語言撰寫應用程式的程式碼，並在本機進行測試。 不論開發人員選擇哪一種語言、架構和平台，只要使用此工作流程，開發人員就一定能開發和測試 Docker 容器，但只能在本機作業。

每個容器 (Docker 映像的執行個體) 包含下列元件：

-   作業系統選取項目 (例如 Linux 發行版本、Windows Nano Server 或 Windows Server Core)。

-   開發人員新增的檔案 (應用程式二進位檔等等)。

-   組態資訊 (環境設定和相依性)。

## <a name="workflow-for-developing-docker-container-based-applications"></a>開發 Docker 容器型應用程式的工作流程

本節描述 Docker 容器型應用程式的「內部迴圈」開發工作流程。 內部迴圈工作流程表示不考慮更廣泛的 DevOps 工作流程，只著重於在開發人員電腦上完成的開發工作。 設定環境的初始步驟不包含在內，因為這些只進行一次。

應用程式是由您自己的服務加上額外的程式庫 (相依性) 所組成。 以下是組建 Docker 應用程式時通常會採用的基本步驟，如圖 5-1 所示。

![](./media/image1.png)

**圖 5-1。** 開發 Docker 容器化應用程式的逐步工作流程

本指南會詳細說明這整個程序，並針對 Visual Studio 環境說明每個主要步驟。

當您使用編輯器/CLI 開發方法 (例如，Visual Studio Code 加上 macOS 或 Windows 上的 Docker CLI) 時，您需要知道每一個步驟，通常要比使用 Visual Studio 更詳細。 如需在 CLI 環境中工作的詳細資訊，請參閱電子書 [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/) (使用 Microsoft 平台和工具的 Docker 容器化應用程式生命週期)。

當您使用 Visual Studio 2015 或 Visual Studio 2017 時，這些步驟有很多已為您處理，大幅提升您的產能。 特別是當您使用 Visual Studio 2017，並以多容器應用程式為目標時。 例如，只要按一下滑鼠，Visual Studio 就會將 Dockerfile 和 docker-compose.yml 檔案新增至您的專案，使用您的應用程式組態。 當您在 Visual Studio 中執行應用程式時，它會組建 Docker 映像並直接在 Docker 中執行多容器應用程式，甚至可讓您立即偵錯數個容器。 這些功能可大幅提高開發速度。

不過，Visual Studio 自動化這些步驟並不表示您不需要知道 Docker 在做什麼。 因此，在後續的指引中，我們會詳細說明每個步驟。

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>步驟 1： 開始撰寫程式碼，並建立您的初始應用程式或服務比較基準

開發 Docker 應用程式類似於不使用 Docker 開發應用程式的方式。 差別在於，開發 Docker 時，您要在本機環境中部署並測試 Docker 容器內執行的應用程式或服務。 容器可以是 Linux 容器或 Windows 容器。

### <a name="set-up-your-local-environment-with-visual-studio"></a>設定使用 Visual Studio 的本機環境

開始前，請確定您已安裝 [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows，如下列指示所述：

[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/) (開始使用 Docker CE for Windows)

此外，您還需要安裝 Visual Studio 2017。 這比 Visual Studio 2015 更適合 Visual Studio Tools for Docker 增益集，因為 Visual Studio 2017 有更進階的 Docker 支援，例如支援偵錯容器。 如已在安裝期間選取 [.NET Core and Docker] 工作負載，則 Visual Studio 2017 會包含適用於 Docker 的工具，如圖 5-2 所示。

![](./media/image3.png)

**圖 5-2**。 在 Visual Studio 2017 安裝期間選取 [.NET Core and Docker] 工作負載

您甚至可以在於您的應用程式中啟用 Docker，並在 Docker 中部署與測試之前，只使用 .NET 開始撰寫應用程式程式碼 (如果您打算使用容器通常會使用 .NET Core)。 不過，建議您盡快開始使用 Docker，因為它會成為實際環境，可以盡快發現任何問題。 我們鼓勵您這麼做，是因為 Visual Studio 和 Docker 合作很容易，您幾乎感覺不到它，最佳範例是從 Visual Studio 偵錯多容器應用程式時。

### <a name="additional-resources"></a>其他資源

-   **開始使用適用於 Windows 的 Docker CE**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>步驟 2： 建立與現有 .NET 基底映像有關的 Dockerfile

每個您想要組建的自訂映像都需要 Dockerfile，每個要部署的容器也需要 Dockerfile，無論您是從 Visual Studio 自動部署或使用 Docker CLI (docker run 和 docker-compose 命令) 手動部署。 如果您的應用程式包含單一的自訂服務，您需要單一的 Dockerfile。 如果您的應用程式包含多項服務 (如微服務架構)，每項服務都需要一個 Dockerfile。

Dockerfile 放在您應用程式或服務的根資料夾中。 它包含告訴 Docker 如何設定及執行容器中應用程式或服務的命令。 您可以使用程式碼手動建立 Dockerfile，將它與您的 .NET 相依性一起新增至您的專案。

使用 Visual Studio 及其適用於 Docker 的工具，這項工作只需要按幾下滑鼠即可。 當您在 Visual Studio 2017 中建立新專案時，有一個選項名為 [Enable Container (Docker) Support] (啟用容器 (Docker) 支援)，如圖 5-3 所示。

![](./media/image5.png)

**圖 5-3**。 在 Visual Studio 2017 中建立新專案時啟用 Docker 支援

您也可以在 Visual Studio 中以滑鼠右鍵按一下您的專案檔，選取 [Add-Docker Project Support] (新增 Docker 專案支援) 選項，啟用新的或現有專案的 Docker 支援，如圖 5-4 所示。

![](./media/image6.png)

**圖 5-4**。 在現有的 Visual Studio 2017 專案中啟用 Docker 支援

專案 (例如 ASP.NET Web 應用程式或 Web API 服務) 的這個動作會將 Dockerfile 和所需組態新增至專案。 它也會新增整個解決方案的 docker-compose.yml 檔案。 在下列章節中，我們會說明這些檔案每一個的詳細資訊。 Visual Studio 可以為您執行這項工作，但深入了解 Dockerfile 會很有幫助。

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>選項 A：使用現有的官方 .NET Docker 映像建立專案

您通常會在基底映像的基礎上，為您的容器組建自訂映像，此基底映像可從 [Docker Hub](https://hub.docker.com/) 登錄的官方存放庫制取得。 這就是當您在 Visual Studio 中啟用 Docker 支援時，實際發生的狀況。 您的 Dockerfile 會使用現有的 aspnetcore 映像。

前文曾說明您可以使用的 Docker 映像和存放庫，視您選擇的架構和作業系統而定。 例如，如果您想要使用 ASP.NET Core (Linux 或 Windows)，則要使用的映像就是 microsoft/aspnetcore:2.0。 因此，您只需要指定要為容器使用的基底 Docker 映像。 將 FROM microsoft/aspnetcore:2.0 新增至您的 Dockerfile 即可完成此作業。 Visual Studio 會自動執行此作業，但如打算更新版本，則要更新此值。

使用 Docker Hub 中有版本號碼的官方 .NET 映像存放庫，可確保所有電腦上都能使用相同的語言功能 (包括開發、測試和生產環境)。

下例示範 ASP.NET Core 容器的範例 Dockerfile。

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

在本例中，容器是以 2.0 版的官方 ASP.NET Core Docker 映像為基礎 (適用於 Linux 和 Windows 的多架構)。 這是 `FROM microsoft/aspnetcore:2.0` 設定。 (如需此基底映像的進一步詳細資訊，請參閱 [ASP.NET Core Docker 映像](https://hub.docker.com/r/microsoft/aspnetcore/)頁面和 [.NET Core Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)頁面。)在 Dockerfile 中，您也需要指示 Docker 接聽您會在執行階段使用的 TCP 通訊埠 (本例中為通訊埠 80，如 EXPOSE 設定的設定)。

您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。 例如，ENTRYPOINT 行中有 \["dotnet"，"MySingleContainerWebApp.dll"\] 會指示 Docker 執行 .NET Core 應用程式。 如果您使用 SDK 和 .NET Core CLI (dotnet CLI) 組建及執行 .NET 應用程式，此項設定會有所不同。 重點是 ENTRYPOINT 行與其他設定會不一樣，視您選擇的應用程式語言和平台而定。

### <a name="additional-resources"></a>其他資源

-   **建置 .NET Core 應用程式的 Docker 映像**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

-   **組建您自己的映像**. 在正式 Docker 文件中。
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>使用多架構映像存放庫

一個存放庫可以包含多種平台變化，例如 Linux 映像和 Windows 映像。 這項功能可讓像 Microsoft (基底映像建立者) 這樣的廠商建立單一存放庫以涵蓋多個平台 (即 Linux 和 Windows)。 例如，Docker Hub 登錄提供的 [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) 存放庫，會使用相同的存放庫名稱提供 Linux 和 Windows Nano Server 支援。

如果您指定標籤，如下列案例一樣明確鎖定平台：

-   **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

但如果您指定相同的映像名稱，即使使用相同的標籤，新的多架構映像 (例如支援多架構的 aspnetcore 映像) 仍會使用 Linux 或 Windows 版本，視您要部署的 Docker 主機作業系統而定，這是 2017 下半年推出的新功能，如下列範例所示：

-   **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

如此一來，當您從 Windows 主機提取映像時，它會提取 Windows variant，而從 Linux 主機提取相同的映像名稱則會提取 Linux variant。

### <a name="option-b-creating-your-base-image-from-scratch"></a>選項 B：建立全新的基底映像

您可以從頭開始建立您自己的 Docker 基底映像。 Docker 新手不建議此方案，但如果您想要設定專屬基底映像的特點，您可以這樣做。

### <a name="additional-resources"></a>其他資源

-   **多架構 .NET Core 映像**。
https://github.com/dotnet/announcements/issues/14 
-   **建立基底映像**。 正式 Docker 文件。
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>步驟 3： 建立您的自訂 Docker 映像並在其中內嵌您的應用程式或服務

您需要為應用程式中的每項服務建立相關的映像。 如果您的應用程式組成為單一的服務或 Web 應用程式，您只需要單一映像。

請注意，Visual Studio 會自動為您建立 Docker 映像。 只有編輯器/CLI 工作流程需要下列步驟，我們會清楚說明發生的狀況。

您身為開發人員，需要在本機上開發和測試，直到完成原始檔控制系統 (例如 GitHub) 的完整功能或變更。 這表示，您需要建立 Docker 映像，將容器部署到本機的 Docker 主機 (Windows 或 Linux VM) 並執行、測試及偵錯這些本機容器。

若要使用 Docker CLI 和您的 Dockerfile 在本機環境中建立自訂映像，您可以使用 docker build 命令，如圖 5-5 所示。

![](./media/image8.png)

**圖 5-5**。 建立自訂的 Docker 映像

(選擇性) 不是直接從專案資料夾執行 docker build，而是可以執行 dotnet publish 使用所需的 .NET 程式庫和二進位檔先產生可部署資料夾，再使用 docker build 命令。

這會以 cesardl/netcore-webapi-microservice-docker:first 名稱建立 Docker 映像。 本例中的 :first 是代表特定版本的標籤。 您可以為組成 Docker 應用程式所需建立的每個自訂映像重複此步驟。

當應用程式組成為多個容器時 (即多容器應用程式)，您也可以使用 docker-compose up --build 命令，使用相關 docker-compose.yml 檔案公開的中繼資料，以單一命令組建所有相關的映像。

您可以使用 docker images 命令在本機存放庫中尋找現有的映像，如圖 5-6 所示。

![](./media/image9.png)

**圖 5-6。** 使用 docker images 命令檢視現有的映像

### <a name="creating-docker-images-with-visual-studio"></a>使用 Visual Studio 建立 Docker 映像

當您使用 Visual Studio 建立具有 Docker 支援的專案時，您不用明確建立映像。 而是在您按下 F5 執行 docker 化的應用程式或服務時，它會為您建立映像。 此步驟在 Visual Studio 中是自動的，您不會看到它運作，可是知道發生什麼事是很重要的。

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>步驟 4： 組建多容器 Docker 應用程式時，在 docker-compose.yml 中定義您的服務

[Docker compose.yml](https://docs.docker.com/compose/compose-file/) 檔案可讓您定義一組相關服務，部署為具有部署命令的組成應用程式。

若要使用 docker-compose.yml 檔案，您需要使用與下列範例類似的內容，在您的 Main 或根解決方案資料夾中建立檔案：

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

請注意，此 docker-compose.yml 檔案為簡化的合併版本。 它包含每個容器的靜態組態資料 (例如自訂映像的名稱)，這一律會套用，再加上可能相依於部署環境的組態資訊，例如連接字串。 在後列各節中，您會了解如何根據環境和執行類型 (偵錯或發行)，將 docker-compose.yml 組態分割成多個 docker-compose 檔案和覆寫值。

docker-compose.yml 檔案範例會定義四項服務：webmvc 服務 (Web 應用程式)、兩項微服務 (catalog.api 和 ordering.api)，以及 sql.data，一個以 SQL Server for Linux 為基礎執行為容器的資料來源容器。 每項服務都會部署為容器，因此每個都需要 Docker 映像。

docker-compose.yml 檔案指定的不只是使用何種容器，還會指定它們個別設定的方式。 例如，.yml 檔案中的 webmvc 容器定義：

-   使用預先組建的 eshop/web:latest 映像。 不過，您也可以設定映像，讓它組建為 docker-compose 的一部分，附帶以 docker-compose 檔案 build: 區段為基礎的額外組態。

-   初始化兩個環境變數 (CatalogUrl 和 OrderingUrl)。

-   將容器上公開的通訊埠 80 轉送至主機的外部通訊埠 80。

-   使用 depends\_on 設定連結 Web 應用程式與目錄和訂購服務。 這會導致服務一直等候到這些服務啟動。

當我們討論到如何實作微服務和多容器應用程式時，會在後節重新審視 docker-compose.yml 檔案。

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 docker-compose.yml

當如圖 5-7 所示，當您將 Docker 解決方案支援新增至 Visual Studio 解決方案的服務專案時，Visual Studio 會將 Dockerfile 新增至您的專案，而且會在您附 docker-compose.yml 檔案的解決方案中新增服務區段 (專案)。 這是撰寫多容器解決方案的簡單方法。 然後您可以開啟 docker-compose.yml 檔案，更新它們增加其他功能。

![](./media/image6.png)

**圖 5-7**。 以滑鼠右鍵按一下 ASP.NET Core 專案，在 Visual Studio 2017 中新增 Docker 支援

在 Visual Studio 中新增 Docker 支援，不僅會將 Dockerfile 新增至您的專案，還會將組態資訊新增至在解決方案層級設定的數個全域 docker-compose.yml 檔案。

在您將 Docker 支援新增至您的 Visual Studio 解決方案之後，您也會在方案總管中看到包含已新增 docker-compose.yml 檔案的新節點 (在 docker-compose.dcproj 專案檔中)，如圖 5-8 所示。

![](./media/image11.PNG)

**圖 5-8**。 Visual Studio 2017 方案總管中新增的 **docker-compose** 樹狀節點

您可以使用 docker-compose up 命令，單用一個 docker-compose.yml 檔案部署多容器應用程式。 不過，Visual Studio 會新增它們的群組，方便您根據環境 (開發與生產) 和執行類型 (發行與偵錯) 覆寫值。 這項功能會在後列各節中說明。

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>步驟 5： 組建並執行您的 Docker 應用程式

如果您的應用程式只有單一容器，您可以將它部署至您的 Docker 主機 (VM 或實體伺服器) 來執行。 不過，如果您的應用程式包含多項服務，您可以使用單一 CLI 命令 (docker-compose up) 或使用 Visual Studio 將它部署為組成的應用程式，這樣就會在幕後使用該命令。 讓我們看看不同的選項。

### <a name="option-a-running-a-single-container-with-docker-cli"></a>選項 A：以 Docker CLI 執行單一容器

您可以使用 docker run 命令執行 Docker 容器，如圖 5-9 所示：

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**圖 5-9**。 使用 docker run 命令執行 Docker 容器

在本列中，命令會將容器的內部通訊埠 5000 繫結到主機電腦的通訊埠 80。 這表示主機會接聽通訊埠 80 並轉送至容器的通訊埠 5000。

### <a name="option-b-running-a-multi-container-application"></a>選項 B：執行多容器應用程式

在大部分的企業案例中，Docker 應用程式會由多項服務組成，這表示您需要執行多容器應用程式，如圖 5-10 所示。

![](./media/image14.png)

**圖 5-10**。 部署了 Docker 容器的 VM

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>執行使用 Docker CLI 的多容器應用程式

若要執行使用 Docker CLI 的多容器應用程式，您可以執行 docker-compose up 命令。 此命令會使用您在解決方案層級的 docker-compose.yml 檔案來部署多容器應用程式。 圖 5-11 顯示從您的主要專案目錄執行命令的結果，這會包含 docker-compose.yml 檔案。

![](./media/image15.png)

**圖 5-11**。 執行的 docker-compose up 命令的範例結果

執行 docker-compose up 命令之後，應用程式及其相關容器會部署到您的 Docker 主機，如圖 5-10 呈現的 VM 所示。

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>使用 Visual Studio 執行和偵錯多容器應用程式 

使用 Visual Studio 2017 執行多容器應用程式不會比較簡單。 您不能只執行多容器應用程式，還要能夠設定一般中斷點，直接從 Visual Studio 偵錯它所有的容器。

如前所述，每次您將 Docker 解決方案支援新增至解決方案內的專案，就會在全域 (解決方案層級) docker-compose.yml 檔案中設定該專案，這可讓您立即執行或偵錯整個解決方案。 Visual Studio 會為每個啟用 Docker 解決方案支援的專案啟動一個容器，並為您執行所有內部步驟 (dotnet publish、docker build 等等)。

此處的重點是，如圖 5-12 中所示，Visual Studio 2017 另有處理 F5 按鍵動作的 **Docker** 命令。 此選項藉由執行在解決方案層級之 docker-compose.yml 檔案中定義的所有容器，讓您執行或偵錯多容器應用程式。 偵錯多容器解決方案的能力，表示您可以設定多個中斷點，不同的專案 (容器) 各一個中斷點；而從 Visual Studio 偵錯時，您會停在不同專案中定義的中斷點，然後在不同的容器上執行。

![](./media/image16.png)

**圖 5-12**。 在 Visual Studio 2017 中執行多容器應用程式

### <a name="additional-resources"></a>其他資源

-   **將 ASP.NET 容器部署至遠端 Docker 主機**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>測試與部署協調器的注意事項

docker-compose up 和 docker run 命令 (在 Visual Studio 中執行和偵錯容器) 適合在開發環境中測試容器。 但如果您的目標是 Docker 叢集和協調器，像是 Docker Swarm、Mesosphere DC/OS 或 Kubernetes，就不應該使用這種方法。 如果您使用類似 [Docker Swarm 模式](https://docs.docker.com/engine/swarm/)的叢集 (自 Docker CE for Windows 和 Mac 1.12 版起提供)，單一服務就需要使用其他命令部署和測試，例如 [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/)。 如果您要部署由數個容器組成的應用程式，要使用 [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) 和 [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) 將組成的應用程式部署為「堆疊」。 如需詳細資訊，請參閱 Docker 文件的部落格文章 [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) (實驗性分散式應用程式組合簡介)。 在 Docker 網站。

若為 [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) 和 [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/)，您也會使用不同的部署命令和指令碼。

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>步驟 6： 使用本機的 Docker 主機測試您的 Docker 應用程式

此步驟會隨應用程式執行的作業而異。 在部署為單一容器或服務的簡單 .NET Core Web 應用程式中，您可以開啟 Docker 主機上的瀏覽器，瀏覽至該網站存取服務，如圖 5-13 所示。 (如果 Dockerfile 中的組態對應至主機通訊埠 80 以外的容器，包括 URL 中的主機連接埠。)

![](./media/image18.png)

**圖 5-13**。 使用 localhost 在本機測試 Docker 應用程式的範例

如果 localhost 未指向 Docker 主機 IP (根據預設，當使用 Docker CE 時應該會指向 Docker 主機 IP)，請使用您電腦網路卡的 IP 位址巡覽至您的服務。

請注意，瀏覽器中這個 URL 為討論中的特定容器範例使用的是通訊埠 80。 不過，要求在內部會重新導向至通訊埠 5000，因為它是以 docker run 命令如此部署的，如上一個步驟中所述。

您也可以從終端機使用 curl 測試應用程式，如圖 5-14 所示。 在 Windows 的 Docker 安裝中，在您電腦的實際 IP 位址以外，預設的 Docker 主機 IP 一律為 10.0.75.1。

![](./media/image19.png)

**圖 5-14**。 使用 curl 在本機測試 Docker 應用程式的範例

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>使用 Visual Studio 2017 測試和偵錯容器

使用 Visual Studio 2017 執行和偵錯容器時，您可以用和不執行容器時一樣的方式，偵錯 .NET 應用程式。

### <a name="testing-and-debugging-without-visual-studio"></a>不使用 Visual Studio 偵錯和測試

如果您正在使用編輯器/CLI 方法進行開發，偵錯容器會更困難，而且您會想要產生追蹤來偵錯。

### <a name="additional-resources"></a>其他資源

-   **在本機 Docker 容器內偵錯應用程式**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker。使用 Docker 組建、偵錯、部署 ASP.NET Core 應用程式。** 影片。
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>使用 Visual Studio 開發容器時的簡化工作流程

實際上，使用 Visual Studio 時的工作流程時遠比您使用編輯器/CLI 方法更簡單。 Visual Studio 會隱藏或簡化與 Dockerfile 和 docker-compose.yml 檔案有關，為 Docker 所需的大部分步驟，如圖 5-15 所示。

![](./media/image20.png)

**圖 5-15**。 使用 Visual Studio 開發時的簡化工作流程

此外，您只需要執行一次步驟 2 (將 Docker 支援新增至您的專案)。 因此，工作流程類似於您使用 .NET 處理任何其他開發時的一般開發工作。 您需要知道實際狀況 (映像建置程序、使用哪些基底映像、容器部署等等)，有時也需要編輯 Dockerfile 或 docker-compose.yml 檔案以自訂行為。 但使用 Visual Studio 已大幅簡化工作，提高您的產能。

### <a name="additional-resources"></a>其他資源

-   **Steve Lasker。利用 Visual Studio 2017 進行 .NET Docker 開發**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz。將 .NET Core 應用程式放在具備新版適用於 Visual Studio 之 Docker 工具的容器內**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>在 DockerFile 中使用 PowerShell 命令來設定 Windows 容器 

[Windows 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)可讓您將現有的 Windows 應用程式轉換成 Docker 映像，並使用相同的工具將它們部署為 Docker 生態系統的其他部分。 您要在 Dockerfile 中執行 PowerShell 命令才能使用 Windows 容器，如下列範例所示：

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

在本例中，我們使用 Windows Server Core 基底映像 (FROM 設定)，並使用 PowerShell 命令 (RUN 設定) 安裝 IIS。 使用類似的方式，您也可以使用 PowerShell 命令安裝其他元件，例如 ASP.NET 4.x、.NET 4.6 或任何其他 Windows 軟體。 例如，Dockerfile 中的下列命令會安裝 ASP.NET 4.5：

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>其他資源

-   **aspnet-docker/Dockerfile.** 從 dockerfiles 執行範例 Powershell 命令以包含 Windows 功能。
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[上一頁](index.md)
[下一頁](../net-core-single-containers-linux-windows-server-hosts/index.md)
