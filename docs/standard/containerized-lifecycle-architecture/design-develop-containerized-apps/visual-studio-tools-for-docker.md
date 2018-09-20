---
title: 使用 Visual Studio Tools for Docker (Windows 上的 Visual Studio)
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: af14c92ab27885deec878dc33e7b94035f43e65b
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46488947"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>使用 Visual Studio Tools for Docker (Windows 上的 Visual Studio)

使用 Visual Studio Code 和 Docker CLI 時，類似於工作流程時使用 Visual Studio Tools for Docker 開發工作流程。 事實上，它根據相同的 Docker CLI，但您更輕鬆地開始使用、 簡化程序，並提供更高的生產力組建、 執行和撰寫工作。 它也可執行和偵錯您的容器，透過簡單的動作，例如 F5 以及從 Visual Studio 的 Ctrl + F5。 選擇性的容器協調流程的支援，除了能夠執行和偵錯單一容器中，您可以執行，並同時在偵錯容器 （整個解決方案） 的群組。 只在同一個定義的容器*docker compose.yml*方案層級的檔案。

## <a name="configuring-your-local-environment"></a>設定您的本機環境

在 Visual Studio 2017 包含 docker 的支援，與任何已安裝的.NET 和.NET Core 工作負載。 個別安裝 Docker for Windows。

使用 Docker for Windows 的最新版本，就比以往若要開發 Docker 應用程式因為下列參考中所述，安裝程式很簡單，更容易。

**更多資訊：** 若要深入了解安裝 Docker for Windows，請前往<https://docs.docker.com/docker-for-windows/>。

**更多資訊：** 如需安裝 Visual Studio 的指示，請移至[ https://visualstudio.microsoft.com/downloads/ ](https://visualstudio.microsoft.com/downloads/)。

若要查看安裝 Visual Studio Tools for Docker 的詳細資訊，請前往<http://aka.ms/vstoolsfordocker>和<https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>。

## <a name="using-docker-tools-in-visual-studio-2017"></a>Visual Studio 2017 中使用 Docker 工具

將 Docker 支援新增至專案時 （請參閱圖 4-26），Visual Studio 會加入*Dockerfile*至專案根目錄。

![開啟 Visual Studio 2017 專案中的 Docker 解決方案支援](./media/image32.png)

圖 4-26： 開啟 Visual Studio 2017 專案中的 Docker 解決方案支援

 新增容器協調流程支援，透過 Docker Compose，預設會在 Visual Studio 2017 版本 15.7 或更早版本。 容器協調流程的支援是在 Visual Studio 2017 版本 15.8 選擇加入的功能或更新版本中，在此情況下 Docker Compose 與 Service Fabric 支援。

使用 Visual Studio 15.8 和更新版本中,，您可以新增多個專案的支援方案，每個有相關聯的容器中。 中的方案或專案節點上按一下滑鼠右鍵**方案總管 中**，然後選擇**新增** > **容器協調流程支援**。  然後選擇**Docker Compose**或是**Service Fabric**管理容器。

當您選擇**Docker Compose**，Visual Studio 在您的方案中新增服務 區段*docker compose.yml*檔案 （或建立檔案，如果不存在的話）。 這是簡單的方法，開始撰寫多容器解決方案;接著，您可以開啟*docker compose.yml*檔案，並使用額外的功能更新這些值。

這個動作會將必要的設定的程式碼來*docker compose.yml*在解決方案層級設定。

您也可以開啟 Docker 支援在 Visual Studio 2017 中，建立 ASP.NET Core 專案時，所示的圖 4-27。

![建立專案時，開啟 Docker 支援](./media/image33.png)

圖 4-27： 在建立專案時，要開啟 Docker 支援

您將 Docker 支援新增至您在 Visual Studio 中的方案之後，您也會看到新的節點樹狀目錄中**方案總管**以加入*docker compose.yml*檔案，如下所述在圖 4-28。

![docker-compose.yml 檔案現在會顯示在 方案總管](./media/image34.PNG)

[圖 4-28: docker-compose.yml 檔案現在會顯示在**方案總管]**

您可以部署多容器應用程式使用單一*docker compose.yml*檔案，當您執行`docker-compose up`; 不過，Visual Studio 會加入它們的群組，因此您可以覆寫值取決於環境 （開發與生產環境） 和輸入 （發行與偵錯） 執行。 後面的章節則會進一步說明這項功能。

您也可以管理多個容器，而不是 Docker Compose 使用 Service Fabric。 請參閱[教學課程： 將 Windows 容器中的.NET 應用程式部署至 Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container)。

**更多資訊：** 如需詳細的服務實作和使用 Visual Studio Tools for Docker，請閱讀下列文章：

建置、 偵錯、 更新和重新整理本機 Docker 容器中的應用程式： [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

將 ASP.NET Core Docker 容器部署至容器登錄： [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[上一頁](docker-apps-inner-loop-workflow.md)
[下一頁](set-up-windows-containers-with-powershell.md)
