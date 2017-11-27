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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 297b3ad9a677d28d12d1b00fdaeec8ec94842263
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="3b494-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="3b494-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="3b494-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3b494-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3b494-104">ID</span><span class="sxs-lookup"><span data-stu-id="3b494-104">ID</span></span>|<span data-ttu-id="3b494-105">1008</span><span class="sxs-lookup"><span data-stu-id="3b494-105">1008</span></span>|  
|<span data-ttu-id="3b494-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3b494-106">Keywords</span></span>|<span data-ttu-id="3b494-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3b494-107">WFRuntime</span></span>|  
|<span data-ttu-id="3b494-108">層級</span><span class="sxs-lookup"><span data-stu-id="3b494-108">Level</span></span>|<span data-ttu-id="3b494-109">資訊</span><span class="sxs-lookup"><span data-stu-id="3b494-109">Information</span></span>|  
|<span data-ttu-id="3b494-110">通道</span><span class="sxs-lookup"><span data-stu-id="3b494-110">Channel</span></span>|<span data-ttu-id="3b494-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3b494-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3b494-112">描述</span><span class="sxs-lookup"><span data-stu-id="3b494-112">Description</span></span>  
 <span data-ttu-id="3b494-113">表示工作流程應用程式已卸載。</span><span class="sxs-lookup"><span data-stu-id="3b494-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3b494-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3b494-114">Message</span></span>  
 <span data-ttu-id="3b494-115">WorkflowInstance Id：'%1' 已卸載。</span><span class="sxs-lookup"><span data-stu-id="3b494-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3b494-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3b494-116">Details</span></span>  
  
|<span data-ttu-id="3b494-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3b494-117">Data Item Name</span></span>|<span data-ttu-id="3b494-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3b494-118">Data Item Type</span></span>|<span data-ttu-id="3b494-119">描述</span><span class="sxs-lookup"><span data-stu-id="3b494-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3b494-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3b494-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="3b494-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="3b494-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="3b494-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3b494-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3b494-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3b494-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
