---
title: Docker 容器、映像和登錄
description: 了解登錄播放整體部署應用程式的 Docker 方式的重要角色。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 7a2e20e09561a5cc91aa29059fb8d19a14205bb5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221195"
---
# <a name="docker-containers-images-and-registries"></a>Docker 容器、映像和登錄

使用 Docker 時，您建立應用程式或服務和封裝它和其相依性至容器映像。 映像是應用程式或服務及其組態和相依性的靜態表示。

為了執行應用程式或服務，應用程式的映像會具現化以建立容器，並將在 Docker 主機上執行該容器。 這些容器一開始會在開發環境或電腦上進行測試。

您將影像儲存在登錄中，做為程式庫的映像。 部署至生產協調器時，您需要登錄。 Docker 透過 [Docker Hub](https://hub.docker.com/) 維護一個公開登錄；其他廠商會針對不同的映像集合提供登錄。 或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。

圖 1-4 顯示映像和登錄在 Docker 中的如何與其他元件。 它也顯示來自廠商的多個登錄供應項目。

![](./media/image4.png)

圖 1-4:Docker 術語和概念分類

將映像放在登錄中，您可以儲存靜態和不可變的應用程式位元，包括所有其相依性，在架構層級。 您接著可以版本和多個環境中部署映像，藉此提供一致的部署單位。

私人映像登錄時，裝載在內部部署或在雲端中，建議用於下列情況：

-   基於機密性，您的映像不得公開共用。

-   您想要在映像與所選擇的部署環境之間有最低的網路延遲。 比方說，如果您的生產環境是 Azure，您可能想要儲存在 Azure Container Registry 的映像，使網路延遲會最小。 同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。

>[!div class="step-by-step"]
>[上一頁](docker-terminology.md)
>[下一頁](road-to-modern-applications-based-on-containers.md)
