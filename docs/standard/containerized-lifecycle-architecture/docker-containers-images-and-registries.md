---
title: "Docker 容器、 影像和登錄"
description: "Microsoft 平台和工具的容器化 Docker 應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0cccead8833c63f19b359f830f555e7ff31daa1a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="docker-containers-images-and-registries"></a>Docker 容器、 影像和登錄

當使用 Docker 時，您建立應用程式或服務和封裝它，並傳遞至容器映像及其相依性。 影像是應用程式或服務，且其組態和相依性的靜態表示。

若要執行的應用程式或服務，應用程式的影像會具現化建立容器，將 Docker 主機執行。 一開始測試容器，在開發環境或 PC。

您將影像儲存在登錄中，做為程式庫的映像。 您需要部署至生產環境 orchestrators 時有登錄。 Docker 所維護透過公用登錄[Docker Hub](https://hub.docker.com/); 其他廠商提供的映像的不同集合的登錄。 或者，企業可以讓私人登錄在內部自己的 Docker 映像。

圖 1-4 顯示映像和登錄在 Docker 中的其他元件關聯的方式。 它也會顯示從廠商的多個登錄機提供項目。

![](./media/image4.png)

圖 1-4： 的 Docker 詞彙和概念的分類表

將映像放在登錄中，您可以儲存靜態和不可變的應用程式位元，包括所有其相依性，在架構層級。 您可以版本和多個環境中部署映像，然後因此，提供一致的部署單位。

私人映像登錄會裝載於內部，或在雲端中，建議用於下列情況：

-   您的映像必須共用可公開由於機密性。

-   您想要有您的映像與所選的部署環境之間的最小的網路延遲。 比方說，如果 Azure 為您的生產環境，您可能想要儲存您的映像在 Azure 容器登錄中，因此網路延遲會最小。 類似的方式，如果您的生產環境內部，您可以將內部部署 Docker Trusted Registry 可用相同的區域網路內。

>[!div class="step-by-step"]
[上一個](docker-terminology.md) [下一步] (Docker-應用程式的生命週期/index.md)
