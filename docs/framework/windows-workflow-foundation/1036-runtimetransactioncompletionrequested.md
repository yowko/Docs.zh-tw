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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f497d777221a98b38603b2ced29342651b1020b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="bd50b-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="bd50b-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="bd50b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="bd50b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd50b-104">ID</span><span class="sxs-lookup"><span data-stu-id="bd50b-104">ID</span></span>|<span data-ttu-id="bd50b-105">1036</span><span class="sxs-lookup"><span data-stu-id="bd50b-105">1036</span></span>|  
|<span data-ttu-id="bd50b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="bd50b-106">Keywords</span></span>|<span data-ttu-id="bd50b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bd50b-107">WFRuntime</span></span>|  
|<span data-ttu-id="bd50b-108">層級</span><span class="sxs-lookup"><span data-stu-id="bd50b-108">Level</span></span>|<span data-ttu-id="bd50b-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="bd50b-109">Verbose</span></span>|  
|<span data-ttu-id="bd50b-110">通道</span><span class="sxs-lookup"><span data-stu-id="bd50b-110">Channel</span></span>|<span data-ttu-id="bd50b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bd50b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bd50b-112">描述</span><span class="sxs-lookup"><span data-stu-id="bd50b-112">Description</span></span>  
 <span data-ttu-id="bd50b-113">表示活動已排程執行階段交易的完成。</span><span class="sxs-lookup"><span data-stu-id="bd50b-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bd50b-114">訊息</span><span class="sxs-lookup"><span data-stu-id="bd50b-114">Message</span></span>  
 <span data-ttu-id="bd50b-115">活動 '%1'、DisplayName：'%2'、InstanceId：'%3' 已排程完成執行階段交易。</span><span class="sxs-lookup"><span data-stu-id="bd50b-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bd50b-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bd50b-116">Details</span></span>  
  
|<span data-ttu-id="bd50b-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="bd50b-117">Data Item Name</span></span>|<span data-ttu-id="bd50b-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="bd50b-118">Data Item Type</span></span>|<span data-ttu-id="bd50b-119">描述</span><span class="sxs-lookup"><span data-stu-id="bd50b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bd50b-120">活動</span><span class="sxs-lookup"><span data-stu-id="bd50b-120">Activity</span></span>|<span data-ttu-id="bd50b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bd50b-121">xs:string</span></span>|<span data-ttu-id="bd50b-122">活動的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="bd50b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="bd50b-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bd50b-123">DisplayName</span></span>|<span data-ttu-id="bd50b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bd50b-124">xs:string</span></span>|<span data-ttu-id="bd50b-125">活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="bd50b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="bd50b-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bd50b-126">InstanceId</span></span>|<span data-ttu-id="bd50b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bd50b-127">xs:string</span></span>|<span data-ttu-id="bd50b-128">活動的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="bd50b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bd50b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bd50b-129">AppDomain</span></span>|<span data-ttu-id="bd50b-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="bd50b-130">xs:string</span></span>|<span data-ttu-id="bd50b-131">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="bd50b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
