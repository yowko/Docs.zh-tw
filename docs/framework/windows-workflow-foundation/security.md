---
title: 安全性
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: c27ac9cf41436332d560e11987e3ce4b68576895
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720627"
---
# <a name="security"></a><span data-ttu-id="6dce3-102">安全性</span><span class="sxs-lookup"><span data-stu-id="6dce3-102">Security</span></span>
<span data-ttu-id="6dce3-103">SQL 工作流程執行個體存放區會使用下列資料庫安全性角色，安全地存取持續性資料庫中的執行個體狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="6dce3-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="6dce3-104">**System.Activities.DurableInstancing.InstanceStoreUsers**。</span><span class="sxs-lookup"><span data-stu-id="6dce3-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="6dce3-105">這個角色具有公用檢視表的讀取與寫入權限，以及執行個體建立、載入及儲存相關之預存程序的執行權限。</span><span class="sxs-lookup"><span data-stu-id="6dce3-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="6dce3-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="6dce3-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="6dce3-107">這個角色具有公用檢視表的唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="6dce3-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="6dce3-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**。</span><span class="sxs-lookup"><span data-stu-id="6dce3-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="6dce3-109">這個角色具有與執行個體啟動程序相關之預存程序的執行權限。</span><span class="sxs-lookup"><span data-stu-id="6dce3-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="6dce3-110">如需有關執行個體啟用的詳細資訊，請參閱[執行個體啟用](instance-activation.md)。</span><span class="sxs-lookup"><span data-stu-id="6dce3-110">For more information about instance activation, see [Instance Activation](instance-activation.md).</span></span> <span data-ttu-id="6dce3-111">請將用於執行泛型主機 (例如 [!INCLUDE[dublin](../../../includes/dublin-md.md)] 的工作流程管理服務) 的使用者帳戶加入至這個資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="6dce3-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 <span data-ttu-id="6dce3-112">如需有關使用 Windows Server App Fabric 持續性存放區安全性的詳細資訊，請參閱[中 App Fabric 持續性存放區的安全性設定](https://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="6dce3-112">For more information about security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](https://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6dce3-113">用戶端若可在執行個體存放區中存取其本身的執行個體資料，即可存取同一個執行個體存放區中的其他所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="6dce3-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="6dce3-114">執行個體存放區不支援指定執行個體層級的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="6dce3-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="6dce3-115">您應建立單獨的執行個體存放區，並對應不同的群組/使用者，使其擁有不同的存放區存取權限。</span><span class="sxs-lookup"><span data-stu-id="6dce3-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
