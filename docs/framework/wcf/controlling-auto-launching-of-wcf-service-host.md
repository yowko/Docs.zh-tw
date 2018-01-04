---
title: "控制 WCF 服務主機的自動啟動功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65daceac9b865f3e8224c709d672344606905d9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="2a801-102">控制 WCF 服務主機的自動啟動功能</span><span class="sxs-lookup"><span data-stu-id="2a801-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="2a801-103">在針對包含多個專案之相同 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 方案中的另一個專案進行偵錯時，您可以控制 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務程式庫專案中 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 服務主機 (WcfSvcHost.exe) 的自動啟動功能。</span><span class="sxs-lookup"><span data-stu-id="2a801-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="2a801-104">若要這樣做，請以滑鼠右鍵按一下[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務專案中**方案總管 中**，選擇**屬性**，然後按一下**WCF 選項** 索引標籤。**啟動 WCF 服務主機相同方案中的另一個專案進行偵錯時**核取方塊預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="2a801-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="2a801-105">您可以清除這個方塊，這樣一來這個特定專案的 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務主機就不會在相同方案中的另一個專案進行偵錯時啟動。</span><span class="sxs-lookup"><span data-stu-id="2a801-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="2a801-106">這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。</span><span class="sxs-lookup"><span data-stu-id="2a801-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="2a801-107">這個選項可供下列專案使用：</span><span class="sxs-lookup"><span data-stu-id="2a801-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="2a801-108"> 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="2a801-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="2a801-109">循序工作流程服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="2a801-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="2a801-110">狀態機器工作流程服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="2a801-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="2a801-111">新聞訂閱服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="2a801-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a801-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a801-112">See Also</span></span>  
 [<span data-ttu-id="2a801-113">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="2a801-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
