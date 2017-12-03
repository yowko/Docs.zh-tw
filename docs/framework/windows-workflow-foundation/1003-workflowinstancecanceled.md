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
ms.openlocfilehash: 6930aeed8c3cd224d5d37dcecf357195e78390ed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="2b2ac-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="2b2ac-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="2b2ac-103">屬性</span><span class="sxs-lookup"><span data-stu-id="2b2ac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b2ac-104">ID</span><span class="sxs-lookup"><span data-stu-id="2b2ac-104">ID</span></span>|<span data-ttu-id="2b2ac-105">1003</span><span class="sxs-lookup"><span data-stu-id="2b2ac-105">1003</span></span>|  
|<span data-ttu-id="2b2ac-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="2b2ac-106">Keywords</span></span>|<span data-ttu-id="2b2ac-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2b2ac-107">WFRuntime</span></span>|  
|<span data-ttu-id="2b2ac-108">層級</span><span class="sxs-lookup"><span data-stu-id="2b2ac-108">Level</span></span>|<span data-ttu-id="2b2ac-109">資訊</span><span class="sxs-lookup"><span data-stu-id="2b2ac-109">Information</span></span>|  
|<span data-ttu-id="2b2ac-110">通道</span><span class="sxs-lookup"><span data-stu-id="2b2ac-110">Channel</span></span>|<span data-ttu-id="2b2ac-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2b2ac-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2b2ac-112">描述</span><span class="sxs-lookup"><span data-stu-id="2b2ac-112">Description</span></span>  
 <span data-ttu-id="2b2ac-113">表示工作流程執行個體已在 Canceled 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="2b2ac-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2b2ac-114">訊息</span><span class="sxs-lookup"><span data-stu-id="2b2ac-114">Message</span></span>  
 <span data-ttu-id="2b2ac-115">WorkflowInstance Id：'%1' 已在 Canceled 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="2b2ac-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2b2ac-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2b2ac-116">Details</span></span>  
  
|<span data-ttu-id="2b2ac-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="2b2ac-117">Data Item Name</span></span>|<span data-ttu-id="2b2ac-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="2b2ac-118">Data Item Type</span></span>|<span data-ttu-id="2b2ac-119">描述</span><span class="sxs-lookup"><span data-stu-id="2b2ac-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2b2ac-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2b2ac-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2b2ac-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="2b2ac-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="2b2ac-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2b2ac-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2b2ac-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="2b2ac-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
