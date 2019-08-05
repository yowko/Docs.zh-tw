---
title: Windows 上的 Visual Studio Tools for Docker
description: 了解 Visual Studio 2017 15.7 版和更新版本中可用的 Docker 工具。
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673875"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>在 Windows 上使用 Visual Studio 2017 中的 Docker 工具

使用 Docker 工具時包含在 Visual Studio 2017 15.7 版和更新版本中的開發人員工作流程，類似於使用 Visual Studio Code 和 Docker CLI (事實上，它是以相同的 Docker CLI 為基礎)，但它可以更輕鬆地開始使用、簡化此處理序，以及針對建置、執行和撰寫工作提供更高的生產力。 它也可以從 Visual Studio 透過常用的 `F5` 和 `Ctrl+F5` 按鍵執行容器並對其進行偵錯。 如果其容器是在解決方案層級的同一個 `docker-compose.yml` 檔案中定義，您甚至可以對整個解決方案進行偵錯。

## <a name="configure-your-local-environment"></a>設定您的本機環境

使用適用於 Windows 的最新版本 Docker 時，因為設定非常簡單，所以開發 Docker 應用程式比以往更加容易，如下列參考中所述。

> [!TIP]
> 若要深入了解如何安裝適用於 Windows 的 Docker，請前往 (<https://docs.docker.com/docker-for-windows/>)。

## <a name="docker-support-in-visual-studio-2017"></a>Visual Studio 2017 中的 Docker 支援

您可以將兩種 Docker 支援層級新增至專案。 在 ASP.NET Core 專案中，您可以啟用 Docker 支援，只將 `Dockerfile` 檔案新增至專案。 下一個層級是容器協調流程支援，這會將 `Dockerfile` 新增至專案 (如果它尚未存在) 和解決方案層級的 `docker-compose.yml` 檔案。 預設會透過 Docker Compose 在 Visual Studio 2017 15.0 版至 15.7 版中新增容器協調流程支援。 容器協調流程支援是 Visual Studio 2017 15.8 版或更新版本中的選擇性功能。 15.8 版和更新版本支援 Docker Compose 與 Service Fabric。

[新增] > [Docker 支援]  和 [新增] > [容器協調器支援]  命令位於 [方案總管]  中 ASP.NET Core 專案的專案節點右鍵功能表 (或操作功能表) 上，如圖 4-31 所示：

![Visual Studio 中的 [新增 Docker 支援] 功能表選項](./media/add-docker-support-menu.png)

**圖 4-31**。 將 Docker 支援新增至 Visual Studio 2017 專案

### <a name="add-docker-support"></a>新增 Docker 支援

您可以透過在 [方案總管]  中選取 [新增]   > [Docker 支援]  ，為現有的 ASP.NET Core 專案新增 Docker 支援。 您也可以在專案建立期間啟用 Docker 支援，方法是在按一下 [新增專案]  對話方塊的 [確定]  之後開啟的 [新增 ASP.NET Core Web 應用程式]  對話方塊中選取 [啟用 Docker 支援]  ，如圖 4-32 所示。

![在 Visual Studio 中為新的 ASP.NET Core Web 應用程式啟用 Docker 支援](./media/enable-docker-support-visual-studio.png)

**圖 4-32**。 在 Visual Studio 2017 中於專案建立期間啟用 Docker 支援

當您新增或啟用 Docker 支援時，Visual Studio 會將 *Dockerfile* 檔案新增至專案中。

> [!NOTE]
> 在專案建立期間為 ASP.NET 專案 (.NET Framework，而不是 .NET Core 專案) 啟用 Docker Compose 支援時，也會新增容器協調流程支援，如圖 4-33 所示。

![針對 ASP.NET 專案啟用 Docker Compose 支援](media/enable-docker-compose-support.png)

**圖 4-33**。 在 Visual Studio 2017 中針對 ASP.NET 專案啟用 Docker Compose 支援

### <a name="add-container-orchestration-support"></a>新增容器協調流程支援

若要撰寫多容器解決方案，請將容器協調流程支援新增至您的專案。 如果它們在同一個 *docker-compose.yml* 文件中定義，則允許您同時執行一組容器 (整個解決方案) 並對其進行偵錯。

若要新增容器協調流程支援，請以滑鼠右鍵按一下 [方案總管]  中的解決方案或專案節點，然後選擇 [新增] > [容器協調流程支援]  。 然後選擇 [Docker Compose]  或 [Service Fabric]  來管理容器。

向專案新增容器協調流程支援後，您會看到專案中新增了 Dockerfile，且 [方案總管]  中的解決方案新增了 **docker-compose** 資料夾，如圖 4-34 所示：

![Visual Studio 中 [方案總管] 中的 Docker 檔案](media/docker-support-solution-explorer.png)

**圖 4-34**. Visual Studio 2017 [方案總管] 中的 Docker 檔案

如果 *docker-compose.yml* 已存在，則 Visual Studio 只會向其新增所需的組態程式碼行。

## <a name="configure-docker-tools"></a>設定 Docker 工具

從主功能表中，選擇 [工具] > [選項]  ，並展開 [容器工具] > [設定]  。 容器工具設定隨即出現。

![Visual Studio Docker 工具選項，其中顯示：自動在專案載入時提取所需的 Docker 映像、自動在背景中啟動容器、自動在解決方案關閉時終止容器，以及不要提示信任 SSL 憑證。](./media/visual-studio-docker-tools-options.png)

**圖 4-35**. Docker 工具選項

下表可協助您決定如何設定這些選項。

| 名稱 | 預設設定 | 適用於 | 說明 |
| -----|:---------------:|:----------:| ----------- |
| 自動在專案載入時提取所需的 Docker 映像 | 開啟 | Docker Compose | 為了提高載入專案時的效能，Visual Studio 會在背景中啟動 Docker 提取作業，因此當您準備好要執行程式碼時，映像已下載或正在下載中。 如果您只要載入專案並瀏覽程式碼，則可以關閉這項功能，避免下載您不需要的容器映像。 |
| 自動在背景中啟動容器 | 開啟 | Docker Compose | 同樣為了提高效能，Visual Studio 會在您建置並執行容器時建立一個容器，內含準備好可供使用的磁碟區裝載。 如果您想要控制何時建立容器，請關閉這項功能。 |
| 自動在解決方案關閉時終止容器 | 開啟 | Docker Compose | 如果您希望解決方案的容器在關閉解決方案或關閉 Visual Studio 之後繼續執行，請關閉這項功能。 |
| 不要提示信任 localhost SSL 憑證 | Off | ASP.NET Core 2.2 專案 | 如果 localhost SSL 憑證不受信任，則除非核取此核取方塊，否則每次執行專案時 Visual Studio 都會提示。 |

> [!WARNING]
> 如果 localhost SSL 憑證不受信任，且您核取隱藏提示的方塊，則 HTTPS Web 要求可能會在應用程式或服務的執行階段失敗。 在此情況下，請取消核取 [不要提示]  核取方塊，執行您的專案，並在提示時表示信任。

> [!TIP]
> 如需服務實作和使用 Visual Studio Tools for Docker 的進一步詳細資料，請閱讀下列文章：
>
>對本機 Docker 容器中的應用程式進行偵錯：<https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>使用 Visual Studio 將 ASP.NET 容器部署到容器登錄：<https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[上一頁](docker-apps-inner-loop-workflow.md)
>[下一頁](set-up-windows-containers-with-powershell.md)
