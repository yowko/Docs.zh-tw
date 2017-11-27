---
title: 1103 - WorkflowActivitySuspend
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a55cd953b294ca5e8a90f6ade666c55b51dc1e58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1103---workflowactivitysuspend"></a><span data-ttu-id="d5e3e-102">1103 - WorkflowActivitySuspend</span><span class="sxs-lookup"><span data-stu-id="d5e3e-102">1103 - WorkflowActivitySuspend</span></span>
## <a name="properties"></a><span data-ttu-id="d5e3e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="d5e3e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5e3e-104">ID</span><span class="sxs-lookup"><span data-stu-id="d5e3e-104">ID</span></span>|<span data-ttu-id="d5e3e-105">1103</span><span class="sxs-lookup"><span data-stu-id="d5e3e-105">1103</span></span>|  
|<span data-ttu-id="d5e3e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d5e3e-106">Keywords</span></span>|<span data-ttu-id="d5e3e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d5e3e-107">WFRuntime</span></span>|  
|<span data-ttu-id="d5e3e-108">層級</span><span class="sxs-lookup"><span data-stu-id="d5e3e-108">Level</span></span>|<span data-ttu-id="d5e3e-109">資訊</span><span class="sxs-lookup"><span data-stu-id="d5e3e-109">Information</span></span>|  
|<span data-ttu-id="d5e3e-110">通道</span><span class="sxs-lookup"><span data-stu-id="d5e3e-110">Channel</span></span>|<span data-ttu-id="d5e3e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d5e3e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d5e3e-112">描述</span><span class="sxs-lookup"><span data-stu-id="d5e3e-112">Description</span></span>  
 <span data-ttu-id="d5e3e-113">表示已暫停工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="d5e3e-113">Indicates a workflow activity has been suspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d5e3e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="d5e3e-114">Message</span></span>  
 <span data-ttu-id="d5e3e-115">WorkflowInstance Id：'%1' E2E 活動</span><span class="sxs-lookup"><span data-stu-id="d5e3e-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="d5e3e-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5e3e-116">Details</span></span>  
  
|<span data-ttu-id="d5e3e-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="d5e3e-117">Data Item Name</span></span>|<span data-ttu-id="d5e3e-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="d5e3e-118">Data Item Type</span></span>|<span data-ttu-id="d5e3e-119">描述</span><span class="sxs-lookup"><span data-stu-id="d5e3e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d5e3e-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="d5e3e-120">WorkflowInstanceId</span></span>|<span data-ttu-id="d5e3e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5e3e-121">xs:string</span></span>|<span data-ttu-id="d5e3e-122">工作流程執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="d5e3e-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="d5e3e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d5e3e-123">AppDomain</span></span>|<span data-ttu-id="d5e3e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5e3e-124">xs:string</span></span>|<span data-ttu-id="d5e3e-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d5e3e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
