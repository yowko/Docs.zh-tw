---
title: 結合容器和無伺服器方法
description: 結合容器和 Kubernetes 與無伺服器方法
ms.date: 06/30/2019
ms.openlocfilehash: 58aff43adbdd2e629370cc685f32c7b61c25f85e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183431"
---
# <a name="combining-containers-and-serverless-approaches"></a><span data-ttu-id="34ded-103">結合容器和無伺服器方法</span><span class="sxs-lookup"><span data-stu-id="34ded-103">Combining containers and serverless approaches</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="34ded-104">微服務為基礎的應用程式經常依賴容器、協調流程和訊息傳遞，來進行節點之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="34ded-104">Frequently, microservices-based applications rely heavily on containers, orchestration, and message-passing for communication between nodes.</span></span> <span data-ttu-id="34ded-105">這項訊息是 Azure Functions 的理想工作，但在使用 Kubernetes 和相關工具設定及部署應用程式的其餘部分時，最好能夠在這個相同的工具組中利用 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="34ded-105">This messaging is an ideal task for Azure Functions, but with the rest of the application configured and deployed using Kubernetes and related tools, it would be nice to be able to leverage Azure Functions within this same toolset.</span></span> <span data-ttu-id="34ded-106">幸好，您可以將 Azure Functions 包裝在 Docker 容器中，並使用與 Kubernetes 應用程式其餘部分相同的進程和工具進行部署。</span><span class="sxs-lookup"><span data-stu-id="34ded-106">Fortunately, you can wrap Azure Functions in Docker containers and deploy them using the same processes and tools as the rest of your Kubernetes-based app.</span></span>

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a><span data-ttu-id="34ded-107">使用無伺服器的容器有何意義？</span><span class="sxs-lookup"><span data-stu-id="34ded-107">When does it make sense to use containers with serverless?</span></span>

<span data-ttu-id="34ded-108">根據預設，您的無伺服器函式不知道其執行所在的平臺。</span><span class="sxs-lookup"><span data-stu-id="34ded-108">By default, your serverless functions have no knowledge of the platform on which they'll run.</span></span> <span data-ttu-id="34ded-109">不過，在某些情況下，您可能會有特定需求，讓您自訂程式碼將在其中執行的容器映射很重要。</span><span class="sxs-lookup"><span data-stu-id="34ded-109">However, in some cases you may have specific requirements that make it important for you to customize the container image in which your code will run.</span></span> <span data-ttu-id="34ded-110">您可能想要使用自訂映射，因為您的函式依賴特定語言版本，或是預設映射不支援的相依性或設定需求。</span><span class="sxs-lookup"><span data-stu-id="34ded-110">You may want to use a custom image because your function relies on a specific language version or has dependencies or configuration requirements that aren't supported by the default image.</span></span> <span data-ttu-id="34ded-111">在這些情況下，自訂您自己的容器，並在自訂的 Docker 容器中部署您的函式可能是合理的做法。</span><span class="sxs-lookup"><span data-stu-id="34ded-111">In these cases, it may make sense to customize your own container and deploy your function in a custom Docker container.</span></span>

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a><span data-ttu-id="34ded-112">何時應避免使用 Azure Functions 的容器？</span><span class="sxs-lookup"><span data-stu-id="34ded-112">When should you avoid using containers with Azure Functions?</span></span>

<span data-ttu-id="34ded-113">如果您預期會受益于您函式的耗用量方案計費，如果您使用自己的容器，就無法這麼做。</span><span class="sxs-lookup"><span data-stu-id="34ded-113">If you're expecting to benefit from the consumption plan billing for your function, you won't be able to do so if you're using your own container.</span></span> <span data-ttu-id="34ded-114">此外，如果您不只是使用 Docker 容器，並將您的函式部署到您自己的 Kubernetes 叢集，就無法再受益于 Azure Functions 所提供的內建調整。</span><span class="sxs-lookup"><span data-stu-id="34ded-114">What's more, if you go beyond just using a Docker container and deploy your functions to your own Kubernetes cluster, you'll no longer benefit from the built-in scaling provided by Azure Functions.</span></span> <span data-ttu-id="34ded-115">您必須使用 Kubernetes 的調整功能，如下所述。</span><span class="sxs-lookup"><span data-stu-id="34ded-115">You'll need to use Kubernetes' scaling features, described below.</span></span>

## <a name="how-to-combine-serverless-and-docker-containers"></a><span data-ttu-id="34ded-116">如何結合無伺服器和 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="34ded-116">How to combine serverless and Docker containers</span></span>

<span data-ttu-id="34ded-117">若要將 Azure 函式包裝在 Docker 容器中，請安裝 Azure Functions Core Tools，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="34ded-117">To wrap an Azure Function in a Docker container, install the Azure Functions Core Tools and then run the following command:</span></span>

```console
func init ProjectName --docker
```

<span data-ttu-id="34ded-118">從下列選項中選擇您要的背景工作執行時間：</span><span class="sxs-lookup"><span data-stu-id="34ded-118">Choose which worker runtime you want from the following options:</span></span>

- <span data-ttu-id="34ded-119">`dotnet` (C#)</span><span class="sxs-lookup"><span data-stu-id="34ded-119">`dotnet` (C#)</span></span>
- <span data-ttu-id="34ded-120">`node` (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="34ded-120">`node` (JavaScript)</span></span>
- `python`

<span data-ttu-id="34ded-121">建立專案時，會包含 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="34ded-121">When the project is created, it will include a Dockerfile.</span></span> <span data-ttu-id="34ded-122">現在，您可以在本機建立及測試您的函式。</span><span class="sxs-lookup"><span data-stu-id="34ded-122">Now, you can create and test your function locally.</span></span> <span data-ttu-id="34ded-123">使用`docker build` 和`docker run`命令來建立並執行它。</span><span class="sxs-lookup"><span data-stu-id="34ded-123">Build and run it using the  `docker build` and `docker run` commands.</span></span> <span data-ttu-id="34ded-124">如需開始使用 Docker 支援來建立 Azure Functions 的詳細步驟，請參閱[使用自訂映射在 Linux 上建立](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)函式教學課程。</span><span class="sxs-lookup"><span data-stu-id="34ded-124">For detailed steps to get started building Azure Functions with Docker support, see the [Create a function on Linux using a custom image](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) tutorial.</span></span>

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a><span data-ttu-id="34ded-125">如何結合無伺服器和 Kubernetes 與 KEDA</span><span class="sxs-lookup"><span data-stu-id="34ded-125">How to combine serverless and Kubernetes with KEDA</span></span>

<span data-ttu-id="34ded-126">Azure 函式會根據以指定函式為目標的事件速率，自動調整以滿足需求。</span><span class="sxs-lookup"><span data-stu-id="34ded-126">Azure functions scale automatically to meet demand based on the rate of events that are targeting a given function.</span></span> <span data-ttu-id="34ded-127">此外，您可以利用 Kubernetes 來裝載您的函式，並使用以 Kubernetes 為基礎的事件驅動自動調整，或 KEDA。</span><span class="sxs-lookup"><span data-stu-id="34ded-127">Additionally, you can leverage Kubernetes to host your functions and use Kubernetes-based Event Driven Autoscaling, or KEDA.</span></span> <span data-ttu-id="34ded-128">當沒有發生任何事件時，KEDA 可以相應減少為0個實例，然後為了回應事件，它可以使用其水準 pod 自動調整程式來相應增加容器的數目，以符合需求。</span><span class="sxs-lookup"><span data-stu-id="34ded-128">When no events are occurring, KEDA can scale down to 0 instances, and then in response to events it can scale up the number of containers to meet the demand using its horizontal pod autoscaler.</span></span> <span data-ttu-id="34ded-129">[深入瞭解如何使用 KEDA 調整 Azure](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)函式。</span><span class="sxs-lookup"><span data-stu-id="34ded-129">[Learn more about scaling Azure functions with KEDA](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).</span></span>

## <a name="references"></a><span data-ttu-id="34ded-130">reference</span><span class="sxs-lookup"><span data-stu-id="34ded-130">References</span></span>

- [<span data-ttu-id="34ded-131">在 Docker 容器中執行 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="34ded-131">Run Azure Functions in a Docker Container</span></span>](https://markheath.net/post/azure-functions-docker)
- [<span data-ttu-id="34ded-132">使用自訂映射在 Linux 上建立函式</span><span class="sxs-lookup"><span data-stu-id="34ded-132">Create a function on Linux using a custom image</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [<span data-ttu-id="34ded-133">具有 Kubernetes 事件驅動自動調整的 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="34ded-133">Azure Functions with Kubernetes Event Driven Autoscaling</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)

>[!div class="step-by-step"]
><span data-ttu-id="34ded-134">[上一頁](leverage-serverless-functions.md)
>[下一頁](deploy-containers-azure.md)</span><span class="sxs-lookup"><span data-stu-id="34ded-134">[Previous](leverage-serverless-functions.md)
[Next](deploy-containers-azure.md)</span></span>
