---
title: 可執行的執行個體偵測週期
ms.date: 03/30/2017
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
ms.openlocfilehash: 7b12353c3bd18367618825d22d020391b14ec3f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513233"
---
# <a name="runnable-instances-detection-period"></a><span data-ttu-id="9c2fe-102">可執行的執行個體偵測週期</span><span class="sxs-lookup"><span data-stu-id="9c2fe-102">Runnable Instances Detection Period</span></span>
<span data-ttu-id="9c2fe-103">SQL 工作流程執行個體存放區會執行內部工作，該工作會定期喚醒及偵測持續性資料庫中可執行或可啟動的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c2fe-103">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects runnable or activatable instances in the persistence database.</span></span> <span data-ttu-id="9c2fe-104">**可執行個體偵測週期**SQL 工作流程執行個體存放區的屬性會指定時間週期之後，SQL 工作流程執行個體存放區會執行偵測工作，偵測到任何可執行或可啟動的工作流程在上一個偵測循環之後，持續性資料庫中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c2fe-104">The **Runnable Instances Detection Period** property of the SQL Workflow Instance Store specifies the time period after which the SQL Workflow Instance Store runs a detection task to detect any runnable or activatable workflow instances in the persistence database after the previous detection cycle.</span></span>  
  
 <span data-ttu-id="9c2fe-105">為這個屬性設定較短的間隔，可縮短與工作流程執行個體相關之計時器逾時和發出事件訊號及後續載入執行個體之間的時間。</span><span class="sxs-lookup"><span data-stu-id="9c2fe-105">Setting a shorter interval for this property reduces the time between the expiration of a timer associated with a workflow instance and the signaling of the event and subsequent loading of the instance.</span></span> <span data-ttu-id="9c2fe-106">不過，這麼做也會增加主機的處理負載，在極少出現永久性計時器和/或主機故障的案例中，可能不是適當的做法。</span><span class="sxs-lookup"><span data-stu-id="9c2fe-106">However, it also increases the processing load on a host and may not be desirable in scenarios where durable timers and/or host failures are rare.</span></span> <span data-ttu-id="9c2fe-107">屬性的型別是 TimeSpan，屬性值的格式則為：hh:mm:ss。</span><span class="sxs-lookup"><span data-stu-id="9c2fe-107">The type of the property is TimeSpan and the value of the property follows the format: hh:mm:ss.</span></span> <span data-ttu-id="9c2fe-108">這個屬性的最小值是 00:00:01。</span><span class="sxs-lookup"><span data-stu-id="9c2fe-108">The minimum value for this property is 00:00:01.</span></span> <span data-ttu-id="9c2fe-109">屬性的預設值為 00:00:05。</span><span class="sxs-lookup"><span data-stu-id="9c2fe-109">The default value for the property is 00:00:05.</span></span>  
  
 <span data-ttu-id="9c2fe-110">如需偵測與啟動可執行及可啟動的工作流程執行個體，請參閱[執行個體啟用](../../../docs/framework/windows-workflow-foundation/instance-activation.md)。</span><span class="sxs-lookup"><span data-stu-id="9c2fe-110">For more information detecting and activating runnable and activatable workflow instances, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span>
