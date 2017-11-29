---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a62a8448319e7b07a3ea302f00f2fa269bf654ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="05418-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="05418-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="05418-103">屬性</span><span class="sxs-lookup"><span data-stu-id="05418-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05418-104">ID</span><span class="sxs-lookup"><span data-stu-id="05418-104">ID</span></span>|<span data-ttu-id="05418-105">1001</span><span class="sxs-lookup"><span data-stu-id="05418-105">1001</span></span>|  
|<span data-ttu-id="05418-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="05418-106">Keywords</span></span>|<span data-ttu-id="05418-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="05418-107">WFRuntime</span></span>|  
|<span data-ttu-id="05418-108">層級</span><span class="sxs-lookup"><span data-stu-id="05418-108">Level</span></span>|<span data-ttu-id="05418-109">資訊</span><span class="sxs-lookup"><span data-stu-id="05418-109">Information</span></span>|  
|<span data-ttu-id="05418-110">通道</span><span class="sxs-lookup"><span data-stu-id="05418-110">Channel</span></span>|<span data-ttu-id="05418-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="05418-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="05418-112">描述</span><span class="sxs-lookup"><span data-stu-id="05418-112">Description</span></span>  
 <span data-ttu-id="05418-113">表示工作流程應用程式已在 Closed 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="05418-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="05418-114">訊息</span><span class="sxs-lookup"><span data-stu-id="05418-114">Message</span></span>  
 <span data-ttu-id="05418-115">WorkflowInstance Id：'%1' 已在 Closed 狀態中完成。</span><span class="sxs-lookup"><span data-stu-id="05418-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="05418-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="05418-116">Details</span></span>  
  
|<span data-ttu-id="05418-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="05418-117">Data Item Name</span></span>|<span data-ttu-id="05418-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="05418-118">Data Item Type</span></span>|<span data-ttu-id="05418-119">描述</span><span class="sxs-lookup"><span data-stu-id="05418-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="05418-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="05418-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="05418-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="05418-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="05418-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="05418-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="05418-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="05418-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
