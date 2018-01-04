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
ms.workload: dotnet
ms.openlocfilehash: dc9f8f72000fe283baa5bb2814e41051c1424983
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="efe4b-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="efe4b-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="efe4b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="efe4b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="efe4b-104">ID</span><span class="sxs-lookup"><span data-stu-id="efe4b-104">ID</span></span>|<span data-ttu-id="efe4b-105">1005</span><span class="sxs-lookup"><span data-stu-id="efe4b-105">1005</span></span>|  
|<span data-ttu-id="efe4b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="efe4b-106">Keywords</span></span>|<span data-ttu-id="efe4b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="efe4b-107">WFRuntime</span></span>|  
|<span data-ttu-id="efe4b-108">層級</span><span class="sxs-lookup"><span data-stu-id="efe4b-108">Level</span></span>|<span data-ttu-id="efe4b-109">資訊</span><span class="sxs-lookup"><span data-stu-id="efe4b-109">Information</span></span>|  
|<span data-ttu-id="efe4b-110">通道</span><span class="sxs-lookup"><span data-stu-id="efe4b-110">Channel</span></span>|<span data-ttu-id="efe4b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="efe4b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="efe4b-112">描述</span><span class="sxs-lookup"><span data-stu-id="efe4b-112">Description</span></span>  
 <span data-ttu-id="efe4b-113">表示工作流程應用程式已閒置。</span><span class="sxs-lookup"><span data-stu-id="efe4b-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="efe4b-114">訊息</span><span class="sxs-lookup"><span data-stu-id="efe4b-114">Message</span></span>  
 <span data-ttu-id="efe4b-115">WorkflowApplication Id：'%1' 閒置。</span><span class="sxs-lookup"><span data-stu-id="efe4b-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="efe4b-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="efe4b-116">Details</span></span>  
  
|<span data-ttu-id="efe4b-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="efe4b-117">Data Item Name</span></span>|<span data-ttu-id="efe4b-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="efe4b-118">Data Item Type</span></span>|<span data-ttu-id="efe4b-119">描述</span><span class="sxs-lookup"><span data-stu-id="efe4b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="efe4b-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="efe4b-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="efe4b-121">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="efe4b-121">The workflow application id</span></span>|  
|<span data-ttu-id="efe4b-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="efe4b-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="efe4b-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="efe4b-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
