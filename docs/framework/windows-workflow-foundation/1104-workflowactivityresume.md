---
title: 1104 - WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 4c9ae5fd386fc93ea19578097aa4e0afdda527e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924120"
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="ecab3-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="ecab3-102">1104 - WorkflowActivityResume</span></span>
## <a name="properties"></a><span data-ttu-id="ecab3-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ecab3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ecab3-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="ecab3-104">ID</span></span>|<span data-ttu-id="ecab3-105">1104</span><span class="sxs-lookup"><span data-stu-id="ecab3-105">1104</span></span>|  
|<span data-ttu-id="ecab3-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ecab3-106">Keywords</span></span>|<span data-ttu-id="ecab3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ecab3-107">WFRuntime</span></span>|  
|<span data-ttu-id="ecab3-108">層級</span><span class="sxs-lookup"><span data-stu-id="ecab3-108">Level</span></span>|<span data-ttu-id="ecab3-109">資訊</span><span class="sxs-lookup"><span data-stu-id="ecab3-109">Information</span></span>|  
|<span data-ttu-id="ecab3-110">通道</span><span class="sxs-lookup"><span data-stu-id="ecab3-110">Channel</span></span>|<span data-ttu-id="ecab3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ecab3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ecab3-112">描述</span><span class="sxs-lookup"><span data-stu-id="ecab3-112">Description</span></span>  
 <span data-ttu-id="ecab3-113">表示已繼續工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="ecab3-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ecab3-114">訊息</span><span class="sxs-lookup"><span data-stu-id="ecab3-114">Message</span></span>  
 <span data-ttu-id="ecab3-115">WorkflowInstance Id：'%1' E2E 活動</span><span class="sxs-lookup"><span data-stu-id="ecab3-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="ecab3-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ecab3-116">Details</span></span>  
  
|<span data-ttu-id="ecab3-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ecab3-117">Data Item Name</span></span>|<span data-ttu-id="ecab3-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ecab3-118">Data Item Type</span></span>|<span data-ttu-id="ecab3-119">描述</span><span class="sxs-lookup"><span data-stu-id="ecab3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ecab3-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="ecab3-120">WorkflowInstanceId</span></span>|<span data-ttu-id="ecab3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ecab3-121">xs:string</span></span>|<span data-ttu-id="ecab3-122">工作流程執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="ecab3-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="ecab3-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ecab3-123">AppDomain</span></span>|<span data-ttu-id="ecab3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ecab3-124">xs:string</span></span>|<span data-ttu-id="ecab3-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ecab3-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
