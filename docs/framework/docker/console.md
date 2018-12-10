---
title: 在 Docker 中執行主控台應用程式
description: 了解如何擷取現有的 .NET Framework 主控台應用程式並在 Windows Docker 容器中執行。
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 379e0814d7d254935ef23a483d5e0f9163babcd1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145276"
---
# <a name="running-console-applications-in-windows-containers"></a>在 Windows 容器中執行主控台應用程式

主控台應用程式的用途有許多種；從簡單的狀態查詢，到長時間執行的文件影像處理工作。 在任何情況下，您都可以啟動並調整這些應用程式的規模，但具有硬體取得、啟動時間或執行多個執行個體的限制。

藉由移動您的主控台應用程式以使用 Docker 和 Windows Server 容器，您就可以從初始狀態啟動這些應用程式，讓這些應用程式執行作業再完全關閉。 本主題說明將主控台應用程式移至 Windows 容器，再使用 PowerShell 指令碼加以啟動所需的步驟。

此範例主控台應用程式是接受引數的簡單範例 (在本例中為一個問題)，並傳回隨機答案。 這可能會擷取 `customer_id` 並處理其稅金，或建立 `image_url` 引數的縮圖。

除了答案之外，也已將 `Environment.MachineName` 加入回應，以顯示在本機執行應用程式與在 Windows 容器中執行應用程式之間的差異。 在本機執行應用程式時，應該傳回您的本機電腦名稱；在 Windows 容器中執行時，則會傳回容器的工作階段識別碼。

[完整範例](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) (英文) 可在 GitHub 上的 dotnet/samples 存放庫取得。 如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

您必須先熟悉一些 Docker 術語，才能開始將應用程式移至容器的工作。

> 「Docker 映像」是唯讀範本，為執行中容器定義環境，包括作業系統 (OS)、系統元件和應用程式。

Docker 映像的一個重要特性是這些映像會從基礎映像組成。 每個新的映像會將一小組功能加入現有的映像。 

> 「Docker 容器」是映像的執行中執行個體。 

您可以在許多容器中執行相同的映像，來調整應用程式的規模。
就概念而言，這類似於在多部主機中執行相同的應用程式。

您可以閱讀 Docker 網站上的 [Docker Overview](https://docs.docker.com/engine/understanding-docker/)，以深入了解 Docker 架構。 

只需要幾個步驟，就可以移動您的主控台應用程式。

1. [建置應用程式](#building-the-application)
1. [建立映像的 Dockerfile](#creating-the-dockerfile)
1. [建置及執行 Docker 容器的程序](#creating-the-image)

## <a name="prerequisites"></a>必要條件
Windows 容器受到 [Windows 10 年度更新版](https://www.microsoft.com/en-us/software-download/windows10/)或 [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server) 的支援。

> [!NOTE]
>如果您使用 Windows Server 2016，您必須手動啟用容器，因為 Docker for Windows 安裝程式不會啟用此功能。 請務必對作業系統執行所有更新，然後遵循[容器主機部署](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server)一文中的指示來安裝容器和 Docker 功能。

您需要有 Docker for Windows 1.12 Beta 26 版或更高版本，才能支援 Windows 容器。 Docker 預設會啟用 Linux 容器；請以滑鼠右鍵按一下系統匣中的 Docker 圖示，然後選取 [切換至 Windows 容器]，以切換至 Windows 容器。 Docker 將會執行變更程序，而且可能需要重新啟動。

![Windows-Containers](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a>建置應用程式
主控台應用程式通常是透過安裝程式、FTP 或檔案共用部署來散發。 部署至容器時，這些資產必須加以編譯並暫存到建立 Docker 映像時可使用的位置。

在 *build.ps1* 中，指令碼會使用 [MSBuild](/visualstudio/msbuild/msbuild) 來編譯應用程式，以完成建立資產的工作。 您可以將幾個參數傳遞至 MSBuild，以確定所需的資產。 像是要編譯的專案檔或方案名稱，輸出的位置，以及最後的組態 (發行或偵錯)。

在 `Invoke-MSBuild` 的呼叫中，`OutputPath` 會設定為 **publish**，而 `Configuration` 會設定為 [發行]。 

```powershell
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj -p:OutputPath=.\publish -p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>建立 Dockerfile
.NET Framework 主控台應用程式所使用的基礎映像為 `microsoft/windowsservercore`，會在 [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/) 上公開提供。 基礎映像包含 Windows Server 2016 的最小安裝 .NET Framework 4.6.2，可作為 Windows 容器的基礎作業系統映像。

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
Docerkfile 中的第一行會使用 [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) 指令來指定基礎映像。 接下來，檔案中的 [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) 會將應用程式資產從 **publish** 資料夾複製到容器的根資料夾；最後設定映像狀態的 [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint)，這是容器啟動時將執行的命令或應用程式。 

## <a name="creating-the-image"></a>建立映像
若要建立 Docker 映像，請將下列程式碼加入 *build.ps1* 指令碼。 執行指令碼時，會使用從 MSBuild 編譯的資產來建立 `console-random-answer-generator` 映像，如[建置應用程式](#building-the-application)一節中所定義。

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

從 PowerShell 命令提示字元使用 `.\build.ps1` 來執行指令碼。

建置完成時，從命令列或 PowerShell 命令提示字元使用 `docker images` 命令；您將會看到映像已建立並準備好執行。

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>執行容器
您可以從命令列使用 Docker 命令來啟動容器。

```
docker run console-random-answer-generator "Are you a square container?"
```

輸出為

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

如果您從 PowerShell 執行 `docker ps -a` 命令，您會看到容器仍然存在。

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

[狀態] 欄顯示在「約一分鐘前」，應用程式已完成並可以關閉。 如果執行此命令一百次，則會有一百個容器保持靜態且沒有可執行的工作。 在一開始的案例中，理想作業是執行工作並關閉或清除。 若要完成該工作流程，將 `--rm` 選項 `docker run` 加入命令會在收到 `Exited` 訊號時立即移除容器。

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

執行命令並搭配此選項，然後檢視 `docker ps -a` 命令的輸出；請注意，容器識別碼 (`Environment.MachineName`) 不在清單中。

### <a name="running-the-container-using-powershell"></a>使用 PowerShell 執行容器
在範例專案檔中，還有 *run.ps1*，此範例示範如何使用 PowerShell 來執行接受引數的應用程式。

若要執行，請開啟 PowerShell 並使用下列命令：

```powershell
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>總結
只要加入 Dockerfile 並發行應用程式，您就可以容器化 .NET Framework 主控台應用程式，並立即利用執行多個執行個體、正常啟動和停止及更多 Windows Server 2016 功能，完全不需要對應用程式程式碼進行任何變更。
