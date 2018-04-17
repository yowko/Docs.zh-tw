---
title: 通用容器的設計原則
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c398e2da979637c450e2c9754ff3c9e8d8233aeb
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="common-container-design-principles"></a><span data-ttu-id="21e7b-103">通用容器的設計原則</span><span class="sxs-lookup"><span data-stu-id="21e7b-103">Common container design principles</span></span>

<span data-ttu-id="21e7b-104">繼續在開發程序而進入 there are 值得一提的是關於如何使用容器的某些基本概念。</span><span class="sxs-lookup"><span data-stu-id="21e7b-104">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="21e7b-105">容器等於處理程序</span><span class="sxs-lookup"><span data-stu-id="21e7b-105">Container equals a process</span></span>

<span data-ttu-id="21e7b-106">在容器的模型中，容器會代表單一處理程序。</span><span class="sxs-lookup"><span data-stu-id="21e7b-106">In the container model, a container represents a single process.</span></span> <span data-ttu-id="21e7b-107">藉由定義容器做為處理序界限，開始建立用於小數位數，或關閉批次、 程序的基本類型。</span><span class="sxs-lookup"><span data-stu-id="21e7b-107">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="21e7b-108">當您執行 Docker 容器時，您會看到[ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint)定義。</span><span class="sxs-lookup"><span data-stu-id="21e7b-108">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="21e7b-109">這會定義處理程序和容器的存留期。</span><span class="sxs-lookup"><span data-stu-id="21e7b-109">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="21e7b-110">當處理程序完成時，容器的生命週期結束。</span><span class="sxs-lookup"><span data-stu-id="21e7b-110">When the process completes, the container life cycle ends.</span></span> <span data-ttu-id="21e7b-111">有長時間執行的程序，例如 web 伺服器和存留較短的程序，例如批次作業，可能會為 Microsoft Azure 實作[WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/)。</span><span class="sxs-lookup"><span data-stu-id="21e7b-111">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="21e7b-112">如果處理序失敗，容器會結束並由 Orchestrator 接管。</span><span class="sxs-lookup"><span data-stu-id="21e7b-112">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="21e7b-113">如果 orchestrator 已指示要保留五個執行個體執行，而其中一個作業失敗，orchestrator 將會建立另一個容器，以取代失敗的處理序。</span><span class="sxs-lookup"><span data-stu-id="21e7b-113">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="21e7b-114">在批次工作中，處理序是透過參數來啟動。</span><span class="sxs-lookup"><span data-stu-id="21e7b-114">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="21e7b-115">當處理序完成時，工作即告完成。</span><span class="sxs-lookup"><span data-stu-id="21e7b-115">When the process completes, the work is complete.</span></span>

<span data-ttu-id="21e7b-116">您可能會發現您想要在單一容器中執行的多個處理序的案例。</span><span class="sxs-lookup"><span data-stu-id="21e7b-116">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="21e7b-117">在任何架構文件，都不會 」 絕不會"也不會有一定的 「 永遠 」。</span><span class="sxs-lookup"><span data-stu-id="21e7b-117">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="21e7b-118">需要多個處理序的情況下，常見的模式是使用[監督員](http://supervisord.org/)。</span><span class="sxs-lookup"><span data-stu-id="21e7b-118">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="21e7b-119">[上一個] (設計-docker-applications.md) [下一步] (龐大 applications.md)</span><span class="sxs-lookup"><span data-stu-id="21e7b-119">[Previous] (design-docker-applications.md) [Next] (monolithic-applications.md)</span></span>
