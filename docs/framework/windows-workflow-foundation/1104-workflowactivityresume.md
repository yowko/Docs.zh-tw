---
title: 1104 - WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 2a9c40e2c403d43dc980af116e4b6e98b3b2090b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243556"
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="f5b68-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="f5b68-102">1104 - WorkflowActivityResume</span></span>

## <a name="properties"></a><span data-ttu-id="f5b68-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f5b68-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5b68-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="f5b68-104">ID</span></span>|<span data-ttu-id="f5b68-105">1104</span><span class="sxs-lookup"><span data-stu-id="f5b68-105">1104</span></span>|  
|<span data-ttu-id="f5b68-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f5b68-106">Keywords</span></span>|<span data-ttu-id="f5b68-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f5b68-107">WFRuntime</span></span>|  
|<span data-ttu-id="f5b68-108">層級</span><span class="sxs-lookup"><span data-stu-id="f5b68-108">Level</span></span>|<span data-ttu-id="f5b68-109">資訊</span><span class="sxs-lookup"><span data-stu-id="f5b68-109">Information</span></span>|  
|<span data-ttu-id="f5b68-110">通路</span><span class="sxs-lookup"><span data-stu-id="f5b68-110">Channel</span></span>|<span data-ttu-id="f5b68-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f5b68-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f5b68-112">描述</span><span class="sxs-lookup"><span data-stu-id="f5b68-112">Description</span></span>  

 <span data-ttu-id="f5b68-113">表示已繼續工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="f5b68-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f5b68-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f5b68-114">Message</span></span>  

 <span data-ttu-id="f5b68-115">WorkflowInstance Id：'%1' E2E 活動</span><span class="sxs-lookup"><span data-stu-id="f5b68-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="f5b68-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f5b68-116">Details</span></span>  
  
|<span data-ttu-id="f5b68-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f5b68-117">Data Item Name</span></span>|<span data-ttu-id="f5b68-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f5b68-118">Data Item Type</span></span>|<span data-ttu-id="f5b68-119">描述</span><span class="sxs-lookup"><span data-stu-id="f5b68-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f5b68-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="f5b68-120">WorkflowInstanceId</span></span>|<span data-ttu-id="f5b68-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5b68-121">xs:string</span></span>|<span data-ttu-id="f5b68-122">工作流程執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="f5b68-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="f5b68-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f5b68-123">AppDomain</span></span>|<span data-ttu-id="f5b68-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f5b68-124">xs:string</span></span>|<span data-ttu-id="f5b68-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f5b68-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
