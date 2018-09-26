---
title: Visual Studio Tools for Windows 上的 Docker
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170791"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>使用 Visual Studio Tools for Docker (Windows 上的 Visual Studio)

Visual Studio Tools for Docker 開發人員工作流程是類似於使用 Visual Studio Code 和 Docker CLI （它根據相同的 Docker CLI）。 Visual Studio Tools Docker 可讓您更容易開始、 簡化程序，並進行建置，提供更高的生產力執行，以及撰寫工作。 執行和偵錯您的容器，透過簡單的動作，例如**F5**並**Ctrl**+**F5**。

> [!NOTE]
> 本文適用於 Visual Studio 在 Windows，而非 Visual Studio for mac。

## <a name="configure-your-local-environment"></a>設定您的本機環境

使用 Docker for Windows 的最新版本 ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/))，簡單的安裝程式可讓您輕鬆地開發 Docker 應用程式。

在 Visual Studio 2017 包含 docker 支援。 從這裡下載 Visual Studio 2017: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Visual Studio 2017 中使用 Docker 工具

有兩種您可以新增至專案的 Docker 支援層級。 在.NET Core web 應用程式專案中，您就可以新增*Dockerfile*專案啟用 Docker 支援的檔案。 下一個層級是容器協調器支援，這會新增*Dockerfile*至專案 （如果它尚未存在） 並*docker compose.yml*方案層級的檔案。

**新增** > **Docker 支援**並**新增** > **容器協調器支援**命令在 web 應用程式專案的專案節點的右鍵操作功能表 （或操作功能表） 位於**方案總管 中**所示，在圖 4-26:

![在 Visual Studio 中新增 Docker 支援 功能表選項](media/add-docker-support-menu.png)

圖 4-26： 新增 Docker 支援新增至 Visual Studio 2017 的專案

### <a name="add-docker-support"></a>新增 Docker 支援

您也可以選取現有的.NET Core web 應用程式專案新增 Docker 支援**新增** > **Docker 支援**中**方案總管 中**。 您也可以啟用 Docker 支援在專案建立期間選取**啟用 Docker 支援**中**新的 ASP.NET Core Web 應用程式**按一下之後開啟的對話方塊 **[確定]** 中**新的專案**對話方塊中，顯示在圖 4-27。

![Visual Studio 中的新 ASP.NET Core web 應用程式中啟用 Docker 支援](./media/enable-docker-support-visual-studio.png)

圖 4-27： 在 Visual Studio 2017 中的專案建立期間啟用 Docker 支援

當您新增或啟用 Docker 支援時，Visual Studio 會加入*Dockerfile*檔案加入專案。

> [!NOTE]
> 圖 4-28 示，您可以啟用.NET Framework web 應用程式專案 （非.NET Core web 應用程式專案） 的專案建立期間的 Docker Compose 的支援，也會加入容器協調器支援。
>
> ![啟用 Docker compose 的.NET Framework web 應用程式專案的支援](media/enable-docker-compose-support.png)

> 圖 4-28： 啟用 Visual Studio 2017 中的.NET Framework web 應用程式專案上的 Docker Compose 的支援

### <a name="add-container-orchestrator-support"></a>新增容器協調器支援

當您想要撰寫多容器解決方案時，將容器協調器支援新增至您的專案。 當您新增容器協調器支援時，Visual Studio 會加入*Dockerfile* （如果它尚未存在） 的專案和全域*docker compose.yml*方案層級的檔案。 這可讓您執行，並同時在偵錯容器 （整個解決方案） 的群組，如果它們定義在相同*docker compose.yml*檔案。 如果*docker compose.yml*已經存在，Visual Studio 只會將必要的組態程式碼的行加入至它。

容器協調流程的支援加入專案之後，您會看到新增至專案的 Dockerfile 並**docker compose**加入至方案中的資料夾**方案總管 中**所示，在圖 4-29:

![在 Visual Studio 中的 [方案總管] 中的 docker 檔案](media/docker-support-solution-explorer.png)

圖 4-29： 在 Visual Studio 2017 中的 [方案總管] 中的 Docker 檔案

**更多資訊：** 如需詳細的服務實作和使用 Visual Studio Tools for Docker，請閱讀下列文章：

建置、 偵錯、 更新和重新整理本機 Docker 容器中的應用程式： [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

將 ASP.NET Core Docker 容器部署至容器登錄： [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[上一頁](docker-apps-inner-loop-workflow.md)
[下一頁](set-up-windows-containers-with-powershell.md)