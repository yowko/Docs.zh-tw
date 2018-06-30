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
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="35bd1-103">Docker 容器、映像和登錄</span><span class="sxs-lookup"><span data-stu-id="35bd1-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="35bd1-104">當使用 Docker 時，您建立應用程式或服務和封裝它，並傳遞至容器映像及其相依性。</span><span class="sxs-lookup"><span data-stu-id="35bd1-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="35bd1-105">映像是應用程式或服務及其組態和相依性的靜態表示。</span><span class="sxs-lookup"><span data-stu-id="35bd1-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="35bd1-106">若要執行的應用程式或服務，應用程式的影像會具現化建立容器，將 Docker 主機執行。</span><span class="sxs-lookup"><span data-stu-id="35bd1-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="35bd1-107">這些容器一開始會在開發環境或電腦上進行測試。</span><span class="sxs-lookup"><span data-stu-id="35bd1-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="35bd1-108">您將影像儲存在登錄中，做為程式庫的映像。</span><span class="sxs-lookup"><span data-stu-id="35bd1-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="35bd1-109">您需要部署至生產環境 orchestrators 時有登錄。</span><span class="sxs-lookup"><span data-stu-id="35bd1-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="35bd1-110">Docker 透過 [Docker Hub](https://hub.docker.com/) 維護一個公開登錄；其他廠商會針對不同的映像集合提供登錄。</span><span class="sxs-lookup"><span data-stu-id="35bd1-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="35bd1-111">或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。</span><span class="sxs-lookup"><span data-stu-id="35bd1-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="35bd1-112">圖 1-4 顯示映像和登錄在 Docker 中的其他元件關聯的方式。</span><span class="sxs-lookup"><span data-stu-id="35bd1-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="35bd1-113">它也顯示來自廠商的多個登錄供應項目。</span><span class="sxs-lookup"><span data-stu-id="35bd1-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="35bd1-114">圖 1-4： 的 Docker 詞彙和概念的分類表</span><span class="sxs-lookup"><span data-stu-id="35bd1-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="35bd1-115">將映像放在登錄中，您可以儲存靜態和不可變的應用程式位元，包括所有其相依性，在架構層級。</span><span class="sxs-lookup"><span data-stu-id="35bd1-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="35bd1-116">您可以版本和多個環境中部署映像，然後因此，提供一致的部署單位。</span><span class="sxs-lookup"><span data-stu-id="35bd1-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="35bd1-117">私人映像登錄會裝載於內部，或在雲端中，建議用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="35bd1-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="35bd1-118">基於機密性，您的映像不得公開共用。</span><span class="sxs-lookup"><span data-stu-id="35bd1-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="35bd1-119">您想要在映像與所選擇的部署環境之間有最低的網路延遲。</span><span class="sxs-lookup"><span data-stu-id="35bd1-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="35bd1-120">比方說，如果 Azure 為您的生產環境，您可能想要儲存您的映像在 Azure 容器登錄中，因此網路延遲會最小。</span><span class="sxs-lookup"><span data-stu-id="35bd1-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="35bd1-121">同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。</span><span class="sxs-lookup"><span data-stu-id="35bd1-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="35bd1-122">[上一頁](docker-terminology.md)
[下一頁](Docker-application-lifecycle/index.md)</span><span class="sxs-lookup"><span data-stu-id="35bd1-122">[Previous](docker-terminology.md)
[Next](Docker-application-lifecycle/index.md)</span></span>
