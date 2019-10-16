---
title: Docker 容器、映像和登錄
description: 了解在使用 Docker 部署應用程式的整個過程中，登錄扮演何種重要角色。
ms.date: 02/15/2019
ms.openlocfilehash: 32240ac4f6dec67531d8e618cff153d235c073c7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394615"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="ab179-103">Docker 容器、映像和登錄</span><span class="sxs-lookup"><span data-stu-id="ab179-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="ab179-104">使用 Docker 時，您可以建立應用程式或服務，並將其與相依性封裝成一個容器映像。</span><span class="sxs-lookup"><span data-stu-id="ab179-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="ab179-105">映像是應用程式或服務及其組態和相依性的靜態表示。</span><span class="sxs-lookup"><span data-stu-id="ab179-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="ab179-106">為了執行應用程式或服務，應用程式的映像會具現化以建立容器，並將在 Docker 主機上執行該容器。</span><span class="sxs-lookup"><span data-stu-id="ab179-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="ab179-107">這些容器一開始會在開發環境或電腦上進行測試。</span><span class="sxs-lookup"><span data-stu-id="ab179-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="ab179-108">您可將映像儲存在登錄中，由該登錄作為映像庫。</span><span class="sxs-lookup"><span data-stu-id="ab179-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="ab179-109">若要部署至實際執行的協調器，您需要使用登錄。</span><span class="sxs-lookup"><span data-stu-id="ab179-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="ab179-110">Docker 會透過 [Docker Hub](https://hub.docker.com/) 維護公開登錄；其他廠商則會針對不同的映像集合提供登錄，包括 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="ab179-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="ab179-111">或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。</span><span class="sxs-lookup"><span data-stu-id="ab179-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="ab179-112">圖 1-4 顯示 Docker 中映像和登錄與其他元件的關係。</span><span class="sxs-lookup"><span data-stu-id="ab179-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="ab179-113">它也顯示來自廠商的多個登錄供應項目。</span><span class="sxs-lookup"><span data-stu-id="ab179-113">It also shows the multiple registry offerings from vendors.</span></span>

![顯示 Docker 中基本分類法的圖表。](./media/docker-containers-images-and-registries/taxonomy-docker-terms-concepts.png)

<span data-ttu-id="ab179-115">**圖 1-4**。</span><span class="sxs-lookup"><span data-stu-id="ab179-115">**Figure 1-4**.</span></span> <span data-ttu-id="ab179-116">Docker 術語和概念分類</span><span class="sxs-lookup"><span data-stu-id="ab179-116">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="ab179-117">登錄就像是一個書架，映像會存放於此處，並供提取用以建置容器，以執行服務或 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab179-117">The registry is like a bookshelf where images are stored and available to be pulled for building containers to run services or web apps.</span></span> <span data-ttu-id="ab179-118">內部部署和公用雲端上都會有私人 Docker 登錄。</span><span class="sxs-lookup"><span data-stu-id="ab179-118">There are private Docker registries on-premises and on the public cloud.</span></span> <span data-ttu-id="ab179-119">Docker Hub 是由 Docker 維護的公開登錄，連同 Docker Trusted Registry 這項企業級解決方案，Azure 提供了 Azure Container Registry。</span><span class="sxs-lookup"><span data-stu-id="ab179-119">Docker Hub is a public registry maintained by Docker, along the Docker Trusted Registry an enterprise-grade solution, Azure offers the Azure Container Registry.</span></span> <span data-ttu-id="ab179-120">AWS、Google 和其他服務也有容器登錄。</span><span class="sxs-lookup"><span data-stu-id="ab179-120">AWS, Google and others also have container registries.</span></span>

<span data-ttu-id="ab179-121">您可以將映像放在登錄中，以儲存靜態和不可變的應用程式位元，包括其在架構層級的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="ab179-121">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="ab179-122">接著，您可以在多個環境中建立這些映像的版本並加以部署，藉此提供一致的部署單位。</span><span class="sxs-lookup"><span data-stu-id="ab179-122">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="ab179-123">建議在下列情況下使用私人映像登錄 (不論是裝載在內部部署或在雲端中)：</span><span class="sxs-lookup"><span data-stu-id="ab179-123">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="ab179-124">基於機密性，您的映像不得公開共用。</span><span class="sxs-lookup"><span data-stu-id="ab179-124">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="ab179-125">您想要在映像與所選擇的部署環境之間有最低的網路延遲。</span><span class="sxs-lookup"><span data-stu-id="ab179-125">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="ab179-126">例如，如果您的生產環境是 Azure，您可以將映像儲存在 [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) 中，使網路延遲降至最低。</span><span class="sxs-lookup"><span data-stu-id="ab179-126">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="ab179-127">同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。</span><span class="sxs-lookup"><span data-stu-id="ab179-127">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ab179-128">[上一頁](docker-terminology.md)
>[下一頁](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="ab179-128">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
