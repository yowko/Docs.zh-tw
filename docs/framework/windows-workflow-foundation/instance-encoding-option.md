---
title: 執行個體編碼選項
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: c4de7c45d899f45a7b5b71d563257d9accb8fdbb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315617"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="6d791-102">執行個體編碼選項</span><span class="sxs-lookup"><span data-stu-id="6d791-102">Instance Encoding Option</span></span>
<span data-ttu-id="6d791-103">**執行個體編碼選項**SQL 工作流程執行個體存放區的屬性可讓您指定 SQL 持續性提供者是否應該壓縮使用 GZip 演算法才能儲存工作流程執行個體狀態資訊將持續性資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="6d791-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="6d791-104">此屬性允許的值為：GZip 和 None。</span><span class="sxs-lookup"><span data-stu-id="6d791-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="6d791-105">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="6d791-105">The default value is None.</span></span> <span data-ttu-id="6d791-106">下列清單描述這些選項。</span><span class="sxs-lookup"><span data-stu-id="6d791-106">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="6d791-107">**GZip**。</span><span class="sxs-lookup"><span data-stu-id="6d791-107">**GZip**.</span></span> <span data-ttu-id="6d791-108">將狀態資訊保存在持續性資料庫中之前，持續性提供者會利用 GZip 演算法編碼狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="6d791-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="6d791-109">**None**：</span><span class="sxs-lookup"><span data-stu-id="6d791-109">**None**.</span></span> <span data-ttu-id="6d791-110">將狀態資訊保存在持續性資料庫中之前，持續性提供者不會將狀態資訊編碼。</span><span class="sxs-lookup"><span data-stu-id="6d791-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="6d791-111">利用 GZip 編碼工作流程執行個體狀態資訊可以減少耗用 SQL 資料庫中的記憶體，同時也能減少耗用網路流量 (如果資料庫所在的電腦與執行工作流程服務主機的電腦位於不同的網路)。</span><span class="sxs-lookup"><span data-stu-id="6d791-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="6d791-112">一般的準則是將**執行個體編碼選項**屬性設**無**如果工作流程執行個體的狀態很小。</span><span class="sxs-lookup"><span data-stu-id="6d791-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
