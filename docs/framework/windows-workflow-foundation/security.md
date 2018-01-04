---
title: "安全性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 461bc36fd85a158e67c29c3f4ad001997218c824
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="security"></a><span data-ttu-id="1657f-102">安全性</span><span class="sxs-lookup"><span data-stu-id="1657f-102">Security</span></span>
<span data-ttu-id="1657f-103">SQL 工作流程執行個體存放區會使用下列資料庫安全性角色，安全地存取持續性資料庫中的執行個體狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="1657f-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="1657f-104">**System.Activities.DurableInstancing.InstanceStoreUsers**。</span><span class="sxs-lookup"><span data-stu-id="1657f-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="1657f-105">這個角色具有公用檢視表的讀取與寫入權限，以及執行個體建立、載入及儲存相關之預存程序的執行權限。</span><span class="sxs-lookup"><span data-stu-id="1657f-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="1657f-106">**System.Activities.DurableInstancing.InstanceStoreObservers**。</span><span class="sxs-lookup"><span data-stu-id="1657f-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="1657f-107">這個角色具有公用檢視表的唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="1657f-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="1657f-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**。</span><span class="sxs-lookup"><span data-stu-id="1657f-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="1657f-109">這個角色具有與執行個體啟動程序相關之預存程序的執行權限。</span><span class="sxs-lookup"><span data-stu-id="1657f-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="1657f-110">如需有關執行個體啟用的詳細資訊，請參閱[執行個體啟用](../../../docs/framework/windows-workflow-foundation/instance-activation.md)。</span><span class="sxs-lookup"><span data-stu-id="1657f-110">For more information about instance activation, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span> <span data-ttu-id="1657f-111">請將用於執行泛型主機 (例如 [!INCLUDE[dublin](../../../includes/dublin-md.md)] 的工作流程管理服務) 的使用者帳戶加入至這個資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="1657f-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="1657f-112">請參閱 Windows Server App Fabric，持續性存放區的安全性[App Fabric 中持續性存放區的安全性組態](http://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="1657f-112"> security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1657f-113">用戶端若可在執行個體存放區中存取其本身的執行個體資料，即可存取同一個執行個體存放區中的其他所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="1657f-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="1657f-114">執行個體存放區不支援指定執行個體層級的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="1657f-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="1657f-115">您應建立單獨的執行個體存放區，並對應不同的群組/使用者，使其擁有不同的存放區存取權限。</span><span class="sxs-lookup"><span data-stu-id="1657f-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
