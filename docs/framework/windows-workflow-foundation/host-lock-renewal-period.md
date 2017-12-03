---
title: Host Lock Renewal Period
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48a5d2e1d8c5381f322ea1b6ffc9022853683efc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="host-lock-renewal-period"></a><span data-ttu-id="32055-102">Host Lock Renewal Period</span><span class="sxs-lookup"><span data-stu-id="32055-102">Host Lock Renewal Period</span></span>
<span data-ttu-id="32055-103">**Host Lock Renewal Period** SQL 工作流程執行個體存放區的屬性可讓您指定主機更新工作流程執行個體上的鎖定的時間週期。</span><span class="sxs-lookup"><span data-stu-id="32055-103">The **Host Lock Renewal Period** property of the SQL Workflow Instance Store lets you specify the time period within which the host renews its lock on a workflow instance.</span></span> <span data-ttu-id="32055-104">Host Lock Renewal Period 的鎖定保持 30 秒以上有效。</span><span class="sxs-lookup"><span data-stu-id="32055-104">The lock remains valid for Host Lock Renewal Period + 30 seconds.</span></span> <span data-ttu-id="32055-105">如果主機沒有在這個時間週期內更新鎖定 (換句話說，延長租用期)，則鎖定會逾時，且持續性提供者會解除鎖定執行個體。</span><span class="sxs-lookup"><span data-stu-id="32055-105">If the host fails to renew the lock (in other words, extend the lease) within this time period, the lock expires and the persistence provider unlocks the instance.</span></span> <span data-ttu-id="32055-106">這個屬性的值是 TimeSpan 表單"hh: mm: 「 型別。</span><span class="sxs-lookup"><span data-stu-id="32055-106">The value for this property is of type TimeSpan of the form "hh:mm:ss".</span></span> <span data-ttu-id="32055-107">允許最小值是"00: 00:01"（1 秒）。</span><span class="sxs-lookup"><span data-stu-id="32055-107">The minimum permitted value is "00:00:01" (1 second).</span></span> <span data-ttu-id="32055-108">這個屬性的預設值是"00: 00:30"（30 秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="32055-108">The default value of this property is "00:00:30" (30 seconds).</span></span>  
  
 <span data-ttu-id="32055-109">在工作流程服務主機解除鎖定擁有的工作流程服務執行個體之前即發生錯誤的案例中，此屬性特別重要。</span><span class="sxs-lookup"><span data-stu-id="32055-109">This property is significant in scenarios where a workflow service host fails before it can unlock a workflow service instance that it owns.</span></span> <span data-ttu-id="32055-110">在這個案例中，持續性提供者在鎖定逾時後，即會移除在持續性資料庫中的工作流程服務執行個體鎖定，這樣在伺服器群中相同電腦或其他電腦上執行的工作流程服務主機，就可將工作流程服務執行個體的鎖定與載入擷取至記憶體，以從最新的持續狀態中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="32055-110">In this scenario, the lock on the workflow service instance in the persistence database is removed by the persistence provider after the lock expires so that another workflow service host running on the same computer or another computer in a server farm can acquire the lock and load the workflow service instance into memory to resume its execution from its last persisted state.</span></span>  
  
 <span data-ttu-id="32055-111">為此屬性設定較高的值，會導致工作流程執行個體在持續性資料庫中鎖定很長的一段時間，因而延遲執行個體從最新持續點復原。</span><span class="sxs-lookup"><span data-stu-id="32055-111">Setting a higher value for this property causes the workflow service instances to be locked in the persistence database for a longer time and therefore delays the recovery of the instance from the last persistence point.</span></span> <span data-ttu-id="32055-112">為此屬性設定較短的間隔，會導致工作流程服務主機的新執行個體快速挑出錯誤的工作流程服務執行個體，但會增加工作流程服務主機和 SQL Server 資料庫的工作負載。</span><span class="sxs-lookup"><span data-stu-id="32055-112">Setting a short interval for this property causes the new instance of the workflow service host to pick up the failed workflow service instance quickly, but causes an increase in workload for the workflow service host and the SQL Server database.</span></span>  
  
 <span data-ttu-id="32055-113">SQL 工作流程執行個體存放區會執行內部工作，定期喚醒及偵測執行個體上是否有逾時的鎖定。</span><span class="sxs-lookup"><span data-stu-id="32055-113">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects instances with expired locks on them.</span></span> <span data-ttu-id="32055-114">找到逾時鎖定的執行個體時，就會將此執行個體放入 RunnableInstances 資料表中，使工作流程主機可挑出並執行這些執行個體。</span><span class="sxs-lookup"><span data-stu-id="32055-114">When it finds instances with expired locks, it places the instances in the RunnableInstances table so that a workflow host can pick up and run these instances.</span></span>
