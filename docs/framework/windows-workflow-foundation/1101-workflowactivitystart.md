---
title: 1101 - WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 1e6db97284b7ca83d532166d96d7a42df0a51091
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924146"
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="9daa9-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="9daa9-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="9daa9-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9daa9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9daa9-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="9daa9-104">ID</span></span>|<span data-ttu-id="9daa9-105">1101</span><span class="sxs-lookup"><span data-stu-id="9daa9-105">1101</span></span>|  
|<span data-ttu-id="9daa9-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9daa9-106">Keywords</span></span>|<span data-ttu-id="9daa9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9daa9-107">WFRuntime</span></span>|  
|<span data-ttu-id="9daa9-108">層級</span><span class="sxs-lookup"><span data-stu-id="9daa9-108">Level</span></span>|<span data-ttu-id="9daa9-109">資訊</span><span class="sxs-lookup"><span data-stu-id="9daa9-109">Information</span></span>|  
|<span data-ttu-id="9daa9-110">通道</span><span class="sxs-lookup"><span data-stu-id="9daa9-110">Channel</span></span>|<span data-ttu-id="9daa9-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9daa9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9daa9-112">描述</span><span class="sxs-lookup"><span data-stu-id="9daa9-112">Description</span></span>  
 <span data-ttu-id="9daa9-113">表示工作流程活動已開始。</span><span class="sxs-lookup"><span data-stu-id="9daa9-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9daa9-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9daa9-114">Message</span></span>  
 <span data-ttu-id="9daa9-115">WorkflowInstance Id：'%1' E2E 活動</span><span class="sxs-lookup"><span data-stu-id="9daa9-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="9daa9-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9daa9-116">Details</span></span>  
  
|<span data-ttu-id="9daa9-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9daa9-117">Data Item Name</span></span>|<span data-ttu-id="9daa9-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9daa9-118">Data Item Type</span></span>|<span data-ttu-id="9daa9-119">描述</span><span class="sxs-lookup"><span data-stu-id="9daa9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9daa9-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="9daa9-120">WorkflowInstanceId</span></span>|<span data-ttu-id="9daa9-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9daa9-121">xs:string</span></span>|<span data-ttu-id="9daa9-122">工作流程執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="9daa9-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="9daa9-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9daa9-123">AppDomain</span></span>|<span data-ttu-id="9daa9-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9daa9-124">xs:string</span></span>|<span data-ttu-id="9daa9-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9daa9-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
