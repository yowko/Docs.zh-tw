---
title: Docker 容器、映像和登錄
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: ff5a1f3e4b09ac9f7ea600d3f127523b96fcce55
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106359"
---
# <a name="docker-containers-images-and-registries"></a>Docker 容器、映像和登錄

當使用 Docker 時，您建立應用程式或服務和封裝它，並傳遞至容器映像及其相依性。 映像是應用程式或服務及其組態和相依性的靜態表示。

若要執行的應用程式或服務，應用程式的影像會具現化建立容器，將 Docker 主機執行。 這些容器一開始會在開發環境或電腦上進行測試。

您將影像儲存在登錄中，做為程式庫的映像。 您需要部署至生產環境 orchestrators 時有登錄。 Docker 透過 [Docker Hub](https://hub.docker.com/) 維護一個公開登錄；其他廠商會針對不同的映像集合提供登錄。 或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。

圖 1-4 顯示映像和登錄在 Docker 中的其他元件關聯的方式。 它也顯示來自廠商的多個登錄供應項目。

![](./media/image4.png)

圖 1-4： 的 Docker 詞彙和概念的分類表

將映像放在登錄中，您可以儲存靜態和不可變的應用程式位元，包括所有其相依性，在架構層級。 您可以版本和多個環境中部署映像，然後因此，提供一致的部署單位。

私人映像登錄會裝載於內部，或在雲端中，建議用於下列情況：

-   基於機密性，您的映像不得公開共用。

-   您想要在映像與所選擇的部署環境之間有最低的網路延遲。 比方說，如果 Azure 為您的生產環境，您可能想要儲存您的映像在 Azure 容器登錄中，因此網路延遲會最小。 同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。

>[!div class="step-by-step"]
[上一頁](docker-terminology.md)
[下一頁](Docker-application-lifecycle/index.md)
