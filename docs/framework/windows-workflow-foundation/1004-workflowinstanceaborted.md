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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7394ebbcb14850af89d906b0b573c4f677346825
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="46b48-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="46b48-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="46b48-103">屬性</span><span class="sxs-lookup"><span data-stu-id="46b48-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46b48-104">ID</span><span class="sxs-lookup"><span data-stu-id="46b48-104">ID</span></span>|<span data-ttu-id="46b48-105">1004</span><span class="sxs-lookup"><span data-stu-id="46b48-105">1004</span></span>|  
|<span data-ttu-id="46b48-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="46b48-106">Keywords</span></span>|<span data-ttu-id="46b48-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="46b48-107">WFRuntime</span></span>|  
|<span data-ttu-id="46b48-108">層級</span><span class="sxs-lookup"><span data-stu-id="46b48-108">Level</span></span>|<span data-ttu-id="46b48-109">資訊</span><span class="sxs-lookup"><span data-stu-id="46b48-109">Information</span></span>|  
|<span data-ttu-id="46b48-110">通道</span><span class="sxs-lookup"><span data-stu-id="46b48-110">Channel</span></span>|<span data-ttu-id="46b48-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="46b48-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="46b48-112">描述</span><span class="sxs-lookup"><span data-stu-id="46b48-112">Description</span></span>  
 <span data-ttu-id="46b48-113">表示工作流程執行個體已中止，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="46b48-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="46b48-114">訊息</span><span class="sxs-lookup"><span data-stu-id="46b48-114">Message</span></span>  
 <span data-ttu-id="46b48-115">WorkflowInstance Id：'%1' 已中止，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="46b48-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="46b48-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="46b48-116">Details</span></span>  
  
|<span data-ttu-id="46b48-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="46b48-117">Data Item Name</span></span>|<span data-ttu-id="46b48-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="46b48-118">Data Item Type</span></span>|<span data-ttu-id="46b48-119">描述</span><span class="sxs-lookup"><span data-stu-id="46b48-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="46b48-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="46b48-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="46b48-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="46b48-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="46b48-122">例外狀況</span><span class="sxs-lookup"><span data-stu-id="46b48-122">Exception</span></span>|`xs:string`|<span data-ttu-id="46b48-123">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="46b48-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="46b48-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="46b48-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="46b48-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="46b48-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
