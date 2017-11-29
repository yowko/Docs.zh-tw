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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a17b77293d9a12fd3720fc54cb6c17a28a8c6ed0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="security"></a>安全性
SQL 工作流程執行個體存放區會使用下列資料庫安全性角色，安全地存取持續性資料庫中的執行個體狀態資訊。  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**。 這個角色具有公用檢視表的讀取與寫入權限，以及執行個體建立、載入及儲存相關之預存程序的執行權限。  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**。 這個角色具有公用檢視表的唯讀存取權。  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**。 這個角色具有與執行個體啟動程序相關之預存程序的執行權限。 如需有關執行個體啟用的詳細資訊，請參閱[執行個體啟用](../../../docs/framework/windows-workflow-foundation/instance-activation.md)。 請將用於執行泛型主機 (例如 [!INCLUDE[dublin](../../../includes/dublin-md.md)] 的工作流程管理服務) 的使用者帳戶加入至這個資料庫角色。  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]請參閱 Windows Server App Fabric，持續性存放區的安全性[App Fabric 中持續性存放區的安全性組態](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  用戶端若可在執行個體存放區中存取其本身的執行個體資料，即可存取同一個執行個體存放區中的其他所有執行個體。 執行個體存放區不支援指定執行個體層級的安全性權限。 您應建立單獨的執行個體存放區，並對應不同的群組/使用者，使其擁有不同的存放區存取權限。
