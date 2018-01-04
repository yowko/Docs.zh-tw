---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc940e1781f821f12efb42c5198e77eb0451a164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="dab37-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="dab37-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="dab37-103">屬性</span><span class="sxs-lookup"><span data-stu-id="dab37-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dab37-104">ID</span><span class="sxs-lookup"><span data-stu-id="dab37-104">ID</span></span>|<span data-ttu-id="dab37-105">1004</span><span class="sxs-lookup"><span data-stu-id="dab37-105">1004</span></span>|  
|<span data-ttu-id="dab37-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="dab37-106">Keywords</span></span>|<span data-ttu-id="dab37-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dab37-107">WFRuntime</span></span>|  
|<span data-ttu-id="dab37-108">層級</span><span class="sxs-lookup"><span data-stu-id="dab37-108">Level</span></span>|<span data-ttu-id="dab37-109">資訊</span><span class="sxs-lookup"><span data-stu-id="dab37-109">Information</span></span>|  
|<span data-ttu-id="dab37-110">通道</span><span class="sxs-lookup"><span data-stu-id="dab37-110">Channel</span></span>|<span data-ttu-id="dab37-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="dab37-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dab37-112">描述</span><span class="sxs-lookup"><span data-stu-id="dab37-112">Description</span></span>  
 <span data-ttu-id="dab37-113">表示工作流程執行個體已中止，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dab37-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dab37-114">訊息</span><span class="sxs-lookup"><span data-stu-id="dab37-114">Message</span></span>  
 <span data-ttu-id="dab37-115">WorkflowInstance Id：'%1' 已中止，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dab37-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dab37-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dab37-116">Details</span></span>  
  
|<span data-ttu-id="dab37-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="dab37-117">Data Item Name</span></span>|<span data-ttu-id="dab37-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="dab37-118">Data Item Type</span></span>|<span data-ttu-id="dab37-119">描述</span><span class="sxs-lookup"><span data-stu-id="dab37-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dab37-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="dab37-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="dab37-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="dab37-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="dab37-122">例外狀況</span><span class="sxs-lookup"><span data-stu-id="dab37-122">Exception</span></span>|`xs:string`|<span data-ttu-id="dab37-123">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="dab37-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="dab37-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dab37-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dab37-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="dab37-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
