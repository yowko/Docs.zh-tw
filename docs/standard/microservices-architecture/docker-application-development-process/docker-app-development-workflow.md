---
title: Docker 應用程式的開發工作流程
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 應用程式的開發工作流程
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/05/2018
ms.openlocfilehash: 00cffde7e7eb548f755b60f64aa596210b570d07
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297513"
---
# <a name="development-workflow-for-docker-apps"></a>Docker 應用程式的開發工作流程

應用程式開發生命週期開始於每位開發人員的電腦，開發人員在電腦上使用其偏好的語言撰寫應用程式的程式碼，並於本機上測試。 不論開發人員選擇哪一種語言、架構和平台，只要使用此工作流程，開發人員就一定能開發和測試 Docker 容器，但只能在本機作業。

每個容器 (Docker 映像的執行個體) 包含下列元件：

- 作業系統選取項目 (例如 Linux 發行版本、Windows Nano Server 或 Windows Server Core)。

- 開發人員新增的檔案 (應用程式二進位檔等等)。

- 組態資訊 (環境設定和相依性)。

## <a name="workflow-for-developing-docker-container-based-applications"></a>開發 Docker 容器型應用程式的工作流程

本節描述 Docker 容器型應用程式的「內部迴圈」開發工作流程。 內部迴圈工作流程表示不考慮更廣泛的 DevOps 工作流程，只著重於在開發人員電腦上完成的開發工作。 設定環境的初始步驟不包含在內，因為這些只進行一次。

應用程式是由您自己的服務加上額外的程式庫 (相依性) 所組成。 以下是組建 Docker 應用程式時通常會採用的基本步驟，如圖 5-1 所示。

![開發 Docker 容器化應用程式的逐步工作流程圖表](./media/image1.png)

**圖 5-1。** 開發 Docker 容器化應用程式的逐步工作流程

本指南會詳細說明這整個程序，並針對 Visual Studio 環境說明每個主要步驟。

當您使用編輯器/CLI 開發方法 (例如，Visual Studio Code 加上 macOS 或 Windows 上的 Docker CLI) 時，您需要知道每一個步驟，通常要比使用 Visual Studio 更詳細。 如需在 CLI 環境中操作的詳細資訊，請參閱電子書 [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/)。

如果您使用的是 Visual Studio，系統會替您處理其中許多步驟，這將大幅提升您的生產力。 特別是當您使用 Visual Studio 2017，並以多容器應用程式為目標時。 舉例來說，只要按一下滑鼠，Visual Studio 就會使用您應用程式的組態，將 *Dockerfile* 及 *docker-compose.yml* 檔案新增至您的專案。 當您在 Visual Studio 中執行應用程式時，其會建置 Docker 映像，並直接在 Docker 中執行多容器應用程式。 甚至可讓您同時對多個容器進行偵錯。 這些功能將大幅提高您的開發速度。

在後續的指引中，我們將解釋 Docker 究竟如何運作。

![步驟 1 - 撰寫您的應用程式圖表](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>步驟 1： 開始撰寫程式碼，並建立您的初始應用程式或服務比較基準

開發 Docker 應用程式類似於不使用 Docker 開發應用程式的方式。 差別在於，開發 Docker 時，您要在本機環境中部署並測試 Docker 容器內執行的應用程式或服務。 容器可以是 Linux 容器或 Windows 容器。

### <a name="set-up-your-local-environment-with-visual-studio"></a>設定使用 Visual Studio 的本機環境

開始前，請確定您已安裝 [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows，如下列指示所述：

[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/) (開始使用 Docker CE for Windows)

此外，您還需要安裝了 **.NET Core 跨平台開發**工作負載的 Visual Studio 2017，如圖 5-2 所示。

![](./media/image3.png)

**圖 5-2**。 在 Visual Studio 2017 安裝期間選取 [.NET Core and Docker] 工作負載

您甚至可以在於您的應用程式中啟用 Docker，並在 Docker 中部署與測試之前，只使用 .NET 開始撰寫應用程式程式碼 (如果您打算使用容器通常會使用 .NET Core)。 不過，建議您盡快開始使用 Docker，因為它會成為實際環境，可以盡快發現任何問題。 我們建議您這樣做，因為 Visual Studio 能夠輕易與 Docker 搭配運作，幾乎暢行無阻 - 最好的例子就是透過 Visual Studio 對多容器應用程式進行偵錯。

### <a name="additional-resources"></a>其他資源

- **Get started with Docker CE for Windows** (開始使用 Docker CE for Windows)

   [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

- **Visual Studio 2017**

   [*https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![步驟 2 - 寫入 Dockerfile 圖表](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>步驟 2： 建立與現有 .NET 基底映像有關的 Dockerfile

每個您想建置的自訂映像都需要 Dockerfile；且不論您是從 Visual Studio 自動部署或使用 Docker CLI (docker run 及 docker-compose 命令) 手動部署，每個要部署的容器也都需要 Dockerfile。 如果您的應用程式包含單一的自訂服務，您需要單一的 Dockerfile。 如果您的應用程式包含多項服務 (如微服務架構)，每項服務都需要一個 Dockerfile。

Dockerfile 放在您應用程式或服務的根資料夾中。 它包含告訴 Docker 如何設定及執行容器中應用程式或服務的命令。 您可以使用程式碼手動建立 Dockerfile，將它與您的 .NET 相依性一起新增至您的專案。

有了 Visual Studio Tools for Docker，這項工作只須按幾下滑鼠即可完成。 當您在 Visual Studio 2017 中建立新專案時，會有一個名為 [啟用 Docker 支援] 的選項，如圖 5-3 所示。

![在 Visual Studio 2017 中建立新專案時啟用 Docker 支援](./media/image5.png)

**圖 5-3**。 在 Visual Studio 2017 中建立新專案時啟用 Docker 支援

您也可以在現有的 .NET Core Web 應用程式專案上啟用 Docker 支援，方法是以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [新增] > [Docker 支援]，如圖 5-4 所示。

![在 Visual Studio 中新增 Docker 支援功能表選項](./media/add-docker-support.png)

**圖 5-4**。 在現有的 Visual Studio 2017 專案中啟用 Docker 支援

這個動作會將具有所需組態的 *Dockerfile* 新增至專案，而且只能在 .NET Core Web 應用程式專案上使用。

若要為整個解決方案新增 *docker-compose.yml* 檔案，請以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [新增] > [容器協調器支援]，如圖 5-5 所示。

![在 Visual Studio 中新增容器協調器支援功能表選項](./media/add-container-orchestrator-support.png)

**圖 5-5**。 將容器協調器支援新增至 Visual Studio 2017 中的現有專案。

在下列章節中，我們會說明這些檔案每一個的詳細資訊。 Visual Studio 可以為您執行這項工作，但深入了解 Dockerfile 會很有幫助。

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>選項 A：使用現有的官方 .NET Docker 映像建立專案

您通常會在基底映像的基礎上，為您的容器組建自訂映像，此基底映像可從 [Docker Hub](https://hub.docker.com/) 登錄的官方存放庫制取得。 這就是當您在 Visual Studio 中啟用 Docker 支援時，實際發生的狀況。 Dockerfile 使用現有的 aspnetcore 映像。

前文曾說明您可以使用的 Docker 映像和存放庫，視您選擇的架構和作業系統而定。 例如，如果您想要使用 ASP.NET Core (Linux 或 Windows)，則要使用的映像就是 microsoft/aspnetcore:2.0。 因此，您只需要指定要為容器使用的基底 Docker 映像。 將 FROM microsoft/aspnetcore:2.0 新增至您的 Dockerfile 即可完成此作業。 Visual Studio 會自動執行此作業，但如果您更新該版本，同時也會更新該值。

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

在本例中，容器是以 2.0 版的官方 ASP.NET Core Docker 映像為基礎 (適用於 Linux 和 Windows 的多架構)。 這是 `FROM microsoft/aspnetcore:2.0` 設定。 (如需這個基底映像的詳細資訊，請參閱 [ASP.NET Core Docker 映像](https://hub.docker.com/r/microsoft/aspnetcore/)頁面及 [.NET Core Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)頁面。)在 Dockerfile 中，您也需要指示 Docker 接聽您會在執行階段使用的 TCP 通訊埠 (本例中為通訊埠 80，如 EXPOSE 設定的設定)。

您可在 Dockerfile 中指定其他的組態設定，視您使用的語言和架構而定。 例如，ENTRYPOINT 行中有 \["dotnet"，"MySingleContainerWebApp.dll"\] 會指示 Docker 執行 .NET Core 應用程式。 如果您使用 SDK 和 .NET Core CLI (dotnet CLI) 組建及執行 .NET 應用程式，此項設定會有所不同。 重點是 ENTRYPOINT 行與其他設定會不一樣，視您選擇的應用程式語言和平台而定。

### <a name="additional-resources"></a>其他資源

- **建置 .NET Core 應用程式的 Docker 映像**

   [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

- **組建您自己的映像**. 在正式 Docker 文件中。

   [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>使用多架構映像存放庫

一個存放庫可以包含多種平台變化，例如 Linux 映像和 Windows 映像。 這項功能可讓像 Microsoft (基底映像建立者) 這樣的廠商建立單一存放庫以涵蓋多個平台 (即 Linux 和 Windows)。 例如，Docker Hub 登錄提供的 [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) 存放庫，會使用相同的存放庫名稱提供 Linux 和 Windows Nano Server 支援。

如果您指定標籤，如下列案例一樣明確鎖定平台：

- **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux

- **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

但如果您指定相同的映像名稱，甚至是使用相同的標籤，新的多架構映像 (例如支援多架構的 aspnetcore 映像) 將會根據您目前部署的 Docker 主機 OS 使用 Linux 或 Windows 版本，這是 2017 年中以來的新功能，如下列範例所示：

- **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

如此一來，當您從 Windows 主機提取映像時，它會提取 Windows variant，而從 Linux 主機提取相同的映像名稱則會提取 Linux variant。

### <a name="option-b-creating-your-base-image-from-scratch"></a>選項 B：建立全新的基底映像

您可以從頭開始建立您自己的 Docker 基底映像。 Docker 新手不建議此方案，但如果您想要設定專屬基底映像的特點，您可以這樣做。

### <a name="additional-resources"></a>其他資源

- **多架構 .NET Core 映像**。

   https://github.com/dotnet/announcements/issues/14

- **建立基底映像**。 正式 Docker 文件。

   [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![步驟 3 - 建立映像圖表](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>步驟 3： 建立您的自訂 Docker 映像並在其中內嵌您的應用程式或服務

您需要為應用程式中的每項服務建立相關的映像。 如果您的應用程式組成為單一的服務或 Web 應用程式，您只需要單一映像。

Docker 映像會自動在 Visual Studio 中替您建置。 只有編輯器/CLI 工作流程需要下列步驟，我們會清楚說明發生的狀況。

您身為開發人員，需要在本機上開發和測試，直到完成原始檔控制系統 (例如 GitHub) 的完整功能或變更。 這表示，您需要建立 Docker 映像，將容器部署到本機的 Docker 主機 (Windows 或 Linux VM) 並執行、測試及偵錯這些本機容器。

若要使用 Docker CLI 及您的 Dockerfile 在本機環境中建立自訂映像，您可以使用 docker build 命令，如圖 5-5 所示。

![建立自訂的 Docker 映像](./media/image8.png)

**圖 5-5**。 建立自訂的 Docker 映像

除了直接從專案資料夾執行 docker build 以外，您可以選擇執行 dotnet publish，這樣就能使用所需的 .NET 程式庫及二進位先產生可部署的資料夾，再使用 docker build 命令。

這會建立一個名為 **cesardl/netcore-webapi-microservice-docker:first** 的 Docker 映像。 本例中的 :first 是代表特定版本的標籤。 您可以為組成 Docker 應用程式所需建立的每個自訂映像重複此步驟。

當應用程式組成為多個容器時 (即多容器應用程式)，您也可以使用 docker-compose up --build 命令，使用相關 docker-compose.yml 檔案公開的中繼資料，以單一命令組建所有相關的映像。

您可以使用 docker images 命令在本機存放庫中尋找現有的映像，如圖 5-6 所示。

![使用 docker images 命令檢視現有映像](./media/image9.png)

**圖 5-6。** 使用 docker images 命令檢視現有的映像

### <a name="creating-docker-images-with-visual-studio"></a>使用 Visual Studio 建立 Docker 映像

當您使用 Visual Studio 建立具有 Docker 支援的專案時，不用明確地建立映像。 反之，當您按 **F5** 執行 Docker 化的應用程式或服務時，就會為您建立映像。 雖然這個步驟會在 Visual Studio 中自動執行，而不會在您眼前發生，但知道背後情況也相當重要。

![步驟 4 - 定義服務圖表](./media/image10.png)

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

此 docker-compose.yml 檔案為簡化的合併版本。 它包含每個容器的靜態組態資料 (例如自訂映像的名稱)，這一律會套用，再加上可能相依於部署環境的組態資訊，例如連接字串。 在後列各節中，您會了解如何根據環境和執行類型 (偵錯或發行)，將 docker-compose.yml 組態分割成多個 docker-compose 檔案和覆寫值。

docker-compose.yml 檔案範例會定義四項服務：webmvc 服務 (Web 應用程式)、兩項微服務 (catalog.api 和 ordering.api)，以及 sql.data，一個以 SQL Server for Linux 為基礎執行為容器的資料來源容器。 每項服務都會部署為容器，因此每個都需要 Docker 映像。

docker-compose.yml 檔案指定的不只是使用何種容器，還會指定它們個別設定的方式。 例如，.yml 檔案中的 webmvc 容器定義：

- 使用預先組建的 eshop/web:latest 映像。 不過，您也可以設定映像，讓它組建為 docker-compose 的一部分，附帶以 docker-compose 檔案 build: 區段為基礎的額外組態。

- 初始化兩個環境變數 (CatalogUrl 和 OrderingUrl)。

- 將容器上公開的通訊埠 80 轉送至主機的外部通訊埠 80。

- 使用 depends\_on 設定連結 Web 應用程式與目錄和訂購服務。 這會導致服務一直等候到這些服務啟動。

當我們討論到如何實作微服務和多容器應用程式時，會在後節重新審視 docker-compose.yml 檔案。

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>在 Visual Studio 2017 中使用 docker-compose.yml

當您將容器協調器支援新增至 Web 應用程式專案時 (如圖 5-7 所示)，Visual Studio 會在包含 docker-compose.yml 檔案的解決方案中新增服務區段 (專案)。 這是開始撰寫多容器解決方案的簡單方法。

![在 Visual Studio 中新增容器協調器支援功能表項目](./media/add-container-orchestrator-support.png)

**圖 5-7**。 以滑鼠右鍵按一下 ASP.NET Core 專案，在 Visual Studio 2017 中新增 Docker 支援

新增容器協調器支援會將 Dockerfile 新增至您的專案 (如果其尚未存在)。 該動作也會將組態資訊新增至解決方案層級的全域 docker-compose.yml 檔案。 您將會在包含 docker-compose.yml 檔案的**方案總管**中看見新的專案節點 (*docker-compose.dcproj* 專案檔)，如圖 5-8 所示。

![方案總管中的 docker-compose 節點](./media/docker-compose-files.png)

**圖 5-8**。 Visual Studio 2017 方案總管中新增的 **docker-compose** 樹狀節點

然後您可以開啟 docker-compose.yml 檔案並予以更新，以增加功能。

您可以透過 `docker-compose up` 命令來使用單一 docker-compose.yml 檔案部署多容器應用程式。

![步驟 5 - 執行應用程式圖表](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>步驟 5： 組建並執行您的 Docker 應用程式

如果您的應用程式只有單一容器，您可以將它部署至您的 Docker 主機 (VM 或實體伺服器) 來執行。 但如果您的應用程式包含多個服務，您可以使用單一 CLI 命令 (docker-compose up) 將其部署為組成應用程式，也可以使用 Visual Studio 來部署，其會在幕後使用該命令。 讓我們看看不同的選項。

### <a name="option-a-run-a-single-container-app"></a>選項 A：執行單一容器應用程式

#### <a name="docker-cli"></a>Docker CLI

您可以使用 docker run 命令來執行 Docker 容器，如圖 5-9 所示：

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![使用 docker run 命令執行 Docker 容器](./media/image13.png)

**圖 5-9**。 使用 docker run 命令執行 Docker 容器

在本列中，命令會將容器的內部通訊埠 5000 繫結到主機電腦的通訊埠 80。 這表示主機會接聽通訊埠 80 並轉送至容器的通訊埠 5000。

#### <a name="visual-studio"></a>Visual Studio

如果您尚未新增容器協調器支援，您也可以按 **F5** 來在 Visual Studio 中執行單一容器應用程式。 容器使用 docker run 於本機上執行。

### <a name="option-b-run-a-multi-container-app"></a>選項 B：執行多容器應用程式

在大部分的企業案例中，Docker 應用程式會由多項服務組成，這表示您需要執行多容器應用程式，如圖 5-10 所示。

![顯示部署了 Docker 容器的 VM 圖表](./media/image14.png)

**圖 5-10**。 部署了 Docker 容器的 VM

#### <a name="docker-cli"></a>Docker CLI

若要執行使用 Docker CLI 的多容器應用程式，您可以執行 docker-compose up 命令。 此命令會使用您在解決方案層級的 docker-compose.yml 檔案來部署多容器應用程式。 圖 5-11 顯示從您的主要專案目錄執行命令的結果，這會包含 docker-compose.yml 檔案。

![執行的 docker-compose up 命令的範例結果](./media/image15.png)

**圖 5-11**。 執行的 docker-compose up 命令的範例結果

在執行 docker-compose up 命令後，應用程式及其相關容器便已部署至您的 Docker 主機。

#### <a name="visual-studio"></a>Visual Studio

使用 Visual Studio 2017 執行多容器應用程式非常簡單。 您不只能執行多容器應用程式，還能藉由設定一般中斷點，直接從 Visual Studio 對其所有容器偵錯。

如前所述，每次您將容器協調器支援新增至解決方案中的專案時，該專案都會在全域 (解決方案層級) docker-compose.yml 檔案中設定，如此可讓您一次執行整個解決方案或對其偵錯。 Visual Studio 會為每個啟用 Docker 解決方案支援的專案啟動一個容器，並為您執行所有內部步驟 (dotnet publish、docker build 等)。

此處的重點是，Visual Studio 2017 中有 **F5** 按鍵動作的額外 **Docker** 命令，如圖 5-12 所示。 此選項藉由執行在解決方案層級之 docker-compose.yml 檔案中定義的所有容器，讓您執行或偵錯多容器應用程式。 偵錯多容器解決方案的能力，表示您可以設定多個中斷點，不同的專案 (容器) 各一個中斷點；而從 Visual Studio 偵錯時，您會停在不同專案中定義的中斷點，然後在不同的容器上執行。

![在 Visual Studio 2017 中執行多容器應用程式](./media/image16.png)

**圖 5-12**。 在 Visual Studio 2017 中執行多容器應用程式

### <a name="additional-resources"></a>其他資源

-  **將 ASP.NET 容器部署至遠端 Docker 主機**

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>測試與部署協調器的注意事項

Docker-compose up 及 docker run 命令 (或在 Visual Studio 中執行容器及對其偵錯) 適用於在您的開發環境中測試容器。 但如果您的目標是 Docker 叢集和協調器，像是 Docker Swarm、Mesosphere DC/OS 或 Kubernetes，就不應該使用這種方法。 如果您使用類似 [Docker Swarm 模式](https://docs.docker.com/engine/swarm/)的叢集 (自 Docker CE for Windows 和 Mac 1.12 版起提供)，單一服務就需要使用其他命令部署和測試，例如 [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/)。 如果您要部署由數個容器組成的應用程式，要使用 [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) 和 [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) 將組成的應用程式部署為「堆疊」。 如需詳細資訊，請參閱 Docker 文件的部落格文章 [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) (實驗性分散式應用程式組合簡介)。 在 Docker 網站。

若為 [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) 和 [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/)，您也會使用不同的部署命令和指令碼。

![步驟 6 圖表](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>步驟 6： 使用本機的 Docker 主機測試您的 Docker 應用程式

此步驟會隨應用程式執行的作業而異。 在部署為單一容器或服務的簡單 .NET Core Web 應用程式中，您可以藉由在 Docker 主機上開啟瀏覽器並瀏覽至該網站來存取服務，如圖 5-13 所示。 (如果 Dockerfile 中的組態對應至主機通訊埠 80 以外的容器，包括 URL 中的主機連接埠。)

![使用 localhost 在本機測試 Docker 應用程式的範例](./media/image18.png)

**圖 5-13**。 使用 localhost 在本機測試 Docker 應用程式的範例

如果 localhost 未指向 Docker 主機 IP (根據預設，當使用 Docker CE 時應該會指向 Docker 主機 IP)，請使用您電腦網路卡的 IP 位址巡覽至您的服務。

此瀏覽器中的 URL 針對討論中的特定容器範例使用連接埠 80。 不過，要求在內部會重新導向至通訊埠 5000，因為它是以 docker run 命令如此部署的，如上一個步驟中所述。

您也可以從終端機使用 curl 測試應用程式，如圖 5-14 所示。 在 Windows 的 Docker 安裝中，在您電腦的實際 IP 位址以外，預設的 Docker 主機 IP 一律為 10.0.75.1。

![使用 curl 在本機測試 Docker 應用程式的範例](./media/image19.png)

**圖 5-14**。 使用 curl 在本機測試 Docker 應用程式的範例

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>使用 Visual Studio 2017 測試和偵錯容器

使用 Visual Studio 2017 執行和偵錯容器時，您可以用和不執行容器時一樣的方式，偵錯 .NET 應用程式。

### <a name="testing-and-debugging-without-visual-studio"></a>不使用 Visual Studio 偵錯和測試

如果您正在使用編輯器/CLI 方法進行開發，偵錯容器會更困難，而且您會想要產生追蹤來偵錯。

### <a name="additional-resources"></a>其他資源

- **對本機 Docker 容器中的應用程式偵錯**

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- **Steve Lasker。使用 Docker 組建、偵錯、部署 ASP.NET Core 應用程式。** 影片。

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>使用 Visual Studio 開發容器時的簡化工作流程

實際上，使用 Visual Studio 時的工作流程時遠比您使用編輯器/CLI 方法更簡單。 Visual Studio 會隱藏或簡化與 Dockerfile 和 docker-compose.yml 檔案有關，為 Docker 所需的大部分步驟，如圖 5-15 所示。

![使用 Visual Studio 開發時的簡化工作流程](./media/image20.png)

**圖 5-15**。 使用 Visual Studio 開發時的簡化工作流程

此外，您只需要執行一次步驟 2 (將 Docker 支援新增至您的專案)。 因此，工作流程類似於您使用 .NET 處理任何其他開發時的一般開發工作。 您需要知道實際狀況 (映像建置程序、使用哪些基底映像、容器部署等等)，有時也需要編輯 Dockerfile 或 docker-compose.yml 檔案以自訂行為。 但使用 Visual Studio 已大幅簡化工作，提高您的產能。

### <a name="additional-resources"></a>其他資源

- **Steve Lasker。使用Visual Studio 2017 進行.NET Docker 開發**

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

- **Jeffrey T. Fritz。使用新的 Docker Tools for Visual Studio 將 .NET Core 應用程式放入容器**

   [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>在 DockerFile 中使用 PowerShell 命令來設定 Windows 容器

[Windows 容器](/virtualization/windowscontainers/about/)可讓您將現有的 Windows 應用程式轉換成 Docker 映像，並使用相同的工具將它們部署為 Docker 生態系統的其他部分。 您要在 Dockerfile 中執行 PowerShell 命令才能使用 Windows 容器，如下列範例所示：

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

- **aspnet-docker/Dockerfile.** 從 dockerfiles 執行範例 Powershell 命令以包含 Windows 功能。

   [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[上一頁](index.md)
[下一頁](../net-core-single-containers-linux-windows-server-hosts/index.md)