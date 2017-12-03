---
title: "執行個體編碼選項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a874f88b787a99af0461ff47c3ae246442af2f19
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="instance-encoding-option"></a><span data-ttu-id="25430-102">執行個體編碼選項</span><span class="sxs-lookup"><span data-stu-id="25430-102">Instance Encoding Option</span></span>
<span data-ttu-id="25430-103">**執行個體編碼選項**SQL 工作流程執行個體存放區的屬性可讓您指定 SQL 持續性提供者是否應該壓縮使用 GZip 演算法，之後再儲存工作流程執行個體狀態資訊將持續性資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="25430-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="25430-104">此屬性允許的值為：GZip 和 None。</span><span class="sxs-lookup"><span data-stu-id="25430-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="25430-105">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="25430-105">The default value is None.</span></span> <span data-ttu-id="25430-106">下列清單描述這些選項。</span><span class="sxs-lookup"><span data-stu-id="25430-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="25430-107">**GZip**。</span><span class="sxs-lookup"><span data-stu-id="25430-107">**GZip**.</span></span> <span data-ttu-id="25430-108">將狀態資訊保存在持續性資料庫中之前，持續性提供者會利用 GZip 演算法編碼狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="25430-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="25430-109">**無**。</span><span class="sxs-lookup"><span data-stu-id="25430-109">**None**.</span></span> <span data-ttu-id="25430-110">將狀態資訊保存在持續性資料庫中之前，持續性提供者不會將狀態資訊編碼。</span><span class="sxs-lookup"><span data-stu-id="25430-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="25430-111">利用 GZip 編碼工作流程執行個體狀態資訊可以減少耗用 SQL 資料庫中的記憶體，同時也能減少耗用網路流量 (如果資料庫所在的電腦與執行工作流程服務主機的電腦位於不同的網路)。</span><span class="sxs-lookup"><span data-stu-id="25430-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="25430-112">通用準則是設定**執行個體編碼選項**屬性**無**如果工作流程執行個體狀態不大。</span><span class="sxs-lookup"><span data-stu-id="25430-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
