---
title: 安全性
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: 0fd77ce335848c58a7b734236124b90999355270
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837671"
---
# <a name="security"></a>安全性
SQL 工作流程執行個體存放區會使用下列資料庫安全性角色，安全地存取持續性資料庫中的執行個體狀態資訊。  
  
- **DurableInstancing. system.activities.durableinstancing.instancestoreusers**。 這個角色具有公用檢視表的讀取與寫入權限，以及執行個體建立、載入及儲存相關之預存程序的執行權限。  
  
- **DurableInstancing. InstanceStoreObservers**。 這個角色具有公用檢視表的唯讀存取權。  
  
- **DurableInstancing. WorkflowActivationUsers**。 這個角色具有與執行個體啟動程序相關之預存程序的執行權限。 如需實例啟用的詳細資訊，請參閱[實例啟用](instance-activation.md)。 一般主機（例如 Windows Server AppFabric 的裝載功能的工作流程管理服務）執行所用的使用者帳戶，應該加入這個資料庫角色。  
  
 如需 Windows Server App Fabric 持續性存放區安全性的詳細資訊，請參閱[App Fabric 中持續性存放區的安全性](https://docs.microsoft.com/previous-versions/appfabric/ff431727(v=azure.10))設定  
  
> [!CAUTION]
> 用戶端若可在執行個體存放區中存取其本身的執行個體資料，即可存取同一個執行個體存放區中的其他所有執行個體。 執行個體存放區不支援指定執行個體層級的安全性權限。 您應建立單獨的執行個體存放區，並對應不同的群組/使用者，使其擁有不同的存放區存取權限。
