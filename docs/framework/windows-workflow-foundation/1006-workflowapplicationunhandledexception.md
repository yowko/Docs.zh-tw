---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a03809be5e5d61c505e295e2f769a0298f770f7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="6281c-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="6281c-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="6281c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="6281c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6281c-104">ID</span><span class="sxs-lookup"><span data-stu-id="6281c-104">ID</span></span>|<span data-ttu-id="6281c-105">1006</span><span class="sxs-lookup"><span data-stu-id="6281c-105">1006</span></span>|  
|<span data-ttu-id="6281c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="6281c-106">Keywords</span></span>|<span data-ttu-id="6281c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6281c-107">WFRuntime</span></span>|  
|<span data-ttu-id="6281c-108">層級</span><span class="sxs-lookup"><span data-stu-id="6281c-108">Level</span></span>|<span data-ttu-id="6281c-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="6281c-109">Error</span></span>|  
|<span data-ttu-id="6281c-110">通道</span><span class="sxs-lookup"><span data-stu-id="6281c-110">Channel</span></span>|<span data-ttu-id="6281c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6281c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6281c-112">描述</span><span class="sxs-lookup"><span data-stu-id="6281c-112">Description</span></span>  
 <span data-ttu-id="6281c-113">表示工作流程應用程式發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6281c-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6281c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="6281c-114">Message</span></span>  
 <span data-ttu-id="6281c-115">WorkflowInstance Id: '%1' 發生未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6281c-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="6281c-116">例外狀況源自活動 '%2'、 DisplayName: '%3'。</span><span class="sxs-lookup"><span data-stu-id="6281c-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="6281c-117">將會採取下列動作: %4。</span><span class="sxs-lookup"><span data-stu-id="6281c-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6281c-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6281c-118">Details</span></span>  
  
|<span data-ttu-id="6281c-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="6281c-119">Data Item Name</span></span>|<span data-ttu-id="6281c-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="6281c-120">Data Item Type</span></span>|<span data-ttu-id="6281c-121">描述</span><span class="sxs-lookup"><span data-stu-id="6281c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6281c-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="6281c-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="6281c-123">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="6281c-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="6281c-124">例外狀況</span><span class="sxs-lookup"><span data-stu-id="6281c-124">Exception</span></span>|`xs:string`|<span data-ttu-id="6281c-125">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="6281c-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="6281c-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6281c-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6281c-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="6281c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
