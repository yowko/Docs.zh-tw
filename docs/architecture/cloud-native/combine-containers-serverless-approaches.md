---
title: 為雲端原生服務結合容器和無伺服器方法
description: 結合容器和 Kubernetes 與無伺服器方法
ms.date: 05/13/2020
ms.openlocfilehash: 67eee89659026db06eb16ef6f1154ab6935725a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614197"
---
# <a name="combining-containers-and-serverless-approaches"></a><span data-ttu-id="fa103-103">結合容器和無伺服器方法</span><span class="sxs-lookup"><span data-stu-id="fa103-103">Combining containers and serverless approaches</span></span>

<span data-ttu-id="fa103-104">雲端原生應用程式通常會利用容器和協調流程來執行服務。</span><span class="sxs-lookup"><span data-stu-id="fa103-104">Cloud-native applications typically implement services leveraging containers and orchestration.</span></span> <span data-ttu-id="fa103-105">通常會有機會將部分應用程式的服務公開為 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="fa103-105">There are often opportunities to expose some of the application's services as Azure Functions.</span></span> <span data-ttu-id="fa103-106">不過，在部署至 Kubernetes 的雲端原生應用程式中，利用此相同工具組中的 Azure Functions 是很好的做法。</span><span class="sxs-lookup"><span data-stu-id="fa103-106">However, with a cloud-native app deployed to Kubernetes, it would be nice to leverage Azure Functions within this same toolset.</span></span> <span data-ttu-id="fa103-107">幸好，您可以將 Azure Functions 包裝在 Docker 容器內，並使用與 Kubernetes 應用程式其餘部分相同的進程和工具進行部署。</span><span class="sxs-lookup"><span data-stu-id="fa103-107">Fortunately, you can wrap Azure Functions inside Docker containers and deploy them using the same processes and tools as the rest of your Kubernetes-based app.</span></span>

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a><span data-ttu-id="fa103-108">使用無伺服器的容器有何意義？</span><span class="sxs-lookup"><span data-stu-id="fa103-108">When does it make sense to use containers with serverless?</span></span>

<span data-ttu-id="fa103-109">您的 Azure 函數不知道其部署所在的平臺。</span><span class="sxs-lookup"><span data-stu-id="fa103-109">Your Azure Function has no knowledge of the platform on which it's deployed.</span></span> <span data-ttu-id="fa103-110">在某些情況下，您可能會有特定需求，而且需要自訂您的函式程式碼將在其上執行的環境。</span><span class="sxs-lookup"><span data-stu-id="fa103-110">For some scenarios, you may have specific requirements and need to customize the environment on which your function code will run.</span></span> <span data-ttu-id="fa103-111">您需要支援相依性的自訂映射，或預設映射不支援的設定。</span><span class="sxs-lookup"><span data-stu-id="fa103-111">You'll need a custom image that supports dependencies or a configuration not supported by the default image.</span></span> <span data-ttu-id="fa103-112">在這些情況下，在自訂的 Docker 容器中部署您的函式是合理的。</span><span class="sxs-lookup"><span data-stu-id="fa103-112">In these cases, it makes sense to deploy your function in a custom Docker container.</span></span>

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a><span data-ttu-id="fa103-113">何時應避免使用 Azure Functions 的容器？</span><span class="sxs-lookup"><span data-stu-id="fa103-113">When should you avoid using containers with Azure Functions?</span></span>

<span data-ttu-id="fa103-114">如果您想要使用取用計費，就無法在容器中執行您的函式。</span><span class="sxs-lookup"><span data-stu-id="fa103-114">If you want to use consumption billing, you won't be able to run your function in a container.</span></span> <span data-ttu-id="fa103-115">此外，如果您將函式部署至 Kubernetes 叢集，將不再受益于 Azure Functions 所提供的內建調整。</span><span class="sxs-lookup"><span data-stu-id="fa103-115">What's more, if you deploy your function to a Kubernetes cluster, you'll no longer benefit from the built-in scaling provided by Azure Functions.</span></span> <span data-ttu-id="fa103-116">您將需要使用 Kubernetes 的調整功能，如本章稍早所述。</span><span class="sxs-lookup"><span data-stu-id="fa103-116">You'll need to use Kubernetes' scaling features, described earlier in this chapter.</span></span>

## <a name="how-to-combine-serverless-and-docker-containers"></a><span data-ttu-id="fa103-117">如何結合無伺服器和 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="fa103-117">How to combine serverless and Docker containers</span></span>

<span data-ttu-id="fa103-118">若要將 Azure 函式包裝在 Docker 容器中，請安裝[Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) ，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="fa103-118">To wrap an Azure Function in a Docker container, install the [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) and then run the following command:</span></span>

```console
func init ProjectName --worker-runtime dotnet --docker
```

<span data-ttu-id="fa103-119">建立專案時，會包含 Dockerfile，以及設定為的背景工作執行時間 `dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="fa103-119">When the project is created, it will include a Dockerfile and the worker runtime configured to `dotnet`.</span></span> <span data-ttu-id="fa103-120">現在，您可以在本機建立及測試您的函式。</span><span class="sxs-lookup"><span data-stu-id="fa103-120">Now, you can create and test your function locally.</span></span> <span data-ttu-id="fa103-121">使用和命令來建立並執行它 `docker build` `docker run` 。</span><span class="sxs-lookup"><span data-stu-id="fa103-121">Build and run it using the  `docker build` and `docker run` commands.</span></span> <span data-ttu-id="fa103-122">如需開始使用 Docker 支援來建立 Azure Functions 的詳細步驟，請參閱[使用自訂映射在 Linux 上建立](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)函式教學課程。</span><span class="sxs-lookup"><span data-stu-id="fa103-122">For detailed steps to get started building Azure Functions with Docker support, see the [Create a function on Linux using a custom image](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) tutorial.</span></span>

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a><span data-ttu-id="fa103-123">如何結合無伺服器和 Kubernetes 與 KEDA</span><span class="sxs-lookup"><span data-stu-id="fa103-123">How to combine serverless and Kubernetes with KEDA</span></span>

<span data-ttu-id="fa103-124">在本章中，您已瞭解 Azure Functions 的平臺會自動相應放大以符合需求。</span><span class="sxs-lookup"><span data-stu-id="fa103-124">In this chapter, you've seen that the Azure Functions' platform automatically scales out to meet demand.</span></span> <span data-ttu-id="fa103-125">不過，將容器化函式部署到 AKS 時，您會失去內建的調整功能。</span><span class="sxs-lookup"><span data-stu-id="fa103-125">When deploying containerized functions to AKS, however, you lose the built-in scaling functionality.</span></span> <span data-ttu-id="fa103-126">若要解決這種情況，就會產生以[Kubernetes 為基礎的事件驅動（KEDA）](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)。</span><span class="sxs-lookup"><span data-stu-id="fa103-126">To the rescue comes [Kubernetes-based Event Driven (KEDA)](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).</span></span> <span data-ttu-id="fa103-127">它可為包含容器化函式提供更細緻的自動調整 `event-driven Kubernetes workloads,` 功能。</span><span class="sxs-lookup"><span data-stu-id="fa103-127">It enables fine-grained autoscaling for `event-driven Kubernetes workloads,` including containerized functions.</span></span>

<span data-ttu-id="fa103-128">KEDA 提供事件驅動的調整功能給 Docker 容器中的函式執行時間。</span><span class="sxs-lookup"><span data-stu-id="fa103-128">KEDA provides event-driven scaling functionality to the Functions' runtime in a Docker container.</span></span> <span data-ttu-id="fa103-129">KEDA 可以根據負載，從零個實例（沒有發生的事件）相應縮小至 `n instances` 。</span><span class="sxs-lookup"><span data-stu-id="fa103-129">KEDA can scale from zero instances (when no events are occurring) out to `n instances`, based on load.</span></span> <span data-ttu-id="fa103-130">它會將自訂計量公開至 Kubernetes 自動調整程式（水準 Pod 自動調整程式）來啟用自動調整。</span><span class="sxs-lookup"><span data-stu-id="fa103-130">It enables autoscaling by exposing custom metrics to the Kubernetes autoscaler (Horizontal Pod Autoscaler).</span></span> <span data-ttu-id="fa103-131">將函式容器與 KEDA 搭配使用，可讓您在任何 Kubernetes 叢集中複寫無伺服器函式功能。</span><span class="sxs-lookup"><span data-stu-id="fa103-131">Using Functions containers with KEDA makes it possible to replicate serverless function capabilities in any Kubernetes cluster.</span></span>

<span data-ttu-id="fa103-132">值得注意的是，KEDA 專案現在是由雲端原生運算基礎（由 CNCF）所管理。</span><span class="sxs-lookup"><span data-stu-id="fa103-132">It is worth noting that the KEDA project is now managed by the Cloud Native Computing Foundation (CNCF).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fa103-133">[上一個](leverage-serverless-functions.md) 
>[下一步](deploy-containers-azure.md)</span><span class="sxs-lookup"><span data-stu-id="fa103-133">[Previous](leverage-serverless-functions.md)
[Next](deploy-containers-azure.md)</span></span>
