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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42d22a7187adc712c0f236111cecac89dd59e2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="0fdf1-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="0fdf1-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="0fdf1-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0fdf1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0fdf1-104">ID</span><span class="sxs-lookup"><span data-stu-id="0fdf1-104">ID</span></span>|<span data-ttu-id="0fdf1-105">1005</span><span class="sxs-lookup"><span data-stu-id="0fdf1-105">1005</span></span>|  
|<span data-ttu-id="0fdf1-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0fdf1-106">Keywords</span></span>|<span data-ttu-id="0fdf1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0fdf1-107">WFRuntime</span></span>|  
|<span data-ttu-id="0fdf1-108">層級</span><span class="sxs-lookup"><span data-stu-id="0fdf1-108">Level</span></span>|<span data-ttu-id="0fdf1-109">資訊</span><span class="sxs-lookup"><span data-stu-id="0fdf1-109">Information</span></span>|  
|<span data-ttu-id="0fdf1-110">通道</span><span class="sxs-lookup"><span data-stu-id="0fdf1-110">Channel</span></span>|<span data-ttu-id="0fdf1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0fdf1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0fdf1-112">描述</span><span class="sxs-lookup"><span data-stu-id="0fdf1-112">Description</span></span>  
 <span data-ttu-id="0fdf1-113">表示工作流程應用程式已閒置。</span><span class="sxs-lookup"><span data-stu-id="0fdf1-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0fdf1-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0fdf1-114">Message</span></span>  
 <span data-ttu-id="0fdf1-115">WorkflowApplication Id：'%1' 閒置。</span><span class="sxs-lookup"><span data-stu-id="0fdf1-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0fdf1-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0fdf1-116">Details</span></span>  
  
|<span data-ttu-id="0fdf1-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0fdf1-117">Data Item Name</span></span>|<span data-ttu-id="0fdf1-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0fdf1-118">Data Item Type</span></span>|<span data-ttu-id="0fdf1-119">描述</span><span class="sxs-lookup"><span data-stu-id="0fdf1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0fdf1-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="0fdf1-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="0fdf1-121">工作流程應用程式 ID</span><span class="sxs-lookup"><span data-stu-id="0fdf1-121">The workflow application id</span></span>|  
|<span data-ttu-id="0fdf1-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0fdf1-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0fdf1-123">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0fdf1-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
