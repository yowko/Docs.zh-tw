---
title: 執行個體完成動作
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 698ac0ed5a7cbd4f6a5623cf8d9b6fbea1128d0a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044334"
---
# <a name="instance-completion-action"></a><span data-ttu-id="62189-102">執行個體完成動作</span><span class="sxs-lookup"><span data-stu-id="62189-102">Instance Completion Action</span></span>

<span data-ttu-id="62189-103">SQL 工作流程實例存放區的 [**實例完成動作**] 屬性, 可讓您指定是否要在完成實例之後, 從持續性資料庫中刪除工作流程實例的資料和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="62189-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="62189-104">此屬性允許的值為**DeleteAll**和**DeleteNothing**。</span><span class="sxs-lookup"><span data-stu-id="62189-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="62189-105">下列清單描述這些選項：</span><span class="sxs-lookup"><span data-stu-id="62189-105">The following list describes these options:</span></span>

- <span data-ttu-id="62189-106">**DeleteAll (預設值)。**</span><span class="sxs-lookup"><span data-stu-id="62189-106">**DeleteAll (default).**</span></span> <span data-ttu-id="62189-107">如果將屬性的值設定為 DeleteAll，則在執行個體完成後，就會自持續性資料庫刪除工作流程執行個體的資料和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="62189-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>

- <span data-ttu-id="62189-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="62189-108">**DeleteNothing.**</span></span> <span data-ttu-id="62189-109">如果將屬性的值設定為 DeleteNothing，則即使執行個體已完成，仍會將工作流程執行個體的資料和中繼資料保存在持續性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="62189-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="62189-110">在執行個體完成後仍保留執行個體狀態資訊，會使持續性資料庫變大。</span><span class="sxs-lookup"><span data-stu-id="62189-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="62189-111">隨著資料庫的擴充，持續性子系統執行資料庫作業的時間就會變長，因此您需要定期清除持續性資料庫中的執行個體狀態資訊，服務的執行層級才能符合您的效能需求。</span><span class="sxs-lookup"><span data-stu-id="62189-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
