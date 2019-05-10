---
title: 執行個體完成動作
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: d68f41a586e44f96c9ca26cf8a142a2782adaa36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662969"
---
# <a name="instance-completion-action"></a><span data-ttu-id="acad9-102">執行個體完成動作</span><span class="sxs-lookup"><span data-stu-id="acad9-102">Instance Completion Action</span></span>
<span data-ttu-id="acad9-103">**執行個體完成動作**SQL 工作流程執行個體存放區的屬性可讓您指定是否的資料和工作流程執行個體的中繼資料從持續性資料庫完成後，刪除執行個體。</span><span class="sxs-lookup"><span data-stu-id="acad9-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="acad9-104">允許的值，這個屬性為**DeleteAll**並**DeleteNothing**。</span><span class="sxs-lookup"><span data-stu-id="acad9-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="acad9-105">下列清單描述這些選項：</span><span class="sxs-lookup"><span data-stu-id="acad9-105">The following list describes these options:</span></span>  
  
- <span data-ttu-id="acad9-106">**DeleteAll （預設值）。**</span><span class="sxs-lookup"><span data-stu-id="acad9-106">**DeleteAll (default).**</span></span> <span data-ttu-id="acad9-107">如果將屬性的值設定為 DeleteAll，則在執行個體完成後，就會自持續性資料庫刪除工作流程執行個體的資料和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="acad9-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
- <span data-ttu-id="acad9-108">**DeleteNothing。**</span><span class="sxs-lookup"><span data-stu-id="acad9-108">**DeleteNothing.**</span></span> <span data-ttu-id="acad9-109">如果將屬性的值設定為 DeleteNothing，則即使執行個體已完成，仍會將工作流程執行個體的資料和中繼資料保存在持續性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="acad9-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="acad9-110">在執行個體完成後仍保留執行個體狀態資訊，會使持續性資料庫變大。</span><span class="sxs-lookup"><span data-stu-id="acad9-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="acad9-111">隨著資料庫的擴充，持續性子系統執行資料庫作業的時間就會變長，因此您需要定期清除持續性資料庫中的執行個體狀態資訊，服務的執行層級才能符合您的效能需求。</span><span class="sxs-lookup"><span data-stu-id="acad9-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
