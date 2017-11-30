---
title: "Docker 容器、 影像和登錄"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Docker 容器、 影像和登錄"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="5f661-104">Docker 容器、 影像和登錄</span><span class="sxs-lookup"><span data-stu-id="5f661-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="5f661-105">當使用 Docker 時，開發人員建立應用程式或服務和封裝它的容器映像至其相依性。</span><span class="sxs-lookup"><span data-stu-id="5f661-105">When using Docker, a developer creates an app or service and packages it and its dependencies into a container image.</span></span> <span data-ttu-id="5f661-106">影像是應用程式或服務，且其組態和相依性的靜態表示。</span><span class="sxs-lookup"><span data-stu-id="5f661-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="5f661-107">若要執行的應用程式或服務，應用程式的影像會具現化建立容器，將 Docker 主機執行。</span><span class="sxs-lookup"><span data-stu-id="5f661-107">To run the app or service, the app’s image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="5f661-108">一開始測試容器，在開發環境或 PC。</span><span class="sxs-lookup"><span data-stu-id="5f661-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="5f661-109">開發人員應該將影像儲存在登錄中，可做為程式庫的映像並部署至生產環境 orchestrators 時需要。</span><span class="sxs-lookup"><span data-stu-id="5f661-109">Developers should store images in a registry, which acts as a library of images and is needed when deploying to production orchestrators.</span></span> <span data-ttu-id="5f661-110">Docker 所維護透過公用登錄[Docker Hub](https://hub.docker.com/); 其他廠商提供的映像的不同集合的登錄。</span><span class="sxs-lookup"><span data-stu-id="5f661-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="5f661-111">或者，企業可以讓私人登錄在內部自己的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="5f661-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="5f661-112">圖 2-4 顯示映像和登錄在 Docker 中的其他元件關聯的方式。</span><span class="sxs-lookup"><span data-stu-id="5f661-112">Figure 2-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="5f661-113">它也會顯示從廠商的多個登錄機提供項目。</span><span class="sxs-lookup"><span data-stu-id="5f661-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image5.PNG)

<span data-ttu-id="5f661-114">**圖 2-4**。</span><span class="sxs-lookup"><span data-stu-id="5f661-114">**Figure 2-4**.</span></span> <span data-ttu-id="5f661-115">Docker 詞彙和概念的分類表</span><span class="sxs-lookup"><span data-stu-id="5f661-115">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="5f661-116">將映像放在登錄中，可讓您儲存靜態和不可變的應用程式位元，包括在架構層級及其所有相依性。</span><span class="sxs-lookup"><span data-stu-id="5f661-116">Putting images in a registry lets you store static and immutable application bits, including all their dependencies at a framework level.</span></span> <span data-ttu-id="5f661-117">這些映像可以則是建立版本和多個環境中部署，並因此提供一致的部署單位。</span><span class="sxs-lookup"><span data-stu-id="5f661-117">Those images can then be versioned and deployed in multiple environments and therefore provide a consistent deployment unit.</span></span>

<span data-ttu-id="5f661-118">私人映像登錄裝載在內部部署或在雲端中，建議使用時機：</span><span class="sxs-lookup"><span data-stu-id="5f661-118">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

-   <span data-ttu-id="5f661-119">您的映像必須共用可公開由於機密性。</span><span class="sxs-lookup"><span data-stu-id="5f661-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="5f661-120">您想要有您的映像與所選的部署環境之間的最小的網路延遲。</span><span class="sxs-lookup"><span data-stu-id="5f661-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="5f661-121">比方說，如果您的生產環境是 Azure 雲端，您可能想要儲存您的映像在 Azure 容器登錄中，因此網路延遲會最小。</span><span class="sxs-lookup"><span data-stu-id="5f661-121">For example, if your production environment is Azure cloud, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="5f661-122">類似的方式，如果您的生產環境內部，您可以將內部部署 Docker Trusted Registry 可用相同的區域網路內。</span><span class="sxs-lookup"><span data-stu-id="5f661-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="5f661-123">[上一個](docker-terminology.md) [下一步] (.../net-core-net-framework-containers/index.md)</span><span class="sxs-lookup"><span data-stu-id="5f661-123">[Previous] (docker-terminology.md) [Next] (../net-core-net-framework-containers/index.md)</span></span>
