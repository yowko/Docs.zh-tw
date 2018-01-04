---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26491c1e2b20f4285aaedbcd12947cad3562f041
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="15184-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="15184-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="15184-103">屬性</span><span class="sxs-lookup"><span data-stu-id="15184-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15184-104">ID</span><span class="sxs-lookup"><span data-stu-id="15184-104">ID</span></span>|<span data-ttu-id="15184-105">1008</span><span class="sxs-lookup"><span data-stu-id="15184-105">1008</span></span>|  
|<span data-ttu-id="15184-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="15184-106">Keywords</span></span>|<span data-ttu-id="15184-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="15184-107">WFRuntime</span></span>|  
|<span data-ttu-id="15184-108">層級</span><span class="sxs-lookup"><span data-stu-id="15184-108">Level</span></span>|<span data-ttu-id="15184-109">資訊</span><span class="sxs-lookup"><span data-stu-id="15184-109">Information</span></span>|  
|<span data-ttu-id="15184-110">通道</span><span class="sxs-lookup"><span data-stu-id="15184-110">Channel</span></span>|<span data-ttu-id="15184-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="15184-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="15184-112">描述</span><span class="sxs-lookup"><span data-stu-id="15184-112">Description</span></span>  
 <span data-ttu-id="15184-113">表示工作流程應用程式已卸載。</span><span class="sxs-lookup"><span data-stu-id="15184-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="15184-114">訊息</span><span class="sxs-lookup"><span data-stu-id="15184-114">Message</span></span>  
 <span data-ttu-id="15184-115">WorkflowInstance Id：'%1' 已卸載。</span><span class="sxs-lookup"><span data-stu-id="15184-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="15184-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="15184-116">Details</span></span>  
  
|<span data-ttu-id="15184-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="15184-117">Data Item Name</span></span>|<span data-ttu-id="15184-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="15184-118">Data Item Type</span></span>|<span data-ttu-id="15184-119">描述</span><span class="sxs-lookup"><span data-stu-id="15184-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="15184-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="15184-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="15184-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="15184-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="15184-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="15184-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="15184-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="15184-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
