---
title: 安全性
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: e4419a7a73015541e0a75b4f8c615485c5fdac1b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267269"
---
# <a name="security"></a><span data-ttu-id="2dfde-102">安全性</span><span class="sxs-lookup"><span data-stu-id="2dfde-102">Security</span></span>

<span data-ttu-id="2dfde-103">SQL 工作流程執行個體存放區會使用下列資料庫安全性角色，安全地存取持續性資料庫中的執行個體狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="2dfde-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
- <span data-ttu-id="2dfde-104">**DurableInstancing. system.activities.durableinstancing.instancestoreusers**。</span><span class="sxs-lookup"><span data-stu-id="2dfde-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="2dfde-105">這個角色具有公用檢視表的讀取與寫入權限，以及執行個體建立、載入及儲存相關之預存程序的執行權限。</span><span class="sxs-lookup"><span data-stu-id="2dfde-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
- <span data-ttu-id="2dfde-106">**DurableInstancing. InstanceStoreObservers**。</span><span class="sxs-lookup"><span data-stu-id="2dfde-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="2dfde-107">這個角色具有公用檢視表的唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="2dfde-107">This role has read-only access to public views.</span></span>  
  
- <span data-ttu-id="2dfde-108">**DurableInstancing. WorkflowActivationUsers**。</span><span class="sxs-lookup"><span data-stu-id="2dfde-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="2dfde-109">這個角色具有與執行個體啟動程序相關之預存程序的執行權限。</span><span class="sxs-lookup"><span data-stu-id="2dfde-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="2dfde-110">如需實例啟用的詳細資訊，請參閱 [實例啟用](instance-activation.md)。</span><span class="sxs-lookup"><span data-stu-id="2dfde-110">For more information about instance activation, see [Instance Activation](instance-activation.md).</span></span> <span data-ttu-id="2dfde-111">一般主機 (（例如 Windows Server) AppFabric 的裝載功能的工作流程管理服務）所使用的使用者帳戶，應該加入至此資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="2dfde-111">The user account under which a generic host (such as the Workflow Management Service of the hosting features of Windows Server AppFabric) runs should be added to this database role.</span></span>  
  
 <span data-ttu-id="2dfde-112">如需有關 Windows Server App Fabric 的持續性存放區安全性的詳細資訊，請參閱[應用程式網狀架構中的持續性存放區安全性](/previous-versions/appfabric/ff431727(v=azure.10))設定</span><span class="sxs-lookup"><span data-stu-id="2dfde-112">For more information about security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](/previous-versions/appfabric/ff431727(v=azure.10))</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2dfde-113">用戶端若可在執行個體存放區中存取其本身的執行個體資料，即可存取同一個執行個體存放區中的其他所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="2dfde-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="2dfde-114">執行個體存放區不支援指定執行個體層級的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="2dfde-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="2dfde-115">您應建立單獨的執行個體存放區，並對應不同的群組/使用者，使其擁有不同的存放區存取權限。</span><span class="sxs-lookup"><span data-stu-id="2dfde-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
