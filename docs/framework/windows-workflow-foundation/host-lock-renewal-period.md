---
title: Host Lock Renewal Period
ms.date: 03/30/2017
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
ms.openlocfilehash: 82073377353be6d4f8a7d0a343c31f2b49a2873f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268186"
---
# <a name="host-lock-renewal-period"></a>Host Lock Renewal Period

SQL 工作流程實例存放區的 [ **主機鎖定更新期間** ] 屬性，可讓您指定主機在工作流程實例上更新其鎖定的時間週期。 Host Lock Renewal Period 的鎖定保持 30 秒以上有效。 如果主機沒有在這個時間週期內更新鎖定 (換句話說，延長租用期)，則鎖定會逾時，且持續性提供者會解除鎖定執行個體。 這個屬性的值是 "hh： mm： ss" 格式的 TimeSpan 類型。 允許的最小值為 "00:00:01" (1 秒) 。 這個屬性的預設值是 "00:00:30" (30 秒) 。  
  
 在工作流程服務主機解除鎖定擁有的工作流程服務執行個體之前即發生錯誤的案例中，此屬性特別重要。 在這個案例中，持續性提供者在鎖定逾時後，即會移除在持續性資料庫中的工作流程服務執行個體鎖定，這樣在伺服器群中相同電腦或其他電腦上執行的工作流程服務主機，就可將工作流程服務執行個體的鎖定與載入擷取至記憶體，以從最新的持續狀態中繼續執行。  
  
 為此屬性設定較高的值，會導致工作流程執行個體在持續性資料庫中鎖定很長的一段時間，因而延遲執行個體從最新持續點復原。 為此屬性設定較短的間隔，會導致工作流程服務主機的新執行個體快速挑出錯誤的工作流程服務執行個體，但會增加工作流程服務主機和 SQL Server 資料庫的工作負載。  
  
 SQL 工作流程執行個體存放區會執行內部工作，定期喚醒及偵測執行個體上是否有逾時的鎖定。 找到逾時鎖定的執行個體時，就會將此執行個體放入 RunnableInstances 資料表中，使工作流程主機可挑出並執行這些執行個體。
