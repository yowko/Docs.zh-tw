---
title: 利用無伺服器函式
description: 利用雲端原生應用程式中的無伺服器和 Azure Functions
ms.date: 06/30/2019
ms.openlocfilehash: 61bf4db6d61160c7ec11ffa3f178cc3917ae6cf9
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182822"
---
# <a name="leveraging-serverless-functions"></a><span data-ttu-id="1422e-103">利用無伺服器函式</span><span class="sxs-lookup"><span data-stu-id="1422e-103">Leveraging serverless functions</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="1422e-104">在管理完整機器和作業系統以利用雲端功能的範圍中，無伺服器的最大目的在於您的程式碼，而您只需要為程式碼執行時才需要付費。</span><span class="sxs-lookup"><span data-stu-id="1422e-104">In the spectrum of managing full machines and operating systems to leveraging cloud capabilities, serverless lives at the extreme end where the only thing you're responsible for is your code, and you only pay for your code when it runs.</span></span> <span data-ttu-id="1422e-105">Azure Functions 提供一種方式，可在您的應用程式中建立無伺服器功能。</span><span class="sxs-lookup"><span data-stu-id="1422e-105">Azure Functions provides a way to build serverless capabilities into your applications.</span></span> 

## <a name="what-is-serverless"></a><span data-ttu-id="1422e-106">什麼是無伺服器？</span><span class="sxs-lookup"><span data-stu-id="1422e-106">What is serverless?</span></span>

<span data-ttu-id="1422e-107">無伺服器運算並不表示執行您的應用程式時，不會有一台伺服器，那就是程式碼仍會在某個伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="1422e-107">Serverless computing doesn't mean there isn't a server involved in running your application - the code still runs on a server somewhere.</span></span> <span data-ttu-id="1422e-108">差別在於應用程式開發小組不再需要自行顧慮管理伺服器基礎結構。</span><span class="sxs-lookup"><span data-stu-id="1422e-108">The distinction is that the application development team no longer needs to concern themselves with managing server infrastructure.</span></span> <span data-ttu-id="1422e-109">無伺服器運算解決方案（例如 Azure Functions 協助小組提高生產力，並可讓組織將其資源優化，並將焦點放在提供解決方案。</span><span class="sxs-lookup"><span data-stu-id="1422e-109">Serverless computing solutions like Azure Functions help teams increase their productivity and allow organizations to optimize their resources and focus on delivering solutions.</span></span>

<span data-ttu-id="1422e-110">無伺服器運算會使用事件觸發的無狀態容器來裝載您的應用程式或部分應用程式。</span><span class="sxs-lookup"><span data-stu-id="1422e-110">Serverless computing uses event-triggered stateless containers to host your application or part of your application.</span></span> <span data-ttu-id="1422e-111">無伺服器平臺可以視需要相應增加和減少，以符合需求。</span><span class="sxs-lookup"><span data-stu-id="1422e-111">Serverless platforms can scale up and down to meet demand as-needed.</span></span> <span data-ttu-id="1422e-112">像 Azure Functions 的平臺可以輕鬆直接存取其他 Azure 服務，例如佇列、事件和儲存體。</span><span class="sxs-lookup"><span data-stu-id="1422e-112">Platforms like Azure Functions have easy direct access to other Azure services like queues, events, and storage.</span></span>

## <a name="what-challenges-are-solved-by-serverless"></a><span data-ttu-id="1422e-113">無伺服器可解決哪些挑戰？</span><span class="sxs-lookup"><span data-stu-id="1422e-113">What challenges are solved by serverless?</span></span>

<span data-ttu-id="1422e-114">無伺服器是從執行您自己的硬體開始的最終抽象概念。</span><span class="sxs-lookup"><span data-stu-id="1422e-114">Serverless is the ultimate abstraction away from running your own hardware.</span></span> <span data-ttu-id="1422e-115">開發人員可以專門專注于撰寫程式碼來解決商務問題，而不需要考慮下列任何可能在裝載您自己的伺服器時所需的工作：</span><span class="sxs-lookup"><span data-stu-id="1422e-115">Developers can focus exclusively on writing code to solve business problems, without concern for any of the following tasks that might have been necessary when hosting your own servers:</span></span>

- <span data-ttu-id="1422e-116">購買機器和軟體授權</span><span class="sxs-lookup"><span data-stu-id="1422e-116">Purchasing machines and software licenses</span></span>
- <span data-ttu-id="1422e-117">存放、保護、設定和維護電腦及其網路功能、電源和 A/C 需求</span><span class="sxs-lookup"><span data-stu-id="1422e-117">Housing, securing, configuring, and maintaining the machines and their networking, power, and A/C requirements</span></span>
- <span data-ttu-id="1422e-118">修補和升級作業系統與軟體</span><span class="sxs-lookup"><span data-stu-id="1422e-118">Patching and upgrading operating systems and software</span></span>
- <span data-ttu-id="1422e-119">設定網頁伺服器或機器服務來裝載應用程式軟體</span><span class="sxs-lookup"><span data-stu-id="1422e-119">Configuring web servers or machine services to host application software</span></span>
- <span data-ttu-id="1422e-120">在其平臺中設定應用程式軟體</span><span class="sxs-lookup"><span data-stu-id="1422e-120">Configuring application software within its platform</span></span>

<span data-ttu-id="1422e-121">許多公司都採用數十個員工成員，並配置大型預算來支援這些硬體基礎結構的考慮。</span><span class="sxs-lookup"><span data-stu-id="1422e-121">Many companies employ dozens of staff members and allocate large budgets to support these hardware infrastructure concerns.</span></span> <span data-ttu-id="1422e-122">直接移至雲端可以排除其中一些問題;將應用程式一直轉移到無伺服器，可以排除其餘部分。</span><span class="sxs-lookup"><span data-stu-id="1422e-122">Simply moving to the cloud eliminates some of these concerns; shifting applications all the way to serverless will eliminate the rest.</span></span>

## <a name="what-scenarios-are-appropriate-for-serverless"></a><span data-ttu-id="1422e-123">什麼是適用于無伺服器的案例？</span><span class="sxs-lookup"><span data-stu-id="1422e-123">What scenarios are appropriate for serverless?</span></span>

<span data-ttu-id="1422e-124">無伺服器會使用個別的簡短執行函式，以回應某個觸發程式來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="1422e-124">Serverless uses individual short-running functions that are called in response to some trigger.</span></span> <span data-ttu-id="1422e-125">這讓它們適合用來處理背景工作。</span><span class="sxs-lookup"><span data-stu-id="1422e-125">This makes them ideal for processing background tasks.</span></span>

<span data-ttu-id="1422e-126">例如，應用程式可能需要在處理要求的過程中傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="1422e-126">For example, an application might need to send an email as part of processing a request.</span></span> <span data-ttu-id="1422e-127">您不需要在處理 web 要求時傳送電子郵件，而是將電子郵件的詳細資料放在佇列上，並使用 Azure 函式來挑選訊息並傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="1422e-127">Instead of sending the email as part of handling the web request, the details of the email could be placed onto a queue and an Azure Function could be used to pick up the message and send the email.</span></span> <span data-ttu-id="1422e-128">應用程式的許多不同元件（或甚至許多應用程式）都可以利用這個相同的 Azure 函式，為應用程式提供改善的效能和擴充性，並使用[佇列型負載調節](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling)來避免與下列相關的瓶頸：傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="1422e-128">Many different parts of the application, or even many applications, could leverage this same Azure Function, providing improved performance and scalability for the applications and using [queue-based load leveling](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) to avoid bottlenecks related to sending the emails.</span></span>

<span data-ttu-id="1422e-129">雖然應用程式和 Azure Functions 之間的[發行者/訂閱者模式](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber)是最常見的模式，但其他模式也是可行的。</span><span class="sxs-lookup"><span data-stu-id="1422e-129">Although a [Publisher/Subscriber pattern](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) between applications and Azure Functions is the most common pattern, other patterns are possible.</span></span> <span data-ttu-id="1422e-130">Azure Functions 可以由其他事件觸發，例如 Azure Blob 儲存體的變更。</span><span class="sxs-lookup"><span data-stu-id="1422e-130">Azure Functions can be triggered by other events, such as changes to Azure Blob Storage.</span></span> <span data-ttu-id="1422e-131">支援的影像上傳的應用程式可能有負責建立縮圖影像的 Azure 函式，或將上傳影像的大小調整為一致的維度，或優化影像大小。</span><span class="sxs-lookup"><span data-stu-id="1422e-131">An application that supported image uploads could have an Azure Function responsible for creating thumbnail images, or resizing uploaded images to consistent dimensions, or optimizing image size.</span></span> <span data-ttu-id="1422e-132">所有這項功能都可以透過插入 Azure Blob 儲存體直接觸發，讓應用程式本身的複雜性和工作負載保持不變。</span><span class="sxs-lookup"><span data-stu-id="1422e-132">All of this functionality could be triggered directly by inserts to Azure Blob Storage, keeping the complexity and the workload out of the application itself.</span></span>

<span data-ttu-id="1422e-133">許多應用程式都有長時間執行的進程，做為其工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="1422e-133">Many applications have long-running processes as part of their workflows.</span></span> <span data-ttu-id="1422e-134">這些工作通常會在使用者與應用程式互動的過程中完成，強制使用者等待並對其體驗造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="1422e-134">Often these tasks are done as part of the user's interaction with the application, forcing the user to wait and negatively impacting their experience.</span></span> <span data-ttu-id="1422e-135">無伺服器運算提供了在使用者互動迴圈外執行較慢工作的絕佳方式，而這些工作可以輕鬆地隨需求調整，而不需要調整整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="1422e-135">Serverless computing provides a great way to perform slower tasks outside of the user interaction loop, and these tasks can easily scale with demand without requiring the entire application to scale.</span></span>

## <a name="when-should-you-avoid-serverless"></a><span data-ttu-id="1422e-136">何時應該避免無伺服器？</span><span class="sxs-lookup"><span data-stu-id="1422e-136">When should you avoid serverless?</span></span>

<span data-ttu-id="1422e-137">無伺服器運算最適合用於不會封鎖使用者介面的工作。</span><span class="sxs-lookup"><span data-stu-id="1422e-137">Serverless computing is best-used for tasks that don't block the user interface.</span></span> <span data-ttu-id="1422e-138">這表示它們不是直接裝載 web 應用程式或 web Api 的理想選擇。</span><span class="sxs-lookup"><span data-stu-id="1422e-138">This means they're not ideal for hosting web applications or web APIs directly.</span></span> <span data-ttu-id="1422e-139">其主要原因是無伺服器解決方案會依需求布建和調整。</span><span class="sxs-lookup"><span data-stu-id="1422e-139">The main reason for this is that serverless solutions are provisioned and scaled on demand.</span></span> <span data-ttu-id="1422e-140">當需要新的函式實例時（稱為*冷啟動*），需要一些時間來布建。</span><span class="sxs-lookup"><span data-stu-id="1422e-140">When a new instance of a function is needed, referred to as a *cold start*, it takes time to provision.</span></span> <span data-ttu-id="1422e-141">這次通常是幾秒鐘的時間，但可能會因為各種不同的因素而變長。</span><span class="sxs-lookup"><span data-stu-id="1422e-141">This time is typically a few seconds, but can be longer depending on a variety of factors.</span></span> <span data-ttu-id="1422e-142">單一實例通常可以無限期地維護（例如，定期向其提出要求），但如果實例數目需要相應增加，則會保留冷啟動問題。</span><span class="sxs-lookup"><span data-stu-id="1422e-142">A single instance can often be maintained indefinitely (for instance, by periodically making a request to it), but the cold start issue remains if the number of instances ever needs to scale up.</span></span>

<span data-ttu-id="1422e-143">![冷與暖開機](./media/cold-start-warm-start.png)
**圖 3-10**。</span><span class="sxs-lookup"><span data-stu-id="1422e-143">![Cold versus warm start](./media/cold-start-warm-start.png)
**Figure 3-10**.</span></span> <span data-ttu-id="1422e-144">冷啟動和暖開機。</span><span class="sxs-lookup"><span data-stu-id="1422e-144">Cold start versus warm start.</span></span>

<span data-ttu-id="1422e-145">如果您需要避免冷啟動，您可以選擇從取用[方案切換到專用的方案](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)。</span><span class="sxs-lookup"><span data-stu-id="1422e-145">If you need to avoid cold starts entirely, you can choose to switch from a [consumption plan to a dedicated plan](https://azure.microsoft.com/blog/understanding-serverless-cold-start/).</span></span> <span data-ttu-id="1422e-146">您也可以使用 premium 方案[設定一或多個預先準備就緒的實例](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)，因此當您需要新增另一個實例時，它已經啟動並準備就緒。</span><span class="sxs-lookup"><span data-stu-id="1422e-146">You can also [configure one or more pre-warmed instances](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) with the premium plan so when you need to add another instance, it's already up and ready to go.</span></span> <span data-ttu-id="1422e-147">這些選項可以減輕與無伺服器運算相關的其中一個重要考慮。</span><span class="sxs-lookup"><span data-stu-id="1422e-147">These options can mitigate one of the key concerns associated with serverless computing.</span></span>

<span data-ttu-id="1422e-148">您通常也應該避免長時間執行之工作的無伺服器。</span><span class="sxs-lookup"><span data-stu-id="1422e-148">You should also typically avoid serverless for long-running tasks.</span></span> <span data-ttu-id="1422e-149">它們最適用于可快速完成的一小段工作。</span><span class="sxs-lookup"><span data-stu-id="1422e-149">They're best for small pieces of work that can be completed quickly.</span></span> <span data-ttu-id="1422e-150">大部分的無伺服器平臺都需要在幾分鐘內完成個別的函式。</span><span class="sxs-lookup"><span data-stu-id="1422e-150">Most serverless platforms require individual functions to complete within a few minutes.</span></span> <span data-ttu-id="1422e-151">Azure Functions 預設為5分鐘的超時期間（最多可設定10分鐘）。</span><span class="sxs-lookup"><span data-stu-id="1422e-151">Azure Functions defaults to a 5-minute time-out duration (can be configured up to 10 minutes).</span></span> <span data-ttu-id="1422e-152">Azure Functions premium 方案也可以緩和此問題，並將時間輸出預設為30分鐘，並允許設定未限制的更高限制。</span><span class="sxs-lookup"><span data-stu-id="1422e-152">The Azure Functions premium plan can mitigate this issue as well, defaulting time outs to 30 minutes and allowing an unbounded higher limit to be configured.</span></span>

<span data-ttu-id="1422e-153">最後，針對應用程式內的特定工作運用無伺服器，會增加複雜度。</span><span class="sxs-lookup"><span data-stu-id="1422e-153">Finally, leveraging serverless for certain tasks within your application adds complexity.</span></span> <span data-ttu-id="1422e-154">通常最好先以模組化、鬆散耦合的方式來設計您的應用程式，然後找出無伺服器可提供的優點，使額外的複雜性更有價值。</span><span class="sxs-lookup"><span data-stu-id="1422e-154">It's often best to architect your application in a modular, loosely coupled manner first, and then identify if there are benefits serverless would offer that make the additional complexity worthwhile.</span></span> <span data-ttu-id="1422e-155">許多較小的應用程式在單一整合式部署中都可以順利執行，而不需要無伺服器運算所需的分散式應用程式架構。</span><span class="sxs-lookup"><span data-stu-id="1422e-155">Many smaller applications will run perfectly well in a single monolithic deployment, without the need for the distributed application architecture serverless computing requires.</span></span>

## <a name="references"></a><span data-ttu-id="1422e-156">reference</span><span class="sxs-lookup"><span data-stu-id="1422e-156">References</span></span>

- [<span data-ttu-id="1422e-157">瞭解無伺服器冷啟動</span><span class="sxs-lookup"><span data-stu-id="1422e-157">Understanding serverless cold start</span></span>](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [<span data-ttu-id="1422e-158">預先準備就緒 Azure Functions 實例</span><span class="sxs-lookup"><span data-stu-id="1422e-158">Pre-warmed Azure Functions instances</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [<span data-ttu-id="1422e-159">使用自訂映射在 Linux 上建立函式</span><span class="sxs-lookup"><span data-stu-id="1422e-159">Create a function on Linux using a custom image</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)

>[!div class="step-by-step"]
><span data-ttu-id="1422e-160">[上一頁](leverage-containers-orchestrators.md)
>[下一頁](combine-containers-serverless-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="1422e-160">[Previous](leverage-containers-orchestrators.md)
[Next](combine-containers-serverless-approaches.md)</span></span>