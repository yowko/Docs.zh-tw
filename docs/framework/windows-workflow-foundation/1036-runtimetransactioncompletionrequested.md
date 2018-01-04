---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91fcac0bdfe885051941d100f1a2c131c547f19e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="d3d71-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="d3d71-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="d3d71-103">屬性</span><span class="sxs-lookup"><span data-stu-id="d3d71-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3d71-104">ID</span><span class="sxs-lookup"><span data-stu-id="d3d71-104">ID</span></span>|<span data-ttu-id="d3d71-105">1036</span><span class="sxs-lookup"><span data-stu-id="d3d71-105">1036</span></span>|  
|<span data-ttu-id="d3d71-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d3d71-106">Keywords</span></span>|<span data-ttu-id="d3d71-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d3d71-107">WFRuntime</span></span>|  
|<span data-ttu-id="d3d71-108">層級</span><span class="sxs-lookup"><span data-stu-id="d3d71-108">Level</span></span>|<span data-ttu-id="d3d71-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="d3d71-109">Verbose</span></span>|  
|<span data-ttu-id="d3d71-110">通道</span><span class="sxs-lookup"><span data-stu-id="d3d71-110">Channel</span></span>|<span data-ttu-id="d3d71-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d3d71-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d3d71-112">描述</span><span class="sxs-lookup"><span data-stu-id="d3d71-112">Description</span></span>  
 <span data-ttu-id="d3d71-113">表示活動已排程執行階段交易的完成。</span><span class="sxs-lookup"><span data-stu-id="d3d71-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d3d71-114">訊息</span><span class="sxs-lookup"><span data-stu-id="d3d71-114">Message</span></span>  
 <span data-ttu-id="d3d71-115">活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程完成執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="d3d71-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d3d71-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d3d71-116">Details</span></span>  
  
|<span data-ttu-id="d3d71-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="d3d71-117">Data Item Name</span></span>|<span data-ttu-id="d3d71-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="d3d71-118">Data Item Type</span></span>|<span data-ttu-id="d3d71-119">描述</span><span class="sxs-lookup"><span data-stu-id="d3d71-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d3d71-120">活動</span><span class="sxs-lookup"><span data-stu-id="d3d71-120">Activity</span></span>|<span data-ttu-id="d3d71-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d3d71-121">xs:string</span></span>|<span data-ttu-id="d3d71-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d3d71-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d3d71-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d3d71-123">DisplayName</span></span>|<span data-ttu-id="d3d71-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d3d71-124">xs:string</span></span>|<span data-ttu-id="d3d71-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="d3d71-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d3d71-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="d3d71-126">InstanceId</span></span>|<span data-ttu-id="d3d71-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="d3d71-127">xs:string</span></span>|<span data-ttu-id="d3d71-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="d3d71-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d3d71-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d3d71-129">AppDomain</span></span>|<span data-ttu-id="d3d71-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="d3d71-130">xs:string</span></span>|<span data-ttu-id="d3d71-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d3d71-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
