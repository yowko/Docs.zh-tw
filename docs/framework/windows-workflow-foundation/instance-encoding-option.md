---
title: 執行個體編碼選項
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 416394eb346a7c82385da32a89bd54179b255cd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279892"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="68fc8-102">執行個體編碼選項</span><span class="sxs-lookup"><span data-stu-id="68fc8-102">Instance Encoding Option</span></span>

<span data-ttu-id="68fc8-103">SQL 工作流程實例存放區的 **實例編碼選項** 屬性，可讓您指定 sql 持續性提供者是否應使用 GZip 演算法壓縮工作流程實例狀態資訊，再將資訊儲存至持續性資料庫中。</span><span class="sxs-lookup"><span data-stu-id="68fc8-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="68fc8-104">此屬性允許的值為：GZip 和 None。</span><span class="sxs-lookup"><span data-stu-id="68fc8-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="68fc8-105">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="68fc8-105">The default value is None.</span></span> <span data-ttu-id="68fc8-106">下列清單描述這些選項。</span><span class="sxs-lookup"><span data-stu-id="68fc8-106">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="68fc8-107">**GZip**。</span><span class="sxs-lookup"><span data-stu-id="68fc8-107">**GZip**.</span></span> <span data-ttu-id="68fc8-108">將狀態資訊保存在持續性資料庫中之前，持續性提供者會利用 GZip 演算法編碼狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="68fc8-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="68fc8-109">**None**：</span><span class="sxs-lookup"><span data-stu-id="68fc8-109">**None**.</span></span> <span data-ttu-id="68fc8-110">將狀態資訊保存在持續性資料庫中之前，持續性提供者不會將狀態資訊編碼。</span><span class="sxs-lookup"><span data-stu-id="68fc8-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="68fc8-111">利用 GZip 編碼工作流程執行個體狀態資訊可以減少耗用 SQL 資料庫中的記憶體，同時也能減少耗用網路流量 (如果資料庫所在的電腦與執行工作流程服務主機的電腦位於不同的網路)。</span><span class="sxs-lookup"><span data-stu-id="68fc8-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="68fc8-112">一般的指導方針是，如果工作流程實例的狀態很小，則將 [ **實例編碼選項** ] 屬性設定為 [ **無** ]。</span><span class="sxs-lookup"><span data-stu-id="68fc8-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
