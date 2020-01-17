---
title: 在工作流程方案中加入服務參考
ms.date: 03/30/2017
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
ms.openlocfilehash: 641d401fb85ea156f35134f54e54840f20fa4c9d
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116695"
---
# <a name="add-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="26fdd-102">在工作流程方案中加入服務參考</span><span class="sxs-lookup"><span data-stu-id="26fdd-102">Add a Service Reference in a Workflow Solution</span></span>

<span data-ttu-id="26fdd-103">在工作流程應用程式中加入服務參考的運作方式與在一般 WCF 應用程式中加入服務參考的運作方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="26fdd-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="26fdd-104">當您選取 [**新增** > **服務參考**] 並指定服務的 URL 時，就會下載中繼資料，並產生可讓您呼叫該 wcf 服務或 wcf 工作流程服務的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="26fdd-104">When you select **Add** > **Service Reference** and specify the URL to the service, the metadata is downloaded and custom activities are generated that allow you to call that WCF service or WCF workflow service.</span></span> <span data-ttu-id="26fdd-105">加入服務參考之後，重建方案，因而建置所產生的活動。</span><span class="sxs-lookup"><span data-stu-id="26fdd-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="26fdd-106">接著，這些活動會出現在工作流程設計工具工具箱中。</span><span class="sxs-lookup"><span data-stu-id="26fdd-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="26fdd-107">只有當您在工作流程方案中加入服務參考時，這才會有效。</span><span class="sxs-lookup"><span data-stu-id="26fdd-107">This will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="26fdd-108">下列 web 轉換顯示如何在其他類型的專案中加入服務參考：[從 Web 專案中的工作流程呼叫 WCF 服務](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)。</span><span class="sxs-lookup"><span data-stu-id="26fdd-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow).</span></span>

<span data-ttu-id="26fdd-109">將兩個或多個服務參考加入至包含相同作業名稱的服務將會造成問題。</span><span class="sxs-lookup"><span data-stu-id="26fdd-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="26fdd-110">產生的活動只會呼叫第一個服務作業。</span><span class="sxs-lookup"><span data-stu-id="26fdd-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="26fdd-111">若要解決此問題，請重新命名服務作業，使其不同，或在每個產生的活動中變更端點設定名稱。</span><span class="sxs-lookup"><span data-stu-id="26fdd-111">To work around this issue, rename the service operations so they are different, or change the endpoint configuration name within each generated activity.</span></span>

## <a name="see-also"></a><span data-ttu-id="26fdd-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="26fdd-112">See also</span></span>

- [<span data-ttu-id="26fdd-113">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="26fdd-113">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="26fdd-114">從 Web 專案中的工作流程呼叫 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="26fdd-114">Calling a WCF Service from a Workflow in a Web Project</span></span>](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
