---
title: 1103 - WorkflowActivitySuspend
ms.date: 03/30/2017
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
ms.openlocfilehash: 2fede703d086ed9653734f626fc38f56e073e416
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243569"
---
# <a name="1103---workflowactivitysuspend"></a><span data-ttu-id="aea93-102">1103 - WorkflowActivitySuspend</span><span class="sxs-lookup"><span data-stu-id="aea93-102">1103 - WorkflowActivitySuspend</span></span>

## <a name="properties"></a><span data-ttu-id="aea93-103">屬性</span><span class="sxs-lookup"><span data-stu-id="aea93-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aea93-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="aea93-104">ID</span></span>|<span data-ttu-id="aea93-105">1103</span><span class="sxs-lookup"><span data-stu-id="aea93-105">1103</span></span>|  
|<span data-ttu-id="aea93-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="aea93-106">Keywords</span></span>|<span data-ttu-id="aea93-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aea93-107">WFRuntime</span></span>|  
|<span data-ttu-id="aea93-108">層級</span><span class="sxs-lookup"><span data-stu-id="aea93-108">Level</span></span>|<span data-ttu-id="aea93-109">資訊</span><span class="sxs-lookup"><span data-stu-id="aea93-109">Information</span></span>|  
|<span data-ttu-id="aea93-110">通路</span><span class="sxs-lookup"><span data-stu-id="aea93-110">Channel</span></span>|<span data-ttu-id="aea93-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="aea93-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aea93-112">描述</span><span class="sxs-lookup"><span data-stu-id="aea93-112">Description</span></span>  

 <span data-ttu-id="aea93-113">表示已暫停工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="aea93-113">Indicates a workflow activity has been suspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aea93-114">訊息</span><span class="sxs-lookup"><span data-stu-id="aea93-114">Message</span></span>  

 <span data-ttu-id="aea93-115">WorkflowInstance Id：'%1' E2E 活動</span><span class="sxs-lookup"><span data-stu-id="aea93-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="aea93-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aea93-116">Details</span></span>  
  
|<span data-ttu-id="aea93-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="aea93-117">Data Item Name</span></span>|<span data-ttu-id="aea93-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="aea93-118">Data Item Type</span></span>|<span data-ttu-id="aea93-119">描述</span><span class="sxs-lookup"><span data-stu-id="aea93-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aea93-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="aea93-120">WorkflowInstanceId</span></span>|<span data-ttu-id="aea93-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="aea93-121">xs:string</span></span>|<span data-ttu-id="aea93-122">工作流程執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="aea93-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="aea93-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aea93-123">AppDomain</span></span>|<span data-ttu-id="aea93-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="aea93-124">xs:string</span></span>|<span data-ttu-id="aea93-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="aea93-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
