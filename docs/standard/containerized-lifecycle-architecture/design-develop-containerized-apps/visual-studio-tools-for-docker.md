---
title: 使用 Visual Studio Tools for Docker (在 Windows 上的 Visual Studio)
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 62da6a3ff595422e42450cb1341976424acc5a52
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314707"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>使用 Visual Studio Tools for Docker (在 Windows 上的 Visual Studio)

開發人員工作流程時使用 Visual Studio Tools for Docker 時，才能與工作流程類似使用 Visual Studio 程式碼和 Docker CLI （事實上，它根據相同的 Docker CLI），但您更輕鬆地開始使用、 可簡化程序，並提供更高組建的產能執行，而且組成的工作。 它也會執行並偵錯您的容器，透過簡單的動作，如 F5 和 Ctrl + F5 從 Visual Studio。 更，與 Visual Studio 2017，除了執行和偵錯單一容器中，您也可以執行和偵錯的容器 （整個方案） 的群組同時如果方案層級相同的 docker compose.yml 檔案中定義。

## <a name="configuring-your-local-environment"></a>設定您的本機環境

Docker for Windows 的最新版本，它就能夠更輕鬆比曾經來開發 Docker 應用程式因為下列參考中所述，很簡單，安裝程式。

**更多資訊：** 若要了解安裝 Docker for Windows 的詳細資訊，請移至<https://docs.docker.com/docker-for-windows/>。

如果您使用 Visual Studio 2015，您必須更新 3 或更新版本以及 Visual Studio Tools for Docker。

**更多資訊：** 如需安裝 Visual Studio 的指示，請移至[https://visualstudio.microsoft.com/\產品/vs-2015年-產品-版本](https://visualstudio.microsoft.com/products/vs-2015-product-editions)。

若要查看安裝 Visual Studio Tools for Docker 的詳細資訊，請移至<http://aka.ms/vstoolsfordocker>和<https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>。

如果您使用 Visual Studio 2017，已經包含 Docker 的支援。

## <a name="using-docker-tools-in-visual-studio-2015"></a>使用 Visual Studio 2015 中的 Docker 工具

Visual Studio Tools for Docker 會提供一致的方式開發，並在本機驗證 Docker 容器適用於 Linux 的 Linux Docker 主機或 VM 或您直接在 Windows 上的 Windows 容器中。

如果您使用單一的容器，您需要開始第一件事就是開啟 Docker 支援到.NET Core 專案。 若要這樣做，以滑鼠右鍵按一下專案檔，如圖 4-25 所示。

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

圖 4-25： 開啟 Visual Studio 專案的 Docker 支援

## <a name="using-docker-tools-in-visual-studio-2017"></a>在 Visual Studio 2017 使用 Docker 工具

當您將 Docker 的支援加入服務專案方案中 （請參閱圖 4-26），Visual Studio 會不只 DockerFile 檔案加入您的專案，它也服務區段中加入您的方案 docker compose.yml 檔案 （或建立檔案，如果他們未存在）。 這是簡單的方法，若要開始撰寫 multicontainer 方案;您可以開啟 docker compose.yml 檔案，然後其他功能用來更新這些。

![](./media/image32.png)

圖 4-26： 開啟 Docker 方案在 Visual Studio 2017 專案中的支援

這個動作不只會將 DockerFile 至您的專案，它也會將必要的組態程式碼加入方案層級設定全域 docker compose.yml。

您也可以開啟 Docker 支援時建立的 ASP.NET Core 專案在 Visual Studio 2017，如圖 4-27 所示。

![](./media/image33.png)

建立專案時，Docker 支援開啟圖 4-27:

在 Visual Studio 方案中加入 Docker 支援之後，您也會看到新節點樹狀，在 [方案總管] 新增的 docker compose.yml 檔案時，如上圖 4-28。

![](./media/image34.PNG)

圖 4-28: docker compose.yml 檔案現在會顯示在 方案總管

您可以部署 multicontainer 應用程式使用單一的 docker compose.yml 檔案，當您執行 docker-撰寫組成;不過，Visual Studio 將群組加入項目，因此您可以覆寫值取決於環境 （與實際執行的程式開發） 和執行類型 （與偵錯版本）。 這項功能將進一步說明，在後續章節。

**更多資訊：** 如需詳細資訊的服務實作和使用 Visual Studio Tools for Docker，請閱讀下列文章：

建置、 偵錯、 更新和重新整理本機的 Docker 容器中的應用程式： [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

將 ASP.NET 容器部署至遠端 Docker 主機： [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)


>[!div class="step-by-step"]
[上一個] (docker-應用程式-內部-迴圈-workflow.md) [下一步] (set-up-windows-containers-with-powershell.md)
