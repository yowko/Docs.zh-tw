---
title: "Docker 應用程式的開發工作流程"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Docker 應用程式的開發工作流程"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5a53aee4261a5a0bfc25b3520c50cf505b84f287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="development-workflow-for-docker-apps"></a>Docker 應用程式的開發工作流程

應用程式開發週期開始執行每個開發人員的電腦，其中代碼使用其偏好的語言的應用程式開發人員，並在本機測試它。 不論哪一個語言、 架構和開發人員選擇，此工作流程中，平台開發人員是一律開發和測試 Docker 容器，但是，在本機。

每個容器 （Docker 映像的執行個體） 包含下列元件：

-   作業系統選擇 （例如 Linux 散發套件、 Windows Nano Server 或 Windows Server Core）。

-   開發人員 （應用程式二進位檔等等） 所加入的檔案。

-   （環境設定和相依性） 的組態資訊。

## <a name="workflow-for-developing-docker-container-based-applications"></a>工作流程開發 Docker 容器為基礎的應用程式

本章節描述*內部迴圈*Docker 容器基礎的應用程式的開發工作流程。 內部迴圈的工作流程表示它不考慮到更廣泛的 DevOps 工作流程，並只著重於開發人員的電腦上完成的開發工作。 設定環境的初始步驟不包含在內，因為這些只進行一次。

應用程式是由您的服務，再加上額外的程式庫 （相依性） 所組成。 以下是您通常會採用建置 Docker 應用程式的說明圖 5-1 的基本步驟。

![](./media/image1.png)

**圖 5-1。** 供開發 Docker 容器化應用程式的逐步工作流程

在本指南中，這整個程序中有詳細說明，每個主要步驟，說明把焦點放在 Visual Studio 環境。

當使用編輯器/CLI 開發方法 （例如，Visual Studio Code 加上 macOS 上的 Docker CLI 或 Windows） 時，您需要知道每個步驟中，通常比使用 Visual Studio 的更多詳細資料中。 如需 CLI 環境中工作的詳細資訊，請參閱電子書[與 Microsoft 平台和工具的 Docker 容器化應用程式生命週期](http://aka.ms/dockerlifecycleebook/)。

當您使用 Visual Studio 2015 或 Visual Studio 2017 時，許多個步驟會為您處理，這會大幅增加產能。 當您使用 Visual Studio 2017，而目標多個容器應用程式，這是特別有用。 比方說，只在一個滑鼠按一下 Visual Studio 將 Dockerfile 並 docker compose.yml 檔案加入您的專案與您的應用程式的組態。 當您在 Visual Studio 中執行應用程式時，建立 Docker 映像和直接在 Docker; 中執行多個容器應用程式即使可讓您一次偵錯數個容器。 這些功能可大幅提高開發速度。

不過，因為 Visual Studio 會自動執行這些步驟並不表示您不需要知道發生什麼事使用 Docker 在下方。 因此，會遵循的指導方針，在我們詳細說明每個步驟。

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>步驟 1： 開始撰寫程式碼，並建立您的初始應用程式或服務比較基準

開發 Docker 應用程式是您開發應用程式沒有 Docker 的方式類似。 差別在於，在開發 Docker 時，會在部署並測試您的應用程式或服務在本機環境中的 Docker 容器內執行。 容器可以 Linux 容器或 Windows 容器。

### <a name="set-up-your-local-environment-with-visual-studio"></a>設定 Visual Studio 中的本機環境

若要開始，請確定您有[Docker Community Edition (CE)](https://www.docker.com/community-edition)適用於 Windows 的安裝，在下列指示中所述：

[開始使用 Docker CE for Windows](https://docs.docker.com/docker-for-windows/)

此外，您必須安裝 Visual Studio 2017。 這是慣用透過 Visual Studio 2015 與 Visual Studio Tools for Docker 增益集，因為 Visual Studio 2017 具有較進階的 Docker，像是支援偵錯容器的支援。 Visual Studio 2017 包含對 Docker 的工具，如果您選取**.NET Core 和 Docker**在安裝期間，如圖 5-2 所示的工作負載。

![](./media/image3.png)

**圖 5-2**。 選取**.NET Core 和 Docker**在 Visual Studio 2017 安裝期間的工作負載

您可以開始撰寫程式碼中 （通常是在.NET Core 如果您打算使用容器) 的一般.NET 應用程式之前在您的應用程式中啟用 Docker 並部署與測試在 Docker 中。 不過，建議您開始使用 Docker 儘速，因為它即是對真實環境，而且可以儘速發現任何問題。 這因為 Visual Studio 會很容易使用，它幾乎感覺透明 Docker 我們鼓勵 — 從 Visual Studio 的多個容器應用程式進行偵錯時的最佳範例。

### <a name="additional-resources"></a>其他資源

-   **開始使用 Docker CE for Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>步驟 2： 建立 Dockerfile，與現有.NET 基底映像

您想要建置; 每個自訂映像所需 Dockerfile。您也需要針對每個容器 Dockerfile 供部署，是否自動部署從 Visual Studio 或以手動方式使用 Docker CLI (執行 docker 和 docker-撰寫命令)。 如果您的應用程式包含單一的自訂服務，您需要單一 Dockerfile。 如果您的應用程式包含多個服務 （如同 microservices 架構），您需要一個 Dockerfile 每個服務。

Dockerfile 被放在應用程式或服務的根資料夾中。 它包含告訴 Docker 如何設定及執行應用程式或服務的容器中的命令。 您可以手動在程式碼中建立了 Dockerfile，並將它加入至您的專案中，您的.NET 相依性。

使用 Visual Studio 和其 tools for Docker，這項工作需要只按幾下滑鼠。 當您在 Visual Studio 2017 中建立新的專案時，名為一個選項是**啟用容器 (Docker) 支援**，如圖 5-3 所示。

![](./media/image5.png)

**圖 5-3**。 在 Visual Studio 2017 中建立新的專案時，啟用 Docker 支援

您也可以以滑鼠右鍵按一下您的專案檔，Visual Studio 中選取的選項來啟用新的或現有的專案上的 Docker 支援**新增 Docker 專案支援**，如圖 5-4 所示。

![](./media/image6.png)

**圖 5-4**。 啟用在現有的 Visual Studio 2017 專案的 Docker 支援

此動作 （例如 ASP.NET Web 應用程式或 Web API 服務） 的專案上將所需的設定與專案的 Dockerfile。 它也會加入整個方案的 docker compose.yml 檔案。 在下列章節中，我們將說明每個這些檔案會進入資訊。 Visual Studio 可以執行這項工作，但有助於您了解什麼進入 Dockerfile。

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>選項 a： 建立專案，使用現有的官方.NET Docker 映像

通常打造您的容器，您可以從官方儲存機制取得基底映像之上的自訂映像[Docker Hub](https://hub.docker.com/)登錄。 明確地說是當您啟用在 Visual Studio 中的 Docker 支援時，實際上會發生什麼事。 Dockerfile 會使用現有 aspnetcore 映像。

我們稍早說明的 Docker 映像和儲存機制，您可以使用，根據的架構和您所選擇的 OS。 比方說，如果您想要使用 ASP.NET Core （Linux 或 Windows），使用的影像是 microsoft / aspnetcore:2.0。 因此，您只需要指定何種基底的 Docker 映像將對您的容器。 您執行此動作將從 microsoft / aspnetcore:2.0 至 Dockerfile。 這將會自動執行 Visual Studio 中，但如果您要更新的版本，您必須更新此值。

使用一個版本號碼從 Docker Hub 官方.NET 映像儲存機制可確保可以相同的語言功能 （包括開發、 測試和生產環境） 的所有電腦上。

下列範例顯示範例 Dockerfile ASP.NET Core 容器。

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

在此情況下，容器根據 2.0 版的官方 ASP.NET Core Docker 映像 (適用於 Linux 和 Windows 多 arch)。 這是設定`FROM microsoft/aspnetcore:2.0`。 (如需此基底映像進一步詳細資訊，請參閱[ASP.NET Core Docker 映像](https://hub.docker.com/r/microsoft/aspnetcore/)頁面和[.NET Core Docker 映像](https://hub.docker.com/r/microsoft/dotnet/)頁面。)在 Dockerfile 中，您也需要會指示 Docker 以在您將會在執行階段 （在此情況下，連接埠 80，公開設定的設定） 使用的 TCP 連接埠上接聽。

在 Dockerfile 中，視語言和您使用的架構而定，您可以指定其他組態設定。 比方說，使用的進入點列\["dotnet"，"MySingleContainerWebApp.dll"\]告訴 Docker 執行.NET Core 應用程式。 如果您會建置並執行.NET 應用程式使用 SDK 和.NET 核心 CLI (dotnet CLI)，此設定會在不同。 營收是進入點線及其他設定將會根據您選擇您的應用程式之語言與平台而不同。

### <a name="additional-resources"></a>其他資源

-   **.NET Core 應用程式的建置 Docker Images**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)

-   **建置您自己的映像**。 中的正式的 Docker 文件。
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>使用多重 arch 映像儲存機制

單一儲存機制可以包含平台的變異，例如 Linux 映像和 Windows 映像。 這項功能可讓廠商像 Microsoft （基底映像建立者） 建立的單一儲存機制以涵蓋多個平台 （這是 Linux 和 Windows）。 例如， [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) Docker Hub 登錄中的儲存機制使用相同的儲存機制名稱提供適用於 Linux 和 Windows Nano Server 的支援。

如果您指定的標籤，以明確的平台為目標喜歡在下列情況：

-   **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

但是，這是新自 mid 2017，如果您指定相同的映像名稱，即使使用相同的標記，新的多 arch 映像 （例如可支援多 arch aspnetcore 映像） 都會使用 Linux 或 Windows 版本視您要部署的 Docker 主機 OS如下列範例所示：

-   **microsoft / aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

如此一來，當您從 Windows 主機提取映像時，它會提取 Windows 的變體，並從 Linux 主機提取相同的映像名稱將會提取 Linux variant。

### <a name="option-b-creating-your-base-image-from-scratch"></a>選項 b： 建立您從頭的基底映像

您可以從頭開始建立您自己的 Docker 基底映像。 這種情況下不建議在開始使用 Docker，向其他人要求，但如果您想要設定特定的位元基底映像，您可以這樣做。

### <a name="additional-resources"></a>其他資源

-   **多重 arch.NET Core 映像**。
https://github.com/dotnet/announcements/issues/14 
-   **建立基底映像**。 官方 Docker 文件集。
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>步驟 3： 建立自訂的 Docker 映像並將應用程式或服務內嵌在其中

每個服務應用程式中，您需要建立相關的映像。 如果您的應用程式所組成的單一服務或 web 應用程式，您只需要單一映像。

請注意，Docker 映像會自動為您建立 Visual Studio 中。 下列步驟只會需要編輯器/CLI 工作流程，而且時會發生的情況下說明為了清楚起見。

您身為開發人員，需要開發和測試推入完成之前，在本機功能或變更為您的原始檔控制系統，（例如，若要 GitHub)。 這表示您要建立 Docker 映像並部署到本機的 Docker 主機 （Windows 或 Linux VM） 的容器和執行、 測試及偵錯對這些本機的容器。

若要使用 Docker CLI 和 Dockerfile，本機環境中建立自訂映像，您可以使用 docker 建置命令，如圖 5-5。

![](./media/image8.png)

**圖 5-5**。 建立自訂的 Docker 映像

（選擇性） 而不是直接執行 docker 建置專案資料夾中，您可以先產生所需的.NET 程式庫的部署資料夾並執行 dotnet 二進位檔發行，然後使用 docker 建置命令。

這將使用名稱 cesardl/netcore-webapi-微服務建立 Docker 映像-docker： 第一個。 在此情況下，： 第一個是代表特定版本的標記。 您可以重複此步驟，針對每個您需要建立 Docker 應用程式組成的自訂映像。

當應用程式由多個容器 （也就是說，它位於多個容器應用程式），您也可以使用 docker 撰寫向上-建置命令，以建置使用公開中相關的中繼資料的所有相關的映像使用單一命令docker compose.yml 檔案。

您可以找到現有的映像在本機儲存機制使用 docker 映像的命令，如圖 5-6 所示。

![](./media/image9.png)

**圖 5-6。** 檢視現有的映像使用 docker 映像的命令

### <a name="creating-docker-images-with-visual-studio"></a>使用 Visual Studio 中建立 Docker 映像

當您使用 Visual Studio 建立專案與 Docker 的支援時，您未明確建立映像。 相反地，建立映像，當您按下 F5，並執行 dockerized 應用程式或服務。 此步驟會自動在 Visual Studio 中，但將不會看到它，就可能發生，請務必確定您知道發生什麼事的下方。

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>步驟 4： 建立多個容器 Docker 應用程式時，docker compose.yml 中定義您的服務

[Docker compose.yml](https://docs.docker.com/compose/compose-file/)檔案可讓您定義一組部署為組成的應用程式部署命令的相關服務。

若要使用 docker compose.yml 檔案，您需要使用類似於下列範例中的內容建立根方案資料夾中的檔案在您的 main 中：

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

請注意，此 docker compose.yml 檔案之簡化且合併版本。 它包含靜態設定的每個容器 （例如自訂映像的名稱），這會一律套用再加上可能會取決於部署環境，例如連接字串的組態資訊的資料。 在稍後的章節裡，您將學習分割成多個 docker compose.yml 組態的方式 docker 撰寫的檔案和覆寫值，視環境和執行的類型 （偵錯或發行） 而定。

Docker compose.yml 檔案範例會定義五個服務： webmvc 服務 （web 應用程式）、 兩個 microservices （catalog.api 和 ordering.api） 和一個資料來源容器，sql.data，根據適用於 Linux 的容器執行的 SQL Server。 每個服務會部署為容器，因此 Docker 映像需要每個。

Docker compose.yml 檔案會指定使用何種容器，不僅個別設定方式。 比方說，webmvc 容器會定義.yml 檔案中：

-   使用預先建置的資格 / web： 最新的映像。 不過，您也可以設定要建置的一部分的映像 docker 撰寫額外的組態執行根據組建： docker-compose 檔案 > 一節。

-   初始化兩個環境變數 （CatalogUrl 和 OrderingUrl）。

-   將轉送公開的連接埠 80 上的容器主機上的外部連接埠 80。

-   連結的 web 應用程式類別目錄和排序服務相依\_上設定。 這會導致等候，直到這些服務都已啟動服務。

我們將討論如何實作 microservices 和多個容器應用程式時，我們會重新審視 docker compose.yml 檔案，在稍後的章節。

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>使用 docker-compose.yml 在 Visual Studio 2017

當如圖 5-7 所示，您可以新增至服務專案在 Visual Studio 方案中的 Docker 解決方案支援時，Visual Studio 將您的專案，加入了 Dockerfile，並在方案中新增服務 > 一節 （專案） docker compose.yml 檔案。 它是簡單的方法，撰寫您的多個容器解決方案。 您可以開啟 docker compose.yml 檔案並加以更新與其他功能。

![](./media/image6.png)

**圖 5-7**。 在 Visual Studio 2017 新增 Docker 的支援，以滑鼠右鍵按一下 ASP.NET Core 專案

Visual Studio 中加入 Docker 支援 Dockerfile 加入您的專案，不僅會在解決方案層級設定的數個通用的 docker compose.yml 檔案中加入組態資訊。

Docker 的支援加入至您在 Visual Studio 中的方案之後，您也會看到新的節點 （docker compose.dcproj 專案檔中） 包含已新增的 docker compose.yml 檔案，如圖 5-8 所示的方案總管 中。

![](./media/image11.PNG)

**圖 5-8**。 **Docker 撰寫**加入 Visual Studio 2017 方案總管 中的樹狀節點

您可以使用單一的 docker compose.yml 檔案部署多個容器應用程式使用 docker 撰寫 up 命令。 不過，Visual Studio 會加入其中的群組讓您可以覆寫值取決於環境 （與實際執行的程式開發） 和執行類型 （與偵錯版本）。 這項功能將在稍後的章節中說明。

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>步驟 5： 建置並執行您的 Docker 應用程式

如果您的應用程式只有單一容器，您可以將它部署至您的 Docker 主機 （VM 或實體伺服器） 來執行。 不過，如果您的應用程式包含多個服務，您可以將其部署為組成的應用程式中，使用單一的 CLI 命令 （docker-撰寫組成），或使用 Visual Studio，就會使用該命令在過程中。 讓我們看看不同的選項。

### <a name="option-a-running-a-single-container-with-docker-cli"></a>選項 a： 執行單一容器與 Docker CLI

您可以執行使用 docker run 命令，如圖 5-9 的 Docker 容器：

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**圖 5-9**。 執行使用 docker run 命令的 Docker 容器

在此情況下，命令會將繫結容器的內部連接埠 5000 到主機電腦的連接埠 80。 這表示主機會接聽通訊埠 80 和轉送至容器的連接埠 5000。

### <a name="option-b-running-a-multi-container-application"></a>選項 b： 執行多個容器應用程式

在大部分的企業案例中，Docker 應用程式將由多個服務，這表示您需要執行多個容器應用程式，如圖 5-10 所示。

![](./media/image14.png)

**圖 5-10**。 使用 Docker 容器部署的 VM

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>使用 Docker CLI 執行多個容器應用程式

若要執行 Docker CLI 多容器應用程式，您可以執行 docker-撰寫 up 命令。 您在解決方案層級來部署多個容器應用程式有此命令會使用 docker compose.yml 檔。 圖 5-11 顯示時從您的主要專案目錄，其中包含 docker compose.yml 檔案中執行命令的結果。

![](./media/image15.png)

**圖 5-11**。 範例會產生執行時 docker 撰寫向上命令

Docker 之後-撰寫排命令、 應用程式和其相關的容器會部署到您的 Docker 主機，如所述的 VM 表示圖 5-10。

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>執行和偵錯 Visual Studio 中的多個容器應用程式 

執行使用 Visual Studio 2017 多容器應用程式無法取得更簡單。 您不只能執行多個容器應用程式，但您可以設定規則的中斷點來偵錯它直接從 Visual Studio 的所有容器。

如所述之前，每次您將 Docker 解決方案支援加入方案中的專案，該專案已在全域 （方案層級） docker compose.yml 檔案中，可讓您執行或偵錯整個方案一次。 Visual Studio 將會啟動一個已啟用，Docker 解決方案支援的每個專案的容器，並為您執行所有內部的步驟 （dotnet 發行，docker 建置等。）。

此處的重點是，即會顯示在圖 5-12 版中，在 Visual Studio 2017 沒有額外**Docker** F5 按鍵動作的命令。 此選項可讓您執行或偵錯多個容器應用程式，藉由執行 docker compose.yml 檔案，在方案層級中定義的所有容器。 偵錯多個容器解決方案的功能表示在不同的專案 （容器），設定多個中斷點，而每個中斷點，從 Visual Studio 偵錯時您會定義在不同的專案上且正在執行的中斷點處停止不同的容器。

![](./media/image16.png)

**圖 5-12**。 在 Visual Studio 2017 中執行多個容器應用程式

### <a name="additional-resources"></a>其他資源

-   **部署至遠端 Docker 主機 ASP.NET 容器**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>關於測試和部署與 orchestrators 附註

向上撰寫 docker 和 docker 執行命令 （或執行和偵錯 Visual Studio 中的容器） 是適合開發環境中測試容器。 但您不應該使用這種方法，如果您的目標 Docker 叢集，而且 orchestrators 像 Docker Swarm、 Mesosphere DC/作業系統或 Kubernetes。 如果您使用 「 類似叢集[Docker Swarm 模式](https://docs.docker.com/engine/swarm/)（適用於 Docker CE for Windows 和 Mac 版本 1.12 之後），您需要部署和測試使用類似的其他命令[docker 服務建立](https://docs.docker.com/engine/reference/commandline/service_create/)的單一服務。 如果您要部署數個容器所組成的應用程式，您使用[docker 撰寫配套](https://docs.docker.com/compose/reference/bundle/)和[docker 部署 myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/)部署組成的應用程式做為*堆疊*. 如需詳細資訊，請參閱部落格文章[簡介實驗的分散式應用程式組合](https://blog.docker.com/2016/06/docker-app-bundle/)Docker 文件中。 上的 Docker 站台。

如[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)和[Kubernetes](http://kubernetes.io/docs/user-guide/deployments/)您會使用不同的部署命令和指令碼以及。

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>步驟 6： 測試 Docker 應用程式使用本機的 Docker 主機

此步驟會因您的應用程式正在進行。 在簡單的.NET Core Web 應用程式部署為單一容器或服務，您可以存取服務開啟 Docker 主機上的瀏覽器並瀏覽至該網站，如圖 5-13 所示。 （如果 Dockerfile 中的設定會對應至連接埠是 80 以外的任何主機上的容器，包括主機 post URL 中）。

![](./media/image18.png)

**圖 5-13**。 測試 Docker 應用程式在本機使用 localhost 的範例

如果 localhost 未指向 Docker 主機 IP （根據預設，當使用 Docker CE，它應該如此），巡覽至您的服務，使用您的電腦網路卡的 IP 位址。

請注意此 URL 在瀏覽器中的使用連接埠 80，例如討論特定容器。 不過，在內部將要求被重新導向至通訊埠 5000，因為這是它的部署方式與 docker 執行命令上, 一個步驟中所述。

如圖 5-14 版中所示，您也可以測試使用 curl 終端機中，從應用程式。 在 Windows 上的 Docker 安裝，預設 Docker 主機 IP 一律為 10.0.75.1 除了您電腦的實際 IP 位址。

![](./media/image19.png)

**圖 5-14**。 測試在本機使用 curl Docker 應用程式的範例

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>測試和偵錯使用 Visual Studio 2017 容器

時執行和偵錯使用 Visual Studio 2017 容器，您可以偵錯.NET 應用程式相同的方式一樣沒有容器執行時。

### <a name="testing-and-debugging-without-visual-studio"></a>測試和不含 Visual Studio 偵錯

如果您正在開發使用編輯器/CLI 方法，偵錯容器是更困難，且您會想要產生追蹤偵錯。

### <a name="additional-resources"></a>其他資源

-   **在本機的 Docker 容器中的應用程式偵錯**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker。建置、 偵錯、 部署與 Docker 的 ASP.NET Core 應用程式。** 視訊。
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>開發 Visual Studio 中的容器時簡化的工作流程

實際上，工作流程時使用 Visual Studio 會比您使用的編輯器/CLI 方法很簡單。 Dockerfile 與的大部分步驟所需的 Docker 和 docker compose.yml 檔案隱藏或簡化 Visual Studio 中，如圖 5-15 所示。

![](./media/image20.png)

**圖 5-15**。 使用 Visual Studio 進行開發時簡化的工作流程

此外，您需要執行步驟 2 （新增 Docker 支援至您的專案），就可以一次。 因此，工作流程是類似於一般的開發工作時使用的.NET 之任何其他開發。 您需要知道狀況實際上映像建置程序、 哪些您使用的基底映像 （部署容器等），有時您也要編輯的 Dockerfile 或 docker compose.yml 檔案，以自訂行為。 但大部分的工作已大幅簡化使用 Visual Studio 中，讓您提高產能。

### <a name="additional-resources"></a>其他資源

-   **Steve Lasker。.NET docker 開發使用 Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T Fritz。將.NET Core 應用程式中放入新的 Docker 工具容器中，適用於 Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>在 Dockerfile 中使用 PowerShell 命令來設定 Windows 容器 

[Windows 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)可讓您將現有的 Windows 應用程式轉換成的 Docker 映像，並將其部署在 Docker 生態系統的其他部分相同的工具。 若要使用 Windows 容器，您執行 PowerShell 命令在 Dockerfile 中，如下列範例所示：

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

在此情況下，我們會使用 Windows Server Core 基本映像 （FROM 設定），並使用 PowerShell 命令 （執行設定） 安裝 IIS。 類似的方式，您也可以使用 PowerShell 命令來設定 ASP.NET 4.x、.NET 4.6 或任何其他 Windows 軟體這類其他元件。 例如，下列命令在 Dockerfile 中的上設定 ASP.NET 4.5:

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>其他資源

-   **aspnet-docker/Dockerfile。** 若要從包含 Windows 功能的 dockerfiles 執行範例 Powershell 命令。
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[上一個](index.md) [下一步] (.../ net-core-single-containers-linux-windows-server-hosts/index.md）
