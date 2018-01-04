---
title: "在工作流程方案中加入服務參考"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee974ee5a9f4564b0e44256bc4773f9898d89fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="dd8e9-102">在工作流程方案中加入服務參考</span><span class="sxs-lookup"><span data-stu-id="dd8e9-102">Adding a Service Reference in a Workflow Solution</span></span>
<span data-ttu-id="dd8e9-103">在工作流程應用程式中加入服務參考的運作方式與在一般 WCF 應用程式中加入服務參考的運作方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="dd8e9-104">當您選取 [加入服務參考]，並指定服務的 URL 時，會下載中繼資料，並產生自訂活動，讓您呼叫您加入參考的 WCF 服務或 WCF 工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-104">When you select Add Service Reference and specify the URL to the service the metadata is downloaded and custom activities are generated that allow you to call the WCF service or WCF workflow service you added a reference to.</span></span> <span data-ttu-id="dd8e9-105">加入服務參考之後，重建方案，因而建置所產生的活動。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="dd8e9-106">接著，這些活動會出現在工作流程設計工具工具箱中。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="dd8e9-107">但是請注意，只有在您於工作流程方案中加入服務參考時，這才有作用。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-107">Note however, that this will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="dd8e9-108">下列的網路廣播說明如何在其他類型的專案中加入服務參考：[從 Web 專案中的工作流程中呼叫 WCF 服務](http://go.microsoft.com/fwlink/?LinkId=207725)。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](http://go.microsoft.com/fwlink/?LinkId=207725).</span></span>  
  
 <span data-ttu-id="dd8e9-109">將兩個或多個服務參考加入至包含相同作業名稱的服務將會造成問題。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="dd8e9-110">產生的活動只會呼叫第一個服務作業。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="dd8e9-111">若要解決這個問題，請重新命名服務作業，使它們不相同，或在每個產生的活動中變更端點組態名稱。</span><span class="sxs-lookup"><span data-stu-id="dd8e9-111">To work around this issue rename the service operations so they are different or change the endpoint configuration name within each generated activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8e9-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd8e9-112">See Also</span></span>  
 [<span data-ttu-id="dd8e9-113">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="dd8e9-113">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="dd8e9-114">如何：建立會呼叫其他工作流程服務的工作流程服務</span><span class="sxs-lookup"><span data-stu-id="dd8e9-114">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [<span data-ttu-id="dd8e9-115">從工作流程中的 Web 專案中呼叫 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="dd8e9-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=207725)
