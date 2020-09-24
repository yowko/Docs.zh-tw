---
title: 針對雲端原生服務合併容器和無伺服器方法
description: 結合容器與 Kubernetes 與無伺服器方法
ms.date: 05/13/2020
ms.openlocfilehash: b1b85519ce02ddd1d69735d872cf24fadcc81ef7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160888"
---
# <a name="combining-containers-and-serverless-approaches"></a><span data-ttu-id="87678-103">結合容器和無伺服器方法</span><span class="sxs-lookup"><span data-stu-id="87678-103">Combining containers and serverless approaches</span></span>

<span data-ttu-id="87678-104">雲端原生應用程式通常會利用容器和協調流程來執行服務。</span><span class="sxs-lookup"><span data-stu-id="87678-104">Cloud-native applications typically implement services leveraging containers and orchestration.</span></span> <span data-ttu-id="87678-105">通常會有機會將部分應用程式的服務公開為 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="87678-105">There are often opportunities to expose some of the application's services as Azure Functions.</span></span> <span data-ttu-id="87678-106">不過，在將雲端原生應用程式部署至 Kubernetes 時，在相同的工具組中充分利用 Azure Functions 是很好的方法。</span><span class="sxs-lookup"><span data-stu-id="87678-106">However, with a cloud-native app deployed to Kubernetes, it would be nice to leverage Azure Functions within this same toolset.</span></span> <span data-ttu-id="87678-107">幸好，您可以在 Docker 容器內包裝 Azure Functions，並使用與 Kubernetes 應用程式其餘部分相同的程式和工具來部署它們。</span><span class="sxs-lookup"><span data-stu-id="87678-107">Fortunately, you can wrap Azure Functions inside Docker containers and deploy them using the same processes and tools as the rest of your Kubernetes-based app.</span></span>

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a><span data-ttu-id="87678-108">使用無伺服器的容器有什麼意義？</span><span class="sxs-lookup"><span data-stu-id="87678-108">When does it make sense to use containers with serverless?</span></span>

<span data-ttu-id="87678-109">您的 Azure 函數不知道其部署所在的平臺。</span><span class="sxs-lookup"><span data-stu-id="87678-109">Your Azure Function has no knowledge of the platform on which it's deployed.</span></span> <span data-ttu-id="87678-110">在某些案例中，您可能會有特定需求，而且需要自訂您的函式程式碼將在其上執行的環境。</span><span class="sxs-lookup"><span data-stu-id="87678-110">For some scenarios, you may have specific requirements and need to customize the environment on which your function code will run.</span></span> <span data-ttu-id="87678-111">您需要支援相依性的自訂映射，或預設映射不支援的設定。</span><span class="sxs-lookup"><span data-stu-id="87678-111">You'll need a custom image that supports dependencies or a configuration not supported by the default image.</span></span> <span data-ttu-id="87678-112">在這些情況下，將您的函式部署在自訂 Docker 容器中是合理的。</span><span class="sxs-lookup"><span data-stu-id="87678-112">In these cases, it makes sense to deploy your function in a custom Docker container.</span></span>

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a><span data-ttu-id="87678-113">何時應避免使用 Azure Functions 的容器？</span><span class="sxs-lookup"><span data-stu-id="87678-113">When should you avoid using containers with Azure Functions?</span></span>

<span data-ttu-id="87678-114">如果您想要使用耗用量計費，您將無法在容器中執行您的函式。</span><span class="sxs-lookup"><span data-stu-id="87678-114">If you want to use consumption billing, you won't be able to run your function in a container.</span></span> <span data-ttu-id="87678-115">此外，如果您將函式部署至 Kubernetes 叢集，您將不再受益于 Azure Functions 所提供的內建擴充功能。</span><span class="sxs-lookup"><span data-stu-id="87678-115">What's more, if you deploy your function to a Kubernetes cluster, you'll no longer benefit from the built-in scaling provided by Azure Functions.</span></span> <span data-ttu-id="87678-116">您必須使用 Kubernetes 的調整功能，如本章節稍早所述。</span><span class="sxs-lookup"><span data-stu-id="87678-116">You'll need to use Kubernetes' scaling features, described earlier in this chapter.</span></span>

## <a name="how-to-combine-serverless-and-docker-containers"></a><span data-ttu-id="87678-117">如何結合無伺服器和 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="87678-117">How to combine serverless and Docker containers</span></span>

<span data-ttu-id="87678-118">若要將 Azure 函數包裝在 Docker 容器中，請安裝 [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) ，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="87678-118">To wrap an Azure Function in a Docker container, install the [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) and then run the following command:</span></span>

```console
func init ProjectName --worker-runtime dotnet --docker
```

<span data-ttu-id="87678-119">建立專案時，它會包含 Dockerfile 和設定為的背景工作執行時間 `dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="87678-119">When the project is created, it will include a Dockerfile and the worker runtime configured to `dotnet`.</span></span> <span data-ttu-id="87678-120">現在，您可以在本機建立及測試您的函式。</span><span class="sxs-lookup"><span data-stu-id="87678-120">Now, you can create and test your function locally.</span></span> <span data-ttu-id="87678-121">使用和命令來建立並執行它  `docker build` `docker run` 。</span><span class="sxs-lookup"><span data-stu-id="87678-121">Build and run it using the  `docker build` and `docker run` commands.</span></span> <span data-ttu-id="87678-122">如需開始使用 Docker 支援建立 Azure Functions 的詳細步驟，請參閱 [使用自訂映射在 Linux 上建立](/azure/azure-functions/functions-create-function-linux-custom-image) 函式教學課程。</span><span class="sxs-lookup"><span data-stu-id="87678-122">For detailed steps to get started building Azure Functions with Docker support, see the [Create a function on Linux using a custom image](/azure/azure-functions/functions-create-function-linux-custom-image) tutorial.</span></span>

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a><span data-ttu-id="87678-123">如何結合無伺服器和 Kubernetes 與 KEDA</span><span class="sxs-lookup"><span data-stu-id="87678-123">How to combine serverless and Kubernetes with KEDA</span></span>

<span data-ttu-id="87678-124">在本章中，您已瞭解 Azure Functions 的平臺會自動相應放大以符合需求。</span><span class="sxs-lookup"><span data-stu-id="87678-124">In this chapter, you've seen that the Azure Functions' platform automatically scales out to meet demand.</span></span> <span data-ttu-id="87678-125">不過，將容器化函式部署至 AKS 時，您會失去內建的調整功能。</span><span class="sxs-lookup"><span data-stu-id="87678-125">When deploying containerized functions to AKS, however, you lose the built-in scaling functionality.</span></span> <span data-ttu-id="87678-126">為了解決這個 [情況，Kubernetes 型事件導向 (KEDA) ](/azure/azure-functions/functions-kubernetes-keda)。</span><span class="sxs-lookup"><span data-stu-id="87678-126">To the rescue comes [Kubernetes-based Event Driven (KEDA)](/azure/azure-functions/functions-kubernetes-keda).</span></span> <span data-ttu-id="87678-127">它可讓您更精細地自動調整，以 `event-driven Kubernetes workloads,` 包含容器化函數。</span><span class="sxs-lookup"><span data-stu-id="87678-127">It enables fine-grained autoscaling for `event-driven Kubernetes workloads,` including containerized functions.</span></span>

<span data-ttu-id="87678-128">KEDA 可為 Docker 容器中的函數執行時間提供事件驅動的調整功能。</span><span class="sxs-lookup"><span data-stu-id="87678-128">KEDA provides event-driven scaling functionality to the Functions' runtime in a Docker container.</span></span> <span data-ttu-id="87678-129">KEDA 可以從零 (的實例進行調整，而不會因為負載而發生) 的事件 `n instances` 。</span><span class="sxs-lookup"><span data-stu-id="87678-129">KEDA can scale from zero instances (when no events are occurring) out to `n instances`, based on load.</span></span> <span data-ttu-id="87678-130">它會將自訂計量公開給 Kubernetes 自動調整程式 (水準 Pod 自動調整程式) ，藉此啟用自動調整。</span><span class="sxs-lookup"><span data-stu-id="87678-130">It enables autoscaling by exposing custom metrics to the Kubernetes autoscaler (Horizontal Pod Autoscaler).</span></span> <span data-ttu-id="87678-131">將 Functions 容器與 KEDA 搭配使用，可讓您在任何 Kubernetes 叢集中複寫無伺服器函式功能。</span><span class="sxs-lookup"><span data-stu-id="87678-131">Using Functions containers with KEDA makes it possible to replicate serverless function capabilities in any Kubernetes cluster.</span></span>

<span data-ttu-id="87678-132">值得注意的是，KEDA 專案現在是由雲端原生運算基礎 (CNCF) 來管理。</span><span class="sxs-lookup"><span data-stu-id="87678-132">It is worth noting that the KEDA project is now managed by the Cloud Native Computing Foundation (CNCF).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="87678-133">[上一個](leverage-serverless-functions.md) 
>[下一步](deploy-containers-azure.md)</span><span class="sxs-lookup"><span data-stu-id="87678-133">[Previous](leverage-serverless-functions.md)
[Next](deploy-containers-azure.md)</span></span>
