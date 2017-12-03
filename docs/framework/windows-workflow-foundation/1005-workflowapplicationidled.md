---
title: 1005 - WorkflowApplicationIdled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2603621eb23747275e6db22a1743c5260967c6a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="69478-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="69478-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="69478-103">屬性</span><span class="sxs-lookup"><span data-stu-id="69478-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69478-104">ID</span><span class="sxs-lookup"><span data-stu-id="69478-104">ID</span></span>|<span data-ttu-id="69478-105">1005</span><span class="sxs-lookup"><span data-stu-id="69478-105">1005</span></span>|  
|<span data-ttu-id="69478-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="69478-106">Keywords</span></span>|<span data-ttu-id="69478-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="69478-107">WFRuntime</span></span>|  
|<span data-ttu-id="69478-108">層級</span><span class="sxs-lookup"><span data-stu-id="69478-108">Level</span></span>|<span data-ttu-id="69478-109">資訊</span><span class="sxs-lookup"><span data-stu-id="69478-109">Information</span></span>|  
|<span data-ttu-id="69478-110">通道</span><span class="sxs-lookup"><span data-stu-id="69478-110">Channel</span></span>|<span data-ttu-id="69478-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="69478-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="69478-112">描述</span><span class="sxs-lookup"><span data-stu-id="69478-112">Description</span></span>  
 <span data-ttu-id="69478-113">表示工作流程應用程式已閒置。</span><span class="sxs-lookup"><span data-stu-id="69478-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="69478-114">訊息</span><span class="sxs-lookup"><span data-stu-id="69478-114">Message</span></span>  
 <span data-ttu-id="69478-115">WorkflowApplication Id：'%1' 閒置。</span><span class="sxs-lookup"><span data-stu-id="69478-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="69478-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="69478-116">Details</span></span>  
  
|<span data-ttu-id="69478-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="69478-117">Data Item Name</span></span>|<span data-ttu-id="69478-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="69478-118">Data Item Type</span></span>|<span data-ttu-id="69478-119">描述</span><span class="sxs-lookup"><span data-stu-id="69478-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="69478-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="69478-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="69478-121">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="69478-121">The workflow application id</span></span>|  
|<span data-ttu-id="69478-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="69478-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="69478-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="69478-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
