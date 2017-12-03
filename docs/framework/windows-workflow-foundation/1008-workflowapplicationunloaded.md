---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dedb1dd389e2308ea8f70d71f057d17a45172517
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="a15db-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="a15db-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="a15db-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a15db-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a15db-104">ID</span><span class="sxs-lookup"><span data-stu-id="a15db-104">ID</span></span>|<span data-ttu-id="a15db-105">1008</span><span class="sxs-lookup"><span data-stu-id="a15db-105">1008</span></span>|  
|<span data-ttu-id="a15db-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a15db-106">Keywords</span></span>|<span data-ttu-id="a15db-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a15db-107">WFRuntime</span></span>|  
|<span data-ttu-id="a15db-108">層級</span><span class="sxs-lookup"><span data-stu-id="a15db-108">Level</span></span>|<span data-ttu-id="a15db-109">資訊</span><span class="sxs-lookup"><span data-stu-id="a15db-109">Information</span></span>|  
|<span data-ttu-id="a15db-110">通道</span><span class="sxs-lookup"><span data-stu-id="a15db-110">Channel</span></span>|<span data-ttu-id="a15db-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a15db-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a15db-112">描述</span><span class="sxs-lookup"><span data-stu-id="a15db-112">Description</span></span>  
 <span data-ttu-id="a15db-113">表示工作流程應用程式已卸載。</span><span class="sxs-lookup"><span data-stu-id="a15db-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a15db-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a15db-114">Message</span></span>  
 <span data-ttu-id="a15db-115">WorkflowInstance Id：'%1' 已卸載。</span><span class="sxs-lookup"><span data-stu-id="a15db-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a15db-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a15db-116">Details</span></span>  
  
|<span data-ttu-id="a15db-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a15db-117">Data Item Name</span></span>|<span data-ttu-id="a15db-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a15db-118">Data Item Type</span></span>|<span data-ttu-id="a15db-119">描述</span><span class="sxs-lookup"><span data-stu-id="a15db-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a15db-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="a15db-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="a15db-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="a15db-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="a15db-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a15db-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a15db-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a15db-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
