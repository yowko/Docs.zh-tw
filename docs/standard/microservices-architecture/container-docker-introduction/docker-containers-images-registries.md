---
title: Docker 容器、映像和登錄
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 容器、映像和登錄
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 02ee40ebab37ae1898dc46e215728cba512a23e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574082"
---
# <a name="docker-containers-images-and-registries"></a>Docker 容器、映像和登錄

使用 Docker 時，開發人員可以建立應用程式或服務，並將該應用程式或服務及其相依性封裝成一個容器映像。 映像是應用程式或服務及其組態和相依性的靜態表示。

為了執行應用程式或服務，應用程式的映像會具現化以建立容器，並將在 Docker 主機上執行該容器。 這些容器一開始會在開發環境或電腦上進行測試。

開發人員應該將映像儲存在登錄中，該登錄可作為映像庫，而且在部署至生產協調器時需要用到。 Docker 透過 [Docker Hub](https://hub.docker.com/) 維護一個公開登錄；其他廠商會針對不同的映像集合提供登錄。 或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。

圖 2-4 顯示 Docker 中的映像和登錄與其他元件的關係。 它也顯示來自廠商的多個登錄供應項目。

![](./media/image5.PNG)

**圖 2-4**： Docker 術語和概念分類

將映像放在登錄中可讓您儲存靜態和不可變的應用程式位元，包括其在架構層級的所有相依性。 您可以接著在多個環境中建立這些映像的版本並加以部署，因此提供一致的部署單位。

建議在下列情況下使用私人映像登錄 (不論是裝載在內部部署或在雲端中)：

-   基於機密性，您的映像不得公開共用。

-   您想要在映像與所選擇的部署環境之間有最低的網路延遲。 例如，如果您的生產環境是 Azure 雲端，您可能想要將映像儲存在 Azure Container Registry 中，因此網路延遲會最小。 同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。

>[!div class="step-by-step"]
[上一個] (docker-terminology.md) [下一個] (../net-core-net-framework-containers/index.md)
