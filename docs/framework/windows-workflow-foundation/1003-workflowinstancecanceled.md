---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008625"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="18833-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="18833-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="18833-103">屬性</span><span class="sxs-lookup"><span data-stu-id="18833-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18833-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="18833-104">ID</span></span>|<span data-ttu-id="18833-105">1003</span><span class="sxs-lookup"><span data-stu-id="18833-105">1003</span></span>|  
|<span data-ttu-id="18833-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="18833-106">Keywords</span></span>|<span data-ttu-id="18833-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="18833-107">WFRuntime</span></span>|  
|<span data-ttu-id="18833-108">層級</span><span class="sxs-lookup"><span data-stu-id="18833-108">Level</span></span>|<span data-ttu-id="18833-109">資訊</span><span class="sxs-lookup"><span data-stu-id="18833-109">Information</span></span>|  
|<span data-ttu-id="18833-110">通道</span><span class="sxs-lookup"><span data-stu-id="18833-110">Channel</span></span>|<span data-ttu-id="18833-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="18833-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="18833-112">描述</span><span class="sxs-lookup"><span data-stu-id="18833-112">Description</span></span>  
 <span data-ttu-id="18833-113">表示工作流程執行個體已在 Canceled 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="18833-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="18833-114">訊息</span><span class="sxs-lookup"><span data-stu-id="18833-114">Message</span></span>  
 <span data-ttu-id="18833-115">WorkflowInstance Id：'%1' 已在 Canceled 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="18833-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="18833-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="18833-116">Details</span></span>  
  
|<span data-ttu-id="18833-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="18833-117">Data Item Name</span></span>|<span data-ttu-id="18833-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="18833-118">Data Item Type</span></span>|<span data-ttu-id="18833-119">描述</span><span class="sxs-lookup"><span data-stu-id="18833-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="18833-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="18833-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="18833-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="18833-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="18833-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="18833-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="18833-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="18833-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
