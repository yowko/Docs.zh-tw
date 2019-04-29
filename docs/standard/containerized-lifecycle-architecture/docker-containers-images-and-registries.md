---
title: Docker 容器、映像和登錄
description: 了解登錄播放整體部署應用程式的 Docker 方式的重要角色。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e69490734a03cf58bf8534bc9e31110a11d44c58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795316"
---
# <a name="docker-containers-images-and-registries"></a>Docker 容器、映像和登錄

使用 Docker 時，您建立應用程式或服務和封裝它和其相依性至容器映像。 映像是應用程式或服務及其組態和相依性的靜態表示。

為了執行應用程式或服務，應用程式的映像會具現化以建立容器，並將在 Docker 主機上執行該容器。 這些容器一開始會在開發環境或電腦上進行測試。

您將影像儲存在登錄中，做為程式庫的映像。 部署至生產協調器時，您需要登錄。 Docker 會透過 [Docker Hub](https://hub.docker.com/) 維護公開登錄；其他廠商則會針對不同的映像集合提供登錄，包括 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)。 或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。

圖 1-4 顯示映像和登錄在 Docker 中的如何與其他元件。 它也顯示來自廠商的多個登錄供應項目。

![在 Docker 中的基本分類：登錄就像是出版品介紹儲存，可用於建置容器來執行服務或 web 應用程式提取映像的所在。 有私用 Docker 登錄在內部和公用雲端上。 Docker Hub 是由 Docker 維護的公開登錄，連同 Docker Trusted Registry 這項企業級解決方案，Azure 提供了 Azure Container Registry。 AWS、Google 和其他服務也有容器登錄。](./media/image4.png)

**圖 1-4**。 Docker 術語和概念分類

將映像放在登錄中，您可以儲存靜態和不可變的應用程式位元，包括所有其相依性，在架構層級。 您接著可以版本和多個環境中部署映像，藉此提供一致的部署單位。

建議在下列情況下使用私人映像登錄 (不論是裝載在內部部署或在雲端中)：

- 基於機密性，您的映像不得公開共用。

- 您想要在映像與所選擇的部署環境之間有最低的網路延遲。 比方說，如果您的生產環境是 Azure，您可能想要儲存在映像[Azure Container Registry](https://azure.microsoft.com/services/container-registry/)使網路延遲最少。 同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。

>[!div class="step-by-step"]
>[上一頁](docker-terminology.md)
>[下一頁](road-to-modern-applications-based-on-containers.md)
