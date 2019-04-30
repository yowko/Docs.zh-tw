---
title: 1103 - WorkflowActivitySuspend
ms.date: 03/30/2017
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
ms.openlocfilehash: 4311bd8dc1c5e2c43bf21b411a4c52a7bfc7b230
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052777"
---
# <a name="1103---workflowactivitysuspend"></a><span data-ttu-id="ca3dc-102">1103 - WorkflowActivitySuspend</span><span class="sxs-lookup"><span data-stu-id="ca3dc-102">1103 - WorkflowActivitySuspend</span></span>
## <a name="properties"></a><span data-ttu-id="ca3dc-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ca3dc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca3dc-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="ca3dc-104">ID</span></span>|<span data-ttu-id="ca3dc-105">1103</span><span class="sxs-lookup"><span data-stu-id="ca3dc-105">1103</span></span>|  
|<span data-ttu-id="ca3dc-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ca3dc-106">Keywords</span></span>|<span data-ttu-id="ca3dc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ca3dc-107">WFRuntime</span></span>|  
|<span data-ttu-id="ca3dc-108">層級</span><span class="sxs-lookup"><span data-stu-id="ca3dc-108">Level</span></span>|<span data-ttu-id="ca3dc-109">資訊</span><span class="sxs-lookup"><span data-stu-id="ca3dc-109">Information</span></span>|  
|<span data-ttu-id="ca3dc-110">通道</span><span class="sxs-lookup"><span data-stu-id="ca3dc-110">Channel</span></span>|<span data-ttu-id="ca3dc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ca3dc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ca3dc-112">描述</span><span class="sxs-lookup"><span data-stu-id="ca3dc-112">Description</span></span>  
 <span data-ttu-id="ca3dc-113">表示已暫停工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="ca3dc-113">Indicates a workflow activity has been suspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ca3dc-114">訊息</span><span class="sxs-lookup"><span data-stu-id="ca3dc-114">Message</span></span>  
 <span data-ttu-id="ca3dc-115">WorkflowInstance Id：'%1' E2E 活動</span><span class="sxs-lookup"><span data-stu-id="ca3dc-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="ca3dc-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ca3dc-116">Details</span></span>  
  
|<span data-ttu-id="ca3dc-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ca3dc-117">Data Item Name</span></span>|<span data-ttu-id="ca3dc-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ca3dc-118">Data Item Type</span></span>|<span data-ttu-id="ca3dc-119">描述</span><span class="sxs-lookup"><span data-stu-id="ca3dc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ca3dc-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="ca3dc-120">WorkflowInstanceId</span></span>|<span data-ttu-id="ca3dc-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca3dc-121">xs:string</span></span>|<span data-ttu-id="ca3dc-122">工作流程執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="ca3dc-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="ca3dc-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ca3dc-123">AppDomain</span></span>|<span data-ttu-id="ca3dc-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca3dc-124">xs:string</span></span>|<span data-ttu-id="ca3dc-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ca3dc-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
