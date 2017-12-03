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
ms.openlocfilehash: 93a6a400576df84faae3cd58940462255b0073c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="e27f7-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="e27f7-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="e27f7-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e27f7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e27f7-104">ID</span><span class="sxs-lookup"><span data-stu-id="e27f7-104">ID</span></span>|<span data-ttu-id="e27f7-105">1002</span><span class="sxs-lookup"><span data-stu-id="e27f7-105">1002</span></span>|  
|<span data-ttu-id="e27f7-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e27f7-106">Keywords</span></span>|<span data-ttu-id="e27f7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e27f7-107">WFRuntime</span></span>|  
|<span data-ttu-id="e27f7-108">層級</span><span class="sxs-lookup"><span data-stu-id="e27f7-108">Level</span></span>|<span data-ttu-id="e27f7-109">資訊</span><span class="sxs-lookup"><span data-stu-id="e27f7-109">Information</span></span>|  
|<span data-ttu-id="e27f7-110">通道</span><span class="sxs-lookup"><span data-stu-id="e27f7-110">Channel</span></span>|<span data-ttu-id="e27f7-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e27f7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e27f7-112">描述</span><span class="sxs-lookup"><span data-stu-id="e27f7-112">Description</span></span>  
 <span data-ttu-id="e27f7-113">表示工作流程應用程式在 Faulted 狀態下終止，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e27f7-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e27f7-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e27f7-114">Message</span></span>  
 <span data-ttu-id="e27f7-115">WorkflowApplication Id：'%1' 已終止。</span><span class="sxs-lookup"><span data-stu-id="e27f7-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="e27f7-116">它已經以 Faulted 狀態完成，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e27f7-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e27f7-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e27f7-117">Details</span></span>  
  
|<span data-ttu-id="e27f7-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e27f7-118">Data Item Name</span></span>|<span data-ttu-id="e27f7-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e27f7-119">Data Item Type</span></span>|<span data-ttu-id="e27f7-120">描述</span><span class="sxs-lookup"><span data-stu-id="e27f7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e27f7-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="e27f7-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="e27f7-122">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="e27f7-122">The workflow application id</span></span>|  
|<span data-ttu-id="e27f7-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="e27f7-123">Exception</span></span>|`xs:string`|<span data-ttu-id="e27f7-124">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="e27f7-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="e27f7-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e27f7-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e27f7-126">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e27f7-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
