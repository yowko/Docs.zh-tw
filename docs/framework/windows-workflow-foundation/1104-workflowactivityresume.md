---
title: 1104 - WorkflowActivityResume
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8ffba47fa7cd865b604704a3819cbe89be1ed5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="fa175-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="fa175-102">1104 - WorkflowActivityResume</span></span>
## <a name="properties"></a><span data-ttu-id="fa175-103">屬性</span><span class="sxs-lookup"><span data-stu-id="fa175-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa175-104">ID</span><span class="sxs-lookup"><span data-stu-id="fa175-104">ID</span></span>|<span data-ttu-id="fa175-105">1104</span><span class="sxs-lookup"><span data-stu-id="fa175-105">1104</span></span>|  
|<span data-ttu-id="fa175-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="fa175-106">Keywords</span></span>|<span data-ttu-id="fa175-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fa175-107">WFRuntime</span></span>|  
|<span data-ttu-id="fa175-108">層級</span><span class="sxs-lookup"><span data-stu-id="fa175-108">Level</span></span>|<span data-ttu-id="fa175-109">資訊</span><span class="sxs-lookup"><span data-stu-id="fa175-109">Information</span></span>|  
|<span data-ttu-id="fa175-110">通道</span><span class="sxs-lookup"><span data-stu-id="fa175-110">Channel</span></span>|<span data-ttu-id="fa175-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fa175-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fa175-112">描述</span><span class="sxs-lookup"><span data-stu-id="fa175-112">Description</span></span>  
 <span data-ttu-id="fa175-113">表示已繼續工作流程活動。</span><span class="sxs-lookup"><span data-stu-id="fa175-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fa175-114">訊息</span><span class="sxs-lookup"><span data-stu-id="fa175-114">Message</span></span>  
 <span data-ttu-id="fa175-115">WorkflowInstance Id：'%1' E2E 活動</span><span class="sxs-lookup"><span data-stu-id="fa175-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="fa175-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fa175-116">Details</span></span>  
  
|<span data-ttu-id="fa175-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="fa175-117">Data Item Name</span></span>|<span data-ttu-id="fa175-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="fa175-118">Data Item Type</span></span>|<span data-ttu-id="fa175-119">描述</span><span class="sxs-lookup"><span data-stu-id="fa175-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fa175-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="fa175-120">WorkflowInstanceId</span></span>|<span data-ttu-id="fa175-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa175-121">xs:string</span></span>|<span data-ttu-id="fa175-122">工作流程執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="fa175-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="fa175-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fa175-123">AppDomain</span></span>|<span data-ttu-id="fa175-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="fa175-124">xs:string</span></span>|<span data-ttu-id="fa175-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="fa175-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
