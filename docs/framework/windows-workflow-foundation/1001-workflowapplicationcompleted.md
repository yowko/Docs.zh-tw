---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ded4558b937a23fbe90d2bca55e6d5e4be0f0290
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="326fb-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="326fb-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="326fb-103">屬性</span><span class="sxs-lookup"><span data-stu-id="326fb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="326fb-104">ID</span><span class="sxs-lookup"><span data-stu-id="326fb-104">ID</span></span>|<span data-ttu-id="326fb-105">1001</span><span class="sxs-lookup"><span data-stu-id="326fb-105">1001</span></span>|  
|<span data-ttu-id="326fb-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="326fb-106">Keywords</span></span>|<span data-ttu-id="326fb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="326fb-107">WFRuntime</span></span>|  
|<span data-ttu-id="326fb-108">層級</span><span class="sxs-lookup"><span data-stu-id="326fb-108">Level</span></span>|<span data-ttu-id="326fb-109">資訊</span><span class="sxs-lookup"><span data-stu-id="326fb-109">Information</span></span>|  
|<span data-ttu-id="326fb-110">通道</span><span class="sxs-lookup"><span data-stu-id="326fb-110">Channel</span></span>|<span data-ttu-id="326fb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="326fb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="326fb-112">描述</span><span class="sxs-lookup"><span data-stu-id="326fb-112">Description</span></span>  
 <span data-ttu-id="326fb-113">表示工作流程應用程式已在 Closed 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="326fb-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="326fb-114">訊息</span><span class="sxs-lookup"><span data-stu-id="326fb-114">Message</span></span>  
 <span data-ttu-id="326fb-115">WorkflowInstance Id：'%1' 已在 Closed 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="326fb-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="326fb-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="326fb-116">Details</span></span>  
  
|<span data-ttu-id="326fb-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="326fb-117">Data Item Name</span></span>|<span data-ttu-id="326fb-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="326fb-118">Data Item Type</span></span>|<span data-ttu-id="326fb-119">描述</span><span class="sxs-lookup"><span data-stu-id="326fb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="326fb-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="326fb-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="326fb-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="326fb-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="326fb-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="326fb-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="326fb-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="326fb-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
