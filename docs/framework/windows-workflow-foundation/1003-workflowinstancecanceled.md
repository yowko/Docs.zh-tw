---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509765"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="88047-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="88047-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="88047-103">屬性</span><span class="sxs-lookup"><span data-stu-id="88047-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="88047-104">ID</span><span class="sxs-lookup"><span data-stu-id="88047-104">ID</span></span>|<span data-ttu-id="88047-105">1003</span><span class="sxs-lookup"><span data-stu-id="88047-105">1003</span></span>|  
|<span data-ttu-id="88047-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="88047-106">Keywords</span></span>|<span data-ttu-id="88047-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="88047-107">WFRuntime</span></span>|  
|<span data-ttu-id="88047-108">層級</span><span class="sxs-lookup"><span data-stu-id="88047-108">Level</span></span>|<span data-ttu-id="88047-109">資訊</span><span class="sxs-lookup"><span data-stu-id="88047-109">Information</span></span>|  
|<span data-ttu-id="88047-110">通道</span><span class="sxs-lookup"><span data-stu-id="88047-110">Channel</span></span>|<span data-ttu-id="88047-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="88047-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="88047-112">描述</span><span class="sxs-lookup"><span data-stu-id="88047-112">Description</span></span>  
 <span data-ttu-id="88047-113">表示工作流程執行個體已在 Canceled 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="88047-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="88047-114">訊息</span><span class="sxs-lookup"><span data-stu-id="88047-114">Message</span></span>  
 <span data-ttu-id="88047-115">WorkflowInstance Id：'%1' 已在 Canceled 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="88047-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="88047-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="88047-116">Details</span></span>  
  
|<span data-ttu-id="88047-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="88047-117">Data Item Name</span></span>|<span data-ttu-id="88047-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="88047-118">Data Item Type</span></span>|<span data-ttu-id="88047-119">描述</span><span class="sxs-lookup"><span data-stu-id="88047-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="88047-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="88047-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="88047-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="88047-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="88047-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="88047-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="88047-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="88047-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
