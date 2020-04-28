---
title: 為雲端原生服務結合容器和無伺服器方法
description: 結合容器和 Kubernetes 與無伺服器方法
ms.date: 04/23/2020
ms.openlocfilehash: fe9e9fd5d07132971d64bc6433a762fb7bd22048
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199660"
---
# <a name="combining-containers-and-serverless-approaches"></a><span data-ttu-id="d7c31-103">結合容器和無伺服器方法</span><span class="sxs-lookup"><span data-stu-id="d7c31-103">Combining containers and serverless approaches</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d7c31-104">雲端原生應用程式通常會利用容器和協調流程來執行服務。</span><span class="sxs-lookup"><span data-stu-id="d7c31-104">Cloud-native applications typically implement services leveraging containers and orchestration.</span></span> <span data-ttu-id="d7c31-105">通常會有機會將部分應用程式的服務公開為 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="d7c31-105">There are often opportunities to expose some of the application's services as Azure Functions.</span></span> <span data-ttu-id="d7c31-106">不過，在部署至 Kubernetes 的雲端原生應用程式中，利用此相同工具組中的 Azure Functions 是很好的做法。</span><span class="sxs-lookup"><span data-stu-id="d7c31-106">However, with a cloud-native app deployed to Kubernetes, it would be nice to leverage Azure Functions within this same toolset.</span></span> <span data-ttu-id="d7c31-107">幸好，您可以將 Azure Functions 包裝在 Docker 容器內，並使用與 Kubernetes 應用程式其餘部分相同的進程和工具進行部署。</span><span class="sxs-lookup"><span data-stu-id="d7c31-107">Fortunately, you can wrap Azure Functions inside Docker containers and deploy them using the same processes and tools as the rest of your Kubernetes-based app.</span></span>

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a><span data-ttu-id="d7c31-108">使用無伺服器的容器有何意義？</span><span class="sxs-lookup"><span data-stu-id="d7c31-108">When does it make sense to use containers with serverless?</span></span>

<span data-ttu-id="d7c31-109">您的 Azure 函數不知道其部署所在的平臺。</span><span class="sxs-lookup"><span data-stu-id="d7c31-109">Your Azure Function has no knowledge of the platform on which it's deployed.</span></span> <span data-ttu-id="d7c31-110">在某些情況下，您可能會有特定需求，而且需要自訂您的函式程式碼將在其上執行的環境。</span><span class="sxs-lookup"><span data-stu-id="d7c31-110">For some scenarios, you may have specific requirements and need to customize the environment on which your function code will run.</span></span> <span data-ttu-id="d7c31-111">您需要支援相依性的自訂映射，或預設映射不支援的設定。</span><span class="sxs-lookup"><span data-stu-id="d7c31-111">You'll need a custom image that supports dependencies or a configuration not supported by the default image.</span></span> <span data-ttu-id="d7c31-112">在這些情況下，在自訂的 Docker 容器中部署您的函式是合理的。</span><span class="sxs-lookup"><span data-stu-id="d7c31-112">In these cases, it makes sense to deploy your function in a custom Docker container.</span></span>

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a><span data-ttu-id="d7c31-113">何時應避免使用 Azure Functions 的容器？</span><span class="sxs-lookup"><span data-stu-id="d7c31-113">When should you avoid using containers with Azure Functions?</span></span>

<span data-ttu-id="d7c31-114">如果您想要使用取用計費，就無法在容器中執行您的函式。</span><span class="sxs-lookup"><span data-stu-id="d7c31-114">If you want to use consumption billing, you won't be able to run your function in a container.</span></span> <span data-ttu-id="d7c31-115">此外，如果您將函式部署至 Kubernetes 叢集，將不再受益于 Azure Functions 所提供的內建調整。</span><span class="sxs-lookup"><span data-stu-id="d7c31-115">What's more, if you deploy your function to a Kubernetes cluster, you'll no longer benefit from the built-in scaling provided by Azure Functions.</span></span> <span data-ttu-id="d7c31-116">您將需要使用 Kubernetes 的調整功能，如本章稍早所述。</span><span class="sxs-lookup"><span data-stu-id="d7c31-116">You'll need to use Kubernetes' scaling features, described earlier in this chapter.</span></span>

## <a name="how-to-combine-serverless-and-docker-containers"></a><span data-ttu-id="d7c31-117">如何結合無伺服器和 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="d7c31-117">How to combine serverless and Docker containers</span></span>

<span data-ttu-id="d7c31-118">若要將 Azure 函式包裝在 Docker 容器中，請安裝[Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) ，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="d7c31-118">To wrap an Azure Function in a Docker container, install the [Azure Functions Core Tools](https://github.com/Azure/azure-functions-core-tools) and then run the following command:</span></span>

```console
func init ProjectName --worker-runtime dotnet --docker
```

<span data-ttu-id="d7c31-119">建立專案時，會包含 Dockerfile，以及設定為`dotnet`的背景工作執行時間。</span><span class="sxs-lookup"><span data-stu-id="d7c31-119">When the project is created, it will include a Dockerfile and the worker runtime configured to `dotnet`.</span></span> <span data-ttu-id="d7c31-120">現在，您可以在本機建立及測試您的函式。</span><span class="sxs-lookup"><span data-stu-id="d7c31-120">Now, you can create and test your function locally.</span></span> <span data-ttu-id="d7c31-121">使用`docker build`和`docker run`命令來建立並執行它。</span><span class="sxs-lookup"><span data-stu-id="d7c31-121">Build and run it using the  `docker build` and `docker run` commands.</span></span> <span data-ttu-id="d7c31-122">如需開始使用 Docker 支援來建立 Azure Functions 的詳細步驟，請參閱[使用自訂映射在 Linux 上建立](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)函式教學課程。</span><span class="sxs-lookup"><span data-stu-id="d7c31-122">For detailed steps to get started building Azure Functions with Docker support, see the [Create a function on Linux using a custom image](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) tutorial.</span></span>

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a><span data-ttu-id="d7c31-123">如何結合無伺服器和 Kubernetes 與 KEDA</span><span class="sxs-lookup"><span data-stu-id="d7c31-123">How to combine serverless and Kubernetes with KEDA</span></span>

<span data-ttu-id="d7c31-124">Azure 函式會根據以其為目標的事件速率，自動調整以滿足需求。</span><span class="sxs-lookup"><span data-stu-id="d7c31-124">Azure functions scale automatically to meet demand based on the rate of events that are targeting it.</span></span> <span data-ttu-id="d7c31-125">您一律可以利用 AKS 來裝載您的函式，並使用以 Kubernetes 為基礎的事件驅動自動調整，或 KEDA。</span><span class="sxs-lookup"><span data-stu-id="d7c31-125">You can always leverage AKS to host your functions and use Kubernetes-based Event Driven Autoscaling, or KEDA.</span></span> <span data-ttu-id="d7c31-126">當沒有發生任何事件時，KEDA 可以相應減少為零個實例。</span><span class="sxs-lookup"><span data-stu-id="d7c31-126">When no events are occurring, KEDA can scale down to zero instances.</span></span> <span data-ttu-id="d7c31-127">[深入瞭解如何使用 KEDA 調整 Azure](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)函式。</span><span class="sxs-lookup"><span data-stu-id="d7c31-127">[Learn more about scaling Azure functions with KEDA](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d7c31-128">[上一頁](leverage-serverless-functions.md)
>[下一頁](deploy-containers-azure.md)</span><span class="sxs-lookup"><span data-stu-id="d7c31-128">[Previous](leverage-serverless-functions.md)
[Next](deploy-containers-azure.md)</span></span>
