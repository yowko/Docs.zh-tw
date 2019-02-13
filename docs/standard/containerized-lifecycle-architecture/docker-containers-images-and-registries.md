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
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="26263-103">Docker 容器、映像和登錄</span><span class="sxs-lookup"><span data-stu-id="26263-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="26263-104">使用 Docker 時，您建立應用程式或服務和封裝它和其相依性至容器映像。</span><span class="sxs-lookup"><span data-stu-id="26263-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="26263-105">映像是應用程式或服務及其組態和相依性的靜態表示。</span><span class="sxs-lookup"><span data-stu-id="26263-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="26263-106">為了執行應用程式或服務，應用程式的映像會具現化以建立容器，並將在 Docker 主機上執行該容器。</span><span class="sxs-lookup"><span data-stu-id="26263-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="26263-107">這些容器一開始會在開發環境或電腦上進行測試。</span><span class="sxs-lookup"><span data-stu-id="26263-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="26263-108">您將影像儲存在登錄中，做為程式庫的映像。</span><span class="sxs-lookup"><span data-stu-id="26263-108">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="26263-109">部署至生產協調器時，您需要登錄。</span><span class="sxs-lookup"><span data-stu-id="26263-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="26263-110">Docker 透過 [Docker Hub](https://hub.docker.com/) 維護一個公開登錄；其他廠商會針對不同的映像集合提供登錄。</span><span class="sxs-lookup"><span data-stu-id="26263-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="26263-111">或者，企業可以在內部部署有針對其專屬 Docker 映像的私人登錄。</span><span class="sxs-lookup"><span data-stu-id="26263-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="26263-112">圖 1-4 顯示映像和登錄在 Docker 中的如何與其他元件。</span><span class="sxs-lookup"><span data-stu-id="26263-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="26263-113">它也顯示來自廠商的多個登錄供應項目。</span><span class="sxs-lookup"><span data-stu-id="26263-113">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="26263-114">圖 1-4:Docker 術語和概念分類</span><span class="sxs-lookup"><span data-stu-id="26263-114">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="26263-115">將映像放在登錄中，您可以儲存靜態和不可變的應用程式位元，包括所有其相依性，在架構層級。</span><span class="sxs-lookup"><span data-stu-id="26263-115">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="26263-116">您接著可以版本和多個環境中部署映像，藉此提供一致的部署單位。</span><span class="sxs-lookup"><span data-stu-id="26263-116">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="26263-117">私人映像登錄時，裝載在內部部署或在雲端中，建議用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="26263-117">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="26263-118">基於機密性，您的映像不得公開共用。</span><span class="sxs-lookup"><span data-stu-id="26263-118">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="26263-119">您想要在映像與所選擇的部署環境之間有最低的網路延遲。</span><span class="sxs-lookup"><span data-stu-id="26263-119">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="26263-120">比方說，如果您的生產環境是 Azure，您可能想要儲存在 Azure Container Registry 的映像，使網路延遲會最小。</span><span class="sxs-lookup"><span data-stu-id="26263-120">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="26263-121">同樣地，如果您的生產環境是內部部署，您可能想要在相同的區域網路內提供內部部署 Docker Trusted Registry。</span><span class="sxs-lookup"><span data-stu-id="26263-121">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="26263-122">[上一頁](docker-terminology.md)
>[下一頁](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="26263-122">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
