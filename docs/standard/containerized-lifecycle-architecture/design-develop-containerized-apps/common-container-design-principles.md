---
title: 一般容器設計準則
description: 了解良好容器設計的基本原則就是「容器應只裝載一個處理序」。
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644801"
---
# <a name="common-container-design-principles"></a><span data-ttu-id="16fc2-103">一般容器設計準則</span><span class="sxs-lookup"><span data-stu-id="16fc2-103">Common container design principles</span></span>

<span data-ttu-id="16fc2-104">在進展到開發程序之前，還有一些值得一提的容器使用方式基本概念。</span><span class="sxs-lookup"><span data-stu-id="16fc2-104">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="16fc2-105">容器等於處理序</span><span class="sxs-lookup"><span data-stu-id="16fc2-105">Container equals a process</span></span>

<span data-ttu-id="16fc2-106">在容器模型中，容器代表單一處理序。</span><span class="sxs-lookup"><span data-stu-id="16fc2-106">In the container model, a container represents a single process.</span></span> <span data-ttu-id="16fc2-107">藉由將容器定義為處理序界限，您即可開始建立用來調整或批次關閉處理序的基本項目。</span><span class="sxs-lookup"><span data-stu-id="16fc2-107">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="16fc2-108">當您執行 Docker 容器時，您會看到 [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) 定義。</span><span class="sxs-lookup"><span data-stu-id="16fc2-108">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="16fc2-109">這會定義容器的處理序以及存留期。</span><span class="sxs-lookup"><span data-stu-id="16fc2-109">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="16fc2-110">當處理序完成時，容器生命週期即告結束。</span><span class="sxs-lookup"><span data-stu-id="16fc2-110">When the process completes, the container life-cycle ends.</span></span> <span data-ttu-id="16fc2-111">有長時間執行的處理序 (例如網頁伺服器) 和存留較短的程序 (例如批次作業)，其可能會實作為 Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/)。</span><span class="sxs-lookup"><span data-stu-id="16fc2-111">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="16fc2-112">如果處理序失敗，容器會結束並由 Orchestrator 接管。</span><span class="sxs-lookup"><span data-stu-id="16fc2-112">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="16fc2-113">如果您已指示協調器保留五個執行中的執行個體，但其中一個失敗，則協調器會建立另一個容器來取代失敗的處理序。</span><span class="sxs-lookup"><span data-stu-id="16fc2-113">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="16fc2-114">在批次工作中，處理序是透過參數來啟動。</span><span class="sxs-lookup"><span data-stu-id="16fc2-114">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="16fc2-115">當處理序完成時，工作即告完成。</span><span class="sxs-lookup"><span data-stu-id="16fc2-115">When the process completes, the work is complete.</span></span>

<span data-ttu-id="16fc2-116">有時候，您可能需要在單一容器中執行多個處理序。</span><span class="sxs-lookup"><span data-stu-id="16fc2-116">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="16fc2-117">在任何架構文件中，並沒有「絕不可能」或「一律如此」的情況。</span><span class="sxs-lookup"><span data-stu-id="16fc2-117">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="16fc2-118">在需要多個處理序的情況下，常見的模式是使用 [Supervisor](http://supervisord.org/)。</span><span class="sxs-lookup"><span data-stu-id="16fc2-118">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="16fc2-119">[上一頁](design-docker-applications.md)
>[下一頁](monolithic-applications.md)</span><span class="sxs-lookup"><span data-stu-id="16fc2-119">[Previous](design-docker-applications.md)
[Next](monolithic-applications.md)</span></span>
