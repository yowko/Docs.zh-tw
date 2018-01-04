---
title: 1002 - WorkflowApplicationTerminated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3f025be90a997839eec2edfea12a099b4c58f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="ec3dc-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="ec3dc-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="ec3dc-103">屬性</span><span class="sxs-lookup"><span data-stu-id="ec3dc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec3dc-104">ID</span><span class="sxs-lookup"><span data-stu-id="ec3dc-104">ID</span></span>|<span data-ttu-id="ec3dc-105">1002</span><span class="sxs-lookup"><span data-stu-id="ec3dc-105">1002</span></span>|  
|<span data-ttu-id="ec3dc-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ec3dc-106">Keywords</span></span>|<span data-ttu-id="ec3dc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ec3dc-107">WFRuntime</span></span>|  
|<span data-ttu-id="ec3dc-108">層級</span><span class="sxs-lookup"><span data-stu-id="ec3dc-108">Level</span></span>|<span data-ttu-id="ec3dc-109">資訊</span><span class="sxs-lookup"><span data-stu-id="ec3dc-109">Information</span></span>|  
|<span data-ttu-id="ec3dc-110">通道</span><span class="sxs-lookup"><span data-stu-id="ec3dc-110">Channel</span></span>|<span data-ttu-id="ec3dc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ec3dc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ec3dc-112">描述</span><span class="sxs-lookup"><span data-stu-id="ec3dc-112">Description</span></span>  
 <span data-ttu-id="ec3dc-113">表示工作流程應用程式在 Faulted 狀態下終止，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ec3dc-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ec3dc-114">訊息</span><span class="sxs-lookup"><span data-stu-id="ec3dc-114">Message</span></span>  
 <span data-ttu-id="ec3dc-115">WorkflowApplication Id：'%1' 已終止。</span><span class="sxs-lookup"><span data-stu-id="ec3dc-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="ec3dc-116">它已經以 Faulted 狀態完成，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ec3dc-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ec3dc-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ec3dc-117">Details</span></span>  
  
|<span data-ttu-id="ec3dc-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="ec3dc-118">Data Item Name</span></span>|<span data-ttu-id="ec3dc-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="ec3dc-119">Data Item Type</span></span>|<span data-ttu-id="ec3dc-120">描述</span><span class="sxs-lookup"><span data-stu-id="ec3dc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ec3dc-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="ec3dc-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="ec3dc-122">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="ec3dc-122">The workflow application id</span></span>|  
|<span data-ttu-id="ec3dc-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="ec3dc-123">Exception</span></span>|`xs:string`|<span data-ttu-id="ec3dc-124">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="ec3dc-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="ec3dc-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ec3dc-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ec3dc-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="ec3dc-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
