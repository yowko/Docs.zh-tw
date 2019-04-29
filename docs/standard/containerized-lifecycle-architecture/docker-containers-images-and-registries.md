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
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="80080-103">Docker 容器、映像和登錄</span><span class="sxs-lookup"><span data-stu-id="80080-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="80080-104">使用 Docker 時，您建立應用程式或服務和封裝它和其相依性至容器映像。</span><span class="sxs-lookup"><span data-stu-id="80080-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="80080-105">映像是應用程式或服務及其組態和相依性的靜態表示。</span><span class="sxs-lookup"><span data-stu-id="80080-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="80080-106">為了執行應用程式或服務，應用程式的映像會具現化以建立容器，並將在 Docker 主機上執行該容器。</span><span class="sxs-lookup"><span data-stu-id="80080-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="80080-107">這些容器一開始會在開發環境或電腦上進行測試。</span><span class="sxs-lookup"><span data-stu-id="80080-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="80080-108">您將影像儲存在登錄中，做為程式庫的映像。</span><span class="sxs-lookup"><span data-stu-id="80080-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="80080-109">部署至生產協調器時，您需要登錄。</span><span class="sxs-lookup"><span data-stu-id="80080-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="80080-110">Docker 會透過 [Docker Hub](https://hub.docker.com/) 維護公開登錄；其他廠商則會針對不同的映像集合提供登錄，包括 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="80080-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="80080-111">或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。</span><span class="sxs-lookup"><span data-stu-id="80080-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="80080-112">圖 1-4 顯示映像和登錄在 Docker 中的如何與其他元件。</span><span class="sxs-lookup"><span data-stu-id="80080-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="80080-113">它也顯示來自廠商的多個登錄供應項目。</span><span class="sxs-lookup"><span data-stu-id="80080-113">It also shows the multiple registry offerings from vendors.</span></span>

![在 Docker 中的基本分類：登錄就像是出版品介紹儲存，可用於建置容器來執行服務或 web 應用程式提取映像的所在。](./media/image4.png)

<span data-ttu-id="80080-118">**圖 1-4**。</span><span class="sxs-lookup"><span data-stu-id="80080-118">**Figure 1-4**.</span></span> <span data-ttu-id="80080-119">Docker 術語和概念分類</span><span class="sxs-lookup"><span data-stu-id="80080-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="80080-120">將映像放在登錄中，您可以儲存靜態和不可變的應用程式位元，包括所有其相依性，在架構層級。</span><span class="sxs-lookup"><span data-stu-id="80080-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="80080-121">您接著可以版本和多個環境中部署映像，藉此提供一致的部署單位。</span><span class="sxs-lookup"><span data-stu-id="80080-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="80080-122">建議在下列情況下使用私人映像登錄 (不論是裝載在內部部署或在雲端中)：</span><span class="sxs-lookup"><span data-stu-id="80080-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="80080-123">基於機密性，您的映像不得公開共用。</span><span class="sxs-lookup"><span data-stu-id="80080-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="80080-124">您想要在映像與所選擇的部署環境之間有最低的網路延遲。</span><span class="sxs-lookup"><span data-stu-id="80080-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="80080-125">比方說，如果您的生產環境是 Azure，您可能想要儲存在映像[Azure Container Registry](https://azure.microsoft.com/services/container-registry/)使網路延遲最少。</span><span class="sxs-lookup"><span data-stu-id="80080-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="80080-126">同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。</span><span class="sxs-lookup"><span data-stu-id="80080-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="80080-127">[上一頁](docker-terminology.md)
>[下一頁](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="80080-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
