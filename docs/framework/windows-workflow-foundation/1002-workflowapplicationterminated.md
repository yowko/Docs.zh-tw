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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54ef06c3aded628e18325b78f55e80e4470ecd01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="73003-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="73003-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="73003-103">屬性</span><span class="sxs-lookup"><span data-stu-id="73003-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73003-104">ID</span><span class="sxs-lookup"><span data-stu-id="73003-104">ID</span></span>|<span data-ttu-id="73003-105">1002</span><span class="sxs-lookup"><span data-stu-id="73003-105">1002</span></span>|  
|<span data-ttu-id="73003-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="73003-106">Keywords</span></span>|<span data-ttu-id="73003-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="73003-107">WFRuntime</span></span>|  
|<span data-ttu-id="73003-108">層級</span><span class="sxs-lookup"><span data-stu-id="73003-108">Level</span></span>|<span data-ttu-id="73003-109">資訊</span><span class="sxs-lookup"><span data-stu-id="73003-109">Information</span></span>|  
|<span data-ttu-id="73003-110">通道</span><span class="sxs-lookup"><span data-stu-id="73003-110">Channel</span></span>|<span data-ttu-id="73003-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="73003-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73003-112">描述</span><span class="sxs-lookup"><span data-stu-id="73003-112">Description</span></span>  
 <span data-ttu-id="73003-113">表示工作流程應用程式在 Faulted 狀態下終止，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73003-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73003-114">訊息</span><span class="sxs-lookup"><span data-stu-id="73003-114">Message</span></span>  
 <span data-ttu-id="73003-115">WorkflowApplication Id：'%1' 已終止。</span><span class="sxs-lookup"><span data-stu-id="73003-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="73003-116">它已經以 Faulted 狀態完成，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73003-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73003-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="73003-117">Details</span></span>  
  
|<span data-ttu-id="73003-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="73003-118">Data Item Name</span></span>|<span data-ttu-id="73003-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="73003-119">Data Item Type</span></span>|<span data-ttu-id="73003-120">描述</span><span class="sxs-lookup"><span data-stu-id="73003-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73003-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="73003-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="73003-122">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="73003-122">The workflow application id</span></span>|  
|<span data-ttu-id="73003-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="73003-123">Exception</span></span>|`xs:string`|<span data-ttu-id="73003-124">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="73003-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="73003-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="73003-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="73003-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="73003-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
