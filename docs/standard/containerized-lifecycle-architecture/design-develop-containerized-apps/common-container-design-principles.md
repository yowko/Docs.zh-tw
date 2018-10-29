---
title: 一般容器設計原則
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3af174279e8b6f56a10413817b05ef68cfcabea5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202170"
---
# <a name="common-container-design-principles"></a><span data-ttu-id="debf1-103">一般容器設計原則</span><span class="sxs-lookup"><span data-stu-id="debf1-103">Common container design principles</span></span>

<span data-ttu-id="debf1-104">直接的放在開發程序有一些值得一提的是關於您如何使用容器的基本概念。</span><span class="sxs-lookup"><span data-stu-id="debf1-104">Ahead of getting into the development process there are a few basic concepts worth mentioning with regard to how you use containers.</span></span>

## <a name="container-equals-a-process"></a><span data-ttu-id="debf1-105">容器等於處理序</span><span class="sxs-lookup"><span data-stu-id="debf1-105">Container equals a process</span></span>

<span data-ttu-id="debf1-106">在容器模型中，容器代表單一處理序。</span><span class="sxs-lookup"><span data-stu-id="debf1-106">In the container model, a container represents a single process.</span></span> <span data-ttu-id="debf1-107">藉由定義做為處理序界限的容器，您開始建立用來擴展，或批次關閉時，處理程序的基本項目。</span><span class="sxs-lookup"><span data-stu-id="debf1-107">By defining a container as a process boundary, you begin to create the primitives used to scale, or batch-off, processes.</span></span> <span data-ttu-id="debf1-108">當您執行 Docker 容器時，您會看到[ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint)定義。</span><span class="sxs-lookup"><span data-stu-id="debf1-108">When you run a Docker container, you'll see an [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definition.</span></span> <span data-ttu-id="debf1-109">這會定義程序和容器的存留期。</span><span class="sxs-lookup"><span data-stu-id="debf1-109">This defines the process and the lifetime of the container.</span></span> <span data-ttu-id="debf1-110">此程序完成時，容器的生命週期結束。</span><span class="sxs-lookup"><span data-stu-id="debf1-110">When the process completes, the container life cycle ends.</span></span> <span data-ttu-id="debf1-111">有長時間執行的程序，例如 web 伺服器，以及存留較短的程序，例如批次作業，可能會實作為 Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/)。</span><span class="sxs-lookup"><span data-stu-id="debf1-111">There are long-running processes, such as web servers, and short-lived processes, such as batch jobs, which might have been implemented as Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/).</span></span> <span data-ttu-id="debf1-112">如果處理序失敗，容器會結束並由 Orchestrator 接管。</span><span class="sxs-lookup"><span data-stu-id="debf1-112">If the process fails, the container ends, and the orchestrator takes over.</span></span> <span data-ttu-id="debf1-113">如果 orchestrator 已指示要保留五個執行個體執行，且其中一個失敗，協調器會建立另一個容器，來取代失敗的程序。</span><span class="sxs-lookup"><span data-stu-id="debf1-113">If the orchestrator was instructed to keep five instances running and one fails, the orchestrator will create another container to replace the failed process.</span></span> <span data-ttu-id="debf1-114">在批次工作中，處理序是透過參數來啟動。</span><span class="sxs-lookup"><span data-stu-id="debf1-114">In a batch job, the process is started with parameters.</span></span> <span data-ttu-id="debf1-115">當處理序完成時，工作即告完成。</span><span class="sxs-lookup"><span data-stu-id="debf1-115">When the process completes, the work is complete.</span></span>

<span data-ttu-id="debf1-116">您可能會發現您想要在單一容器中執行的多個處理序的案例。</span><span class="sxs-lookup"><span data-stu-id="debf1-116">You might find a scenario in which you want multiple processes running in a single container.</span></span> <span data-ttu-id="debf1-117">在任何架構文件中，沒有永遠不會 」 永不，"，也不會有一個 「 永遠 」。</span><span class="sxs-lookup"><span data-stu-id="debf1-117">In any architecture document, there's never a "never," nor is there always an "always."</span></span> <span data-ttu-id="debf1-118">需要多個處理序的情況下，常見的模式是使用[監督員](http://supervisord.org/)。</span><span class="sxs-lookup"><span data-stu-id="debf1-118">For scenarios requiring multiple processes, a common pattern is to use [Supervisor](http://supervisord.org/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="debf1-119">[上一頁](design-docker-applications.md)
[下一頁](monolithic-applications.md)</span><span class="sxs-lookup"><span data-stu-id="debf1-119">[Previous](design-docker-applications.md)
[Next](monolithic-applications.md)</span></span>
