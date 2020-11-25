---
title: Windows 上的 Visual Studio Tools for Docker
description: 了解 Visual Studio 2017 15.7 版和更新版本中可用的 Docker 工具。
ms.date: 08/06/2020
ms.custom: vs-dotnet
ms.openlocfilehash: ae20ebf7c3c27d7f2ebe51c33719b82048f86241
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032186"
---
# <a name="use-docker-tools-in-visual-studio-on-windows"></a>在 Windows 上的 Visual Studio 中使用 Docker 工具

使用 Docker 工具時包含在 Visual Studio 2017 15.7 版和更新版本中的開發人員工作流程，類似於使用 Visual Studio Code 和 Docker CLI (事實上，它是以相同的 Docker CLI 為基礎)，但它可以更輕鬆地開始使用、簡化此處理序，以及針對建置、執行和撰寫工作提供更高的生產力。 它也可以從 Visual Studio 透過常用的 `F5` 和 `Ctrl+F5` 按鍵執行容器並對其進行偵錯。 如果其容器是在解決方案層級的同一個 `docker-compose.yml` 檔案中定義，您甚至可以對整個解決方案進行偵錯。

## <a name="configure-your-local-environment"></a>設定您的本機環境

使用適用於 Windows 的最新版本 Docker 時，因為設定非常簡單，所以開發 Docker 應用程式比以往更加容易，如下列參考中所述。

> [!TIP]
> 若要深入了解如何安裝適用於 Windows 的 Docker，請前往 (<https://docs.docker.com/docker-for-windows/>)。

## <a name="docker-support-in-visual-studio"></a>Visual Studio 中的 Docker 支援

您可以將兩種 Docker 支援層級新增至專案。 在 ASP.NET Core 專案中，您可以啟用 Docker 支援，只將 `Dockerfile` 檔案新增至專案。 下一個層級是容器協調流程支援，這會將 `Dockerfile` 新增至專案 (如果它尚未存在) 和解決方案層級的 `docker-compose.yml` 檔案。 預設會透過 Docker Compose 在 Visual Studio 2017 15.0 版至 15.7 版中新增容器協調流程支援。 容器協調流程支援是 Visual Studio 2017 15.8 版或更新版本中的選擇性功能。 Visual Studio 2019 和更新版本也支援 **Kubernetes/Helm** 部署。

[新增] > [Docker 支援] 和 [新增] > [容器協調器支援] 命令位於 [方案總管] 中 ASP.NET Core 專案的專案節點右鍵功能表 (或操作功能表) 上，如圖 4-31 所示：

![Visual Studio 中的 [新增 Docker 支援] 功能表選項](media/add-docker-support-menu.png)

**圖 4-31**。 將 Docker 支援新增至 Visual Studio 2019 專案

### <a name="add-docker-support"></a>新增 Docker 支援

除了如上一節所示，將 Docker 支援新增至現有應用程式的選項之外，您也可以在專案建立期間啟用 docker 支援，方法是在 [**新增專案**] 對話方塊中按一下 **[確定**] 之後，在 [**新增 ASP.NET Core Web 應用程式**] 對話方塊中選取 [**啟用 docker 支援**]，如圖4-32 所示。

![在 Visual Studio 中為新的 ASP.NET Core Web 應用程式啟用 Docker 支援](media/enable-docker-support-visual-studio.png)

**圖 4-32**。 在 Visual Studio 2019 的專案建立期間啟用 Docker 支援

當您新增或啟用 Docker 支援時，Visual Studio 會將 _Dockerfile_ 檔案新增至專案，其中包含解決方案中所有必要專案的參考。

### <a name="add-container-orchestration-support"></a>新增容器協調流程支援

若要撰寫多容器解決方案，請將容器協調流程支援新增至您的專案。 如果它們在同一個 _docker-compose.yml_ 文件中定義，則允許您同時執行一組容器 (整個解決方案) 並對其進行偵錯。

若要新增容器協調流程支援，請以滑鼠右鍵按一下 [方案總管] 中的解決方案或專案節點，然後選擇 [新增] > [容器協調流程支援]。 然後選擇 **Kubernetes/Helm** 或 **Docker Compose** 來管理容器。

將容器協調流程支援新增至您的專案之後，您會看到已新增至專案的 Dockerfile，以及在 **方案總管** 中新增至解決方案的 **docker 組成** 資料夾，如圖4-33 所示：

![Visual Studio 中 [方案總管] 中的 Docker 檔案](media/docker-support-solution-explorer.png)

**圖 4-33**。 Visual Studio 2019 中方案總管的 Docker 檔案

如果 _docker-compose.yml_ 已存在，則 Visual Studio 只會向其新增所需的組態程式碼行。

## <a name="configure-docker-tools"></a>設定 Docker 工具

從主功能表中，選擇 [工具] > [選項]，並展開 [容器工具] > [設定]。 容器工具設定隨即出現。

![Visual Studio Docker 工具選項，顯示三個頁面： [一般]、[單一專案] 和 [Docker Compose] 文章文字中的詳細資料。](media/visual-studio-docker-tools-options.png)

**圖 4-34**. Docker 工具選項

下表可協助您決定如何設定這些選項。

| 頁面/設定                                |  預設值   | 描述                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------------------------------- | :----------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **一般頁面**                            |
| 視需要安裝 Docker Desktop            |     提示我      |
| 視需要啟動 Docker Desktop              |     提示我      |
| 信任 ASP.NET Core SSL 憑證          |     提示我      | 如果未將 localhost SSL 憑證標示為受信任的 (`dotnet dev-certs https --trust`) ，Visual Studio 會在每次執行專案時提示。                                                                                                                                                                                                                                                    |
| **單一專案頁面**                     |
| 在專案開啟時提取所需的 Docker 映射 |        True        | 為了提高執行專案時的效能，Visual Studio 會在背景中啟動 Docker 提取作業，如此一來，當您準備好要執行程式碼時，影像就已經下載或正在下載。 如果您只要載入專案並瀏覽程式碼，則可以關閉這項功能，避免下載您不需要的容器映像。 這可能會使開放式專案使用者體驗變慢。 |
| 在專案載入時提取更新的 Docker 映射  | .NET Core 專案 | 提取現有映射的更新，以取得專案開啟的最新更新。 這可能會使開放式專案使用者體驗變慢。                                                                                                                                                                                                                                                                                          |
| 在專案關閉時移除容器          |        True        | 清除專案關閉時，這可能會使關閉專案的使用者體驗變慢，但通常仍會快速。                                                                                                                                                                                                                                                                                                            |
| 在專案開啟時執行容器              |        True        | 為了提高執行專案時的效能，Visual Studio 會啟動方案中的所有容器。 這可能會使開放式專案使用者體驗變慢。                                                                                                                                                                                                                                                        |
| **Docker Compose**                          |                    | Docker Compose 頁面包含與單一專案頁面相同的設定，但這些設定適用于多容器解決方案。                                                                                                                                                                                                                                                                                           |

> [!WARNING]
> 如果 localhost SSL 憑證不受信任，而且您將此選項設定為 [ **永不**]，則 HTTPS web 要求可能會在您的應用程式或服務中的執行時間失敗。 在這種情況下，請再次將值設定為 [ **提示我** ]，或者，更好的是，使用命令來信任您開發電腦上的憑證 `dotnet dev-certs https --trust` 。

> [!TIP]
> 如需服務實作和使用 Visual Studio Tools for Docker 的進一步詳細資料，請閱讀下列文章：
>
> 在本機 Docker 容器中偵錯工具： <https://docs.microsoft.com/visualstudio/containers/edit-and-refresh>
>
> 使用 Visual Studio 將 ASP.NET 容器部署到容器登錄：<https://docs.microsoft.com/visualstudio/containers/hosting-web-apps-in-docker>

> [!div class="step-by-step"]
> [上一個](docker-apps-inner-loop-workflow.md) 
> [下一步](set-up-windows-containers-with-powershell.md)
