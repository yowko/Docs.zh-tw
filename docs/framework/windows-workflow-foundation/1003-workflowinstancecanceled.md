---
title: 1003 - WorkflowInstanceCanceled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b264450703090edfcf99f9584c16d33eb82a76e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="bf92e-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="bf92e-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="bf92e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="bf92e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf92e-104">ID</span><span class="sxs-lookup"><span data-stu-id="bf92e-104">ID</span></span>|<span data-ttu-id="bf92e-105">1003</span><span class="sxs-lookup"><span data-stu-id="bf92e-105">1003</span></span>|  
|<span data-ttu-id="bf92e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="bf92e-106">Keywords</span></span>|<span data-ttu-id="bf92e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bf92e-107">WFRuntime</span></span>|  
|<span data-ttu-id="bf92e-108">層級</span><span class="sxs-lookup"><span data-stu-id="bf92e-108">Level</span></span>|<span data-ttu-id="bf92e-109">資訊</span><span class="sxs-lookup"><span data-stu-id="bf92e-109">Information</span></span>|  
|<span data-ttu-id="bf92e-110">通道</span><span class="sxs-lookup"><span data-stu-id="bf92e-110">Channel</span></span>|<span data-ttu-id="bf92e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bf92e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bf92e-112">描述</span><span class="sxs-lookup"><span data-stu-id="bf92e-112">Description</span></span>  
 <span data-ttu-id="bf92e-113">表示工作流程執行個體已在 Canceled 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="bf92e-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bf92e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="bf92e-114">Message</span></span>  
 <span data-ttu-id="bf92e-115">WorkflowInstance Id：'%1' 已在 Canceled 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="bf92e-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bf92e-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bf92e-116">Details</span></span>  
  
|<span data-ttu-id="bf92e-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="bf92e-117">Data Item Name</span></span>|<span data-ttu-id="bf92e-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="bf92e-118">Data Item Type</span></span>|<span data-ttu-id="bf92e-119">描述</span><span class="sxs-lookup"><span data-stu-id="bf92e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bf92e-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="bf92e-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="bf92e-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="bf92e-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="bf92e-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bf92e-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bf92e-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="bf92e-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
