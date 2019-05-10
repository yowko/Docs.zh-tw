---
title: Visual Studio Tools for Windows 上的 Docker
description: 了解 Visual Studio 2017 15.7 版及更新版本中可用的 Docker 工具。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: d361b0c471402c097dfac799eb58ef08209d4343
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664362"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>在 Windows 上的 Visual Studio 2017 中使用 Docker 工具

使用 Docker 工具包含在 Visual Studio 2017 15.7 版及更新版本時，開發人員工作流程，類似於使用 Visual Studio Code 和 Docker CLI （事實上，它根據相同的 Docker CLI），但它可以更輕鬆地開始使用，可簡化此程序，以及提供更高的生產力組建、 執行和撰寫工作。 它也可以執行和偵錯您的容器，透過一般`F5`和`Ctrl+F5`從 Visual Studio 的索引鍵。 可以在同一個定義其容器如果甚至偵錯整個解決方案`docker-compose.yml`方案層級的檔案。

## <a name="configure-your-local-environment"></a>設定您的本機環境

使用 Docker for Windows 的最新版本，就比以往若要開發 Docker 應用程式因為下列參考中所述，安裝程式很簡單，更容易。

> [!TIP]
> 若要深入了解安裝 Docker for Windows，請移至 (<https://docs.docker.com/docker-for-windows/>)。

## <a name="docker-support-in-visual-studio-2017"></a>Visual Studio 2017 中的 docker 支援

有兩種您可以新增至專案的 Docker 支援層級。 在 ASP.NET Core 專案中，您就可以新增`Dockerfile`專案啟用 Docker 支援的檔案。 下一個層級是容器協調流程支援，這會新增`Dockerfile`至專案 （如果它尚未存在） 和`docker-compose.yml`方案層級的檔案。 預設會在 Visual Studio 2017 版本 15.0 到 15.7 新增容器協調流程的支援，透過 Docker Compose。 容器協調流程的支援是選擇性功能 15.8 或更新版本的 Visual Studio 2017 版本中。 更新版本的版本 15.8 支援 Docker Compose 與 Service Fabric。

**新增 > Docker 支援**並**新增 > 容器協調器支援**命令位於 ASP.NET Core 專案的專案節點的右鍵操作功能表 （或操作功能表） 中**方案總管] 中**，如 [圖 4-31 的所示：

![Visual Studio 中的 [新增 Docker 支援] 功能表選項](./media/add-docker-support-menu.png)

**圖 4-31**。 將 Docker 支援新增至 Visual Studio 2017 的專案

### <a name="add-docker-support"></a>新增 Docker 支援

您也可以選取現有的 ASP.NET Core 專案新增 Docker 支援**新增** > **Docker 支援**中**方案總管 中**。 您也可以啟用 Docker 支援在專案建立期間選取**啟用 Docker 支援**中**新的 ASP.NET Core Web 應用程式**按一下之後開啟的對話方塊**確定**中**新的專案**對話方塊中，顯示 圖 4-32。

![在 Visual Studio 中為新的 ASP.NET Core Web 應用程式啟用 Docker 支援](./media/enable-docker-support-visual-studio.png)

**圖 4-32**。 在 Visual Studio 2017 中的專案建立期間啟用 Docker 支援

當您新增或啟用 Docker 支援時，Visual Studio 會加入*Dockerfile*檔案加入專案。

> [!NOTE]
> 圖 4-33 示，您可以啟用 ASP.NET 專案 (.NET Framework，.NET Core 專案) 的專案建立期間的 Docker Compose 的支援，也會加入容器協調流程支援。

![針對 ASP.NET 專案啟用 Docker Compose 支援](media/enable-docker-compose-support.png)

**圖 4-33**。 啟用 Docker Compose 的 ASP.NET 專案中 Visual Studio 2017 的支援

### <a name="add-container-orchestration-support"></a>新增容器協調流程的支援

當您想要撰寫多容器解決方案時，將容器協調流程支援新增至您的專案。 這可讓您執行，並同時在偵錯容器 （整個解決方案） 的群組，如果它們定義在相同*docker compose.yml*檔案。

若要新增容器協調流程的支援，請以滑鼠右鍵按一下的方案或專案節點上**方案總管 中**，然後選擇**新增 > 容器協調流程支援**。 然後選擇**Docker Compose**或是**Service Fabric**管理容器。

協調流程的容器支援新增至您的專案之後，您會看到加入至專案的 Dockerfile 並**docker compose**加入至方案中的資料夾**方案總管] 中**所示，[圖 4-34:

![Visual Studio 中 [方案總管] 中的 Docker 檔案](media/docker-support-solution-explorer.png)

**圖 4-34**。 Visual Studio 2017 中的 [方案總管] 中的 docker 檔案

如果 *docker-compose.yml* 已存在，則 Visual Studio 只會向其新增所需的組態程式碼行。

## <a name="configure-docker-tools"></a>設定 Docker 工具

從主功能表中，選擇**工具 > 選項**，展開**容器工具 > 設定**。 容器的 [工具] 設定會出現。

![Visual Studio Docker 工具選項，顯示：自動在專案載入提取所需的 Docker 映像、 自動在背景中啟動容器、 自動終止容器關閉、 解決方案和不要提示信任 SSL 憑證。](./media/visual-studio-docker-tools-options.png)

**圖 4-35**。 Docker 工具選項

下表可協助您決定如何設定這些選項。

| 名稱 | 預設設定 | 適用於 | 描述 |
| -----|:---------------:|:----------:| ----------- |
| 自動在專案載入提取所需的 Docker 映像 | 開啟 | Docker Compose | 為了提高效能載入專案時，Visual Studio 會啟動 Docker 提取作業在背景中，因此當您準備好要執行您的程式碼，將映像已下載，或是正在下載。 如果您只會載入專案，並瀏覽程式碼，您可以避免下載容器映像，您不需要將此關閉。 |
| 自動在背景中啟動容器 | 開啟 | Docker Compose | 再次為了提高效能，Visual Studio 會建立一個容器與磁碟區掛接供當您建置並執行您的容器。 如果您想要控制您的容器建立時，請關閉這個功能。 |
| 自動終止容器解決方案關閉 | 開啟 | Docker Compose | 如果您想要繼續執行之後關閉解決方案，或關閉 Visual Studio 方案的容器，請開啟此功能。 |
| 不要提示信任 localhost SSL 憑證 | Off | ASP.NET Core 2.2 專案 | 如果 localhost SSL 憑證不受信任，Visual Studio 在除非已選取此核取方塊，會先提示每次您執行您的專案。 |

> [!WARNING]
> 如果 localhost SSL 憑證不受信任，而且您核取方塊來隱藏提示，則 HTTPS web 要求可能會在您的應用程式或服務執行階段失敗。 在此情況下，取消核取**不要提示**核取方塊，執行您的專案，並指出在提示字元中的信任。

> [!TIP]
> 如需詳細的服務實作和使用 Visual Studio Tools for Docker，閱讀下列文章：
>
>偵錯本機 Docker 容器中的應用程式： <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>將 ASP.NET 容器部署到使用 Visual Studio 的容器登錄： <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[上一頁](docker-apps-inner-loop-workflow.md)
>[下一頁](set-up-windows-containers-with-powershell.md)
