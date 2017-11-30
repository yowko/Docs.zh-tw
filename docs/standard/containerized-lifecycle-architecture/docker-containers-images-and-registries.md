---
title: "Docker 容器、 影像和登錄"
description: "Microsoft 平台和工具與 Docker 容器化應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b115b25d8ae335aafbe41bac0d694170be7e3c49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="ff789-104">Docker 容器、 影像和登錄</span><span class="sxs-lookup"><span data-stu-id="ff789-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="ff789-105">當使用 Docker 時，您建立應用程式或服務和封裝它，並傳遞至容器映像及其相依性。</span><span class="sxs-lookup"><span data-stu-id="ff789-105">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="ff789-106">影像是應用程式或服務，且其組態和相依性的靜態表示。</span><span class="sxs-lookup"><span data-stu-id="ff789-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="ff789-107">若要執行的應用程式或服務，應用程式的影像會具現化建立容器，將 Docker 主機執行。</span><span class="sxs-lookup"><span data-stu-id="ff789-107">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="ff789-108">一開始測試容器，在開發環境或 PC。</span><span class="sxs-lookup"><span data-stu-id="ff789-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="ff789-109">您將影像儲存在登錄中，做為程式庫的映像。</span><span class="sxs-lookup"><span data-stu-id="ff789-109">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="ff789-110">您需要部署至生產環境 orchestrators 時有登錄。</span><span class="sxs-lookup"><span data-stu-id="ff789-110">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="ff789-111">Docker 所維護透過公用登錄[Docker Hub](https://hub.docker.com/); 其他廠商提供的映像的不同集合的登錄。</span><span class="sxs-lookup"><span data-stu-id="ff789-111">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="ff789-112">或者，企業可以讓私人登錄在內部自己的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="ff789-112">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="ff789-113">圖 1-4 顯示映像和登錄在 Docker 中的其他元件關聯的方式。</span><span class="sxs-lookup"><span data-stu-id="ff789-113">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="ff789-114">它也會顯示從廠商的多個登錄機提供項目。</span><span class="sxs-lookup"><span data-stu-id="ff789-114">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="ff789-115">圖 1-4： 的 Docker 詞彙和概念的分類表</span><span class="sxs-lookup"><span data-stu-id="ff789-115">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="ff789-116">將映像放在登錄中，您可以儲存靜態和不可變的應用程式位元，包括所有其相依性，在架構層級。</span><span class="sxs-lookup"><span data-stu-id="ff789-116">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="ff789-117">您可以版本和多個環境中部署映像，然後因此，提供一致的部署單位。</span><span class="sxs-lookup"><span data-stu-id="ff789-117">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="ff789-118">私人映像登錄會裝載於內部，或在雲端中，建議用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="ff789-118">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="ff789-119">您的映像必須共用可公開由於機密性。</span><span class="sxs-lookup"><span data-stu-id="ff789-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="ff789-120">您想要有您的映像與所選的部署環境之間的最小的網路延遲。</span><span class="sxs-lookup"><span data-stu-id="ff789-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="ff789-121">比方說，如果 Azure 為您的生產環境，您可能想要儲存您的映像在 Azure 容器登錄中，因此網路延遲會最小。</span><span class="sxs-lookup"><span data-stu-id="ff789-121">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="ff789-122">類似的方式，如果您的生產環境內部，您可以將內部部署 Docker Trusted Registry 可用相同的區域網路內。</span><span class="sxs-lookup"><span data-stu-id="ff789-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="ff789-123">[上一個](docker-terminology.md) [下一步] (Docker-應用程式的生命週期/index.md)</span><span class="sxs-lookup"><span data-stu-id="ff789-123">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>
